---
title: "Extracting a section from a dvd"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by gj_clt on 2009-04-30
My daughter has lost the source material for a dvd she made of her kids. She wants me to extract a section of this (I haven't asked why). Looking at the forums I see there a number of programmes to copy a dvd but am not clear if I can extract a section. I have not tried copying or ripping a dvd before so any help would be appreciated.

---

### Post by kanikilu on 2009-04-30
Someone may have a better solution than this, but here's probably how I'd tackle this:

1) Use **k9copy**, **dvdbackup** (CLI-only), or similar program to rip the contents of the DVD to your hard-drive. This shoulds like a home-made DVD, if that's the case and it's not encrypted, you can probably just copy-and-paste the files from the DVD to your hard drive (or just skip this step and use the DVD as the source in step 2).

2) Use [Handbrake]("http://handbrake.fr/") to encode the DVD as a video file such as MPEG-4 (mp4).

3) Use a program such as [avidemux]("http://fixounet.free.fr/avidemux/") to cut the desired portion of the video out and export to a new file.

Step 3 is what I haven't personally done myself, but looking at their website, it seems like it should fit the bill

---

