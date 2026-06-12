---
title: "WoW just won't work"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by myolbug on 2009-09-26
I am merely trying to install WoW.  I have tried following two different guides and I can't get it.

WoW trials and even the downloaded full version of Lich King installed no problem in Wine, but I can't get the dang DVD to work.  I am running 9.04

---

### Post by mharrison on 2009-09-30
> **myolbug said:**
> I am merely trying to install WoW.  I have tried following two different guides and I can't get it.

WoW trials and even the downloaded full version of Lich King installed no problem in Wine, but I can't get the dang DVD to work.  I am running 9.04

Have you run Wine Config and clicked on the Drives tab and then clicked on AutoDetect to pick up the DVD mount point?

---

### Post by starcannon on 2009-09-30
> **myolbug said:**
> I am merely trying to install WoW.  I have tried following two different guides and I can't get it.

WoW trials and even the downloaded full version of Lich King installed no problem in Wine, but I can't get the dang DVD to work.  I am running 9.04

My solution for DVD installer problems, is to rip the dvd to the hard drive as an ISO, then I use Gisomount to mount the ISO, and run it that way. So far this method has not let me down.

GL

---

### Post by wobin77 on 2009-10-01
Do it like i did. Just copy the WoW folder from your Vista/XP partition to your linux partition. (after you installed Wine)
Doubleclick WoW.exe

Happy gaming!

---

### Post by myolbug on 2009-10-09
> **wobin77 said:**
> Do it like i did. Just copy the WoW folder from your Vista/XP partition to your linux partition. (after you installed Wine)
Doubleclick WoW.exe

Happy gaming!

I can't.  My PC is 100% Ubuntu!  I have an old XP machine, but the DVD drive won't initialize.

Also, with both Crossover Games 8.0 and Wine I get this message:
Unable to create folder Temporary file or something like that.

---

### Post by sandyd on 2009-10-09
```

wget  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
./winetricks volnum

```

then try again.

---

### Post by myolbug on 2009-10-10
No change

At first I was getting an access denied message, now I am getting the same cannot create temporary folder...

---

### Post by myolbug on 2009-10-11
Any Ideas?  Now I am getting Access Denied.

---

### Post by falconindy on 2009-10-11
> **starcannon said:**
> My solution for DVD installer problems, is to rip the dvd to the hard drive as an ISO, then I use Gisomount to mount the ISO, and run it that way. So far this method has not let me down.

GL
+1 for this idea. If your DVD drive is called /dev/sr0, then you can do this with nothing but built in tools:
```
sudo dd if=/dev/sr0 of=~/lichking.iso bs=1024
sudo mount -t iso9660 ~/lichking.iso /path/to/mount/ -o loop

```
The mount point can be whatever you want. Just make the directory before running that second command.

Personally, I was still pretty new to Linux when I switched over and was still playing World of Warcrack, so I didn't know any better. I just grabbed the downloader and let it run overnight. OH GOD I MISSED AN ULDUAR RAID! Glad those days are over.

---

### Post by Emancipation on 2009-10-11
[SIZE="2"]The way I did it, was getting the frontend for WINE. PlayOnLinux, you can download it from [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html").
Have fun! ;-)[/SIZE]

---

### Post by myolbug on 2009-10-20
> **Emancipation said:**
> [SIZE="2"]The way I did it, was getting the frontend for WINE. PlayOnLinux, you can download it from [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html").
Have fun! ;-)[/SIZE]

Thnk you!  For some reason it cannot find my dvd drive.  It lists cdrom, cdrom0 and other.  IT cannot find it that way.  How do I correct this?

---

### Post by myolbug on 2009-10-21
Anyone?

---

### Post by Absolut Newbee on 2009-10-21
just a question, why do you need to get the DVD to work?
if you can get it to work via the client download?

---

### Post by myolbug on 2009-10-21
> **Absolut Newbee said:**
> just a question, why do you need to get the DVD to work?
if you can get it to work via the client download?

I would like to get the disc to work as I have paid $20 for it.  I guess I'll try contacting the WoW folks and see if I can get some way of downloading it so that I can just play that instead.

---

### Post by HarrisonNapper on 2009-10-21
If you have a paid WoW subscription, you can get it via the client download, which worked best for me in running WoW. You did pay $20 and you're paying even more than that in wasted time trying to get the CD to run. Check out the wine guides for installing via the client downloader and tweaking for best results in WoW.

I haven't tried PlayOnLinux, but it looks pretty awesome; might help you out.

However, if you insist, post the output of ```
ls -l /media
``` so we can see what your cdrom is called. An easier way to do this might be ```
ls -l /media > younameit.txt
``` and then get the file "younameit.txt" from whatever your working directory was and post it here.

Cheers.

---

### Post by nwadams on 2009-10-21
> **myolbug said:**
> I would like to get the disc to work as I have paid $20 for it.  I guess I'll try contacting the WoW folks and see if I can get some way of downloading it so that I can just play that instead.

i don't play wow, but from what i understood of WoW, if you download the game off the website (the trial version), it is the full version of the game, then all you have to do is log in with your login info. 

Or you can just go torrent images...

---

