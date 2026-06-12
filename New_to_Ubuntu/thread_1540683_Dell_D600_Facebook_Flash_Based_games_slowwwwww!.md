---
title: "Dell D600 Facebook Flash Based games slowwwwww!"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by ickle97116084 on 2010-07-28
Hi all,
 
This is my first venture into Linux so please be patient if my technical understanding and my Linux Lingo is affable.
 
I recently installed Ubuntu 10.04 Netbook edition onto a Dell D600 Lattitude Laptop using a Linux Format Cover Disc. All went swimmingly and Ubuntu started with no problems. I know from reading various web forums that wireless drivers for this laptop are not on the disk or at least not the optimal drivers. So using NDISWRAPPER and the sudo command I installed the wireless driver which works perfetly. Ubuntu auto updated al software and drivers last night so I think my install is optimal. I have also updated the ATI driver to the latest version. So that wall of text was meant to give you an idea of where I currently stand.
 
Heres my gripe, I installed Ubuntu as a replacement for Windows XP SP3 on this laptop as it was criminaly slow. My wife uses Farmville on this laptop and she was upset with the poor speed and the fact it freezes regularly to the point of being unuseable. SO I thought Ubuntu to the rescue, ouch I was so wrong. It is equally as slow using both firefox and Chromium. I cant understand why as I was getting download speeds of almost 1Mbps.

---

### Post by overdrank on 2010-07-28
> **ickle97116084 said:**
> Hi all,
 
This is my first venture into Linux so please be patient if my technical understanding and my Linux Lingo is affable.
 
I recently installed Ubuntu 10.04 Netbook edition onto a Dell D600 Lattitude Laptop using a Linux Format Cover Disc. All went swimmingly and Ubuntu started with no problems. I know from reading various web forums that wireless drivers for this laptop are not on the disk or at least not the optimal drivers. So using NDISWRAPPER and the sudo command I installed the wireless driver which works perfetly. Ubuntu auto updated al software and drivers last night so I think my install is optimal. I have also updated the ATI driver to the latest version. So that wall of text was meant to give you an idea of where I currently stand.
 
Heres my gripe, I installed Ubuntu as a replacement for Windows XP SP3 on this laptop as it was criminaly slow. My wife uses Farmville on this laptop and she was upset with the poor speed and the fact it freezes regularly to the point of being unuseable. SO I thought Ubuntu to the rescue, ouch I was so wrong. It is equally as slow using both firefox and Chromium. I cant understand why as I was getting download speeds of almost 1Mbps.

Hi and welcome, the issue may be the older ATI RADEONTM 9000 graphics card. 

How much memory do you have in the system and do you have the desktop effects enabled?

---

### Post by ickle97116084 on 2010-07-28
Hi I have installed the radeon driver from the cover disc from this months Linux Format. I am sure it is the latest version. I tried to disable any special effects but the option is greyed out and set to none. The graphics chip has 32MB of dedicated memory and there is 1GB of RAM.
 
Ickle!

---

### Post by Kellemora on 2010-07-28
Hi Ickle

I'm on FaceBook almost all day playing games.

I no longer play any game made by Zynga though, they ALL have very serious problems with them.

I have several computers here and most of them run like the wind playing games except one, the Dell, it's as slow as molasses in the dead of winter.

In order to play Country Life, just as an example, we had to roll back to FireFox version 3.6.3 because FireFox introduced a serious memory leak when they moved up to version 3.6.4, they tried to fix it, and released version 3.6.5 and a couple of days later 3.6.6, but the problem keeps getting worse.  Now they've come out with 3.6.7 and 3.6.8 and the memory leak is still there, only now it moves around, making it even worse yet.
By moving back to version 3.6.3 ALL problems of using FireFox with Flash on FaceBook hosted games went away again.
Didn't help the speed of the Dell any, they are just naturally slow beasts.

TTUL
Gary

---

### Post by ickle97116084 on 2010-07-29
THankyou very much for your response although it kinda sucks that I have a Dell. It was donated to my wife from her father and is our backup laptop. My wife has a Windows 7 laptop puting Linux on this is not going to happen. So back to the Dell! As a project I dont mind hacking around with Linux adding or removing code but I am a complete beginner so need HELP. I work in desktop support (Windows NT-XP) so quite happy to dig around within an OS as long as what I do can be tracked and reversed which as I am lead to believe Linux is beutifully designed to do. 
 
I have to be honest and say this experience with Ubuntu being slow on flash games that a Windows 7 PC flies through is pretty poor, dont know or care who is to blame as the end experience is what counts. So if anybody has any information I can use to make my Dell D600 run smoother I would love to hear it. I am willing to try anything. 
 
Last bit of information, Windows XP is still on the PC so I can dual boot and go back to the slow but useable OS.

---

### Post by P4man on 2010-07-29
I got the same laptop and ubuntu has been a .. hate to say it; disaster on it. Suspend doesnt work, hibernate doesnt work, getting wifi to work is an ongoing problem (i dont have the original wifi card in it but an acx111 based card), the touchpad buttons get stuck or live a life on their own and the only solution that works for that, disables touchpad scrolling..

Anyway, the graphics card in that machine is an ATI mobile fireGL 9000. That and flash is probably your problem. I dont even get youtube to play in fullscreen without stuttering (though it plays even HD fine using minitube, smplayer or whatever). 

To be honest, I pretty much gave up. Yesterday I tried windows 7 on it (since I have 2 GB Ram) but that was an even bigger disaster. No audio drivers; no videodrivers (only VGA), no wifi, not even wired networking worked.

Long story short: for this machine Im going back to XP. A fresh install and it performs pretty well.

---

### Post by Kellemora on 2010-07-29
Perhaps trying a lighter version of Linux may help?

On my Dell, I dropped back from XP-Pro to XP-Home and noticed a little difference.  But Ubuntu is still faster on it than Windows, but not by much.

It's been too long to remember which one now, but I tried a lighter version of Ubuntu, XUbuntu maybe, and it ran much faster.  But then I tried the new 10.04 on it and ended up going back to 8.04 for now.

I may have been around for awhile now, but for all practical purposes, I'm still just a newbie myself.  8.04 has been virtually plug n play for me, very few problems after I got over the first week of learning and using Linux.  It just works so I don't mess with it, hi hi........

Good Luck on getting your speed up on those games!

TTUL
Gary

---

### Post by Jazzy_Jeff on 2010-07-29
Unfortunatly ATI driver support sucks in Linux and Flash is not much better. Sorry you are having so much trouble. I don't know if there is anything that can be done unless Adobe or ATI give us better support. You may want to try an older version of Ubuntu to see if that works better for you. 8.04 is still supported for a while.

---

