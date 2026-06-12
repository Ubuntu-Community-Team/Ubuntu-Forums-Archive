---
title: "Intermittent crashes and bugs on 2 week old hardy install"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by BlakeWolf on 2009-07-13
Hi all!

I'm having some trouble with my maiden voyage into Linux (in this case Ubuntu 8.04). It's been two weeks since I installed Hardy on my system, with quite a bit of help from this forum. (Thanks!) Since then it has unfortunately shown considerable instability. 

Frequently the system simply hangs - often in connection to some kind of audio/video activity, either online or directly on my hard drive. Sometimes the system spontaneously switches into a command-line only mode, which I've now found can be accessed using ctlr+alt+f8. Also, quite frequently, the graphics give out and the screen goes black at the login screen during boot. Up until this point the display is alive. I can login "blindly", but the display remains black even after login, and restart is the only option.

From reading on these forums and others I suspect that my graphics are somehow to blame. I'm not excluding problems with my hardware either (the system is 4 years old, and has taken quite a beating under Windows during this time).

My system:
Ubuntu 8.04 x64
AMD64 3700+
MSI K8N SLI Platinum
Saphire Radeon X1650 (Proprietary driver installed)

Please let me know what other info is needed to diagnose the problem. Thanks!

---

### Post by LewRockwell on 2009-07-13
Hi and thanks for the feedback

Take 9.04 Jaunty Jackalope LiveCD for a test drive and see how it works with your equipment

Also note, I recommend backing-up what you need to and then doing a fresh install of Jaunty(personal preference learned from previous problems with "upgrades")

as always, your mileage may vary...

.

---

### Post by BlakeWolf on 2009-07-14
Thanks for your reply LewRockwell!

I'm afraid I've tried Jaunty, however briefly, already. My graphics card works very poorly under Jaunty as it is an ATI card no longer supported by ATI. As I understand it Jaunty packs a newer version of something called Xorg for which I need a newer driver. For this reason, I opted to try for Hardy instead.

I'm afraid I don't think Jaunty is the solution.

---

### Post by shifty_powers on 2009-07-14
is that a pci-e card? if so, then getting even the cheapest nvidia card will potentially solve your problems... it'll certainly allow you to use jaunty...(not what you are looking for i'm sure, but thought i'd mention it :P)

---

### Post by ivikas on 2009-07-14
Hello BlakeWolf,

                As you said it's your maiden voyage into Linux and i presume you may not have advanced knowledge of Linux.Ubuntu is a good userfriendly OS and there's no doubt about it.Your system is AMD64 and i presume based on my experiance things won't work better on especially AMD 64 .It will work, but will require a whole lot of patience to troubleshoot errors as and when it occurs.I used ubuntu 8.04.2 64 bit version but for me most of things worked for first time but later problem began to happen like "connecting to internet with windows driver",screen resolution losses often,sometime no GUI only command line text login.i used to trouble shoot them with patience but most time is wasted on this effort.if still you want to try download this(ubuntu **8.04.2** AMD) version and run the live cd to test whether everything is working like  sound,recording etc...if satisfied go on for the install.This is the link

```
http://releases.ubuntu.com/8.04/ubuntu-8.04.2-desktop-amd64.iso
```

Since you are a new comer to linux,i suggest you to try other distribution like mandriva linux,so you will start to love linux (rather than hating it as first expriance being bad) and may be continue the journey back to ubuntu.

I think mandriva is a good simple os for new bees.I hope the other community members will help you to get on with a good starter os for your new maiden journey...

Enjoy the journey....Good Luck

with regards,
Vikas

---

### Post by shifty_powers on 2009-07-14
or indeed linux mint, a very good ubuntu based distro..

---

### Post by tarps87 on 2009-07-14
You say you are using the proprietary driver, do you still notice these problems when using the open source driver?

@ivikas

I don't believe that it being a 64 bit processor will be causing these issues, the only problems I have ever had with the 64 bit version was support in terms of proprietary applications like flash, but this was a while a go. It is more likely to be related to the graphics driver

---

### Post by BlakeWolf on 2009-07-14
shifty_powers:
Yes, the card is pci-e. And you're right - buying a new card is not my preferred solution. But if it turns out to be the only viable solution then I will of course consider doing so. Do you think using Jaunty will sort out my problems? Along the same lines - do you think Linux Mint will solve my issues, and why?


ivikas:
I am currently using the amd64 version of Ubuntu as a matter of fact (unfortunately, that might have been an easy fix otherwise). Do you think Mandriva would be a better distro for me to try out, and if so why?

tarps87:
Is the open source driver the default driver that comes with a fresh install? I opted to use the proprietary driver within hours of installing Hardy, as it allows me to use ATI Catalyst Control Center and by extension TV-out. This is a very important feature for me, as my system serves as my home entertainment system and DVD.

---

### Post by Mulenmar on 2009-07-14
I have a PCI-E based ATI Radeon HD 2700, and it worked fine under Jaunty with the open-source drivers. Try those on your system. They weren't as good back in the Hardy days, but they should work.

