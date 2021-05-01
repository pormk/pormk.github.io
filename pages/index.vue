<template>
  <div>
    <b-row>
      <b-col v-for="post in posts" :key="post.slug">
        <b-card
          :title="post.title"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 20rem"
          class="mb-2"
        >
          <b-card-text>
            {{ post.description }}
          </b-card-text>

          <b-button
            :to="{ name: 'posts-slug', params: { slug: post.slug } }"
            variant="primary"
            >Go somewhere</b-button
          >
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const propsData = await $content("posts").fetch();
    return {
      posts: propsData,
    };
  },
  mounted() {
    // this.posts;
    console.log("THIS.POSTS", this.posts);
  },
};
</script>

<style></style>
