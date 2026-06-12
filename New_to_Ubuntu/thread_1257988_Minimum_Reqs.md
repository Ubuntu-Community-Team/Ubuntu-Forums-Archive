---
title: "Minimum Reqs"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by txbbqdude on 2009-09-04
Hello all...

I am new to the Ubuntu community and am looking for advise, please.

To begin with, I am FED  UP and absolutely SICK of Windows!!! I want to install Ubuntu on one of my laptop computers as a "test run" to see if I want to do the same for all my machines.

The laptop I am trying to install it on is 'ancient' in computer years. Its a Panasonic CF47 with only 128mg of RAM and and 60g HD and a PIII processor. Will this be enough to run Ubuntu and get a fair evaluation?  All help appreciated.

TXBBQ

---

### Post by defacto on 2009-09-04
128MB of RAM might be not enough for running Ubuntu ( Gnome ) - I would suggest Xubuntu ( XFCE ).

---

### Post by drs305 on 2009-09-04
Here is the Ubuntu specs page:
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

Even the lightweight Xubuntu says it needs 192MB minimum for a full, normal install. But check the bottom of the page anyway, where alternatives are mentioned (48MB min for GUI).

---

### Post by halitech on 2009-09-04
Use the alt install cd and do a minimal install and then put LXDE on it for the desktop, should work fine.

---

