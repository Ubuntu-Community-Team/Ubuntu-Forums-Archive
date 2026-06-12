---
title: "Pictures and Rhythmbox"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2010-06-10
**Background:**
So, I've used easytag to add album art and change the album name for some mp3s. 

**Issue:**
The problem is that when I right click on the mp3 and view the properties, it doesn't show the new, updated album name. Moreover, when I add these mp3s to my rhythmbox library and then transfer them to my ipod, the new album names do not appear in either the library or on the ipod. The album artwork also doesn't show.

I know that easytag works because it is able to successfully change the album artwork and name for some songs that is shown in the properties menu in nautilus and on my ipod.

All of the mentioned files are mp3s.

**Question:**
What do I need to do so the updated album name appears on the properties menu and rhythmbox and the album art shows on my ipod?

**Possible Solution**
I was thinking that it might be the way the album name is cached. Some mp3s have their album names update correctly while one set from one particular album does not. Another possible cause of the problem is the type of tag that it uses. The type may prevent not work well with easytag. 




**More Info:**
I have one set of mp3s from one album where neither the album name changes nor the cover art changes. I also have another set of mp3s from multiple, different albums where the cover art doesn't change after using easytag.





So how do I fix this and does anyone need anymore information?

---

### Post by Sup3r3g0 on 2010-06-10
bump

---

### Post by kiddykoff on 2010-06-10
I've never run easytag. run this

sudo apt-get install picard

check out their site for more info.

[www.Musicbrainz.org](www.Musicbrainz.org)

---

### Post by lolobu on 2010-08-08
The default setup for easytag is to use tags ID3v2.4 which is nto supported by all players. You can try to switch to ID3v2.3 in the preferences (ID3 tags tab)

---

### Post by Sup3r3g0 on 2010-08-12
Thanks. I'll try switching to ID3v2.3 and see if that also lets me view album art on my IPod Touch.

---

