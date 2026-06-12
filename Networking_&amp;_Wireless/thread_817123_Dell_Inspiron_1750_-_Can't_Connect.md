---
title: "Dell Inspiron 1750 - Can't Connect"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Gant on 2008-06-03
I'm sure there's probably other topics about this, and I'm sorry in advance if there is. However, I'm easily frustrated and I just want to get this done.

I'm 100% brand-new to ubuntu and linux in general. I installed Ubunutu just fine, but I can't seem to connect to the network. My network has no security (no WEP or anything, I turned it off to try and get this to work) but I still can't get in. Even if I plug my laptop right up to my desktop's LAN cable, I can't get Ubuntu to connect to the internet at all. What's the simplest, quickest way to get this working for a complete and total newb?

---

### Post by superprash2003 on 2008-06-03
go to the terminal and type ifconfig and post output here

---

### Post by Gant on 2008-06-03
I have no internet on my laptop so I'll try and re-type it here as best as I can (oh boy, this is gonna be a project.)

```
eth0      Link encap:Ethernet  HWaddr 00:18:8b:a8:8d:7f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collision:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 0)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436 Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:76600 (74.8 KB)  TX bytes:76600 (74.8 KB)
```

It may be a little different then it would be at my house since I'm at my girlfriend's, but they're both the same brand + model number of Linksys router and it's the same computer, so I don't see what difference it would make.

---

### Post by vexingmodstwo on 2008-06-03
> **Gant said:**
> I have no internet on my laptop so I'll try and re-type it here as best as I can (oh boy, this is gonna be a project.)

```
eth0      Link encap:Ethernet  HWaddr 00:18:8b:a8:8d:7f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collision:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 0)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436 Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:76600 (74.8 KB)  TX bytes:76600 (74.8 KB)
```

It may be a little different then it would be at my house since I'm at my girlfriend's, but they're both the same brand + model number of Linksys router and it's the same computer, so I don't see what difference it would make.

This is gonna suck but if you can post the output of:

```
sudo lshw -C network
```

... that will help with troubleshooting.

EDIT:  It will really really help if you get an ethernet cable and plug directly into the router.

---

### Post by Gant on 2008-06-03
All it says is 

PCI (sysfs)

and I don't know why. D:

EDIT: I tried plugging it right into the router previously, thinking it would work, but to no avail. I'll try it here though in a second. She's playing Nibbles... :x

---

### Post by vexingmodstwo on 2008-06-03
> **Gant said:**
> All it says is 

PCI (sysfs)

and I don't know why. D:

EDIT: I tried plugging it right into the router previously, thinking it would work, but to no avail. I'll try it here though in a second. She's playing Nibbles... :x

Nothing comes up after PCI (sysfs)?  That's usually just a little message telling you that stuff is being looked up.

You might have some deeper problems that I can't help you with if you don't get an output from the command above.

---

