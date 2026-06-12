---
title: "various Ubuntu 9.10 problems!"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by malcburt on 2009-10-30
Hi,
OK so I've taken the plunge and running Ubuntu 9.10 from LiveCD.  Eventually booted up - though took several minutes (longer than XP does :-( ).  More frustratingly though, I've had 2 complete freezes where nothing responds except I can move the mouse.  Also from reading around here I thought that my Netgear WG111v2 Wireless USB Adaptor was meant to work out of the box...

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB)

but no joy.  When I disconnect and reconnect it, I get a little wireless network icon on my desktop which it prompts me to click on, but when I move the mouse over it, it disappears!  I looked at the help pages which talked about a networkmanager icon in the system notification area.  What/where is the system notification area?  I couldn't find that in the help.

I hope it gets easier........

---

### Post by philinux on 2009-10-30
The livecd runs completely in ram, it's not installed on your hard drive at this point.  No windows os can do this feat.

What are your full system psecs.

---

### Post by malcburt on 2009-10-30
2.66 GHz Intel Celeron with 1GB RAM.  Worse problem now is that I can't even eject my CD to boot up into Windows...... :(  I can't ejedt it when it's switched off and the disk utilty eject function just tells me the disk's busy.  What on earth do I do?  I saw a thread about some command line entry "sudo eject" or something, how do I do that?

---

### Post by phillw on 2009-10-30
> **malcburt said:**
> 2.66 GHz Intel Celeron with 1GB RAM.  Worse problem now is that I can't even eject my CD to boot up into Windows...... :(  I can't ejedt it when it's switched off and the disk utilty eject function just tells me the disk's busy.  What on earth do I do?  I saw a thread about some command line entry "sudo eject" or something, how do I do that?

Click on the top right of your screen, select shut-down. When ubuntu is done, it'll spit the disk out and ask you to hit enter.

Phill.

---

