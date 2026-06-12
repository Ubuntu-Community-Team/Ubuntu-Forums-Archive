---
title: "any good file transferring software for ipod nano 5th gen?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-17
Just bought a ipod nano 5th generation.  It's great!! It's 16 gig's and I'm really happy w/ it.  I loaded the music from itunes (windows) but I've got more on my ubu partition.  I tried hipo and gtk ipod manager.  Hipo is telling me it can't find the ipod and gtk pod is kinda confusing and i'm not sure that program is "seeing" my ipod.  I know that the ipod is mounted as there is an icon on the desktop and I can transfer the files.  Does anyone know of any programs that I can use to transfer these music files??  All other info should be in my signature thanks in advance for any advice all!!!!

---

### Post by llamabr on 2010-03-17
if it's showing up on your desktop, you should just be able to drag and drop.

Many people here are quite fond of amarok

[http://www.google.com/search?q=amarok&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=amarok&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by bradmayne04 on 2010-03-17
Yeah uhh I don't know how I can transfer files to my ipod through amarok........

---

### Post by nc-kane on 2010-03-17
Although it doesn't really help right this moment....
10.04 promises I-pod support. 
It's less than a month away.

---

### Post by bradmayne04 on 2010-03-17
> **nc-kane said:**
> Although it doesn't really help right this moment....
10.04 promises I-pod support. 
It's less than a month away.
 
 
ARRRGGGGHHH I don't wanna wait a month!!! Any other ideas???

---

### Post by tom.swartz07 on 2010-03-17
> **bradmayne04 said:**
> ARRRGGGGHHH I don't wanna wait a month!!! Any other ideas???

Gtk-Pod and Rhythmbox, the way that I manage my 1st gen iPod Touch. :D

---

### Post by bradmayne04 on 2010-03-18
> **tom.swartz07 said:**
> Gtk-Pod and Rhythmbox, the way that I manage my 1st gen iPod Touch. :D

Okay my man you must not have listened to what I said at all.  In fact I'm not sure why you even posted that here.  It was not helpful at all.  In fact you just wasted more of my time.  Gtk ipod does not support 5th generation ipod at all!!!  in fact i said that in the original post and rythmbox will not even send files FROM the ipod.  I'm going to bite my tongue now before I say anything more.

---

### Post by tom.swartz07 on 2010-03-18
> **bradmayne04 said:**
> Okay my man you must not have listened to what I said at all.  In fact I'm not sure why you even posted that here.  It was not helpful at all.  In fact you just wasted more of my time.  Gtk ipod does not support 5th generation ipod at all!!!  in fact i said that in the original post and rythmbox will not even send files FROM the ipod.  I'm going to bite my tongue now before I say anything more.

Well bud,

First things first, the iPod Touch and the 5th Gen Nano both use the same updated iTunes directory structure. This setup is different than any of the other iPods, and thus it creates the problem that you are having.

I suppose you didnt take the time to look in to how to use GTKPod, did you? Granted, the interface looks a bit clunky, but it works great to do EXACTLY what you mentioned.

You need to mount the iPod in your FUSE directory, not just plug it in. When you mount in FUSE, it assigns a specific folder, similar to how you have the cdrom folder in your /media/ directory. There are a few helpful hints here: [http://ubuntuforums.org/showthread.php?t=1267180&page=4](http://ubuntuforums.org/showthread.php?t=1267180&page=4)

JUST MAKE SURE YOU USE THE RIGHT CASE FOR YOUR IPOD WHEN YOU MOUNT IT!!! I used a mix of upper and lower case letters and it ended up not working correctly. Check and double check before you edit your FUSE files.

FROM THERE, you can simply load up whatever program you want. Once its mounted in FUSE, you could use GTKpod to take the music off/on or, if you prefer, do it through Rhythmbox.



Several people have said that the only way to get proper syncing is to compile GTKPod from source. Not knowing your experience with this sort of work, I will refrain from going into details just yet. If this is the route you want to take, Id be more than willing to help.

For reference:
[http://ubuntuforums.org/showthread.php?t=1366083](http://ubuntuforums.org/showthread.php?t=1366083)
[http://ubuntuforums.org/tags.php?tag=gtkpod](http://ubuntuforums.org/tags.php?tag=gtkpod)
[http://ubuntuforums.org/showthread.php?t=1364733](http://ubuntuforums.org/showthread.php?t=1364733)


Sorry that I was so curt, but I was simply suggesting that you should take another look at it.

---

### Post by echo.whoami on 2010-03-18
Have you tried banshee? This is what i use with my ipod

---

### Post by bradmayne04 on 2010-03-18
> **tom.swartz07 said:**
> Well bud,
 
First things first, the iPod Touch and the 5th Gen Nano both use the same updated iTunes directory structure. This setup is different than any of the other iPods, and thus it creates the problem that you are having.
 
I suppose you didnt take the time to look in to how to use GTKPod, did you? Granted, the interface looks a bit clunky, but it works great to do EXACTLY what you mentioned.
 
You need to mount the iPod in your FUSE directory, not just plug it in. When you mount in FUSE, it assigns a specific folder, similar to how you have the cdrom folder in your /media/ directory. There are a few helpful hints here: [http://ubuntuforums.org/showthread.php?t=1267180&page=4](http://ubuntuforums.org/showthread.php?t=1267180&page=4)
 
JUST MAKE SURE YOU USE THE RIGHT CASE FOR YOUR IPOD WHEN YOU MOUNT IT!!! I used a mix of upper and lower case letters and it ended up not working correctly. Check and double check before you edit your FUSE files.
 
FROM THERE, you can simply load up whatever program you want. Once its mounted in FUSE, you could use GTKpod to take the music off/on or, if you prefer, do it through Rhythmbox.
 
 
 
Several people have said that the only way to get proper syncing is to compile GTKPod from source. Not knowing your experience with this sort of work, I will refrain from going into details just yet. If this is the route you want to take, Id be more than willing to help.
 
For reference:
[http://ubuntuforums.org/showthread.php?t=1366083](http://ubuntuforums.org/showthread.php?t=1366083)
[http://ubuntuforums.org/tags.php?tag=gtkpod](http://ubuntuforums.org/tags.php?tag=gtkpod)
[http://ubuntuforums.org/showthread.php?t=1364733](http://ubuntuforums.org/showthread.php?t=1364733)
 
 
Sorry that I was so curt, but I was simply suggesting that you should take another look at it.
 
Well I guess I gotta take back some of what I said however I wish you had told me that ipod nano 5th gen had the same drivers as the touh upfront that may be why gtk ipod is not "seeing" or mounting the ipod?? I dunno.  I'm on my desktop right now linux is on one of my lappy's.  So i'll check into it this afternoon.  And yes if I had to I could compile your talking with the "make" && "make install"  or something along those lines right?  Anyway's like I said I'll post  again and let you know what's going on.

---

### Post by tom.swartz07 on 2010-03-18
> **bradmayne04 said:**
> Well I guess I gotta take back some of what I said however I wish you had told me that ipod nano 5th gen had the same drivers as the touh upfront that may be why gtk ipod is not "seeing" or mounting the ipod?? I dunno.  I'm on my desktop right now linux is on one of my lappy's.  So i'll check into it this afternoon.  And yes if I had to I could compile your talking with the "make" && "make install"  or something along those lines right?  Anyway's like I said I'll post  again and let you know what's going on.

Yep, no big. That was an error on my part.

Thats essentially what you have to do to compile it from source.


Let us know! Id be glad to help

---

