<template>
<nav class="navbar">
    <div class="wrapper-nav container">
        <div class="logo"><router-link tag="a" :to="{name: 'Home'}">Pizzeriery</router-link></div>
        <input type="radio" name="slider" id="menu-btn">
        <input type="radio" name="slider" id="close-btn">
        <ul class="nav-links">
            <label for="close-btn" class="navbar-btn close-btn">
				<i class='bx bx-x'></i>
			</label>
            <!-- <li>
                <a href="#" class="desktop-item">Dropdown Menu</a>
                <input type="checkbox" id="showDrop">
                <label for="showDrop" class="mobile-item">Dropdown Menu</label>
                <ul class="drop-menu">
                    <li><a href="#">Drop menu 1</a></li>
                    <li><a href="#">Drop menu 2</a></li>
                    <li><a href="#">Drop menu 3</a></li>
                    <li><a href="#">Drop menu 4</a></li>
                </ul>
            </li>
            <li>
                <a href="#" class="desktop-item">Mega Menu</a>
                <input type="checkbox" id="showMega">
                <label for="showMega" class="mobile-item">Mega Menu</label>
                <div class="mega-box">
                    <div class="content">
                        <div class="row">
                            <img :src="imgBanner" alt="">
                        </div>
                        <div class="row">
                            <header>Design Services</header>
                            <ul class="mega-links">
                                <li><a href="#">Graphics</a></li>
                                <li><a href="#">Vectors</a></li>
                                <li><a href="#">Business cards</a></li>
                                <li><a href="#">Custom logo</a></li>
                            </ul>
                        </div>
                        <div class="row">
                            <header>Email Services</header>
                            <ul class="mega-links">
                                <li><a href="#">Personal Email</a></li>
                                <li><a href="#">Business Email</a></li>
                                <li><a href="#">Mobile Email</a></li>
                                <li><a href="#">Web Marketing</a></li>
                            </ul>
                        </div>
                        <div class="row">
                            <header>Security services</header>
                            <ul class="mega-links">
                                <li><a href="#">Site Seal</a></li>
                                <li><a href="#">VPS Hosting</a></li>
                                <li><a href="#">Privacy Seal</a></li>
                                <li><a href="#">Website design</a></li>
                            </ul>
                        </div>
                    </div>
                </div>
            </li> -->
            <li><router-link tag="a" :to="{name: 'Products'}">Products</router-link></li>
            <li><router-link tag="a" :to="{name: 'Cart'}">Cart</router-link></li>
            <li v-if="!isAuthenticated"><router-link tag="a" :to="{name: 'Login'}">Login</router-link></li>
            <li v-if="!isAuthenticated"><router-link tag="a" :to="{name: 'Register'}">Register</router-link></li>
            <li v-if="isAuthenticated"><a href="#" @click="logout(AUTH_LOGOUT)">Logout</a></li>
        </ul>
        <label for="menu-btn" class="navbar-btn menu-btn">
			<i class='bx bx-menu-alt-right'></i>
		</label>
    </div>
</nav>
</template>

<script>
import { mapActions, mapGetters } from 'vuex';
import imgBannerMenu from '../../img/banner-meta-menu.jpg';
export default {
    data() {
        return {
            imgBanner: imgBannerMenu,
        }
    },
    computed: {
        ...mapGetters(['isAuthenticated']),
    },
    methods: {
        ...mapActions(['AUTH_LOGOUT']),
        logout (func) {
            func().then(() => this.$router.push({ name: 'Home' }));
        }
    },
    created(){
    },
    beforeUpdate(){
        console.log(this.isAuthenticated);
    }
}
</script>

<style>

</style>