### Post by malcburt on 2009-11-01
Thanks, discovered that the first time I shut down normally... back to my original questions: I know liveCD is supposed to be slow, but seems even slower than my old XP installation, is that normal?  Worse still, what about the freezes, and why doesn't my Netgear WG111v2 Wireless USB Adaptor work?  Seeing all the problems written here about 9.10, I'm wondering if I'd be better off with 9.04, is it generally more stable?  At the moment I'm on the point of giving up altogether, I thought it was meant to "just work" :-(  By the way if I decide to install as dual boot, is it reversible if I can't easily fix the problems I'm getting?
Sorry, that;s probably a lot of questions at once, but not sure which one to tackle first!

---

### Post by x C0MMAND0 x on 2009-11-01
It could be drivers for wireless that you can't install from a live cd and keep for next time.  You can make a bootable USB however and that will allow you to save drivers

---

### Post by linux6994 on 2009-11-01
Having set it up in dual boot you have the windows OS on one partition and Ubuntu on the other. During the installation process you can manually select the Ubuntu partition to overwrite and proceed from there. If your Netgear WG111v2 Wireless USB Adaptor will not work right out of the box then you can always use the Ndiswrapper to run the windows driver. To do that you will need a network connection via your eth0.

---

### Post by Dougie187 on 2009-11-01
Just so you know, the speed of the live cd that you are mentioning as a problem is probably working just fine. It will be significantly slower than the machine will be when/if you install. For your wireless, and from what I remember, not all USB adapters work, there is some link where you can figure out if yours will work or not. One thing that should work however is using ndiswrapper to get the windows drivers for it to work. I don't know what to tell you about the crashing though, that seems like a separate problem in itself.

---

### Post by malcburt on 2009-11-01
> For your wireless, and from what I remember, not all USB adapters work, there is some link where you can figure out if yours will work or not. One thing that should work however is using ndiswrapper to get the windows drivers for it to work. 

According to this link it's just supposed to work, all this business about ndiswrapper sounds like a bit of a hack to me.

[https://help.ubuntu.com/community/Ha...rdsNetgear#USB](https://help.ubuntu.com/community/Ha...rdsNetgear#USB)

> I don't know what to tell you about the crashing though, that seems like a separate problem in itself.

While it's doing this I'm tempted not to touch with a bargepole... anybody any ideas before I give up in disgust?  I started out very optimistic about this, and the PC is very stable (if slow) in windows and just hoped this might give it a new lease of life.

---

### Post by malcburt on 2009-11-01
> **linux6994 said:**
> Having set it up in dual boot you have the windows OS on one partition and Ubuntu on the other. During the installation process you can manually select the Ubuntu partition to overwrite and proceed from there. 

I don't quite understand - are you saying this option to select the Ubuntu partition to overwrite will effectively wipe it and leave my windows partition intact if I decide to abandon this?

---

### Post by malcburt on 2009-11-02
Sorry, had a bit of a rant last night and don't want to appear ungrateful for the help I'm getting, but I have 2 particular problems which I think are stopping me moving on:
 
1. probably the most serious at the moment, I have had frequent freezes a few minutes after startup using LiveCD, where everything appears to lock up except the mouse continues to move.  Anybody any idea how to diagnose this, is it really less likely to happen if booting from hard drive (as I said I'm very nervous about installing properly at the moment while I've got so many problems)?
 
2. My Netgear WG111v2 Wireless USB Adaptor does not work.  When I disconnect it and reconnect it, *something* happens, i.e. I get a wireless network icon on my desktop which it prompts me to click on but when I move my mous over it, the icon vanishes.  According to [[COLOR=#000000]https://help.ubuntu.com/community/Ha...rdsNetgear#USB[/COLOR]]("https://help.ubuntu.com/community/Ha...rdsNetgear#USB") it seems that this adaptor ought to work out of the box, and I didn't think should need ndiswrapper so I don't know what to do.
 
Any help much appreciated!

---

### Post by apparle on 2009-11-02
Hey, why don't you try Wubi installtion.
Wubi installtion means ubuntu will get installed as a software on your existing windows system. You don't need to partition your disk. You only need a drive(NTFS) which has enough space (>6GB IMHO) and  is defragmented well. When starting the computer you will get an option to boot either into windows or into Ubuntu.
The hard disk performance in ubuntu will be low by this method(NTFS limiting it) but that will be negligible. And it will be much much faster than LiveCD. And your settings/files will be saved.

And if you ever want to remove it then you can just remove it from 'Add/Remove Programs' in Windows.

Warning: You won't be able to easily access the drive on which you install Ubuntu wubi. Eg: If your (D:\) has 20GB and you install Ubuntu in it in 6GB then you will not be able to access the remaining 14GB in Ubuntu directly(but you can by some tricks :) )

Apart from 6GB lost you will notice no diffrence in Windows and you will be able to learn Ubuntu well. :popcorn:

Crashing/Driver problems/Unstability can be fun once you start liking Ubuntu :D

Also IMHO 9.10 is much better than 9.04

---

### Post by malcburt on 2009-11-02
Hi Apparle,
Yeah I'd read about Wubi and it did sound comparatively easy.  However my main reason for trying Ubuntu in the first place was that my Windows XP had become so cripplingly slow, which is what I thought happened to Windows in the end.  So if it's running under Windows surely its performance will be limited by the c**p OS underneath it.... won't it?  So it didn't seem like a solution to my problem, since I'd read how good Ubuntu was at eking life out of old hardware with an old OS.  I'm prepared to be told I'm wrong though, this was just an assumption.
Thanks

---

### Post by malcburt on 2009-11-03
Hi,
I'm getting a bit dispirited at the lack of simple suggestions to diagnose or solve my various problems. I'm an absolute beginner with this and was attracted by some of the press I'd read that suggested that 9.10 was really easy to install. But this isn't my first impression and without any help it'll become my final impression and a possible convert will have been lost.
So if anyone can help I'd REALLY appreciate it or else I'll just go away.

---

### Post by paynek716 on 2009-11-03
Live CD is for evaluation and, in my opinion, will not fully emulate the installed version. This is due in part to proprietary drivers which may not be part of the Live CD demo. In my case I was never able to get the Live CD version to connect to the internet. It turns out my laptop had a proprietary driver for the wireless connection. Fortunately when I installed Ubuntu 9.04 it automatically detected and installed the right driver.

If you decide to stick with XP and performance is slow you may want to update RAM. 1 GB of RAM is sufficient for most applications, 2 GB if you are a power user or running video intensive apps. If RAM is not the answer maybe your hard drive is fragmented, too full, or both. Try running the Windows defrag utility. You can find it somewhere through Control Panel. If your disk is over 85% full your computer will not work very well regardless of the OS and you will need to install a larger drive or remove some files.

If you decide to install Ubuntu and want to keep Windows XP as well, you will want to look at the dual boot installation option. Here is a good starting point [https://help.ubuntu.com/9.10/switching/index.html]("https://help.ubuntu.com/9.10/switching/index.html")

---

### Post by malcburt on 2009-11-03
Thanks for the reply...

> Live CD is for evaluation and, in my opinion, will not fully emulate the installed version.

I'm confused about that since I've read other posts where people have been castigated for NOT trying LiveCD first, so I can't tell what advice I should follow...

> If you decide to stick with XP and performance is slow you may want to update RAM. 

Don't honestly think that's my problem. Was trying LiveCD on my tower PC with 1GB RAM which (since I upgraded it form 256MB...) doesn't actually run too badly in XP, but way slower with LiveCD.  Was just trying it here to evaluate its usefulness for my laptop which is cripplingly slow in XP, which is only 512MB and can't take any more RAM.  So LiveCD definitely seems to be my problem.

There do seem to be a hell of a lot of problems with 9.10. Objectively speaking, might I be better off with 9.04 if it's more stable and more proven?  And what about the suggestion of Wubi, will its performance be limited by the slowness of Windows running underneath it?

---

### Post by quinnten83 on 2009-11-03
Wubi is an installation in and by itself. It's just that the means to install is through Windows. Once installed they will have nothing to do with each other.
I do not know about your wireless usb dongle. My guess is it doesn't work, you might want to try some other one.
Notification panel is in the upper-right corner. This is where you get the messages to appear telling you that all hell might have broken loose, or that you have new mail.

About the freezing.
previous versions of Ubuntu have had a locking up problem where I could only turn off the PC and start over.
I noticed on my acer laptop that it too freezes, but this was different, after about a minute the system would again be responsive.
maybe exercise a bit of patience?

also, it is noticeable that you become increasingly agitated when people do not respond immediately to your questions. you might want to calm down and be a bit more patient, people will be more inclined to help if they can. Also, it might help you to clearly discern what people are telling you, cause I saw several suggestions fly right over you.

If all this with Ubuntu is getting to you, you might want to try linux mint, as it is easier...

---

### Post by malcburt on 2009-11-04
Thanks for the suggestions. I think I might try Wubi first in that case and see how it performs. A job for the weekend I think.  The problem with my USB wireless adaptor can't be the unit itself because it's fine running from XP, I can only guess its a driver problem of some description.

By the way my frustration wasn't at the lack of replies, more that the replies often didn't directly answer my questions or sometimes seemed to contradict each other.

---

### Post by paynek716 on 2009-11-04
> **malcburt said:**
> I'm confused about that since I've read other posts where people have been castigated for NOT trying LiveCD first, so I can't tell what advice I should follow...

With LiveCD you are running Ubuntu from the CD without installing anything to your hard drive, so it will tend to be slow. I think the castigation is for people don't do a test drive first, jump in with no investigation, then complain about Ubuntu.

---

### Post by Tholley on 2009-11-04
One of the things I remember with the Live CD, whether it be with 9.04 and probably the same with 9.10, is since it doesn't write to your hard drive, you will have to manually configure your wireless each time. It has no way of remembering the settings on the CD. You should be able to right click on the icon at the top, click properties, and put in your wireless settings. 
 
It should connect after that.
 
I still have a copy of all my settings lying around just for that, which I may be trying to do the same thing tonight when I get home.

---

### Post by SunnyRabbiera on 2009-11-04
You may want to try a dualboot, as yes sometimes certain network cards dont like linux too much.
You can try to download what you need in windows and then try to install them in linux, I have done it myself.
Its not the most simple solution but again it all hangs on the card you have sadly.

---

### Post by malcburt on 2009-11-05
Thanks for all the ideas. I tried installing Wubi last night onto my laptop which didn't go too badly, boots up nice and quickly and seems stable (though haven't run it that long yet).  However, yes I'm having problems with my Wireless connection and have got to the point where I need some more help with this.... see new thread

[http://ubuntuforums.org/showthread.php?t=1314641](http://ubuntuforums.org/showthread.php?t=1314641)

---

### Post by wheatpenny on 2009-11-05
> **apparle said:**
> 

Warning: You won't be able to easily access the drive on which you install Ubuntu wubi. Eg: If your (D:\) has 20GB and you install Ubuntu in it in 6GB then you will not be able to access the remaining 14GB in Ubuntu directly(but you can by some tricks :) )

The drive you installed Ubuntu on can be accessed via the "Host" folder (Computer/filesystem/host)

---

### Post by Jitterplate on 2009-11-05
Hi.

I'm a total newbie, as I installed Ubuntu 9.10 a couple of days ago, and i've had a host of baffling moments. 
I installed from a USB drive, incidentally, which went off pretty smoothly. 
But I have a problem now when for various installations, I'm asked to insert the karmic koala CD (my CD drive doesn't work!) to get things to move ahead.

> Media change: please insert the disc labeled        
 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)'
in the drive '/cdrom/' and press enter

 I try to redirect to the USB drive path, but it doesn't work. 

Then I tried enabling the multiverse option, to create repositories for s/w downloads, but even that didn't work out, as 'the package could not be found'. 

Also, I tried installing an IP Messenger client (tried Gnome, xmemo, iptux) but I wasn't able to figure it out, in the sense, I downloaded the file and unzipped it, but I didn't know what next to do. 

Could anyone please help me with this?

---

### Post by sliketymo on 2009-11-05
> **Jitterplate said:**
> Hi.

I'm a total newbie, as I installed Ubuntu 9.10 a couple of days ago, and i've had a host of baffling moments. 
I installed from a USB drive, incidentally, which went off pretty smoothly. 
But I have a problem now when for various installations, I'm asked to insert the karmic koala CD (my CD drive doesn't work!) to get things to move ahead.



 I try to redirect to the USB drive path, but it doesn't work. 

Then I tried enabling the multiverse option, to create repositories for s/w downloads, but even that didn't work out, as 'the package could not be found'. 

Also, I tried installing an IP Messenger client (tried Gnome, xmemo, iptux) but I wasn't able to figure it out, in the sense, I downloaded the file and unzipped it, but I didn't know what next to do. 

Could anyone please help me with this?

You may want to start a new thread on this one.

---

### Post by lindix on 2009-11-05
> **malcburt said:**
> Sorry, had a bit of a rant last night and don't want to appear ungrateful for the help I'm getting, but I have 2 particular problems which I think are stopping me moving on:
 
1. probably the most serious at the moment, I have had frequent freezes a few minutes after startup using LiveCD, where everything appears to lock up except the mouse continues to move.  Anybody any idea how to diagnose this, is it really less likely to happen if booting from hard drive (as I said I'm very nervous about installing properly at the moment while I've got so many problems)?
 
2. My Netgear WG111v2 Wireless USB Adaptor does not work.  When I disconnect it and reconnect it, *something* happens, i.e. I get a wireless network icon on my desktop which it prompts me to click on but when I move my mous over it, the icon vanishes.  According to [[COLOR=#000000]https://help.ubuntu.com/community/Ha...rdsNetgear#USB[/COLOR]]("https://help.ubuntu.com/community/Ha...rdsNetgear#USB") it seems that this adaptor ought to work out of the box, and I didn't think should need ndiswrapper so I don't know what to do.
 
Any help much appreciated!

I have the same problems.Works fine and fast from CD for 1-2 min and then freeze except the mouse(but I can't click). Sometimes works longer but looks like wireless(network manager) crash(freeze).A Report To Dev. windows appear.But how can I report the bug if don't have internet?Am I stupid?Or this is a stupid way to report bugs?

---

### Post by malcburt on 2009-11-05
> I have the same problems.Works fine and fast from CD for 1-2 min and then freeze except the mouse(but I can't click). Sometimes works longer but looks like wireless(network manager) crash(freeze).A Report To Dev. windows appear.But how can I report the bug if don't have internet?Am I stupid?Or this is a stupid way to report bugs?
 
This problem only seemed to occur using LiveCD (though admittedly haven't tried installing Wubi on that machine yet so I may be premature).  After my experiences with LiveCD I've got a pretty low opinion of it, though Wubi's looking better (a bit).
 
>  
But how can I report the bug if don't have internet?Am I stupid?Or this is a stupid way to report bugs? 

 
Sometimes having a PC that runs Windows on it is quite handy ;)

---

### Post by olofcadiz on 2010-01-01
> **malcburt said:**
> Hi,
I'm getting a bit dispirited at the lack of simple suggestions to diagnose or solve my various problems. I'm an absolute beginner with this and was attracted by some of the press I'd read that suggested that 9.10 was really easy to install. But this isn't my first impression and without any help it'll become my final impression and a possible convert will have been lost.
So if anyone can help I'd REALLY appreciate it or else I'll just go away.

Try ubuntu 9.04 instead of 9.10.
I am a ubuntu user for many years.
When I tried to upgrade to 9.10 I have got screen problems.
I have tried on three different computers and all had similar problems.
Asus, Medion and thinkpad x31.
Nothing of this happen with 8.04 or 9.04.
Dont give up

---

