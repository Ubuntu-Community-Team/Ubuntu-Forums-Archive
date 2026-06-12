---
title: "Signal over range issue with Unreal 2004! New game i can't play!!"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by beckyxe on 2010-06-18
This is my first post, and am very much a newbie. And a girl.

I managed to install wine and run Unreal GOTY edition, and it works fine. So i ordered Unreal 2004 and installed in correctly, but when i go to play it my screen goes black and the screen says 'signal over range'.

From reading loads of forum posts regarding this i know it is something to do with the screen resolution, but when i put my resolution up manually to go to 1920x1080 it does this too.

I have a Nvidia 180.44 video card.

Is the game even compatible with my pc? I'm not sure i could tell you the other spec as this pc was given to us by a friend, hence the newbie-ness to ubuntu.

Any help would be greatly appreciated as really want to play it!
And please let me know any other details you need before answering my question.

Seriously though, talk to me like a child and i shall be sort this out!

---

### Post by mk1w86 on 2010-06-18
Welcome to the forums.

Nvidia 180.44 is the driver version, not the actual card model, could you please post the output of:

```
lspci
```

so we can see what hardware you have.

It looks like the resolution the game is outputting is too high for your monitor, although UT2004 usually starts at 800x600 by default which your monitor should be able to display. :confused:

What resolution do you normally use your machine at and what resolution have you been playing UT GOTY at?

Also, which Ubuntu version are you using?  I tried UT2004 in Wine myself a while back (Ubuntu 9.04 I think) but the performance was so bad (I don't know whether it was because of Wine or the proprietary Nvidia drivers) I continued to use it on Windows.  There is actually a native Linux port of the game but I have never got it to work on newer distros because it requires older versions of certain libraries.

EDIT: I've just had a look at the Wine website:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5425](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5425)

and there is mention of the resolution problem you are having towards the bottom of the page, it involved editing you UT2004.ini file which you can find by going to:

Applications > Wine > Browse C: Drive

The file itself should be under UT2004/System. ;)

---

### Post by Perfect Storm on 2010-06-18
If you're using 64-bit version of Ubuntu, I've writen a guide here (tested with ubuntu 10.04): [http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

---

### Post by beckyxe on 2010-06-18
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7500 LE] (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

This is the stuff that appeared in the terminal after lspci.

I am currently running at 1280x1024 and this was also what GOTY was running at too i assume as never had to change it,

I am running Ubuntu 9.04.

Thanks for your help!!!

---

### Post by beckyxe on 2010-06-18
Thanks will try your guide and let you know!

---

### Post by Perfect Storm on 2010-06-18
Signal over range means that your a) card/monitor doesn't support the default resolution the games start with or b) system is not supporting the games default resolution. 
You need to find ut2004 .cfg files in .ut2004 folder and edit th file manually to change the disre resolution.

---

### Post by warfacegod on 2010-06-18
> This is my first post, and am very much a newbie. And a girl.

Welcome to the Forum. What does being a girl have to do with anything? Last time i checked, an excess of estrogen and x chromosomes wasn't a hindrance in computer use. Then again, I'm not a girl so my hands on experience is somewhat limited.:p

---

### Post by mk1w86 on 2010-06-18
> **Artificial Intelligence said:**
> If you're using 64-bit version of Ubuntu, I've writen a guide here (tested with ubuntu 10.04): [http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

Thanks, I'll have to try that.  Thinking back it may have been UT2003 that I had the library problems with, but I have defiantly had UT2003 working on Linux (it would have been Debian 3.1 or 4.0) before. :-k

---

### Post by DrMelon on 2010-06-18
You should find a UT2004.ini file in your Unreal Tournament 2004/System directory - this contains resolution and graphics configurations. Try setting "StartFullscreen" to false, to see if you can run it in a window first.

---

### Post by beckyxe on 2010-06-18
DrMelon 	 		**Re: Signal over range issue with Unreal 2004! New game i can't play!!**
 You should find a UT2004.ini file in your Unreal Tournament 2004/System directory - this contains resolution and graphics configurations. Try setting "StartFullscreen" to false, to see if you can run it in a window first.

YES I CAN SEE IT IN A WINDOW! whoop!

What next?

---

### Post by beckyxe on 2010-06-18
> **warfacegod said:**
> Welcome to the Forum. What does being a girl have to do with anything? Last time i checked, an excess of estrogen and x chromosomes wasn't a hindrance in computer use. Then again, I'm not a girl so my hands on experience is somewhat limited.:p

Lol - Not actually sure why I said that.

---

### Post by beckyxe on 2010-06-18
Ok so i can now play it not full screen but with the task bar still showing at the bottom, this is how GOTY was playing too.

But it is so jumpy!! It i unbearable gameplay, and after a few minutes the game and and the window just disappear!!
Any ideas on why it would do that?

---

### Post by warfacegod on 2010-06-18
Check: System> Admin.> Hardware Drivers> "Recommended" video driver is Activated.

---

### Post by mk1w86 on 2010-06-18
> **beckyxe said:**
> Ok so i can now play it not full screen but with the task bar still showing at the bottom, this is how GOTY was playing too.

But it is so jumpy!! It i unbearable gameplay, and after a few minutes the game and and the window just disappear!!
Any ideas on why it would do that?

Sounds similar to the problem I had when I tried it in Wine, assuming you're still using Wine, not the native Linux version.  Like I said in my previous post, I'm not sure whether it is Wine or the Nvidia drivers and your graphics card should be able to handle the game.

You could try turning down some of the quality settings.  Also what resolution are you running it at in the window?  If it is quite high try lowering it.

The game may also work better in a newer Ubuntu version with newer drivers. ;)

