---
title: "Transmission seeding w/o downloading?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by kansasnoob on 2009-01-24
OK, this is my nOObishness showing, but I always (if possible) use torrents for downloading operating systems. And I leave that torrent open to seed after I'm done recieving my DL!

In fact I quite often start a download at bedtime and then it can seed all night long. And I have a fairly fast connection: about 2500kb/s DL & 500kb/s UL.

So here's my stupid noob question:

I'd like to help obscure open source projects like Crunchbang and Opengeu by seeding all night long! But I can't for the life of me figure out how to start Transmission to seed only!

My machine is incredibly energy efficient, so seeding all night is like running a 10 watt light bulb or less!

I'd appreciate some advice.

---

### Post by ugm6hr on 2009-01-24
You don't need to set anything.

If you already have the file, when opening the .torrent file, just select the same location / directory (where the completed download is) to "download" it, and it will seed.

Initially, it checks the integrity of the previously downloaded file, then completes the download.  Obviously, there is nothing to download once it is already completed - so it will just seed.

---

### Post by kansasnoob on 2009-01-24
> **ugm6hr said:**
> You don't need to set anything.

If you already have the file, when opening the .torrent file, just select the same location / directory (where the completed download is) to "download" it, and it will seed.

Initially, it checks the integrity of the previously downloaded file, then completes the download.  Obviously, there is nothing to download once it is already completed - so it will just seed.

Thanks, before I'd even read your answer I'd figured out what my "hang-up" was.

I was downloading these torrents to my Desktop, then checking the md5sum, then moving to my downloads file!

When I'd restart the torrent it would look at "Desktop" and start a new download!

Just stupid really! But then sometimes I am stupid!

Thank you anyway! Come to think of it, you've helped me a lot!

Like from day #1!

---

### Post by ugm6hr on 2009-01-24
Have to say, I only use Transmission on my Dell Mini; I prefer other apps really.

But most others allow you to automatically move "completed" downloads to a different directory.  Wine + Utorrent certainly does, and I believe (from memory) Ktorrent and Deluge do too.

You might like to look into it.

---

