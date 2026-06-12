---
title: "uShare presents files too messily on my xbox360"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Gaymer on 2009-01-06
I managed to get uShare to work, and I have my Music and Video folders linked to in a special folder that uShare makes available to my Xbox360.

The problem I'm having is that all of my media is mixed together in a messy unstructured manner. (even worst than they appear on my computer)  

I noticed that on my 360 it has tabs for albums/artists/etc.; but all of these tabs list the names of the songs, again and again, but with them only being playable under the 'songs' tab.  I was wondering if it would be possible to re-organize my media so it would be presented correctly...  Probably by emulating Windows Media Player's file-heirarchy.

I think I might be able to figure it out if I knew what folder the windows upnp client uses as it's main folder, and how WMP organizes your media by artists, albums, and genres.  Unfortunately, I don't have a windows PC...  Does anybody think they could get this information for me?

---

### Post by JoshuaRL on 2009-01-06
As far as I can remember, WMP uses the Music\Artist\Album\Song hierarchy.  But are you sure your ID3 tags are good?

On everything I've seen, those are the issue.  From different media players reading stuff wrong to media applications doing the same.  Try Kid3 from the repos and go in to make sure both ID3 V1 and V2 are both correct and agree with each other.  It always seems to work for me.  It's a long process to go through everything manually like that, but it's the only thing that works.

---

### Post by Gaymer on 2009-01-06
> **JoshuaRL said:**
> As far as I can remember, WMP uses the Music\Artist\Album\Song hierarchy.  But are you sure your ID3 tags are good?

On everything I've seen, those are the issue.  From different media players reading stuff wrong to media applications doing the same.  Try Kid3 from the repos and go in to make sure both ID3 V1 and V2 are both correct and agree with each other.  It always seems to work for me.  It's a long process to go through everything manually like that, but it's the only thing that works.

To be honest, when I read your post I had no idea what ID3 tags were, although I did assume it was wear the information about the media was stored.  I looked it up, and it definitely seems like that might be the issue.  I'll check it out!  That would definitely be a lot simpler than making a mock-WMP filestructure.  lol

---

### Post by Gaymer on 2009-01-06
Looking at my media, I'm not sure if this is the problem...  If it were, then some of my media should be organized and displayed correctly by my Xbox 360.  It appears that Microsoft designed their media software for the 360 specifically JUST to work properly with their upnp client.  :/

Looks like I'm back to square one here...  I'll try downloading Microsofts Windows XP client myself, but I doubt it'll even install in Wine.

EDIT: Ugh...  Looks like it's designed to work with Windows Media Player directly, or with Microsoft's Zune media player directly.  I know I can't install WMP, so I'll try Zune.  I don't expect it to work.

---

