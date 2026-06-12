---
title: "Help for a total noob"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by mister_pal on 2009-01-01
Hey gang, I recently made the switch to Ubuntu after a virus nearly wrecked my computer in Windows, and this is my very first time using any sort of Linux-based OS. I was wondering if anyone could recommend some good, user-friendly programs for media and things like that, I really have no idea what's what.

My number one priority is I need a program that can upload my MP3's from my iPod onto my computer. My iPod is the only place I have my music collection right now, so I need to do this right. I also need to find a good replacement for iTunes, so I can manage my music and my iPod. 

Any help is much appreciated, thanks!

---

### Post by evilkastel on 2009-01-01
You might want to try banshee, but you have to upgrade to the latest version. other nice alternative is gtkpod. altough there are not apps with enough power to supply everything that itunes does.

For Banshee:

```
sudo gedit /etc/apt/sources.list
```

Then add at the bottom: 
```
# deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
# deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
```

Then, banshee should try to upgrade. hope this helps. cheers.

---

### Post by caro on 2009-01-01
I've heard that iPods and Linux don't play well together in general.  However, for mp3, I use Rhymthmbox or Songbird.  Both have their good points and their faults.  Many users on this forum like Amorok.

---

### Post by ken22 on 2009-01-01
vlc supports more formats under Linux than on any other OS.

I use it for all my media although it doesn't support Ipod.

---

### Post by thinking2loud on 2009-01-01
Unfortunately, I don't think there exists a 1:1 replacement for iTunes.  This is both good and bad.  The issues are many and may start a flame war if discussed in detail.  IPods and most other music/video players will appear to Ubuntu as USB mass storage.  If you bought content through the iTunes Store (current video, older music) then it may have Digital Rights Management on it.  Some iPods only deal with AAC as the audio codec.

You mention that the only place your music currently exists is your iPod.  Because of this, I would recommend that you take that iPod and put it in a safe place with a charger, which is far away from your computer.  Go to a discount store and buy the cheapest off-brand knockoff MP3 player you can find.  Screw up that one first.

---

### Post by joukez on 2009-01-01
Yes, Amarok is a very good player. When you want to convert audio files use sound converter. Smplayer for your video for msn Emesene, Amsn is better but acts funny when you have a off-line message and you klick on it to read it. Have you installed the restricted extras yet? [http://help.ubuntu.com/community/RestrictedFormats]("http://help.ubuntu.com/community/RestrictedFormats") Here you can also find the link for installing codec to play encrypted dvd. And the W32 codec

                              gr. Jouke

---

### Post by mister_pal on 2009-01-01
It turns out I already had Rhythmbox, so I'm gonna try that out. Anymore suggestions on the problem of getting my music OFF my iPod would be greatly appreciated. Thanks.

---

### Post by abn91c on 2009-01-01
i have Amarok, the new version 2.0 has a drag and drop feature to transfer all your mp3's from the ipod to the hardrive. I have 5th Gen 30 gig ipod video and works very well in amarok

---

### Post by lkraemer on 2009-01-01
More Information for you to look at.

Replacement Software for Windows:
http://www.linuxrsp.ru/win-lin-soft/table-eng.html
http://linuxappfinder.com/
http://www.linuxalt.com/

Dual Boot:
http://users.bigpond.net.au/hermanzone/
http://www.ubuntugeek.com/
http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_instal led_first.htm
ttp://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11
http://ubuntuforums.org/showthread.php?t=1004514

Tutorial:
http://ubuntuforums.org/showthread.php?t=1004514
https://help.ubuntu.com/
http://www.howtoforge.com/howtos/linux
http://www.linux.org/lessons/beginner/toc.html
http://www.linux-tutorial.info/
http://rute.2038bug.com/index.html.gz

GRUB:
http://www.dedoimedo.com/computers/grub.html
http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD

SUPERGRUB:
http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html

Conky:
http://ubuntuforums.org/showthread.php?t=867076&highlight=beginners+guide+ conky

This is good information for you to look over.

lkraemer

---

### Post by linuxisfree on 2009-01-01
> **mister_pal said:**
> Hey gang, I recently made the switch to Ubuntu after a virus nearly wrecked my computer in Windows, and this is my very first time using any sort of Linux-based OS. I was wondering if anyone could recommend some good, user-friendly programs for media and things like that, I really have no idea what's what.

My number one priority is I need a program that can upload my MP3's from my iPod onto my computer. My iPod is the only place I have my music collection right now, so I need to do this right. I also need to find a good replacement for iTunes, so I can manage my music and my iPod. 

Any help is much appreciated, thanks!

For Ipod management, i use a program called gtkpod, it's very simple, yet does what i need it to do. It also does the copy from Ipod to computer thingy that you want.

Couple of links about it:

[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)
[http://en.wikipedia.org/wiki/Gtkpod](http://en.wikipedia.org/wiki/Gtkpod)

You can install it from the repositories. Enjoy!

---

### Post by xarte on 2009-01-01
You may have a problem. My sister got a new iPod for Christmas and her computer-tech husband spent most of an evening trying to find ways to get the music from the ipod onto a computer with no success. I did a bit of googling on it too, and my understanding is that it's strictly a one-way thing - it syncs from your computer to the ipod. I suppose it's meant to prevent illegal copying of music.

To get my daughter's music from my computer onto her new one, I have to burn it to a CD and load it from that. I can't do it from her ipod.

So did you go ahead and overwrite your iTunes without checking this out first? Bad mistake.


BUT WAIT.....
I found this, which might be helpful. Gets a couple of nods from readers so maybe it works!

[http://www.mydigitallife.info/2006/07/16/copy-or-transfer-music-and-songs-from-ipod-to-pc-and-computer-without-itunes/](http://www.mydigitallife.info/2006/07/16/copy-or-transfer-music-and-songs-from-ipod-to-pc-and-computer-without-itunes/)

---

### Post by caro on 2009-01-01
Some other general things to know:

[LIST]
[*]Synaptic is the easiest way to add applications for a new user
[*]Open Office does most of what Microsoft Office does (and you can download a Windows version on your Windows machine too.)
[*]Firefox, Opera, and others replace Internet Explorer
[*]Thunderbird, Evolution, etc replace Outlook and Outlook Express
[*]F-Spot, GIMP, gThumb are some of the image and photo apps
[*]Pidgin is for instant messaging
[/LIST]

A handy reference guide for understanding Linux commands is [http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

---

### Post by mister_pal on 2009-01-01
Thanks again, guys! I was pretty worried about having to learn how to use a whole new OS, but Ubuntu really is easy to use! I'm gonna try gtkpod, and I'll let you know how it works out. Wish me luck!

---

### Post by hyper_ch on 2009-01-02
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

