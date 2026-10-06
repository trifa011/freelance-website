<template>
  <v-app>
    <!-- Navigation Bar -->
    <v-app-bar color="primary" dark>
      <v-app-bar-title>ProServices</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn text @click="scrollTo('services')">Services</v-btn>
      <v-btn text @click="scrollTo('pricing')">Pricing</v-btn>
      <v-btn text @click="scrollTo('contact')">Contact</v-btn>
    </v-app-bar>

    <v-main>
      <!-- Hero Section -->
      <div style="background: linear-gradient(135deg, #2563eb 0%, #1e40af 100%); color: white; padding: 100px 20px; text-align: center;">
        <h1 style="font-size: 3rem; margin-bottom: 20px;">Transform Your Ideas into Reality</h1>
        <p style="font-size: 1.2rem; margin-bottom: 30px;">Professional web design, development, and consulting</p>
        <v-btn color="white" text-color="primary" size="large" @click="scrollTo('services')">Start Your Project</v-btn>
      </div>

      <!-- Services Section -->
      <div id="services" style="padding: 80px 20px;">
        <v-container>
          <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 50px;">Our Services</h2>
          <v-row>
            <v-col cols="12" md="6" lg="4" v-for="service in services" :key="service.id">
              <v-card elevation="2">
                <v-card-text>
                  <div style="font-size: 3rem; margin-bottom: 20px;">{{ service.icon }}</div>
                  <h3 style="font-size: 1.25rem; font-weight: bold;">{{ service.title }}</h3>
                  <p style="color: #666;">{{ service.description }}</p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </div>

      <!-- Pricing Section -->
      <div id="pricing" style="padding: 80px 20px; background: #f5f5f5;">
        <v-container>
          <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 50px;">Pricing Plans</h2>
          <v-row>
            <v-col cols="12" md="4" v-for="plan in plans" :key="plan.id">
              <v-card>
                <v-card-text style="text-align: center; padding: 30px;">
                  <h3 style="font-size: 1.5rem;">{{ plan.name }}</h3>
                  <p style="font-size: 2rem; color: #2563eb; font-weight: bold; margin: 15px 0;">{{ plan.price }}</p>
                  <p style="color: #666; margin-bottom: 20px;">{{ plan.description }}</p>
                  <v-btn color="primary" block>Get Started</v-btn>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </div>

      <!-- Contact Section -->
      <div id="contact" style="padding: 80px 20px;">
        <v-container>
          <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 50px;">Get in Touch</h2>
          <v-row justify="center">
            <v-col cols="12" md="6">
              <v-text-field v-model="form.name" label="Your Name" outlined></v-text-field>
              <v-text-field v-model="form.email" label="Your Email" outlined type="email"></v-text-field>
              <v-textarea v-model="form.message" label="Your Message" outlined rows="5"></v-textarea>
              <v-btn color="primary" block size="large" @click="sendMessage">Send Message</v-btn>
            </v-col>
          </v-row>
        </v-container>
      </div>
    </v-main>

    <!-- Footer -->
    <footer style="background: #1e293b; color: white; padding: 40px 20px; text-align: center;">
      <p style="margin: 0;">&copy; 2024 ProServices. All rights reserved.</p>
    </footer>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'

const services = ref([
  { id: 1, icon: '🎨', title: 'Web Design', description: 'Beautiful, user-friendly designs that captivate and convert.' },
  { id: 2, icon: '⚙️', title: 'Web Development', description: 'Robust, scalable applications built with modern technologies.' },
  { id: 3, icon: '📱', title: 'Mobile Apps', description: 'Native and cross-platform mobile apps for any device.' },
  { id: 4, icon: '📊', title: 'Consulting', description: 'Strategic guidance for your digital transformation.' },
  { id: 5, icon: '🔧', title: 'Maintenance', description: 'Ongoing support and maintenance for your applications.' },
  { id: 6, icon: '🚀', title: 'Optimization', description: 'Speed up your applications and improve performance.' },
])

const plans = ref([
  { id: 1, name: 'Starter', price: '$999', description: 'Perfect for small projects' },
  { id: 2, name: 'Professional', price: '$2,999', description: 'For growing businesses' },
  { id: 3, name: 'Enterprise', price: '$9,999', description: 'For large-scale projects' },
])

const form = ref({
  name: '',
  email: '',
  message: '',
})

const scrollTo = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const sendMessage = () => {
  if (form.value.name && form.value.email && form.value.message) {
    alert('Message sent! We will contact you soon.')
    form.value = { name: '', email: '', message: '' }
  } else {
    alert('Please fill all fields')
  }
}
</script>

<style scoped>
</style>