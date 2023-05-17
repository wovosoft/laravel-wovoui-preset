<script setup lang="ts">
import DropdownLink from '@/Components/DropdownLink.vue';
import {Collapse, Nav, Navbar, NavItemDropdown} from "@wovosoft/wovoui";
import {Link} from "@inertiajs/vue3";
import NavItemLink from "@/Components/NavItemLink.vue";
import route from "ziggy-js";
</script>

<template>
    <Navbar variant="dark" bg-variant="dark" class="py-0">
        <template #brand>
            <Link :href="route('dashboard')" class="navbar-brand">
                Navbar Brand
            </Link>
        </template>
        <template #default="{collapsed}">
            <Collapse is-nav :visible="collapsed">
                <Nav class="me-auto" navs>
                    <NavItemLink href="dashboard">
                        Dashboard
                    </NavItemLink>
                    <NavItemDropdown :text="$page.props.auth?.user?.name">
                        <DropdownLink :href="route('profile.edit')">Profile</DropdownLink>
                        <DropdownLink :href="route('logout')" method="post" as="button">
                            Log Out
                        </DropdownLink>
                    </NavItemDropdown>
                </Nav>
                <Nav navs>
                    <NavItemDropdown :text="$page.props.auth?.user?.name">
                        <DropdownLink :href="route('profile.edit')">Profile</DropdownLink>
                        <DropdownLink :href="route('logout')" method="post" as="button">
                            Log Out
                        </DropdownLink>
                    </NavItemDropdown>
                </Nav>
            </Collapse>
        </template>
    </Navbar>
    <slot/>
</template>
