---
title: "Need help........ :'("
date: 2009-01-23
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-01-23
Hi everybody!! :) Well a couple hours ago I just finished installing Ubuntu (Yey) but now I cant boot up xp... and i'm real paranoid that I just lost all my stuff in windows :( to be more specific, the option to boot up windows xp doesnt show up, it just loads up ubuntu... well any help would be appreciated thanks alot guys :)

---

### Post by lykwydchykyn on 2009-01-23
Can you open up a terminal and post the output from this command:
```

sudo fdisk -l

```

That will list all the hard drive partitions on your system.  Hopefully we will see an NTFS partition listed, and that will get us started on getting you back to dual-booting.

---

### Post by cosine352 on 2009-01-23
can you see the windows partition? Hope that you have not installed Ubuntu in the whole harddrive. 

what does this file says 
> gedit /boot/grub/menu.lst

---

### Post by lil_kid1333 on 2009-01-23
this is what it showed...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2c8e2c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19270   154786243+  83  Linux
/dev/sda2           19271       19457     1502077+   5  Extended
/dev/sda5           19271       19457     1502046   82  Linux swap / Solaris

and i have no idea why it says solaris... but from what im looking at im guessing no more windows xp huh.............................. :'(

<a href="http://s96.photobucket.com/albums/l180/lil_kid1333/?action=view&current=P012209214614.jpg" target="_blank"><img src="http://i96.photobucket.com/albums/l180/lil_kid1333/P012209214614.jpg" border="0" alt="Photobucket"></a>

<a href="http://s96.photobucket.com/albums/l180/lil_kid1333/?action=view&current=P012209214501.jpg" target="_blank"><img src="http://i96.photobucket.com/albums/l180/lil_kid1333/P012209214501.jpg" border="0" alt="Photobucket"></a>

those are pics I took with my celly of what it said when i booted up..

---

### Post by diablo75 on 2009-01-23
> **lil_kid1333 said:**
> this is what it showed...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2c8e2c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19270   154786243+  83  Linux
/dev/sda2           19271       19457     1502077+   5  Extended
/dev/sda5           19271       19457     1502046   82  Linux swap / Solaris

and i have no idea why it says solaris... but from what im looking at im guessing no more windows xp huh.............................. :'(

Oh no.... who wants to tell him?  :(

---

### Post by Zack McCool on 2009-01-23
Well, you DID make a complete backup before modifying your hard disk, right?

Now, you see, during installation, there was this question about partitioning.  It gave options.  One was Guided - resize, and another was Guided - use entire disk.  It would appear that you chose the latter.

So, now your best bet is to restore from that backup you made, then try again while being more careful to make the appropriate choice during partitioning.

---

### Post by lykwydchykyn on 2009-01-23
Yah... sorry bub, it's gone.

---

### Post by lil_kid1333 on 2009-01-23
umm........................ no... :( only pix that I put online like in photobucket thats about it.. so... my adobe photoshop is gone... :'( well as long as I can run utorrent here ill cheer up.. and anyways im sure Ubuntu will be ALOT better than windows in the long run...

---

### Post by diablo75 on 2009-01-23
> **lil_kid1333 said:**
> umm........................ no... :( only pix that I put online like in photobucket thats about it.. so... my adobe photoshop is gone... :'( well as long as I can run utorrent here ill cheer up.. and anyways im sure Ubuntu will be ALOT better than windows in the long run...

That's the spirit!!  :D

---

### Post by lil_kid1333 on 2009-01-23
yeah and i'm currently reading your 10 things to install when you get ubuntu lol :P well thanks alot guys :D

---

### Post by Muffinabus on 2009-01-23
You can run uTorrent through Wine and it runs pretty decently (:  Though I've just switched to Vuze as I kinda feel better about using a native Linux app.

---

### Post by lil_kid1333 on 2009-01-23
whats the difference between em? :S im scared of using new applications im still all paranoid about those damn viruses from windows... I know Linux is like virus proof but still im traumatized :evil:

---

### Post by Lod on 2009-01-23
> **lil_kid1333 said:**
> well as long as I can run utorrent here ill cheer up.. and anyways im sure Ubuntu will be ALOT better than windows in the long run...Linux is a lot better, but often will take you a while before you realise it... It took me about five years before I really could live without Windows and still sometimes I long back to its lack of choice.

---

### Post by Lod on 2009-01-23
> **lil_kid1333 said:**
> whats the difference between em? :S im scared of using new applications im still all paranoid about those damn viruses from windows... I know Linux is like virus proof but still im traumatized :evil:You could take a look at Deluge or QTorrent. The difference is mostly a different location to set your preferences.

---

### Post by leonardo_neo on 2009-01-23
Cheer up buddy! This happens to many new users. Even I made many mistakes when installing Ubuntu for the first time in my comp. Gradually you tend to learn the basics, and then you realize that you have installed one of the best OS available :)

Sorry for any data you lost. All I can is that for the next time, before doing some modifications on Ubuntu which you are not sure, study about that beforehand. That way you can avoid mistakes and troubles. 

But again, I must say, that you did a wise thing that you installed Ubuntu.

Best of luck

---

### Post by lil_kid1333 on 2009-01-23
hehe thats my name 2 leo xD well yeah I guess when I installed ubuntu I didnt read the part about installing in the whole hard drive :( but yeah thanks guys and i'm sure I made the best "mistake" in my life :D

---

### Post by leonardo_neo on 2009-01-23
Don't be sacred of virus. When someone first switches from Windows to Linux, the first thing that haunts his brain is that how come a system is running without antivirus?? lol

Well, let me help you with that. First, the file system in Linux is different from Windows, and almost none of the Windows virus can install on Linux.
Second, the softwares that you download for Liunx, come directly from enlisted repositories. So again no fear to install something which you don't know.
There is a very feeble possibility that some freak would create a Linux virus in .deb pacakage form, for which you only need to double click the package to install that virus. But again, .deb package installer give you notification that you are going to install this software, are you sure you want to install this? If you don't know the item which is being installed, then you simply wouldn't give permission in that case. As simple as that.

---

### Post by lil_kid1333 on 2009-01-23
thats real cool :O so that means that i dnt need firewalls either? so all those window viruses wnt affect linux at all??? :)

---

### Post by tariquepark on 2009-01-23
NO all those widows virus' are thing of the past for you my friend!!!

as for firewall, well thats up to you. If you are using an adsl modem/router then you are already behind a hardware firewall and you should be fine
that has been my setup for 3 yrs and never even once have i had a problem :)

---

### Post by lil_kid1333 on 2009-01-23
chea :D well thanks alot guys imma go chill and watch some naruto in my brand new Linux yey :popcorn:

I'm sure i'll be back to bug you guys again. This site is wonderfull with all the members willing to support! Imma get me some Linux books to read and learn more stuff about Ubuntu :)

---

### Post by hyper_ch on 2009-01-23
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Synt4xError on 2009-01-23
It's always a good thing to back everything up before you mess around with operating systems. Get an external HD of some size and just keep all files off your computer and on to your HD.

TeraBytes for 120$!!!! They are getting really freaking cheap nowadays.

---

### Post by Synt4xError on 2009-01-23
ALSO, I have Adobe Master Suites CS3 with a working keygen! I get updates all the time. No problem and have reinstalled this 5 times already. I will just give you the key-gen, if you want. PM Me if you want it.

---

