---
title: "rtorrent: how to setup upload limit for each file?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by uarale on 2008-12-10
okay, now i'm very happy with rtorrent, it's very excellent in its kind, lightweight, fast and reliable. except one: i didn't find a way to set up the upload limit for a specific file. as far as i know, rtorrent only lets me set up the download and upload limits globally.

just to be curious, is there any way to solve this problem?

---

### Post by hyper_ch on 2008-12-10
there's an individual throttling patch... what version of rtorrent/libtorrent do you use?

---

### Post by uarale on 2008-12-10
> **hyper_ch said:**
> there's an individual throttling patch... what version of rtorrent/libtorrent do you use?

I'm using rtorrent 0.8.2 / libtorrent 0.12.2

where should i find the patch?

---

### Post by hyper_ch on 2008-12-10
well, you will have to do a source install and patch the sources before compiling. I made howtos on that (7.10 and 8.04 but also works for 8.10).$

The patch is here: [http://ttdpatch.net/~jdrexler/throttles.diff](http://ttdpatch.net/~jdrexler/throttles.diff)

---

