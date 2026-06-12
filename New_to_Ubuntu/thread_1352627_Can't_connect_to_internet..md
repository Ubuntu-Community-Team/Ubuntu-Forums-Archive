---
title: "Can't connect to internet."
date: 2009-12-11
forum: New to Ubuntu
---

### Post by JustMario on 2009-12-11
Hi, today I did a clean install of ubuntu 9.10. I'm a total noob and have had the worst time first I got the boot error: no such device after spending the whole day I found out what to do, now that I can get to the desktop I can't connect to the internet. Here's what I got router: dlink dir-655 connecting threw a dlink dwl-g122 usb stick, don't have a ethernet card on this pc just wireless stick. I can see my network I can even put in my key but it just doesn't connect, I've been searching all day can't find a solution, I'm about to give up and install xp. I had 9.04 before and the wireless internet worked perfect. I read the previous post here about not being able to connect:

I went to System/Administration/Hardware Drivers, after a short while it reported back that there are ' No proprietary drivers are in use on this system '

same thing for me, I don't know what to install from the cd, please someone help me out this 9.10 install has been a nightmare someone wake me up lol.

---

### Post by bkratz on 2009-12-11
> **JustMario said:**
> Hi, today I did a clean install of ubuntu 9.10. I'm a total noob and have had the worst time first I got the boot error: no such device after spending the whole day I found out what to do, now that I can get to the desktop I can't connect to the internet. Here's what I got router: dlink dir-655 connecting threw a dlink dwl-g122 usb stick, don't have a ethernet card on this pc just wireless stick. I can see my network I can even put in my key but it just doesn't connect, I've been searching all day can't find a solution, I'm about to give up and install xp. I had 9.04 before and the wireless internet worked perfect. I read the previous post here about not being able to connect:

I went to System/Administration/Hardware Drivers, after a short while it reported back that there are ' No proprietary drivers are in use on this system '

same thing for me, I don't know what to install from the cd, please someone help me out this 9.10 install has been a nightmare someone wake me up lol.



According to this post

[http://ubuntuforums.org/showthread.php?t=1266106&highlight=dwl-g122](http://ubuntuforums.org/showthread.php?t=1266106&highlight=dwl-g122)

it is supposed to work out of the box in 9.04 and 9.10.  You might try it without encryption just in case, or maybe whatever problem you had originally is not quite solved.

Good luck

---

### Post by JustMario on 2009-12-11
Thx for the link but I have no idea what to do:

"This wireless adapter works with both Ubuntu 9.04 and 9.10, using the built in Linux driver."

D-Link DWL-G122 USB Wireless Adapter
ID: 07d1:3c03
Linux Driver:  RT73usb


Where do I find this? I'm a total noob, can someone please tell me step by step what to do, I put in the ubuntu 9.10 dvd in the drive went to system, administration, then software sources clicked check the cd box, then went to system, administration, synaptic package manager, this is where im stuck if that's even where im supposed to go from the beginning.

---

### Post by bkratz on 2009-12-11
Go to Applications:Accessories:terminal

A small screen will pop up

Type in

lshw -C network            (that is LSHW in lowercase)

Copy and paste the output back here.

---

### Post by JustMario on 2009-12-11
Thanks for the quick replies appreciate it. Here is what I got:  WARNING: you should run this program as super-user.  *-network       description: Wireless interface       physical id:1       logical name: wlan0       serial: 00:15:e9:31:8c:60       capabilities: ethernet physical wireless       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg wolfpac@wolfpac-desktop:$

---

### Post by JustMario on 2009-12-12
Any ideas what I'm supposed to do? I read somewhere that the drivers might not have been installed from the cd, if that's the case where or what am I supposed to look for?

---

### Post by coffeecat on 2009-12-12
First thing:

> **JustMario said:**
> "This wireless adapter works with both Ubuntu 9.04 and 9.10, using the built in Linux driver."

D-Link DWL-G122 USB Wireless Adapter
ID: 07d1:3c03
Linux Driver:  RT73usb

That was a quote from one of the posts in that linked thread, wasn't it? If your device was using the rt73usb driver it would most likely work just fine, as others have said. Unfortunately, some (all?) wireless device manufacturers have a horrible habit of putting different wireless chipsets in their devices at different times, while still using the same model number, which confuses things badly. We need to confirm whether or not you have the same chipset or a more problematic one.

> **JustMario said:**
>   WARNING: you should run this program as super-user.

Yes, unfortunately you get incomplete output if you don't run that command as superuser. Try again, but this time run:

```
sudo lshw -C network
```That will prompt you for your password which will appear not to be going in when you type it. Don't worry - it is. You should get a large amount of output which you'll need to copy and paste into your post. The keyboard shortcut for copy in the terminal is SHIFT-ctrl-C. Please put the pasted output between [noparse]```

```[/noparse] tags otherwise the formatting is lost.

While you're in the terminal, post the output of:

```
lsusb
```That will give us the ID code for your adapter to compare with the above.

---

### Post by JustMario on 2009-12-13
Hey thanks for the help but unfortunately I had already given up and went back to xp. PC is running slow with xp but at least I have my wireless running. I'll wait for another ubuntu release hopefully they will have some of the bugs ironed out by then.

---

### Post by M4st0d0n on 2010-01-06
Check this thread :

[http://ubuntuforums.org/showthread.php?t=1344100&highlight=DWL+G122](http://ubuntuforums.org/showthread.php?t=1344100&highlight=DWL+G122)

I'm a noob too, enjoying ubuntustudio karmic koala with this <snip> dongle.

Cheers.

---

### Post by santik-solnce on 2010-01-17
Hello. I'm a noob ubuntu user. I upgraded jaunty to koala and the firefox didn't work (it was impossible to connect the Internet). After this > do that open up Mozilla or Firefox and type in '[about:config']("http://about%3Cb%3E%3C/b%3E:config%27") in the address bar
Scroll down to "network.dns.disableIPv6", it's defaulted to a value of false, change it to true.
 it works. But any other browsers, and empathy, and system uploads do not. Also it's impossible to use software center, I can't download anything..
I tried this 
sudo lshw -C networkand

lsusb
After it:

> sveta@sveta-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:80:48:1d:27:8f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.1.2 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:b400(size=256) memory:dc800000-dc8000ff memory:dff00000-dff0ffff(prefetchable)
sveta@sveta-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 3538:0054 Power Quotient International Co., Ltd Flash Drive (2GB)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Please, help me.

---

### Post by santik-solnce on 2010-01-17
Nobody knows? :(

---

