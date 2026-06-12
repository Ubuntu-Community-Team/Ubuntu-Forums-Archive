---
title: "transmissoin is too slow,can i transfer my torrents to another program?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by waxyfresh on 2009-02-24
How could i speed up transmission bit torrent client or move my torents to another program?

---

### Post by x33a on 2009-02-24
yes you can. just import the torrent files in the other program, and point the download location to the existing location (the one made with transmission). the torrents will be checked and the download should continue from where you left.

you can try deluge, ktorrent, vuze, etc.

---

### Post by waxyfresh on 2009-02-24
Where do i find the torrent files? not the ones im downloading but the actual torrent?

---

### Post by Panzor on 2009-02-24
Umm, do you mean the ones you already downloaded, or just a place to torrents in general? I don't think we're allowed to talk about the second thing, so I'll answer the first :P.

The gui way to do it would be to go to Places>>Search for files ; switch it to "file system" then type in ".torrent"

terminal would be using the 'find' util.

---

### Post by adult swim on 2009-02-25
my transmission uses default settings and i believe the .torrent files are saved to /tmp

---

### Post by Rolcol on 2009-02-25
> **waxyfresh said:**
> Where do i find the torrent files? not the ones im downloading but the actual torrent?

They're in ~/.config/transmission/torrents/

---

