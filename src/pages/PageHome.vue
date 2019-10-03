<template>
  <q-page class="prys_homepage flex">
    <div class="row q-pb-xl q-px-lg">
      <div class="col-md-7 hero">
        <h1>Pryspry.com</h1>
        <h3 class="q-pb-lg">I am a Full Stack Developer based in Jakarta, Indonesia</h3>
        <p>Welcome to my site. Please visit my profile or download my resume for your reference.</p><p>You can also browse my writings about poems/ fiction, tech news or review, and other topics.</p>
        <div class="q-pt-lg q-gutter-md">
        <q-btn color="primary" @click="downloadResume()" label="Download Resume" />
        <q-btn color="white" icon="search" text-color="black" label="Browse More" to="/about" />
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import axios from 'axios'

export default {
  meta: {
    title: "Pryspry.com",
    titleTemplate: title => `${title} - Full Stack Developer based in Jakarta`,
    description: { name: 'description', content: 'Pry S full stack developer based in Jakarta, Indonesia' },
    keywords: { name: 'keywords', content: 'Full Stack Developer, Jakarta, Indonesia' },
    equiv: { 'http-equiv': 'Content-Type', content: 'text/html; charset=UTF-8' }
},
  methods: {
          downloadResume() {
              axios({
                    url: 'https://api.pryspry.com/uploads/a0e671cd025841e7b3642ceedcea0716.pdf',
                    method: 'GET',
                    responseType: 'blob',
                }).then((response) => {
                     var fileURL = window.URL.createObjectURL(new Blob([response.data]));
                     var fileLink = document.createElement('a');
   
                     fileLink.href = fileURL;
                     fileLink.setAttribute('download', 'PriyonoSantosa-Resume.pdf');
                     document.body.appendChild(fileLink);
   
                     fileLink.click();
                });
          }
      }
}
</script>

<style>
</style>
