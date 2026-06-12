---
title: "help a new guy with UNetbootin"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by smoresforbrawl on 2009-03-15
I tried using a live CD and that didn't work because my CD might be messed up, I found UNetbootin and made a live USB of Ubuntu. My question is, what is it supposed to do when it starts? So far, when I boot from USB it starts with a screen asking default or OEM (i think there is one more but I can't remember). So I hit enter on  default. Then it loads UBUNKERN and UBUNINIT, don't quote me on those, I have a terrible memory. After UBUNINIT it has alot of ...'s and then it says ready. Thats it.

   Is it supposed to start loading something else? The keyboard didn't work so I got a non USB keyboard and tried again. Same thing, and keyboard doesn't work (both keyboards had lights on though so i know they were on they just wouldn't type anything).

   Am I just being impatient? I waited about an hour when I tried the live CD, so I don't want to waste another hour waiting on this to load. 

   Thanks, SmoresForBrawl

---

### Post by Sealbhach on 2009-03-15
Doesn't sound good. If the Live CD and the USB bootup didn't work then it very likely that your hardware doesn't work with Ubuntu.:(

What kind of hardware have you got?

.

---

### Post by smoresforbrawl on 2009-03-15
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103159](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103159)
I added a different graphics card too

Is it supposed to just zip right past that part that says ready? Should I wait longer? I am really new at this. Is there anywhere that shows what it looks like when it loads?

EDIT: also, my USB is a Sony 4GB. I used Ubuntu 8.10. I am deleting everything off of the USB and switching to 8.04 (maybe that will work).

---

### Post by smoresforbrawl on 2009-03-15
Sorry for the double post

