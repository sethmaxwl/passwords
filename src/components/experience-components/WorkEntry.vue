<template lang='pug'>
  v-card.pt-2.pb-5(color='#fbf7f5', flat='', tile='')
    v-card-title.card-header {{ work.title }}
    v-card-subtitle.card-subheader.pt-0
      | {{ work.company }}
      | ({{ work.dates.startDate }} - {{ work.dates.endDate }})
    v-card-text.card-description.pb-0 {{ work.overview }}
    v-card-text.card-subheader Skills
    template(v-for='skill in work.skills')
      v-row.skills.pl-6.pb-2.d-block(align='center')
        span.card-description
          v-icon mdi-arrow-right
        |  {{ skill }}
    template(v-if='work.links')
      v-card-text.card-subheader Relevant Links
      template(v-for='link in work.links')
        v-row.skills.pl-7.pb-2.d-block(align='center')
          span.card-description {{ link.description }}
            a.card-link.ml-1(:href='link.link',
              target='blank', ref='noopener noreferrer')
              v-icon.pb-1 mdi-open-in-new

</template>

<script>
export default {
  name: 'WorkEntry',
  props: {
    work: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss">
.skills {
  padding-right: 5%;
}

.skills, .card-description {
    color: rgba(0,0,0,.6);
}

.card-subheader {
  color: rgba(0,0,0,.7) !important;
}
</style>
