---
title: "Ubuntu 10.10 on HP Compaq NC6000"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by garya on 2011-01-13
Hello--

My wife's old Dell Laptop has died.  In its place, I was able to purchase a used HP Compaq NC6000 Laptop.  It has an Intel Pentium M, 1.6GHZ Processor, 512MB RAM, and a 60GB Hard drive.  It does not have an operating system, however, so I thought I could try Ubuntu.  I have a small amount of experience with Xubuntu and Ubuntu on some old Laptops, but my wife has none.  I have a couple of questions:
[LIST=1]
[*]The recommendations for 10.10 ask for 1 GB of RAM. :o WIll it still run on 512MB?
[*]My works from home using Citrix. Are there any issues to be aware of with Ubuntu and Citrix?
[*]My wife also uses her iPod and iTunes with her laptop.  Anything else she needs to be aware of?
[/LIST]

I suppose I could just download the live disk and and try it, but it will take several hours to download and I don't want to do that if it's not going to work.
Thank you.

EDIT: It's an iPod, not iPad.

---

### Post by SuaSwe on 2011-01-13
Hi garya,

1. I can't imagine that will be a problem, but you could always go for 10.04 (Lucid Lynx) instead - it's a Long Term Support release so will be supported for longer and is likely to be and remain more stable, and its minimal requirement is only 256MB (see [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes))
2. I use Citrix for work and it works fine - took about 20 minutes to set up but wasn't too complicated, and there's plenty of documentation available online
3. Can't say for sure though I do believe it should work, however I have seen many report issues with getting iTunes to work on any OS that is not Apple-stamped and approved :D

Remember that you can try Ubuntu using a LiveCD before installing - you won't have lost anything: it's free after all. :)

---

### Post by khelben1979 on 2011-01-15
To answer your last question: [WineHQ - iTunes]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347") has reports on how it works. I recommend you have a look at that if you seriously want to try it out.

Compiling up a new version of Wine and using that with a version of iTunes which works best with Wine would be the thing to go for as the reports on the above link suggests.

---

### Post by Jerry N on 2011-01-15
Since you don't have anything on the drive now, just go ahead and install Ubuntu and see how well things work.  Worst case, you might have to replace it with something else - no big deal!  Personally, I would try Ubuntu 10.04 or Mint 9.  I put Mint 9 on my 5 year old HP laptop as a dual boot with XP and it seems to work just fine.  I did upgrade the RAM from 1GB to 2GB.

Jerry

---

### Post by garya on 2011-01-15
Thank you to everyone that replied.  I downloaded 10.10, installed it, and it works great right out of the box.  I followed the directions for Citrix up to a point [here]("http://www.liberiangeek.net/2010/09/install-citrix-ica-client-ubuntu-10-10-maverick-meerkat/"). She was able to remote into her desktop. So far everything works great, and my wife is surprised and pleased.

Now the problem is the iPod--we have the old hard drive hooked up, and her iTunes library is in M4P format, which doesn't seem to work.  Is there a way to convert them, or is there a program that will play them? She doesn't care about going to the iTunes store, but she would like to able to download music from a CD and save it to the iPod.  Is that possible?

---

### Post by garya on 2011-01-15
ok, new problem--the toolbars have disappeared.  I can't access any applications.  How do I get them back?

---

### Post by khelben1979 on 2011-01-16
I did a google search and found a software ([Protected Music converter]("http://www.m4p-mp3.com/")) which can convert the music files, but the software is written for Windows, so I don't know if Wine can handle it. Also, I have never tried it myself so use at your own risk.

ffmpeg is a powerful tool for converting sound/video files for different formats, but when it comes to using a protected file format as how it looks like, I suspect that it cannot handle this, just go for Windows software and hope it works. Once converted, then you got no problems using the files with your Ubuntu system.

---

### Post by boldford on 2011-04-28
> **garya said:**
> Thank you to everyone that replied.  I downloaded 10.10, installed it, and it works great right out of the box.  I followed the directions for Citrix up to a point [here]("http://www.liberiangeek.net/2010/09/install-citrix-ica-client-ubuntu-10-10-maverick-meerkat/"). She was able to remote into her desktop. So far everything works great, and my wife is surprised and pleased.

Now the problem is the iPod--we have the old hard drive hooked up, and her iTunes library is in M4P format, which doesn't seem to work.  Is there a way to convert them, or is there a program that will play them? She doesn't care about going to the iTunes store, but she would like to able to download music from a CD and save it to the iPod.  Is that possible?
What did you do for Wifi drivers etc?

---

