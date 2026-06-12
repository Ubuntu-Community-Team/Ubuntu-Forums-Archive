---
title: "Netgear WG511 v2 (China) not supported: true?"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by noisyjazzman on 2007-02-03
According to [this (link)]("http://linux-wless.passys.nl/query_chipset.php?chipset=Marvell"), my made-in-China Netgear WG511 v2 (man code as given by lspci: 11ab:1faa (rev 03) ) will not work with Linux. So it appears my efforts to date to get it working with Edgy (failed so far) have been wasted.

Does anyone know for certain that this is true or false? Any successes with this exact model?

---

### Post by tturrisi on 2007-02-03
[http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear)
islsm: [http://prism54.org/newdrivers.html](http://prism54.org/newdrivers.html)

---

### Post by noisyjazzman on 2007-02-03
> **tturrisi said:**
> [http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear)


That's essentially the same as the link I posted. As in general I've found that information on wireless networking under Linux is wildly inconsistent, I was interested to hear whether anyone has reason to believe it is either  true or false that this card does not work. 

> **tturrisi said:**
> [http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear)


Not quite clear what that's about. What's islsm?

---

### Post by noisyjazzman on 2007-02-04
Could any one here who understands this stuff advise whether or not the diagnostic info I have below offers any hope for getting this working?

I've followed all the standard instructions for installing the Windows 2000 driver under ndiswrapper, and am using gnome-network-manager (and have commented out all my /etc/network/interfaces other than loopback).

The network manager applet *does* show me my available wireless networks. When I click on my  (WPA-Personal-encrypted) network to connect, it disconnects the wired network and gives me a dialog to type my key into. When I submit that, the applet whirs about for a bit, and then just reconnects the wired network.

iwlist scan does show my available networks.

Here's some selected output from some other diagnostic stuff:

**lspci**: 04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

**ndiswrapper -l**: wg511v2         driver installed, hardware present 

**iwconfig: **
```
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**tail /var/log/messages:**
```
Feb  4 14:01:11 jupiter kernel: [17253356.704000] ndiswrapper: driver wg511v2 (NETGEAR,09/17/2004,3.1.0.19) loaded
Feb  4 14:01:11 jupiter kernel: [17253356.708000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
Feb  4 14:01:11 jupiter kernel: [17253356.708000] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [C0C0] -> GSI 11 (level, low) -> IRQ 11
Feb  4 14:01:11 jupiter kernel: [17253356.708000] ndiswrapper: using irq 11
Feb  4 14:01:11 jupiter kernel: [17253357.276000] wlan0: vendor: ''
Feb  4 14:01:11 jupiter kernel: [17253357.276000] wlan0: ethernet device 00:0f:b5:8e:d4:ae using NDIS driver wg511v2, 11AB:1FAA:1385:4E00.5.conf
Feb  4 14:01:11 jupiter kernel: [17253357.276000] ndiswrapper (set_encr_mode:689): setting encryption mode to 6 failed (C00000BB)
Feb  4 14:01:11 jupiter kernel: [17253357.276000] wlan0: encryption modes supported: WEP; TKIP with WPA
Feb  4 15:02:10 jupiter kernel: [17257015.220000] ndiswrapper (set_encr_mode:689): setting encryption mode to 6 failed (C00000BB)
Feb  4 15:02:12 jupiter kernel: [17257017.220000] ndiswrapper (set_essid:59): setting essid failed (C0000001)
Feb  4 15:02:12 jupiter kernel: [17257017.228000] ndiswrapper (set_encr_mode:689): setting encryption mode to 6 failed (C00000BB)
```

Clearly some things appear OK here (eg. the hardware is being recognised, and network discovery is happening), but I don't know enough about how all this works to be able to tell what the next step might be. I'd be grateful for any advice.

---

### Post by noisyjazzman on 2007-02-04
I really don't know where to go with this, so any suggestions would really be appreciated. 

If no-one has any direct thoughts, any idea where else I might go, what to read, etc?

---

### Post by gradedcheese on 2007-02-04
Hmm... your card has a Marvell 'libertas' chipset.  That should actually work fine in Linux but the libertas driver isn't fully matured and thus isn't included with the kernel yet.  

Unless I'm mistaken, you need to grab the libertas driver (and firmware for the 8335) separately and install them.  The firmware is just a matter of putting the firmware file in the right place (/lib/firmware/kernel_name_here on recent Ubuntu distributions) and you can snag the file off the Windows install CD.

---

### Post by noisyjazzman on 2007-02-04
> **gradedcheese said:**
> Hmm... your card has a Marvell 'libertas' chipset.  That should actually work fine in Linux but the libertas driver isn't fully matured and thus isn't included with the kernel yet.  

Unless I'm mistaken, you need to grab the libertas driver (and firmware for the 8335) separately and install them.  The firmware is just a matter of putting the firmware file in the right place (/lib/firmware/kernel_name_here on recent Ubuntu distributions) and you can snag the file off the Windows install CD.

Forgive the further questions here, but my knowledge about this stuff is limited.

Is this libertas driver a linux-native one that I would use instead of ndiswrapper? If it isn't included in the kernel does that mean I find sources and recompile the kernel? 

Also the reference to 'firmware' confuses me. Isn't firmware what goes into an EEPROM? What's its role here?

---

### Post by gradedcheese on 2007-02-04
Hi.  Yes, it's a real Linux driver.  I'm not in to the ndiswrapper thing...  you might find an ubuntu package but chances are you will need to compile the driver (not the whole kernel).  To do that you will need development packages and kernel source installed, so it will be a bit of learning and work.

An explanation about the firmware: wireless chipsets actually consist of a microcontroller (ie: small CPU) running the logic of the WiFi card in software.  This is done so that bugs can easily be fixed and features added by just modifying the software.  When the card is detected by an OS, it expects to have this software sent to it each time.  The software is a compiled binary (in this case for an ARM9 CPU) that your OS have to have ready to send.  Until that happens, the card can't do anything because its micrcontroller has no code to run (aside from the firmware loader).  A further complication is FCC requirements and regulations, requiring that WiFi cards (being radios) don't violate certain rules.  In order to do that, the chipset's manufacturer has to ensure that you can't mess with radio settings on the card to make it act in a non-compliant way, and thus they provide binary-only firmware.

---

### Post by noisyjazzman on 2007-02-04
> **gradedcheese said:**
> Hi.  Yes, it's a real Linux driver.  I'm not in to the ndiswrapper thing...  you might find an ubuntu package but chances are you will need to compile the driver (not the whole kernel).  To do that you will need development packages and kernel source installed, so it will be a bit of learning and work.

An explanation about the firmware: wireless chipsets actually consist of a microcontroller (ie: small CPU) running the logic of the WiFi card in software.  This is done so that bugs can easily be fixed and features added by just modifying the software.  When the card is detected by an OS, it expects to have this software sent to it each time.  The software is a compiled binary (in this case for an ARM9 CPU) that your OS have to have ready to send.  Until that happens, the card can't do anything because its micrcontroller has no code to run (aside from the firmware loader).  A further complication is FCC requirements and regulations, requiring that WiFi cards (being radios) don't violate certain rules.  In order to do that, the chipset's manufacturer has to ensure that you can't mess with radio settings on the card to make it act in a non-compliant way, and thus they provide binary-only firmware.

Thanks for the information, much appreciated. It's looking to me like it's going to be too difficult for a non-expert like me to get wireless networking going; but I'll keep on trying for a while.

---

### Post by gradedcheese on 2007-02-04
yeah, you may want to keep trying the ndiswrapper route to get it working as it will probably be easier.  later, when libertas is stable and accepted into the kernel, things should 'just work'

---

### Post by noisyjazzman on 2007-02-04
> **gradedcheese said:**
> yeah, you may want to keep trying the ndiswrapper route to get it working as it will probably be easier.  later, when libertas is stable and accepted into the kernel, things should 'just work'
 
I may have to wait for that point before using Ubuntu (or some other linux) as so far my ndiswrapper experiments have failed (as described above). This is no doubt due to the fact that I don't really know what I'm doing, and (I freely admit) am only willing to spend a very limited amount of time to learn.

But also I think the state of documentation is chaotic and inconsistent, which doesn't help non-experts. I've had a look through threads on wireless here, and the advice given tends to be contradictory, off in all kinds of different directions etc. Obviously people are just trying to help. But it doesn't always actually help. Certainly I'm getting nowhere.

---

### Post by gradedcheese on 2007-02-04
Well, here's how I look at it: you happen to have a WiFi card that is not exactly supported.  This is because its manufacturer didn't help the community work (for free!) to add support, nor did they step in and help themselves.  So you have two options, install an in-development driver that the community is working on (which indeed is not easy) or use ndiswrapper to install the Windows driver under a wrapper, so to speak.  Neither option is that nice but you can sort of see why, right?

Now, on the other hand, you could grab a different card where either the manufacturer was more helpful or the community had enough time to reverse-engineer and otherwise build a stable driver.  I have one in my laptop right now and, once I plug it in, wireless works instantly and reliably.  In fact, this same card is very difficult to use on Windows because the manufacturer's supplied driver (Belkin) is really bad (in Windows with the Belkin driver, the installer barely works, the wireless is unreliable, etc).  

You probably won't like this, but my advice is to change cards (they're pretty cheap anyhow) and enjoy a nice Ubuntu experience :)

---

### Post by noisyjazzman on 2007-02-04
> **gradedcheese said:**
> Well, here's how I look at it: you happen to have a WiFi card that is not exactly supported.  This is because its manufacturer didn't help the community work (for free!) to add support, nor did they step in and help themselves.  So you have two options, install an in-development driver that the community is working on (which indeed is not easy) or use ndiswrapper to install the Windows driver under a wrapper, so to speak.  Neither option is that nice but you can sort of see why, right?

Now, on the other hand, you could grab a different card where either the manufacturer was more helpful or the community had enough time to reverse-engineer and otherwise build a stable driver.  I have one in my laptop right now and, once I plug it in, wireless works instantly and reliably.  In fact, this same card is very difficult to use on Windows because the manufacturer's supplied driver (Belkin) is really bad (in Windows with the Belkin driver, the installer barely works, the wireless is unreliable, etc).  

You probably won't like this, but my advice is to change cards (they're pretty cheap anyhow) and enjoy a nice Ubuntu experience :)

I don't disagree with any of that, and I'm certainly not blaming the OS community for not supporting a card, when really the manufacturer should be doing the supporting (ie. of linux).

But I'm still not that likely to buy a new card ;) I have a personal rule, for good environmental and anti-consumerist reasons, to get at least 3 years out of every bit of gear I buy.

I'll keep trying for a bit, and perhaps in the end just accept that I'll have to wait a while before being a full-time linux user.

---

### Post by richbouchard on 2007-02-06
Hi njm,

Thought I'd post to give you hope!  I've been fiddling around trying to get a WG511v2 (made in China) card working for 18 months, on and off.  Yesterday, I got it to work for the first time!

Just to be absolutely clear here, I'm talking about the card with the Marvell/Libertas chipset, using ndiswrapper.  lspci gives the same output as you.  ndiswrapper -l is almost identical, except includes the chip identifier 11AB:1FAA between 'driver installed' and 'hardware present'.

Now the disappointing bit: I'm not using Ubuntu any more.  I gave up on it a few months back when I just couldn't get the thing working.  Finally installed OpenSUSE and had another week of frustration, until it worked (almost out of the blue) yesterday.

That said, I think my setup could probably help you.  SUSE uses KNetworkManager to handle wireless networks, but I couldn't get it to work for me, so I had to 'revert to manual'.  In the control centre, under network devices, you can select to use NetworkManager or the 'Traditional Method with ifup'.  I selected the latter, told it to use ndiswrapper as the module name and suddenly it worked!

I must've changed just about every setting imaginable over the last week or so, and fiddled around in a root console ifconfig, iwconfig and iwlist etc.  And some of this is SUSE specific, but this is a rough guide to what I did...

[LIST]
[*]Install ndiswrapper
[*]get Windows XP driver from CD (W2k didn't work)
[*]install driver with ndiswrapper -i [path to inf file]
[*]check installation with ndiswrapper -l
[*]start SUSE YaST Control Centre
[*]choose 'Traditionl Method with ifup' (rather than NetworkManager)
[*]enter ndiswrapper as Module Name
[*]auto DHCP config, with 'Request Broadcast Response' selected
[*]enter network name (ESSID)
[*]choose 'Open' mode (for no encryption)
[*]OK everything and wait, while holding breath!
[/LIST]

Green light on card flashes away, slowly, then suddenly goes solid green (I'd had this a couple of times with NetworkManager, but still had no access to the internet).  Orange light flickers showing data transfer (again, I'd had this with NM, but was unable to ping or browse, even to my router).  But this time, using 'ifup' method, I got a connection!  

Re-booted - card came up during boot and connected fine.

Reset router to use WEP - reset YaST control centre settings - card connected fine.

Reset router to use WPA - reset YaST control centre settings - green light just blinks. No connection :-(

Now, my level of knowledge is about the same as yours, by the sounds of it(!)  But I'm pretty sure that YaST is just changing text files in etc/config/ blah blah all those linux paths to files that windows users hate!  So if some expert can come along and tell us what settings YaST is changing, I can delve and find out what's what and pass it on to you.

Hope the above helps.  All the best,

Rich

> **noisyjazzman said:**
> 

**lspci**: 04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

**ndiswrapper -l**: wg511v2         driver installed, hardware present 

---

### Post by noisyjazzman on 2007-02-07
> **richbouchard said:**
> Hi njm,

Thought I'd post to give you hope!  I've been fiddling around trying to get a WG511v2 (made in China) card working for 18 months, on and off.  Yesterday, I got it to work for the first time!

... 


Many thanks for the info. It's great to hear an instance proof that it can work. I've temporarily given up, as I have again hit a limit of how much time I dare afford just to get stuff working. But I've filed away your post for reference for the next time I play around with this stuff. Maybe I'll even give openSUSE a try.

Cheers.

---

