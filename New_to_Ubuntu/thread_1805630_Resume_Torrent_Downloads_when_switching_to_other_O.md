---
title: "Resume Torrent Downloads when switching to other OS."
date: 2011-07-16
forum: New to Ubuntu
---

### Post by kranthi.doss on 2011-07-16
Hello ,
        I have a dual boot laptop with windows xp prof. and ubuntu 11.04 running just fine. I use windows for gaming and other stuff that i can't do on ubuntu. I use Transmission in ubuntu and uTorrent on windows xp as my Torrent clients. I have a shared NTFS partition that i use for torrents. I queue up all the torrents in transmission. But when login to XP doing other stuff like gaming, is there a way to resume the incomplete downloads of Transmission (I added in ubuntu earlier)?

       I tried but that doesnt work with utorrent and transmission. So i installed the same client Deluge, in both OS. Still im not able to resume the download when i switch OS. If there is any other way or if im doing it the wrong way plz guide me.

---

### Post by TheMatej on 2011-07-16
you just have to make one folder for torrents (/whatever/torrents/) and one for data (/whatever/data/), then set utorrent and transmission to automaticly add torrents from /whatever/torrents/ and save data in /whatever/data/. So, when you add torrent in transmission, torrent will be moved to /whatever/torrents/ and when you'll open utorrent it'll add torrents and check in /whatever/data what is already downloaded

Note: you also have to set transmission and uTorrent to save torrents /whatever/torrents

---

### Post by akand074 on 2011-07-16
> **TheMatej said:**
> you just have to make one folder for torrents (/whatever/torrents/) and one for data (/whatever/data/), then set utorrent and transmission to automaticly add torrents from /whatever/torrents/ and save data in /whatever/data/. So, when you add torrent in transmission, torrent will be moved to /whatever/torrents/ and when you'll open utorrent it'll add torrents and check in /whatever/data what is already downloaded

Note: you also have to set transmission and uTorrent to save torrents /whatever/torrents

Yup exactly. Just set both applications to point to the same directories and they'll save and read torrents from the same place.

---

### Post by kranthi.doss on 2011-07-16
I have already done what you suggested me but when i switch the OS, the download doesn't resume. It starts from first again. Neither clients are able to resume the downloads. They only resume from where they have downloaded. Did this work practically? I mean do someone use this technique?? If so what clients are you using.

---

### Post by amjjawad on 2011-07-16
> **kranthi.doss said:**
> I have already done what you suggested me but when i switch the OS, the download doesn't resume. It starts from first again. Neither clients are able to resume the downloads. They only resume from where they have downloaded. Did this work practically? I mean do someone use this technique?? If so what clients are you using.

If I were you, I would save my time finding a solution for this and just wait until the download is finished. That's what I would do :)

---

### Post by TheMatej on 2011-07-16
> **kranthi.doss said:**
> I have already done what you suggested me but when i switch the OS, the download doesn't resume. It starts from first again. Neither clients are able to resume the downloads. They only resume from where they have downloaded. Did this work practically? I mean do someone use this technique?? If so what clients are you using.
then you have to force re-check ...

---

### Post by kranthi.doss on 2011-07-18
ThanQ for the suggestion but I did force-recheck mate.  I will try and see if anything is wrong with my settings.

@amjjawad - If you think a little bit u wud understand that i was trying not to waste download time when i switch OS. I don't think a newbie searching for the forums wud like it when he finds answers like yours!

---

### Post by amjjawad on 2011-07-18
> **kranthi.doss said:**
> ThanQ for the suggestion but I did force-recheck mate.  I will try and see if anything is wrong with my settings.

@amjjawad - If you think a little bit u wud understand that i was trying not to waste download time when i switch OS. I don't think a newbie searching for the forums wud like it when he finds answers like yours!

I'm afraid you missed my point :) please read the post again. That was how I would do and of course you don't have to do the same. Anyway, I'm sorry if my post didn't help. 
Don't be offended please!

---

### Post by kranthi.doss on 2011-07-19
Working fine now. :grin:

I totally forgot about the '.!ut' and '.part' suffixes i use in uTorrent  and Transmission for incomplete downloads. Removed automatically adding  suffixes in the torrent client settings and it is working as needed.

ThanQ for the support.

---

