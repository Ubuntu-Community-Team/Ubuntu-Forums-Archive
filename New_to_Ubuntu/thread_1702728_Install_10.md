---
title: "Install 10"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-03-08
Hello all
Having had problems with my graphics card + boot loader, I have decided to reformat my drive and start from scratch
Having just fitted a new AsRock main brd, nvida 8400gs graphics card and hard drive
Ubuntu 9 failed to pick up on the graphics card, hence the fresh reinstall which will also include winxp "needed"

So fresh download and burn of ubuntu 10.04 last night
Placed CD in drive, boot first CD to get message

Insert boot-able media etc etc what did I do wrong or how do I boot from CD after I reinstall winxp

help needed :confused:

Dave

---

### Post by grahammechanical on 2011-03-08
Which CD did you try to boot from first? It is alway best to install any Windows operating system before installing a Linux operating system. So, were you trying to install Microsoft Windows? If so, then you need to determine if you do indeed have a Windows Install CD.

Regards.

---

### Post by DaveMcC on 2011-03-08
As I had to wipe or do an fdisk /mbr which winxp can't do, I started off with the ubuntu 10 disk, 
I then reused ubuntu 9 which has done a full format but again failed to find the 
**GeForce 8400 GS 256MB PCI-E Graphics Card**

I am back to where I started "other nite"

So what I am going to do next is reformat the disk and reinstall winxp "needed" and then ubuntu 10, but not from with-in winxp if possible

So what is the best way to install ubuntu 10? :confused:

Dave

---

### Post by mastablasta on 2011-03-08
make a separate partition of about 30 GB (or more) disk space and elave it unformated.
 
then just install to largest empty disk space. the rest will be done automaticly.

---

### Post by DaveMcC on 2011-03-08
Ya, that is what I am doing, working on the idea that the ubuntu 10 will boot next time I try to use it?

Dave

---

### Post by Ben Page on 2011-03-08
> **DaveMcC said:**
> 
So fresh download and burn of ubuntu 10.04 last night
Placed CD in drive, boot first CD to get message

Insert boot-able media etc etc what did I do wrong or how do I boot from CD after I reinstall winxp

help needed :confused:

Dave

You did not burn your CD correctly. You need to burn your CD in "burn image to disc" mode. I'm assuming you have burned a .iso file you downloaded as a regular file on a regular data CD. This way you won't get a bootable CD.

If you still can't manage to boot your CD post what burning software are you using.

---

### Post by DaveMcC on 2011-03-08
This an image of what I done in the burn
[IMG]http://i7.photobucket.com/albums/y282/dtmcc/Screenshot-12.png[/IMG]

 I get this message
from both Kubuntu and Ubuntu 10

Reboot and Select proper Boot device or Insert Boot Media in selected Boot Device and press a key

Dave

Done a reburn of the CD for ubuntu still the same old message
Yet ubuntu 9 boots fine just cant work my graphics card

Dave

---

### Post by Ben Page on 2011-03-08
You are burning the CD in data mode. Even if CD has the same content as the image, it doesn't mean it's bootable. I could be wrong.

Burn the CD with Brasero, it's a CD/DVD burning software preinstalled in Ubuntu. Go to --> Applications --> Sound & Video --> Brasero.

If you don't have Brasero installed:

```
sudo apt-get install brasero
```

Then you'll get this menu, choose the "Burn Image" option, then you'll get a prompt to point Brasero to the Image location on your HDD, find it and burn it this way.

---

### Post by DaveMcC on 2011-03-08
Done that as stated, thank you...Ben
Only I burned Kubuntu first, so I'll give it a try, at least now it boots

Hope fully I will get my graphics card to work

Dave

YES     YES

YES

YES

YES

I am happy

Dave

---

### Post by Ben Page on 2011-03-08
Glad to hear you managed to install successfully, please mark thread as "SOLVED" ;)

---

