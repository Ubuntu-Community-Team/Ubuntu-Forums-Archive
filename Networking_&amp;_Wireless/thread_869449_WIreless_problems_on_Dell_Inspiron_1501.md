---
title: "WIreless problems on Dell Inspiron 1501"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Tupopoflungo on 2008-07-24
I'm a little new to linux, and I did a search of these forums and couldn't find any answers.

I am trying to figure out how to get my wireless card to work on Ubuntu Hardy.  I updated the firmware...the b43 fwcutter or something along those lines, but I still cannot connect to my wireless network, nor any for that matter, my card is not reading any networks in the area...Help?!?!?!?!?!

---

### Post by Ayuthia on 2008-07-24
> **Tupopoflungo said:**
> I'm a little new to linux, and I did a search of these forums and couldn't find any answers.

I am trying to figure out how to get my wireless card to work on Ubuntu Hardy.  I updated the firmware...the b43 fwcutter or something along those lines, but I still cannot connect to my wireless network, nor any for that matter, my card is not reading any networks in the area...Help?!?!?!?!?!

Can you help provide some additional information for us?  If you don't mind, please open up the Terminal and report back the results of:
```
lshw -C network
uname -a
```
This information will help us identify your wireless card info (make, model, revision) and the current version of Ubuntu you are using.  If you have a Broadcom card, there are some instances where the b43 module might not work with certain kernel versions.

---

### Post by Tupopoflungo on 2008-07-24
heres what i got.

Hardware Lister (lshw) - B.02.12.01


Linux dan-laptop 2.6.24-19-rt #1 SMP PREEMPT RT Sat Jul 12 02:53:01 UTC 2008 i686 GNU/Linux


I had it working at one time, about a week ago, but it was only part working, I could connect to my home wireless network, but none of the other ones I tried.  I did a fresh install of Ubuntu hardy, to see if that would help, and now I can't get it to work at all.

---

### Post by Ayuthia on 2008-07-24
> **Tupopoflungo said:**
> heres what i got.

Hardware Lister (lshw) - B.02.12.01


Linux dan-laptop 2.6.24-19-rt #1 SMP PREEMPT RT Sat Jul 12 02:53:01 UTC 2008 i686 GNU/Linux


I had it working at one time, about a week ago, but it was only part working, I could connect to my home wireless network, but none of the other ones I tried.  I did a fresh install of Ubuntu hardy, to see if that would help, and now I can't get it to work at all.

It seems that the lshw command might have missed something.  The lshw -C network should show your network cards.  Can you do me a favor and post the results of:
```
lspci -nn|grep 14e4
```It will provide the wireless card info as long as it is a Broadcom card.

---

### Post by Tupopoflungo on 2008-07-24
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

---

### Post by Ayuthia on 2008-07-24
> **Tupopoflungo said:**
> 05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

If you have not done this already, you can go to System->Adminstration->Hardware Drivers and look for the Broadcom card.  Enable the card in there and it should download the firmware for you.  If I recall correctly, it will ask you to restart your computer.  After doing all that, you can go to the Terminal and try:
```
sudo iwlist scan
```
This will check and see if it can find any wireless sites.  If it can't, please try and post lshw -C network again.  The lshw -C network command will help us see if it is having any problems with getting the driver up and running.

---

### Post by Tupopoflungo on 2008-07-25
Results of lshw -c Network:

> dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
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
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:4d:ca:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.104 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:54:5c:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Tried the other thing to...to see if there were any networks in range, it didnt find any...but i know that the network is there...because i can  connect to it on my windows pc.

---

### Post by Ayuthia on 2008-07-25
Well, you might try installing NDISwrapper and see if you can get a signal.  I have seen that this card works with the b43 driver, but if this is a fresh install and it appears that you have the firmware installed.

If you do choose to go the NDISwrapper route.  You will need to find an XP driver for it.  If your computer came with XP, just look for bcmwl5.inf and bcmwl5.sys.  Those are the files that are needed.  NDISwrapper is also in the repositories and you will need to download ndiswrapper-common and ndiswrapper-utils-1.9.  Here is a link to a guide that has helped a lot of people:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Tupopoflungo on 2008-07-25
will that guide still help me if im using Hardy?

---

### Post by Ayuthia on 2008-07-25
> **Tupopoflungo said:**
> will that guide still help me if im using Hardy?

Yes.  Even though is still has Feisty in the title, the document has been updated for Hardy.  If you get stuck anywhere, you can always come back here and we should be able to help you along.

---

### Post by Tupopoflungo on 2008-07-26
I followed that guide you sent me to...and i ran into a probem...I got to this

> Hardy Heron (Ubuntu 8.04) users: Issue the command lshw -C network (and ignore the initial warning it gives). This command usually usually lists details about more than one network device: Your wired "ethernet" device is usually listed first, followed by your wireless device--the one we're trying to configure. If, in the "configuration" line, the wireless interface says "module=ssb" instead of "module=ndiswrapper", you've got a problem, so jump to the next section, "Hardy Bug Fix," and then jump right back here.

