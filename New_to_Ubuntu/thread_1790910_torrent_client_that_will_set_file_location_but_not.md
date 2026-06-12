---
title: "torrent client that will set file location but not move anything"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by w_barnes on 2011-06-25
Hi, I'm looking for a torrent client that will allow me to set the location of individual files within a torrent as well as the torrent itself but not actually move anything. Specifically, I need a torrent client that will make no changes whatsoever to the file system until I press start and the torrent begins downloading.

I need to be able to set the file location so that I can reorganize the folder structure of a torrent with many files and to test a torrent to see if the file(s) it contains matches the file(s) I already have by "pointing" the torrent client to file(s) I have then doing a force recheck.

I've been using uTorrent for years in Windows and have gotten used to being able to do these things and installed qBittorrent thinking it would be the same as uTorrent. Unfortunately, qBittorrent will only allow you to move a torrent and not the files in it. Plus, it not only moves the torrent but seems to move everything else in the same folder - including sub folders!

So does anybody know of torrent client that behaves like uTorrent even if it looks completely different? I'll even use a command line program or something based on ncurses if it will allow me to set arbitrary file locations but not actually move anything.

Thanks!

---

### Post by haqking on 2011-06-25
> **w_barnes said:**
> Hi, I'm looking for a torrent client that will allow me to set the location of individual files within a torrent as well as the torrent itself but not actually move anything. Specifically, I need a torrent client that will make no changes whatsoever to the file system until I press start and the torrent begins downloading.

I need to be able to set the file location so that I can reorganize the folder structure of a torrent with many files and to test a torrent to see if the file(s) it contains matches the file(s) I already have by "pointing" the torrent client to file(s) I have then doing a force recheck.

I've been using uTorrent for years in Windows and have gotten used to being able to do these things and installed qBittorrent thinking it would be the same as uTorrent. Unfortunately, qBittorrent will only allow you to move a torrent and not the files in it. Plus, it not only moves the torrent but seems to move everything else in the same folder - including sub folders!

So does anybody know of torrent client that behaves like uTorrent even if it looks completely different? I'll even use a command line program or something based on ncurses if it will allow me to set arbitrary file locations but not actually move anything.

Thanks!

[http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux)

bare in mind this is a alpha release and CLI...you could use WINE and install Utorrent though ?

there are tons of different torrent clients, my suggestions is try them all until you find one you like like transmission,deluge etc etc

---

### Post by w_barnes on 2011-06-25
Thanks haqking, I'll try out the Linux version of uTorrent but as it's alpha it may be too unstable so I'll keep this thread open for other suggestions. I have no issues with CLI; in fact, I prefer it many cases despite using Windows for many years.

---

### Post by w_barnes on 2011-06-26
uTorrent for Linux doesn't seem to be working for me...

I'm getting an infinite loading screen when I go to localhost:8080/gui. After doing some research I found this is a JavaScript issue so I disabled NoScript and restarted Firefox and still no luck.... I guess Firefox 3.6 is not supported but I can't upgrade right now.

So does anyone else have any other suggestions for a torrent client that allows setting the location of individual files without changing the file structure on disk?

---

### Post by w_barnes on 2011-06-26
I was going through the docs for uTorrent Server for Linux and found this way down at the bottom:

>  **Limitations**

 It is not possible to rename or relocate individual files in a torrent job.
 


That pretty much puts the final nail in that coffin! lol

---