### Post by Gant on 2008-06-03
When I initially installed Ubuntu, I downloaded the .iso off the official website and burned it to a DVD-R using ImgBurn at 2x speed. The first time I tried, I got an error, but the second time I tried it seemed to work smoothly (barring the fact that when it cycled the tray, I needed to push it in since it's a laptop).

A lot of programs say that I can't install them because they don't support i386 computers. Does the type of computer I have have anything to do with it? I stated the model number off the top of my head before; it's actually an Inspiron E1705. Maybe my computer just can't run Ubuntu properly?

---

### Post by vexingmodstwo on 2008-06-03
> **Gant said:**
> When I initially installed Ubuntu, I downloaded the .iso off the official website and burned it to a DVD-R using ImgBurn at 2x speed. The first time I tried, I got an error, but the second time I tried it seemed to work smoothly (barring the fact that when it cycled the tray, I needed to push it in since it's a laptop).

A lot of programs say that I can't install them because they don't support i386 computers. Does the type of computer I have have anything to do with it? I stated the model number off the top of my head before; it's actually an Inspiron E1705. Maybe my computer just can't run Ubuntu properly?

We're treading in an area I'm not very well versed in (I'm a newbie too, I just happened to get this to work).

Did you download the 64 bit version?

---

### Post by Gant on 2008-06-03
Oh...Maybe that's where I went wrong.

On this page:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I checked the "Personal Computer" button...is that the problem? Should I have checked the 64-bit AMD/Intel button? If so, that's a pretty n00bish mistake on my part...

---

### Post by vexingmodstwo on 2008-06-03
> **Gant said:**
> Oh...Maybe that's where I went wrong.

On this page:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I checked the "Personal Computer" button...is that the problem? Should I have checked the 64-bit AMD/Intel button? If so, that's a pretty n00bish mistake on my part...

You want to have downloaded the desktop version (the top choice in the top section) and the "Standard Personal Computer" option in the  second section (the top choice in the second section).

Is that what you downloaded?  If so, you have the right one as far as I know and hopefully someone with a bit more knowledge can pipe in here.

Unless you have a 64 bit laptop, of course.  But then you're definitely in another area that I just have no experience with.

---

### Post by Ayuthia on 2008-06-03
> **Gant said:**
> All it says is 

PCI (sysfs)

and I don't know why. D:

EDIT: I tried plugging it right into the router previously, thinking it would work, but to no avail. I'll try it here though in a second. She's playing Nibbles... :x

Can you see if it will work without the sudo?
```
lshw -C network
```It will tell you that you need to be super user, but that is ok.

EDIT:
Can you also post your uname -a info?  It will tell us what you are using.

---

### Post by Gant on 2008-06-03
It worked without the "sudo" prefix. 

```
gant@gant-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:a8:8d:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.101 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:f6:b0:d8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by vexingmodstwo on 2008-06-03
Okay... since that's the case, I would suggest you follow this How To:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf)

---

### Post by Ayuthia on 2008-06-03
You can try the b43 driver first.  It is the easiest to install.  Here is a link on how to get installed:

[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

---

### Post by Ayuthia on 2008-06-03
> **vexingmodstwo said:**
> Okay... since that's the case, I would suggest you follow this How To:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf)

You can try this one also, it has more steps and you will need to add the b44 fix to ndiswrapper also since you do have the Broadcom wired card that uses the b44 driver.

I would recommend going with the b43 option first.  I have the same card and it works with with either option.

---

### Post by vexingmodstwo on 2008-06-03
> **Ayuthia said:**
> You can try this one also, it has more steps and you will need to add the b44 fix to ndiswrapper also since you do have the Broadcom wired card that uses the b44 driver.

I would recommend going with the b43 option first.  I have the same card and it works with with either option.

Yes, good call.  It's always good to have options.

---

### Post by Gant on 2008-06-03
> **Ayuthia said:**
> You can try the b43 driver first.  It is the easiest to install.  Here is a link on how to get installed:

[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Sweet. It worked. Thanks a ton, and thanks to everyone else who helped too.

I do have a couple smaller questions though...One for safety's sake:

- I've read that restarting will cancel out all these settings. Is this true? If so, how do I stop that from happening?

And one for my own curiosity:

- What does the "sudo" prefix mean or do?

Thanks you guys/girls. You have made me a very happy camper.

---

### Post by Ayuthia on 2008-06-04
Restarting should not cancel out these changes.  The b43 driver is part of the Ubuntu kernel so the driver will boot every time.  It just needed a portion of the proprietary firmware to make it work.  The b43-fwcutter installed the missing firmware so now it will be able to run.

The NDISwrapper option is the one that needs to have additional work to make it start up the next time.  You have to blacklist the b43 driver and make sure that NDISwrapper is in /etc/modules so that it will load up the next time.  

This is the reason why I recommended the b43 option first.  It is not that I like or dislike NDISwrapper.  It just has extra steps that need some extra knowledge to help make it install easier.

EDIT:
I forgot to answer the second portion of your post.  sudo is used to provide super-user privileges.  What this means is that it places you in administrator mode and allows you to make changes to files that could affect your system.

---