only, I cant understand what to do after that part...I get easily confused by all this coding and stuff...is there a simple way to do this?

---

### Post by Tupopoflungo on 2008-07-26
I was doing fine...(i think) until i got to this part.

> Hardy Heron (Ubuntu 8.04) users: Issue the command lshw -C network (and ignore the initial warning it gives). This command usually usually lists details about more than one network device: Your wired "ethernet" device is usually listed first, followed by your wireless device--the one we're trying to configure. If, in the "configuration" line, the wireless interface says "module=ssb" instead of "module=ndiswrapper", you've got a problem, so jump to the next section, "Hardy Bug Fix," and then jump right back here.

which i then tried to fix, but I really dont understand all of this coding and stuff...It confuses me.  Is there an easier way to do all of this?

---

### Post by Ayuthia on 2008-07-26
> **Tupopoflungo said:**
> I followed that guide you sent me to...and i ran into a probem...I got to this



only, I cant understand what to do after that part...I get easily confused by all this coding and stuff...is there a simple way to do this?

The next part that you need to do is the Trying It Temporariliy section.  This section will check and make sure that ndiswrapper is working.  If it is, then you can proceed to the Making It Permanent section.

I am not for sure if there is an easy way to do the configuration.  You can try the app that I have posted at the end of the first post of this thread:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754).  It should configure it for you, but it is usually better to test it out before making things permanent.

---

### Post by Tupopoflungo on 2008-07-29
I followed that guide to a T and it still is not working... :(

Please help me.

---

### Post by Ayuthia on 2008-07-29
> **Tupopoflungo said:**
> I followed that guide to a T and it still is not working... :(

Please help me.
Ok.  Let's check the following:
```
ndiswrapper -v
ndiswrapper -l
lshw -C network
```

The first two will check and make sure that we have a valid version and that the driver is installed and device is present.  The last command should show that ndiswrapper is the driver being used.  If it does not:
```
sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up

```
These commands will unload all the conflicting modules and load ndiswrapper.  The last two commands are actually for your wired connection.  It will load it back and then make your wired connection ready.  We had to remove it because ssb is the module that is causing the conflict and the b44 module needs ssb.

---

### Post by Tupopoflungo on 2008-07-29
> dan@dan-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-rt/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-rt SMP preempt mod_unload 586 
> dan@dan-laptop:~$ ndiswrapper -l
WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with 'cat'
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'sudo'
bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: bcm43xx)

> dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
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
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:4d:ca:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.104 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:54:5c:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I don't know where to look for the stuff you were talking about.

---

### Post by Ayuthia on 2008-07-29
> **Tupopoflungo said:**
> I don't know where to look for the stuff you were talking about.Sorry about that.  I did not create my code section correctly.  What I wanted you to try is the following in the Terminal:
```
sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up
```

---

### Post by Tristam Green on 2008-07-29
If I remember correctly, I actually had to press Fn+F2 to get my wireless card working after enabling it.  Did the "WiFi Logo" light ever even come on?

---

### Post by Tupopoflungo on 2008-07-29
> dan@dan-laptop:~$ sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper
[sudo] password for dan: 
WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with 'cat'
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'sudo'

that is what i get when i do the first two...im guessing something is wrong..


And about the FN-F2 thing. I think I did that when i first installed.  It didnt help me, the light randomly comes on every now and then, but it never helps...

---

### Post by Ayuthia on 2008-07-29
[QUOTE=Tupopoflungo;5482818]that is what i get when i do the first two...im guessing something is wrong../QUOTE]
It is saying that there are some things in /etc/modprobe.d/blacklist that should not be in there.  At this point, it should not hurt anything.

Are you able to see any wireless sites when you do this:
```
sudo iwlist scan
```

---

### Post by Tupopoflungo on 2008-07-29
no...I wasn't

Randomly though, I restarted my computer...and I'm seeing my home wireless network now...I dont know what happened...but I'm at least able to see my network.  Which, for the time being, Is enough...



Thanks everyone for whatever it was you did to help me, I may be back in a while though if I have problems!

---

### Post by Ayuthia on 2008-07-29
> **Tupopoflungo said:**
> no...I wasn't

Randomly though, I restarted my computer...and I'm seeing my home wireless network now...I dont know what happened...but I'm at least able to see my network.  Which, for the time being, Is enough...



Thanks everyone for whatever it was you did to help me, I may be back in a while though if I have problems!

Before you restart, please keep track of lshw -C network so that we know what driver it is using.  It will be easier to get it back if we have this information.

---

### Post by Tupopoflungo on 2008-07-29
> dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
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
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:4d:ca:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:54:5c:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=IEEE

Thanks again!

---

