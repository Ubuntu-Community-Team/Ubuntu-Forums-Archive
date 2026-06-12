---
title: "Network speed crawls, and what card do I have?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Longshot9 on 2011-02-08
I'm a total Ubuntu noob, I try just about every major release just to see if I can actually use it and make the switch from Windows... but there's always something I can't figure out how to do so I just give up.  I just installed a dual-boot of Win7 and Ubuntu 10.10 and here's the issue i'm having...

Whenever I try to download anything... updates to the OS... files from the internet... Amarok... whatever, my speed starts out normally (500-1000 KB/s)... my office has a 25mbps internet connection... but after downloading about 12mb of data, it just crawls... i'm talking like 2-3 BYTES/s.  One of my linux user friends told me I should try another mirror, same problem.  I was trying to figure out if there's an updated driver but I don't know how to find out what network card I have in my system.  I suppose I could look on Asus's website.  

Does anything think it's a NIC driver issue, or is there something else that could be causing this to happen?  FYI, I also have 10.10 installed on my netbook, no problems.  Win7 on this desktop works just fine also (re: internet speed)

Thanks for the advice.

---

### Post by P4man on 2011-02-08
to find out what hardware you have, open a terminal (apps > accessories > terminal) and copy paste these commands:
```
lspci
```

or more detailed info:

```
lshw -C network
```

(caution, case sensitive, C has to be UPPERcase). Copy paste the output here.

---

### Post by Longshot9 on 2011-02-08
> **P4man said:**
> to find out what hardware you have, open a terminal (apps > accessories > terminal) and copy paste these commands:
```
lspci
```or more detailed info:

```
lshw -C network
```(caution, case sensitive, C has to be UPPERcase). Copy paste the output here.

Here's what it says I have - Atheros Communications L1 Gigabit Ethernet (rev b0)

---

### Post by P4man on 2011-02-08
PLease copy paste the entire output of both commands.

---

### Post by Longshot9 on 2011-02-08
jhough@U-jhough:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet (rev b0)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
jhough@U-jhough:~$

---

### Post by Tyggna on 2011-02-08
Well, you can always try tweaking with the card settings with ethtool.

```
ethtool -s eth# duplex full autoneg off
```

---

### Post by Longshot9 on 2011-02-08
jhough@U-jhough:~$ ethtool -s eth# duplex full autoneg off
Cannot get current device settings: No such device
  not setting duplex
  not setting autoneg
jhough@U-jhough:~$ ethtool -s eth0 duplex full autoneg off
Cannot get current device settings: Operation not permitted
  not setting duplex
  not setting autoneg

---

### Post by Tyggna on 2011-02-08
sorry, it's not literally eth#, you need to know what number linux has given you, you can see that by typing ifconfig, and it'll list all your network cards on the left side.

eth means ethernet, or wired internet

lo  is loopback and used for diagnostics

wlan is wireless

Also, it needs to be ran as root, so put a sudo in front of it for the eth0.

```
sudo ethtool -s eth0 duplex full autoneg off
```

---

### Post by Longshot9 on 2011-02-08
ok, yeah i figured that out and ran it with eth0 but it still didn't work.  didn't know i had to put sudo in front.  it ran ok, but still getting horrid speed.

[IMG]http://img826.imageshack.us/img826/3856/screenshot3bf.png[/IMG]

---

### Post by Tyggna on 2011-02-08
> **Longshot9 said:**
> ok, yeah i figured that out and ran it with eth0 but it still didn't work.  didn't know i had to put sudo in front.  it ran ok, but still getting horrid speed.

[IMG]http://img826.imageshack.us/img826/3856/screenshot3bf.png[/IMG]

there's also a speed directive, you can type in:
```
ethtool eth0
```
for a list of all the operating parameters on your network card.
This seems like its barking up the wrong tree, but you could try the following options and one of them might work:
```

ethtool -s eth0 speed 1000 duplex full autoneg off
ethtool -s eth0 speed 100 duplex full autoneg off
ethtool -s eth0 speed 100 duplex half autoneg off
ethtool -s eth0 speed 10 duplex full autoneg off
ethtool -s eth0 speed 10 duplex half autoneg off

```
If it works at a lower speed, that's a sign of a damaged card.  If it works when you use one of the duplex half options, then the network that you're plugging into is either crappy quailty or old.

Like I said, might be barking up the wrong tree with that--but it's worth trying.

Looking over this, it seems that this problem is seen with the 64-bit drivers on the aetheros cards.  Are you running the 64-bit version of Ubuntu?  If none of those options above work, then the above posts are spot on--and you need to hunt down newer drivers for your card--which it looks like you're doing from the picture you posted.  
[This]("http://partner.atheros.com/Drivers.aspx") might be a useful place to start.

---

### Post by Longshot9 on 2011-02-08
ok, ran those and no help.  i am running 64b so i'll check that link.

---

### Post by Tyggna on 2011-02-08
> **Longshot9 said:**
> ok, ran those and no help.  i am running 64b so i'll check that link.

K, make sure you re-run the top one to make sure your card doesn't operate at speeds slower than what it's capable of when it does start working.

Also you didn't make any permanent changes so when you restart the computer it'll be a moot point.

---

### Post by Longshot9 on 2011-02-08
I found the driver on their website but everytime I try to extract it, I get the following...

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error is not recoverable: exiting now

Is this just a bad archive or am I doing something wrong?

---

### Post by Tyggna on 2011-02-08
> **Longshot9 said:**
> I found the driver on their website but everytime I try to extract it, I get the following...

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error is not recoverable: exiting now

Is this just a bad archive or am I doing something wrong?

Probably, I'm not sure to be honest.

---