---

### Post by beckyxe on 2010-06-18
> **warfacegod said:**
> Check: System> Admin.> Hardware Drivers> "Recommended" video driver is Activated.

Yes, the recommended driver is selected.

---

### Post by beckyxe on 2010-06-18
> **mk1w86 said:**
>  The game may also work better in a newer Ubuntu version with newer drivers. ;)

Yeah i was thinking of upgrading.

It's being really odd now. Let me play a whole game, relatively choppy free, but my mouse kept refusing to go right and left sometimes. Strange. Mouse is fine usually.

Thanks for everybody who helped, this morning i couldnt see it and now i can. So progress has been made!

---

### Post by warfacegod on 2010-06-18
> Yeah i was thinking of upgrading.

If you're going to go that route, I suggest a Fresh Install. In your particular situation, an Upgrade Install is probably going to make things no different or worse.

---

### Post by beckyxe on 2010-06-18
Boo Hiss.

A lot of forums keep saying to down the patchs. Which i have done and then extracted to the desktop, but i have no idea if they are even being run with Unreal. They seem to just be folders on the desktop...
How do i connect the patch download to the game files?

I have changed the resolution to 800x600 but it still has this weird problem with the mouse blipping out. It won't move and then the mouse pointer ends put of the window and on the desktop behind it, obviously leaving me readyfor a pounding.... after doing this a few times... it vanishes to desktop, never to be seen again!

---

### Post by beckyxe on 2010-06-19
Sorry to bump...
But does anyone have any idea where the patch folder i downloaded needs to go? Extracted to desktop so it is just sitting there.
This is starting to annoy me now.... Really want to play!!

---

### Post by Perfect Storm on 2010-06-19
Where did you install the game?
The patch for ut2004 you need: [http://www.gamershell.com/download_11937.shtml](http://www.gamershell.com/download_11937.shtml)


If you install it systemwide default:
```
cd ~/Desktop
tar jxfv ut2004megapack-linux.tar.bz2 
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004
```

---

### Post by beckyxe on 2010-06-19
bexdre@bexdre-desktop:~$ cd ~/Desktop
bexdre@bexdre-desktop:~/Desktop$ tar jxfv ut2004megapack-linux.tar.bz2 
tar: ut2004megapack-linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
bexdre@bexdre-desktop:~/Desktop$ cd UT2004MegaPack
bash: cd: UT2004MegaPack: No such file or directory
bexdre@bexdre-desktop:~/Desktop$ sudo cp -r * /usr/local/games/ut200

This is what i get when put into terminal.
I downloaded the patch you suggested, it downloaded onto my desktop.

---

### Post by Perfect Storm on 2010-06-19
```
ls -a  ~/Desktop
```

---

### Post by beckyxe on 2010-06-19
Do you want what that brings up?

---

### Post by Perfect Storm on 2010-06-19
I need to see if you're in the right directory, where the file you downloaded. Because the error output you previous posted tells me that you're in the wrong directory when executing the commands.

---

### Post by beckyxe on 2010-06-19
.
..
Becky Stuff
Doco's
Games
jimmy shid
Movies
Music
Pictures
rhythmbox.desktop
TV 
Unreal Tournament 2004.desktop
UT2004-Patch
bexdre@bexdre-desktop:~$

---

### Post by Perfect Storm on 2010-06-19
The patch file isn't at your Desktop.

You need to change directory to the place you downloaded the patch files.

eg. if you downloaded to your Downloads folder;
```
cd Downloads
tar jxfv ut2004megapack-linux.tar.bz2 
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004
```

Also you need to change line 4 if ut2004 isn't installed at /usr/local/games/


...and also cut your previous post for pirated movies and music, by the protocol I could ban you for it. I hope you did not pirated ut2004 as the linux game industry is very fragile for such behavior.

---

### Post by beckyxe on 2010-06-19
Understandable.
Although to make myself feel better i did say in a previous post this desktop has been given to me. The stuff on it came with it...

I am not into downloading and haven't given it a thought as have only used this pc for gaming as have my own laptop.
But hey ho.

Unreal 2004 was bought and paid for from amazon. As was GOTY... as are all the other games i own.

Thanks for your help prior to this, still not quite understanding your instructions but i guess i am tainted now.

---