If all else fails, try the plain VESA driver (package xserver-xorg-video-vesa, and uninstall the other video drivers). It supposedly is slower, but I haven't noticed.

---

### Post by tarps87 on 2009-07-15
> **BlakeWolf said:**
> 
tarps87:
Is the open source driver the default driver that comes with a fresh install? I opted to use the proprietary driver within hours of installing Hardy, as it allows me to use ATI Catalyst Control Center and by extension TV-out. This is a very important feature for me, as my system serves as my home entertainment system and DVD.

Is there any way that you could try and recreate the problem with the open source driver (default), is would determine if it is the driver or something else. If it is not easy to recreate this probably isn't and option.
The only other thing I can think of at the moment is that it is related to the OS being 64 bit.

---

### Post by BlakeWolf on 2009-07-15
Ok, I've deactivated the ATI proprietary driver now. I have no idea how to recreate the problems intentionally, but I'll let my system run with the default driver for a while and see what happens. I'll let you know if anything has happened in a day or two.

In case this turns out to solve the stability issues - does anyone know how to get TV-out support without using ATI Catalyst Control Center? This is really important to me.

---

### Post by BlakeWolf on 2009-07-16
Alright, I've now run my system with all the usual apps (browser w. streaming video, vlc, etc) for a full day on the open source driver without errors.

Apparently my system isn't stable with the fglrx driver. The problem is - I don't know how to get tv-out without it! This is a deal-breaker for me.

Does anyone know how to get tv-out using the open source driver, or how to tweak the fglrx driver to run stable?

---

### Post by tarps87 on 2009-07-17
There are two things you can try (I have not tried ethier method as I am using a nvidia card with out the tv out option):

1) Configure the open source driver
(Using these steps from the [Arch wiki]("http://wiki.archlinux.org/index.php/ATI#TV_out"))

The first step is to look at the output of 
```
xrandr
```

you are looking for this line "S-video disconnected" or "S-video connected"

2) Try using the driver from ati's website.
To do this you will need to download the driver from here:
[support.amd.com]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English")
and follow the instructions here:
[BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20%28latest%20version%20of%20drivers%29") section titled Install from ati.com (latest version of drivers)
Where is says "ensure the ATi drivers have the execute flag set first"
```
chmod a+x *filename*
```

---

### Post by Bartender on 2009-07-17
Blake -
I'd like to repeat the earlier "get an Nvidia card" message.  It's not worth it screwing around with a poorly supported ATI card.
I don't know how different things are in Sweden, but I've used the ASUS EN8400GS in three different Linux installs now.  It's a PCI-X card with D-sub, DVI and S-video outputs.  It's fanless.  Not a gaming card but works great for everything else.  I picked another one up at Newegg recently for $33.  It'll be $22 after the $10 rebate.
Ubuntu 9.04 identified hardware drivers, downloaded and installed, very nice and hassle-free.

---

### Post by BlakeWolf on 2009-07-17
**Bartender:**
Things are quite similar here, getting a cheap card would be easy. 

As a matter of principle, however, I would consider it a horrible failure to have to buy new hardware in order to run an OS that I switched to in the first place because I thought my old one didn't work well enough (XP). Kind of defeats the purpose of my switch - don't you think? If the new OS can't even handle the basics of the hardware as well as the old OS, well ... See my point?

Along the same line of thought - another argument for switching to Ubuntu Linux was that it is free, as opposed to any Microsoft Windows. If I then have to pay money (even if it isn't much) in order to use Ubuntu, this argument too fails. I'm not running an exotic set of hardware here, I expect my OS to handle it.

Sorry for the rant, I'm not mad at you. Just a little frustrated with my seemingly poor options at the moment. :S

**tarps87:**
Thanks for the ideas! I'll try both of your suggestions tomorrow or the next day. I'll check back afterwards to let you know how it went.

---

### Post by BlakeWolf on 2009-08-01
Sorry for the long pause in activity from my part - I haven't had the will power to work on my problem for a while. Today, however, I did.

**tarps87**, your suggestion about using the latest driver from ati.com seems to have worked! I've run the computer through a full movie, meanwhile streaming video from skynews in firefox and no crashes or freezes. Couldn't get the open source driver to work with tv-out though, sadly. xrandr reports that the s-video connection is in fact detected, but I can't get any output from following the how-to.

Thanks a load for the help and support!

---

### Post by tarps87 on 2009-08-03
> **BlakeWolf said:**
> Sorry for the long pause in activity from my part - I haven't had the will power to work on my problem for a while. Today, however, I did.

**tarps87**, your suggestion about using the latest driver from ati.com seems to have worked! I've run the computer through a full movie, meanwhile streaming video from skynews in firefox and no crashes or freezes. Couldn't get the open source driver to work with tv-out though, sadly. xrandr reports that the s-video connection is in fact detected, but I can't get any output from following the how-to.

Thanks a load for the help and support!

I'm glad to here it's solved.

---