I just thought of something (if this is right, i'm going to feel really stupid). Is there a special Live version of Ubuntu that is different than this download? 

ubuntu-8.10-desktop-i386

---

### Post by Sealbhach on 2009-03-15
You could try the alternate installer

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

It's text based, but very simple to use, it might be that your graphics have to be configured after you've installed it.

Another option is Wubi, for a dual boot.

[http://wubi-installer.org/](http://wubi-installer.org/)

.

---

### Post by smoresforbrawl on 2009-03-16
So I tried using A virtual machine. This is what I get, it had text scrolling past at the top for a little bit but I couldn't read it.

[IMG]http://i413.photobucket.com/albums/pp219/smoresforbrawl/MyCompHatesChange.jpg[/IMG]

Now it says it has to run in low graphics mode. I think you were right, that torrent is almost done so we'll see soon. 

Thanks!

---

### Post by smoresforbrawl on 2009-03-16
now it says 

------------------------------------------------

How would you like to reconfigure your display?

(.) Use default (generic) configuration
( ) Create new configuration for this hardware
( ) Use your backed-up configuration

Cancel   OK

-------------------------------------------------

what should I do?

EDIT: my graphics cards box says "ASUS EAH4350 SILENT" if that helps.

EDIT2: I got it to go to a desktop, now it looks like its in "low graphics mode" I'm not 100% sure of this.
I found this though, [http://ubuntuforums.org/archive/index.php/t-985774.html](http://ubuntuforums.org/archive/index.php/t-985774.html) but have no idea what any of it means. Like I said, I know very little about this stuff. Am I too computer stupid to get this going? Can anyone tell me what that thread means? I don't know what to do with any of that info.

---

### Post by Sealbhach on 2009-03-16
Hi sorry for delay. Was at work today.:(

OK, so you have a desktop?

First thing, let's see what Ubuntu thinks your graphics card is. Open up a terminal from the Applications/Accessories menu and type this:

```
sudo lshw -C display
```

Copy and paste what you get in your next post.

Following the links in that post you mentioned, I found a page with precompiled Radeon HD drivers.

[https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)

This is probably the one you want here:

Install both of these:

[http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-radeonhd/xserver-xorg-video-radeonhd-dbg_1.2.4+git20090313.d9c8f9ce-0ubuntu0tormod_i386.deb](http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-radeonhd/xserver-xorg-video-radeonhd-dbg_1.2.4+git20090313.d9c8f9ce-0ubuntu0tormod_i386.deb)

[http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-radeonhd/xserver-xorg-video-radeonhd_1.2.4+git20090313.d9c8f9ce-0ubuntu0tormod_i386.deb](http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-radeonhd/xserver-xorg-video-radeonhd_1.2.4+git20090313.d9c8f9ce-0ubuntu0tormod_i386.deb)

Give it a try, you can always uninstall it if it doesn't work.


.

---

### Post by smoresforbrawl on 2009-03-16
I can't copy and paste from the virtual pc for some reason. Heres a screencap though. Is this low graphics mode?

[IMG]http://i413.photobucket.com/albums/pp219/smoresforbrawl/ubuntuhelppic.jpg[/IMG]

Also I tried to install the two packages and they said

Error: Dependency is not satisfiable: xserver-xorg-core

I looked on the box to the graphics card, and found where it said Radeon HD 4350

It didn't say that on the card list for those drivers.

Thanks for helping me!

---

### Post by Sealbhach on 2009-03-16
OK, because you're inside a virtual machine, ubuntu is not detecting your real hardware, just the virtual machine "hardware".

See this post here:

[http://ubuntuforums.org/showthread.php?t=359244](http://ubuntuforums.org/showthread.php?t=359244)

It doesn't look like low graphics mode, but according to that thread you won't be able to use accelerated graphics (somebody correct this if it's wrong). 


.

---

### Post by smoresforbrawl on 2009-03-16
Okay, I am going to try to use the text only torrent you gave me. But before I do, can I get to this site in text only mode? Can I install those drivers in text only mode? Hopefully it won't hang up. 

On an unrelated note, I have an old laptop that doesn't have internet capability, is there a way to install without having an internet connection? Every time I try to install it stops and asks to connect.

---

### Post by Sealbhach on 2009-03-16
> **smoresforbrawl said:**
> Okay, I am going to try to use the text only torrent you gave me. But before I do, can I get to this site in text only mode? Can I install those drivers in text only mode? Hopefully it won't hang up.

The text-based installer won't do anything different. The issue is that you are using a virtual machine, so your accelerated graphics driver won't work. That's how I understand it.


> 
On an unrelated note, I have an old laptop that doesn't have internet capability, is there a way to install without having an internet connection? Every time I try to install it stops and asks to connect.

I'm sure you can install Ubuntu without needing a connection, it will try to connect but them timeout. How old is it? If it's low in RAM you might need to use Xubuntu or even a smaller distro like Crashbang or Puppy or Damn Small Linux.


.

---

### Post by smoresforbrawl on 2009-03-16
(desktop PC)
The only way I can get it to not hang is try it on virtual machine. But with the text based version I will use a USB and boot from that. 

(Laptop)
Sorry I don't know what some stuff means, when you say "times out", you mean just wait for a while and it will go away? It had 256MB RAM but when I try to install in windows (it won't boot from USB) it  says "you have 255MB of RAM, ubuntu needs 256MB of RAM". Then it asks to go ahead and I click yes. (linux mint also did this)

---

### Post by smoresforbrawl on 2009-03-17
(Desktop PC)
I tried to boot with the alt version (text based) by USB.
It still hangs at the- 

(I can't remember what it said, I think it was ubnkern)
        
Loading ubnkern.................................
......................................ready
_ (flashing)

-screen. Would a graphics card make it do that? So far the only way I can get it go past that screen is in virtual PC.

(Laptop)
I let it set on that screen overnight and this morning it was still on it. I am trying to find a way to boot from USB, maybe it won't need an internet connection if I boot from USB instead of trying to install from Windows. I also tried Puppy Linux on it, but couldn't find a way to install from windows.

EDIT: I found something that said Smart Boot Manager needs a floppy disk to start. I don't have on though, but I do have a floppy drive in the laptop. Maybe I can find a floppy disk somewhere.

EDIT 2: Finally some progress! I ran Puppy linux on my desktop PC just to see if it would work. It booted from USB and ran right past the part that other distros hung at. It configured something called XORG and then started up great. Does that narrow down any issues why Ubuntu won't work? I am going to try Ubuntu again... I know it is illogical and literally the definition of insanity, but I am bored and want to do something.

EDIT 3: I just looked, the first line says "ubnkern" then the next line says "ubninit" then a bunch of periods, then ready. It just sits there.

---

### Post by Sealbhach on 2009-03-18
> **smoresforbrawl said:**
> 

EDIT 3: I just looked, the first line says "ubnkern" then the next line says "ubninit" then a bunch of periods, then ready. It just sits there.

There's probably not much you can do if it's in that state. Between the boot menu and the loading of Xorg (the graphical environment) it's all a bit of a black box (unless you can run dmesg from the command line) so I don't think there's much you can do...

Good to see the Puppy worked for you.


.

---

