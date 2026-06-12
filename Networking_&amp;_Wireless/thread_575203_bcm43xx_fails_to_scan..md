---
title: "bcm43xx fails to scan."
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by etricks on 2007-10-13
Hello.
I've been lurking these forums for a few months now, and I usually figure things out by people's past solutions, but this one doesn't seem to have been solved yet.

I am running 7.04 Feisty on an HP dv6000 model laptop with a built in wireless adapter using a Broadcom Chipset.  I should probably start off by saying that I can, and have been able to get this working fairly easily using Ndiswrapper.  However, I'm taking a wireless security course and I will need to run Kismet on this laptop.  In order to do that, I need to use the native drivers for the bcm43xx that have been included in the kernel since 2.6.17-rc2.  These were installed using fwcutter.  When I do a 'modprobe bcm43xx', the blue light comes on meaning that my wireless adapter is, in fact on.  The problem comes up when I use 'sudo iwlist eth1 scan':

```

eth1          No scan results

```

So without further ado, here is some information about my system.

The output from a 'uname -a' command:
```

Linux stardestroyer 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux

```

The output from an 'iwconfig' command:
```

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The output from 'ifconfig eth1' (my wireless adapter)
```

eth1      Link encap:Ethernet  HWaddr 00:00:00:1A:73:7C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3528 (3.4 KiB)
          Interrupt:255 Base address:0x8000 

```

When I run 'dmesg', I see a lot of this lovely business:
```

...
[ 4949.933380] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4954.930739] printk: 1249 messages suppressed.
[ 4954.930745] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4959.928096] printk: 1249 messages suppressed.
[ 4959.928102] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4964.925465] printk: 1244 messages suppressed.
[ 4964.925472] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
...

```

Other information:

- I am booting with the options 'noapic noirqfixup irqpoll'

- Kismet *is* running, I just can't capture anything.  This means that the adapter is successfully entering monitor mode?

- ndiswrapper is blacklisted in my /etc/modprobe.d/blacklist file, there should be no conflict here.

- There are, in fact APs that I should be able to see.  I tested this in a lab with an AP operating a few feet away from me.

I have spent days trying to troubleshoot this problem, and I have no idea at this point.  If the adapter is on, what is stopping me from at the very least seeing APs in my area?  Please help, and thank you for reading all this :)

- Eric

---

### Post by j.bunce on 2007-10-13
Take a look at this post [http://ubuntuforums.org/showthread.php?t=256795](http://ubuntuforums.org/showthread.php?t=256795)

---

### Post by etricks on 2007-10-13
> **j.bunce said:**
> Take a look at this post [http://ubuntuforums.org/showthread.php?t=256795](http://ubuntuforums.org/showthread.php?t=256795)

Thanks for the reply.  I read through that thread before making my post and nfortunately, there was no solution found.  I'm trying to see if maybe a little more information will help get this sorted out.

---

### Post by gdselzer on 2007-10-25
I'm having the same issue.  I'm pretty sure it's because the new version of this card is still unsupported by the bcm43xx project.

See:[http://linuxwireless.org/en/users/Drivers/b43#unsupported]("http://linuxwireless.org/en/users/Drivers/b43#unsupported")

> unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * bcm4311 rev 2
    * There is no support for any Draft 802.11n features. 

I have the following

```
lshw

*-network
             description: Wireless interface
             product: BCM94311MCG wlan mini-PCI
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             logical name: eth1
             version: 02
             serial: 00:00:00:1a:73:61
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14
```

I'm pretty sure the version: 02 means I have rev 2 of the 4311 card.  I'm curious if you have the same?  If I'm wrong about this, I'd sure like to know before I completely give up.

---

### Post by jardo on 2007-10-25
i have rev01 and it either works with bcm4311:(

---

### Post by jeromio on 2007-12-15
> **gdselzer said:**
> I'm having the same issue.  I'm pretty sure it's because the new version of this card is still unsupported by the bcm43xx project.

See:[http://linuxwireless.org/en/users/Drivers/b43#unsupported]("http://linuxwireless.org/en/users/Drivers/b43#unsupported")



I have the following

```
lshw

*-network
             description: Wireless interface
             product: BCM94311MCG wlan mini-PCI
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             logical name: eth1
             version: 02
             serial: 00:00:00:1a:73:61
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14
```

I'm pretty sure the version: 02 means I have rev 2 of the 4311 card.  I'm curious if you have the same?  If I'm wrong about this, I'd sure like to know before I completely give up.This is bad news for me. I finally seem to have the card "working" - that is, it is enabled (as seen in knetworkmanager), the light on the toggle is blue as opposed to red. However, I still cannot connect. My lshw output is almost identical to yours. Rev2, eh? Crap.

---

### Post by Coward on 2007-12-16
> I finally seem to have the card "working" - that is, it is enabled (as seen in knetworkmanager), the light on the toggle is blue as opposed to red.

I have a Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) card, ndiswrapper is installed with the bcmwl5 driver working, yet no wireless networks are detected and the light on my computer is still red. What did you do to make your light blue?

---

### Post by gdselzer on 2007-12-16
I followed this guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") and it worked like a charm.

Just to check, you do have the wireless switch in the "on" position, right?

---

### Post by Cybermax on 2007-12-16
How come every thread about the BCM43xx problem always ends up in 2-3 ppl linking "ndiswrapper" howto's? I mean.. read what the OP posted, cos i have exactly the same problem, xept im having a bcm4312 (rev 02) chip in mine.. but the problem is the same..

The OP posted that he basically want kismet to work.. And we know that Kismet is not working with the ndiswrapper package, as the ndiswrapper cannot put the windows driver in monitor mode. Kismet "may" work with bcm43xx kernel module, but that depends atleast to get the module working first before twiddling with any kismet config files.

So.. Any hints on getting the bcm43xx driver to work (without linking to yet another ndiswrapper-howto).

C

---

### Post by gdselzer on 2007-12-16
Cybermax, you'll notice that Coward had indicated that he had ndiswrapper loaded but that the card was still not working.  I was just trying to help point him in the right direction.

Previously within this thread I had pointed out that bcm43xx does not support rev 02 of these cards.  You should try the new b43 driver if you need kismet.  I saw somewhere that it will be part of Hardy, but to install on Gutsy you need to recompile the kernel.  Have fun.

---

### Post by Flare183 on 2007-12-16
The files you need are attached. Install the firmware then the fwcutter. Then use the fwcutter to extract the firmware. After that, in the terminal type in this:

sudo modprobe bcm43xx

then 

sudo dhclient

---

### Post by Cybermax on 2007-12-18
> **Flare183 said:**
> The files you need are attached. Install the firmware then the fwcutter. Then use the fwcutter to extract the firmware. After that, in the terminal type in this:

sudo modprobe bcm43xx

then 

sudo dhclient
Sadly this did not help. Same problem as before with my broadcom 4312 (rev 02) chip.

--
bcm43xx: Unsupported 80211 core revision 13
bcm43xx: Invalid PHY Revision 9
bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
bcm43xx: MAC suspend failed
...
...
---

C

---

