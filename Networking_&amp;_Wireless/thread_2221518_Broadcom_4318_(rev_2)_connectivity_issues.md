---
title: "Broadcom 4318 (rev 2) connectivity issues"
date: 2014-05-02
forum: Networking &amp; Wireless
---

### Post by retropedro on 2014-05-02
HI guys, I'm a total linux newbie, but I've read every possible post related to the issue and everything I do seems to just make it worse.  The closest I've gotten was to install the linux-firmware-nonfree package straight after a clean install, which at least let me display a Manage Networks tray icon that shows the wireless networks but won't let me connect after putting in the password.  It have the error for limited or no connectivity, but I can't sort it out T.T

I'm running Lubuntu 14.04 x86 on an old Aspire 3000.  You have to push an external button to activate the wireless, but the light is on and flashing from time to time.  Another problem I seem to be having is that there is no wireless option in the network connections and when I click to configure the ethernet connection, I get an error that the interface does not exist.  Right-clicking on the Manage Networks wireless icon and clicking repair has no effect.

Thanks guys!

---

### Post by mörgæs on 2014-05-02
HI, welcome to the fora.

Your thread has been moved to Networking and Wireless. Please read the sticky notes.

---

### Post by retropedro on 2014-05-02
Hi!  Thanks, I've already read the sticky notes, but the first email I got said to post any queries to the beginner's section.  I'm afraid that nothing they've suggested has solved my problem :/

---

### Post by Rex Bouwense on 2014-05-02
I have to ask.  You said that you installed the firmware, did you also install the correct Broadcom Driver?

---

### Post by retropedro on 2014-05-02
I have no idea - I just followed the tutorial step by step and it ended after the linux-firmware-nonfree install.  Before that, I couldn't see the wireless networks coming up at all, but now I can, if that makes a difference?

---

### Post by Rex Bouwense on 2014-05-02
Because Broadcom Wi-Fi cards have always been a problem, there has been a wealth of threads here and on Ask Ubuntu.
Can you please post the output of placing this command in the LXTerminal
```
lspci -vnn -d 14e4:
```

---

### Post by retropedro on 2014-05-02
Ha yeah I've noticed... I've been trawling the forums for 3 days!  I started off with the b43 drivers installed manually, but it didn't fix the problem.  Having said that though, I don't know if I had the firmware installed first!

acer@acer-Aspire-3000:~$ lspci -vnn -d 14e4:
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at e2000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge

---

### Post by retropedro on 2014-05-02
Additionally, could it have to do with it being a 802.11g controller?

---

### Post by Rex Bouwense on 2014-05-02
OK.  Your card is supported.  How did you install ther firmware (via a connection via ethernet cable hooked directly to your modum or some other way)?   The commands that you should have used are
```
sudo apt-get update
```
and  
```
sudo apt-get install firmware-b43-installer
```
Are we on track so far?

The g is also supported.

---

### Post by retropedro on 2014-05-02
Yeah ethernet is working fine.  Okay I've done the update and installed b43.  It installed fwcutter as well. Shall I reboot?

---

### Post by Rex Bouwense on 2014-05-02
Go ahead and reboot.  There are some commands to test the driver without rebooting but I cannot find them at this minute.  Sorry.

---

### Post by retropedro on 2014-05-02
Sadly, no dice... same issue with the limited connectivity.

---

### Post by Rex Bouwense on 2014-05-02
And one more terminal entry
```
sudo lshw -C network
```

---

### Post by retropedro on 2014-05-02
acer@acer-Aspire-3000:~$ sudo lshw -C network
[sudo] password for acer: 
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:fe:eb:31
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.2 latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:20020000-2003ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e2000000-e2001fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:67:8f:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-24-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by Rex Bouwense on 2014-05-02
It appears that you have the driver loaded.  I am not sure why you are connecting with limited connectivity.
I found a command that apparently worked with Ubuntu 12.10
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```
I cannot vouch for the results.

---

### Post by retropedro on 2014-05-02
No problem - I apprecaite any help!  I gave those commands a whirl and got a an internal error - lxpanel crashed.  Let me reboot and see the result.

---

### Post by retropedro on 2014-05-02
Ah sorry I forgot to reply!  Nope no change!  It's so weird that I can see the networks but not connect to them!

---

### Post by Rex Bouwense on 2014-05-02
Are you sure that you are putting in the correct password?  And that your Caps Lock is not on?  This is weird.

If any of the networks is an open one, try to connect to it.

---

### Post by retropedro on 2014-05-02
Haha yep... pretty sure.  Would it show the limited connectivity error just because I wasn't connected to a network?  Also, this 802.11g thing is bothering me... my router options only have 54g and 802.11b, but it's currently set to auto?

---

### Post by Rex Bouwense on 2014-05-02
According to the chart your card supports b or g, so it should connect.  Out of idle curiosity, before you installed, did you try Lubuntu?  If you did try it, was the Wi-Fi working then?  If you disconnect the ethernet cable, will the Wi-Fi connect?  I am running out of ideas.  Perhaps someone with more knowledge will jump in.

---

### Post by retropedro on 2014-05-02
Oh okay - how come under all that info I pasted earlier it only mentioned g?  Do I have to set it to auto somewhere?  I'm using lubuntu on my current machine with no problem, but it's a much more modern Dell, although also sporting a broadcom controller.  I had to fiddle with that to get it working as well, but I think it's probably down to the new version of Lubuntu if nothing else - I was using 13 previously.  No the error persists if I unplug the ethernet, even from boot, and I can't connect.  Haha well, I'm kind of glad it wasn't a 2 second fix to make me look like an idiot!  I really have read everything I could find and nothing's worked!  Is there any way to raise the priority of the thread if we need a more knowlegable user?

PS, I still really appreciate all your help!

---