### Post by Simian Man on 2009-09-04
Frankly no.  You can install Linux on that machine, but it will either take a lot more work (you'll have to go with a different set of default software or a different distribution), or it will be unbearably slow.  To get a really fair idea of a modern Linux system, you will need a more modern computer.

I'd recommend trying [Puppy]("http://puppylinux.org/wikka/HomePage") on that machine personally, it has very low [requirements]("http://www.puppylinux.org/wikka/MinReq") while still being fairly easy to use.

---

### Post by earthpigg on 2009-09-04
Desktop Linux really took off in user friendliness around the time that machines with more than 256 mb of ram became normal...

...a lot of the effort developers have put into making Linux friendly on the desktop assume (and thus require) that the machine have 256 mb of ram.

essentially, you will be going back in time to the way Linux was a decade or so ago.

if you are prepared to face that learning curve, then have at it & good luck!

i wrote the following and have an ego, so keep in mind that may have something to do with the link i am about to post :D 

take a loot at the first two paragraphs here, and then step 2. see how much sense you can make of that. if the answer is 'not to much', then you need to ask if you are willing to overcome that and put forth some effort into learning.

[http://sites.google.com/site/masonux/home/notes-to-myself](http://sites.google.com/site/masonux/home/notes-to-myself)

if you can google around yourself to fill in the holes of your knowledge (i did not write that as a beginner's guide at all), that will give you an outline/idea of what you need to do to install and get a simple desktop up and running.

focus your googling on:
LXDE
Linux Desktop Environments
Linux Window Managers
Software Repository
debian package
sudo & root

---

### Post by ashwinhgtx on 2009-09-04
> **halitech said:**
> Use the alt install cd and do a minimal install and then put LXDE on it for the desktop, should work fine.

Seconded. LXDE is available in the repositories. So you can install it using apt. 
After you have installed using the alternative CD, do this.

```
sudo apt-get install lxde
```

This will give you the LXDE package. LXDE is a fast, stable and very light desktop environment while it is very functional and user friendly.

[http://www.lxde.org/](http://www.lxde.org/)
[http://en.wikipedia.org/wiki/LXDE](http://en.wikipedia.org/wiki/LXDE)

The above instructions will only give you a basic install with a desktop environment. Search through the repositories and install whatever media player, browser etc. you need. 

apt is your best friend.

Have fun.

---

### Post by earthpigg on 2009-09-04
more like:

```
sudo apt-get install xorg lxde
sudo mkdir /usr/share/backgrounds
```

xorg is not a dependency of the lxde package, for some reason.

/usr/share/backgrounds needs to exist or the screen saver app of LXDE gives annoying error messages.

:D

---

### Post by ashwinhgtx on 2009-09-04
> **earthpigg said:**
> more like:

```
sudo apt-get install xorg lxde
sudo mkdir /usr/share/backgrounds
```

xorg is not a dependency of the lxde package, for some reason.

/usr/share/backgrounds needs to exist or the screen saver app of LXDE gives annoying error messages.

:D

That's weird. The LXDE package in Debian pulls up xorg as a dependency.
BTW I'm downloading your distrolet right now. :)

---

### Post by mbzn on 2009-09-04
Personally I would suggest to try the live cd on one of your newer systems to get the feel of what Ubuntu is as the lightweight desktops will give you a different feel. the live cd won't mess with your windose installation if you don't tell it to. It will be allot slower than what the (installed) Ubuntu on your hdd will be, but it will give you the idea.

---

### Post by hockeytux on 2009-09-04
> **txbbqdude said:**
> Hello all...

I am new to the Ubuntu community and am looking for advise, please.

To begin with, I am FED  UP and absolutely SICK of Windows!!! I want to install Ubuntu on one of my laptop computers as a "test run" to see if I want to do the same for all my machines.

The laptop I am trying to install it on is 'ancient' in computer years. Its a Panasonic CF47 with only 128mg of RAM and and 60g HD and a PIII processor. Will this be enough to run Ubuntu and get a fair evaluation?  All help appreciated.

TXBBQ

I can only confirm that. Ive got a 256MB Ram laptop with a 40 gig HD and Ubuntu is veeery slow. Xubuntu works a little better.
If you would like the full version of Ubuntu you can try the Live CD in your desktop (if you have one). You dont have to install anything.

For your laptop I recommend installing Ubuntu Minimal and then get LXDE as a desktop environment which is very lightweight. Alternatively you could wait for the release of Lubuntu or try a different lightweight Linux distro like Crunchbang which is also very easy to install.

---

### Post by snowpine on 2009-09-04
> **txbbqdude said:**
> Hello all...

I am new to the Ubuntu community and am looking for advise, please.

To begin with, I am FED  UP and absolutely SICK of Windows!!! I want to install Ubuntu on one of my laptop computers as a "test run" to see if I want to do the same for all my machines.

The laptop I am trying to install it on is 'ancient' in computer years. Its a Panasonic CF47 with only 128mg of RAM and and 60g HD and a PIII processor. Will this be enough to run Ubuntu and get a fair evaluation?  All help appreciated.

TXBBQ

If you have a newer/faster computer, use that instead. Ubuntu is a fantastic distro when run on up-to-date hardware. If you try to install it on an ancient computer, you might walk away with the mistaken impression that "Linux sucks!" ;) 

ps You don't need to get rid of Windows entirely--you can set up a dual boot where you choose which OS to use each time you boot. It is good to have Windows to fall back on if you need it. Good luck!

---

### Post by achianese on 2009-09-04
I second the people who suggest trying a dual-boot with a newer computer. That way you get a more modern experience. Installing a dual-boot setup is incredibly easy, assuming your hardware is supported.. Just pop in the Live CD and let Ubuntu make some space automatically on your hard drive.

Of course, backing up your data first is essential.

---

### Post by txbbqdude on 2009-09-04
Hey everybody....

Thanks a bunch for your time and suggestions. I will try the xubunto and await the Lubuntu.

Can I download the Xubuntu and accompanying LXDE? (whatever the desktop is). Also, do I need the i386 version or which one should I DL? I have a PIII remember? Can someone point me in the right direction please? I am sorry to sound so clueless, but I really am. This is my very first experience looking into Ubuntu, so I am learning from scratch and will appreciate all the help & guidance I can get.

Thanks in advance
TXBBQ

---

### Post by Windows Nerd on 2009-09-04
> **txbbqdude said:**
> Hey everybody....

Thanks a bunch for your time and suggestions. I will try the xubunto and await the Lubuntu.

Can I download the Xubuntu and accompanying LXDE? (whatever the desktop is). Can someone point me in the right direction please? I am sorry to sound so clueless, but I really am. This is my very first experience looking into Ubuntu, so I am learning from scratch and will appreciate all the help & guidance I can get.

Thanks in advance
TXBBQ

That's okay, Ubuntu can be quite confusing at first! The first would be to familiarise yourself with Xubuntu. This can be done by making a "Live CD" of the most recent distro of Xubuntu. You can find them at Xubuntu's official site, here:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

It is pretty staightfoward to navigate thier site. You may want to try the alternate install CD, as it only requires 64 Mb of RAM. When you download this, it will come as an ISO, or a CD image, which you must burn to a blank CD. IsoRecorder or ImageBurn work quite well to do this. You may also want to check the quality of the download before burning it too. Go here for more information on doing this:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

After you burn a LiveCd, pop it into the Computer's disk drive, and restart the machine. If your computer can boot from a CD, you will be presented with a list of options after the the BIOS loads. Choose "try Ubuntu without any change to you computer" and hit enter. Then you will boot from the CD. You will come up to a normal Xubuntu desktop. Note that the LiveCD may be slow to load, but this is because you are running an entire operating system from your disk drive. 

If you like what you see, double-click the install icon to install it to your system. Chosoe Guided, unless you want to keep your Windows partition. The installer will guide you through the install process.

This is all I have time for to type, so I hope all goes well.

Scott

---

### Post by oldos2er on 2009-09-05
The recommended minimum RAM for a LiveCD is 384MB. The OP might want to look into Puppy Linux, DSL, or something similar.

---

### Post by txbbqdude on 2009-09-09
Thanks Scott and everyone else who responded. I appreciate it and am DLing Xubuntu alternative. I'll be back to post notes of my impressions. I am looking forward to it.

TXBBQ

---

### Post by earthpigg on 2009-09-09
this thread happened today, and may be of interest to you:

[http://ubuntuforums.org/showthread.php?t=1262121](http://ubuntuforums.org/showthread.php?t=1262121)

---

