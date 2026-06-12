---
title: "Network Drive Access Timeout"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by Arlo012 on 2008-11-09
Hey everyone,

I switched to using Ubuntu a little over a year ago, and I just recently installed it on an old dell Latitude D600 that was gathering dust. I setup the wireless and such, and everything has been working fine. Being a laptop, however, there isn't much space to store my music collection. As such, I setup sharing on another computer in the house (a gaming desktop running Windows Vista). I set the folder "Music-Database" on the desktop to be shared, and is accessible on the network (from Ubuntu) under smb://192.168.1.129/Music-Database. The problem, however, comes when trying to play one of these music files. Mid-way through, my music player would stop playing the songs and an error "Network Timeout" appeared. I figured it was just the music player, however in attempting to copy the files to a local folder the same error "Network Timeout" occurs. Any ideas what is causing this timeout?

I am mounting the drive using this command:

sudo mount -t cifs //192.168.1.129/Music-Database /media/Vista-Music -o username=Jeff,password=<private>,iocharset=utf8,file_mode=0777,dir_mode=0777

Many thanks,
Jeff

---

