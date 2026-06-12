---
title: "Dell 1390 WiFi (Broadcom 4311) On Gutsy w/Restricted Drivers"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by marke1 on 2007-10-22
So I have Gutsy x64 installed and everything works great except the Dell 1390 wireless mini-PCI card with Broadcom 4311 chipset.

I installed the restricted driver firmware that ships with Gutsy so the card does come up on the system without any need for ndiswrapper stuff. I can see if with ifconfig just fine. The problem is that it won't see any wireless APs even when I'm sitting 3 feet in front of my access point. There's no prob with the AP since I can connect with other computers in the house. 

Anybody know why the card can't see any networks? I'm almost thinking that the radio is disabled, ,but then again I doubt it - it was enabled when I ran WinXP on the same system before wiping that and installing Gutsy. 

Anybody have a clue why I can see any networks? I even installed Kismet, got that config'd for the card, and it doesn't help to see any networks either. Even if I manually enter AP access info it still won't connect. 

Here's the lspic -v info: 

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint IRQ 0

lspci -n info: 

0c:00.0 0280: 14e4:4311 (rev 01)

iwconfig info: 

eth1      IEEE 802.11b/g  ESSID:"thishouse"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s   Tx-Power=18 dBm
          RTS thr: off   Fragment thr: off
          Encryption key: ECF5-E8B-D7   Security mode: open
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid :0  Rx invalid crypt :0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

---

### Post by noob12 on 2007-10-23
My story FWIW

After trying for a while to get the restricted driver to work on my Dell 620 with the same 4311 rev 01 chipset, I abandoned that and went back to the ndiswrapper-based solution I was using with Feisty which I installed using  the online installer in this sticky HOWTO thread: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Minutes later I was up and running.

Frankly, that ndiswrapper-based solution has been so robust and full-featured for me (using it with WPA and NetworkManager in roaming mode just fine) that I don't have any motivation to expend the effort go native.

I'm on the 32-bit generic kernel BTW.

---

### Post by marke1 on 2007-10-23
Well I'm actually using Kubuntu so the guy's script that you pointed to won't run since it's designed around python-gtk.  But maybe I can take a look at the code and figure out what it does and do that stuff manually.  Does it automatically download a copy of the Windows driver file? I don't have a copy myself and if I use ndiswrapper I'll need the driver.

---

### Post by marke1 on 2007-10-23
So I disabled the "restricted drivers" bcm43 firmware, then I install bcm43xx using the ndiswrapper method and the 1390 comes up on the system. BUT, it still will not scan any networks. 

Anybody know what the problem might be?

---

### Post by marke1 on 2007-10-23
SOLVED!

OK, so for anyone else who might have a similar situation as me where the radio on the 1390 just seemed to NOT work, or at least the card wouldn't scan for networks when using the built-in bcm43xx driver and "restricted drivers" firmware on Ubuntu 7.10 or Kubuntu 7.10 Gutsy Gibbon here's the deal: 

I went to the BIOS settings and disabled the Bluetooth card. Then suddenly the Dell 1390 works fine with both built-in drivers and ndiswrapper method ! 

This was on an Inspiron E1705. It might help to try this on other problematic systems.

:)

---

### Post by rosegarden78 on 2008-01-21
Type nm-applet from a terminal to activate wireless and network scanner in all Ubuntu flavors.

---

### Post by diablo75 on 2008-03-01
I found the solution to this problem in the BIOS as well, but it had nothing with Bluetooth.  It had to do with the wireless adapters presense to the OS on boot, with a simple Yes or No option.  It was set to be off by default at start.

In addition to this, another option allows you to decide if you want to let software control your wireless adapter, or whether or not you want to enforce the use of Fn-F2 in order to turn the adapter on and off manually.

What a stupid feature, eh!  :)

This was on a Dell Inspiron 1300 by the way.

---

