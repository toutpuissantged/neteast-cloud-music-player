<template>
  <v-card
    class="mx-auto mb-3"
    color="secondary darken-1"
    :to="{ path: '/album', query: { id: id }}"
    ripple
  >
    <v-list-item class="px-2">
      <v-list-item-avatar size="48">
        <v-img
          :src="ArtistPicUrl + '?param=50y50'"
        ></v-img>
      </v-list-item-avatar>
      <v-list-item-content class="py-0">
        <v-list-item-title class="headline">{{name}}</v-list-item-title>
        <v-list-item-subtitle>{{artistName}}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>

    <v-img
      :src="picUrl + '?param=400y400'"
      height="194"
    ></v-img>

    <v-card-text class="py-2 px-5">
      <v-row class="align-center">

      <div>
        {{company}} {{subType?' - ':''}} {{subType}}
      </div>
      <v-spacer/>
      <v-chip
        small=""
      >
        {{type}}
      </v-chip>
      </v-row>

    </v-card-text>

    <v-card-actions class="py-0 pb-2">
      <v-btn
        v-if="!fromAlbumDetailPage"
        block
        text
        color="primary"
        :to="{ path: '/album', query: { id: id }}"
      >
        This Album has <span class="inline-block mx-2 font-weight-bold title">{{size}}</span> Song{{size>1?'s':''}}
      </v-btn>
      <v-btn
        v-else
        block
        color="primary"
        rounded
        @click.prevent.stop="$emit('setMusic')"
      >
        Play All <span class="inline-block mx-2 font-weight-bold title">{{size}}</span> Songs
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    id: {
      type: Number
    },
    name: {
      type: String
    },
    artistName: {
      type: String
    },
    picUrl: {
      type: String
    },
    ArtistPicUrl: {
      type: String
    },
    company: {
      type: String
    },
    subType: {
      type: String
    },
    type: {
      type: String
    },
    size: {
      type: Number
    },
    paid: {
      type: Boolean,
      default: false
    },
    fromAlbumDetailPage: {
      type: Boolean,
      default: false
    }
  }
}
</script>
