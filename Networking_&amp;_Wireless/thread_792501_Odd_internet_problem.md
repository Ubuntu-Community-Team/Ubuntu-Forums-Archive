---
title: "Odd internet problem"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by kmc77 on 2008-05-13
Just installed Hardy on Sat. and I've noticed an odd problem.  When my computer is running on a wireless network, everything runs fine.  Speeds are fast and stable.  But when I plug in to a wired network, everything changes.  I really didn't notice it this weekend, as I only use the wireless at home, but I plug my laptop in at work, so it was very apparent today.

While plugged in the wired network, all network activity stops unless my mouse is in motion (and it's only the mouse that will help it - touch pad does nothing).  I know, this sounds silly, but I've messed with it all day, and I'm positive that this is the case.  Web pages freeze mid image load.  Bittorrent drops to nothing.  FTP uploads stall.  It's quite odd.  But, as soon as I move the mouse things begin to load again.  If I stop moving the mouse while loading a web page, it never times out ("unable to load web page error".)  It just sits there indefinitely.  I'm a little stumped.  I've attached some images but I don't know if they're worth anything.

Any help would be appreciated.
[IMG]http://myweb.cebridge.net/kmc77/images/extra/Screenshot_1.png[/IMG]
[IMG]http://myweb.cebridge.net/kmc77/images/extra/Screenshot_2.png[/IMG]
[IMG]http://myweb.cebridge.net/kmc77/images/extra/Screenshot_3.png[/IMG]

---

### Post by hermes0710 on 2008-05-13
Is this happening when running on AC too?

---

### Post by chili555 on 2008-05-13
Please open a terminal and do:```
sudo tail -f /var/log/messages
```Then leave the terminal open as you reproduce this activity. Does the kernel throw out any complaints? Any IRQ complaints?

---

### Post by kmc77 on 2008-05-13
> Is this happening when running on AC too? 
Yes.  I just noticed with updates this morning, that the update manager times out if I don't constantly wiggle my mouse.  When I try to access network files (on a windows network ((not over internet)) the same thing happens.  It seems that everything network related is affected.

@chili555
> sudo tail -f /var/log/messages returns
> kevin@kevin-laptop:~$ sudo tail -f /var/log/messages
May 13 07:14:02 kevin-laptop syslogd 1.5.0#1ubuntu1: restart.
May 13 07:27:37 kevin-laptop -- MARK --
May 13 07:47:37 kevin-laptop -- MARK -- with no change during "wiggle" vs "non-wiggle" events. (Wow, just reading that makes me feel silly)

---

### Post by chili555 on 2008-05-13
How about letting us see:```
sudo cat /var/log/messages | grep eth0
```Substitute whatever your wired interface is, if it's not eth0. *messages* keeps its log for several days, so just give us the messages for today. As long as we're at it, let's see:```
sudo cat /var/log/messages | grep IRQ
```It reminds me, based on nothing but hunch and a scratch of my white beard, of an IRQ conflict.

---

### Post by kmc77 on 2008-05-13
> sudo cat /var/log/messages | grep eth0
> sudo cat /var/log/messages | grep IRQ
come up with nothing, which I thought was strange, so I went to /var/log to see what was going on.  

While the messages file was empty, messages.0 was not, and messages.1 was compressed to a .gz.  Also my syslog was jam packed, with 4 compressed files.  Just out of curiosity I checked the file size of messages.0 - 24Mb.

Anyway on to the info.

> sudo cat /var/log/messages.0 | grep eth0
returned too much to post, but essentially many repeats of this:
```
May 12 08:20:39 kevin-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 12 08:20:39 kevin-laptop kernel: [   70.791405] b44: eth0: Flow control is off for TX and off for RX.
May 12 08:20:43 kevin-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
May 12 08:20:43 kevin-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
May 12 08:20:43 kevin-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 12 08:20:43 kevin-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 12 08:20:43 kevin-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
May 12 11:19:03 kevin-laptop kernel: [ 7336.196090] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:03:25:08:6d:f2
May 12 11:19:06 kevin-laptop kernel: [24773.191515] b44: eth0: Link is up at 100 Mbps, full duplex.
May 12 11:19:06 kevin-laptop kernel: [24773.191533] b44: eth0: Flow control is off for TX and off for RX.
May 12 11:20:02 kevin-laptop kernel: [   17.304970] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:03:25:08:6d:f2
May 12 11:20:06 kevin-laptop kernel: [   48.915868] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:03:25:08:6d:f2
May 12 11:20:10 kevin-laptop kernel: [   51.714940] b44: eth0: Link is up at 100 Mbps, full duplex.
May 12 11:20:10 kevin-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 12 11:20:10 kevin-laptop kernel: [   51.714948] b44: eth0: Flow control is off for TX and off for RX.

```
and
> sudo cat /var/log/messages.0 | grep IRQ
returned a lot of this:
```
May 13 07:07:38 kevin-laptop kernel: [   20.190989] ACPI: PCI Interrupt 0000:00:0d.1[B] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
May 13 07:07:38 kevin-laptop kernel: [   20.379262] ACPI: PCI Interrupt 0000:00:0d.2[C] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
May 13 07:07:38 kevin-laptop kernel: [   34.373398] Yenta: ISA IRQ mask 0x00f8, PCI irq 10
May 13 07:07:38 kevin-laptop kernel: [   37.464923] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 11
May 13 07:07:38 kevin-laptop kernel: [   37.464928] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK7] -> GSI 11 (level, low) -> IRQ 11
May 13 07:07:41 kevin-laptop kernel: [   48.853018] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
May 13 07:07:42 kevin-laptop kernel: [   48.861148] ndiswrapper: using IRQ 10
May 13 07:07:42 kevin-laptop kernel: [   49.331795] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNK3] -> GSI 11 (level, low) -> IRQ 11
May 13 07:07:47 kevin-laptop kernel: [   64.236647] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10

```
Also, visual inspection of the entire file revealed, thousands of lines of this:
```
May 12 16:19:49 kevin-laptop kernel: [ 6108.456060] recvmsg bug: copied 7F170466 seq 7F170693
May 12 16:19:49 kevin-laptop kernel: [ 6108.456067] recvmsg bug: copied 29DA98E4 seq 29DA9E8C
May 12 16:19:49 kevin-laptop kernel: [ 6108.456078] recvmsg bug: copied 7F170466 seq 7F170693
May 12 16:19:49 kevin-laptop kernel: [ 6108.456084] recvmsg bug: copied 29DA98E4 seq 29DA9E8C
May 12 16:19:49 kevin-laptop kernel: [ 6108.456095] recvmsg bug: copied 7F170466 seq 7F170693
```

Please tell me this gives you some clue as to what's happening.

---

### Post by chili555 on 2008-05-13
I was reading this: [https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360](https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360)  especially this:> I have traced back as far as I can, and find dhcdbd is an **optional** package. I also find that the only thing that depends on it is network managerAre you using Network Manager? Does it appear under System -> Administration -> Services so that we may banish it, even temporarily?

I don't have NM on any of my five machines, so I am at a disadvantage.

---

### Post by chili555 on 2008-05-13
> recvmsg bug: copied 7F170466 seq 7F170693This has me stumped. I am hoping the banishment of NM will somehow fix this.

---

### Post by kmc77 on 2008-05-13
> Are you using Network Manager? Does it appear under System -> Administration -> Services so that we may banish it, even temporarily?Yes I was using it, but It didn't appear under services, so I completely removed it.  No change in network problems, but I don't see any sign of the "recvmesg bug" in the log now.  So, I'm assuming that the Network Manager was simply a symptom.  Problem still persists.

---

### Post by chili555 on 2008-05-13
Did you:```
sudo apt-get remove dhcdbd
```> don't see any sign of the "recvmesg bug" in the log nowExcellent! One problem down, at least.

---

### Post by kmc77 on 2008-05-13
Yes I removed dhcdbd, as well as network-manager and network-manager-gnome.  No change yet.

---

### Post by unutbu on 2008-05-13
Just out of curiosity: if you go to a virtual terminal (CTRL-ALT-F2), and type

```
wget <some url>
```

does anything happen? There is no mouse at the virtual terminal. So does wiggling matter there?

---

### Post by unutbu on 2008-05-13
When you are connected to a wired network, what happens if you remove the wireless driver (temporarily) with
```

sudo rmmod b44
```
Maybe there is some coordination problem between the wired and wireless drivers?

---

### Post by kmc77 on 2008-05-13
> Just out of curiosity: if you go to a virtual terminal (CTRL-ALT-F2), and type[QUOTE]wget <some url>[/QUOTE]

Actually, I noticed it earlier.  I did a ifdown/ifup of eth0 when I was making some changes, and the mouse is still a factor.  ifup would hang when trying to get DHCP info.  Here's the output if I don't move the mouse:
```
kevin@kevin-laptop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:03:25:08:6d:f2
Sending on   LPF/eth0/00:03:25:08:6d:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by kmc77 on 2008-05-13
> When you are connected to a wired network, what happens if you remove the wireless driver (temporarily) with[QUOTE]sudo rmmod b44[/QUOTE]

If I remove b44 then I am unable to use/find eth0.

---

### Post by unutbu on 2008-05-13
Oops. It would be nice to know if the problem goes away if you boot without your wireless driver. 

How about blacklisting ndiswrapper (temporarily):

```
gksudo gedit /etc/modprobe.d/blacklist
```

add the line

```
blacklist ndiswrapper
```

Reboot with a wired connection.

---

### Post by kmc77 on 2008-05-13
Ndiswrapper blacklisted.  Rebooted.  No change.

---

### Post by stevanbt on 2008-05-13
Hi,
I've been having problems with my network under Hardy 64-bit (sometimes downloads are ok, then zero network traffic, even to pcs on my local network)... They are now resolved so I can't say for certain if they're the same as yours (i.e. due to mouse).  

But I solved my problems by making the ip address of my Hardy 64-bit machine static.

I don't know if this will help, but it may be worth a go.

Thanks, Steve.

---

### Post by kmc77 on 2008-05-13
> But I solved my problems by making the ip address of my Hardy 64-bit machine static.
That'd be nice if that would work, but, unfortunately it's not an option at my office.

---

### Post by unutbu on 2008-05-13
Please post:

```
cat /proc/interrupts
```

---

### Post by kmc77 on 2008-05-13
Output:
> kevin@kevin-laptop:~$ cat /proc/interrupts
           CPU0       
  0:     179851    XT-PIC-XT        timer
  1:        191    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          1    XT-PIC-XT      
  4:          1    XT-PIC-XT      
  5:          1    XT-PIC-XT      
  6:          1    XT-PIC-XT      
  7:          2    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:        114    XT-PIC-XT        acpi
 10:          4    XT-PIC-XT        ohci1394, yenta, ndiswrapper, radeon@pci:0000:01:05.0
 11:      27850    XT-PIC-XT        ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, ALI 5451, eth0
 12:       2217    XT-PIC-XT        i8042
 14:      36313    XT-PIC-XT        ide0
 15:      13872    XT-PIC-XT        ide1
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0


---

### Post by unutbu on 2008-05-13
Notice that eth0 is sharing irq 11 with 3 usb devices and the sound card. 

```
11: 27850 XT-PIC-XT **ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, ALI 5451, eth0**
```

This is just a hypothesis -- it could be wrong -- but it may be the case that eth0 does not interact well with one of these other devices -- they don't share the IRQ nicely. (Is your mouse a usb device?)
Maybe somehow the mouse is blocking eth0 from communicating with the kernel, and only when the mouse is moving is the IRQ channel "open", allowing eth0 to sneak in its own communication as well.

Please understand that I know next to nothing about IRQ issues, and what I said above is just speculation based on my limited understanding of IRQ.

Daniel Robbins, creator of Gentoo, wrote a very interesting article on how he dealt with IRQ conflicts on his own machine:
[http://www.ibm.com/developerworks/linux/library/l-hw2.html#author](http://www.ibm.com/developerworks/linux/library/l-hw2.html#author)

Following his advice may or may not solve your problem, but perhaps it's worth a shot.

---

### Post by kmc77 on 2008-05-14
@ unutbu

The irq share problem made sense to me, unfortunately, my BIOS does not allow me to turn off pnp, and because I'm working on a laptop, the process of shuffling pci slots is impossible.  So I did a little experiment.  I reinstalled Ubuntu (A fresh install has no problems with eth0) and checked "cat /proc/interrupts" and everything looks the same, so I'm assuming that shared irq are not the problem.

After checking the interrupts, I reinstalled ndiswrapper and my wireless drivers, using the information contained on [THIS PAGE.]("http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4306").    (Using my BCM4306 (2) drivers). The problem begins after that.  Nothing else was done to the fresh install.  Is there another way to get my wireless working, other than ndiswrapper?  If not, what in the process on the above mentioned page, could be breaking eth0?

---

### Post by chili555 on 2008-05-14
> unfortunately, my BIOS does not allow me to turn off pnpDoes it allow you to manipulate the IRQs in the BIOS? I set mine all to AUTO. At any rate, can you change them from what they are in the BIOS to *anything* else?

---

### Post by kmc77 on 2008-05-14
> Does it allow you to manipulate the IRQs in the BIOS? I set mine all to AUTO. At any rate, can you change them from what they are in the BIOS to anything else?
No, I can't manipulate any aspect pertaining to IRQ's.  I have a very limited BIOS.

Here's another question.  Part of the process of getting the wireless running thru ndiswrapper requires the insertion of ```
auto lo\niface lo inet loopback\n
```in /etc/network/interfaces.  I'm not particularly sure of what this does.  Could it be creating problems?

---

### Post by chili555 on 2008-05-14
I am not aware of the exact wording of the command, however that looks malformed. It could be a problem, but let's see if it needs fixing. Please do *sudo gedit /etc/network/interfaces*. Please be sure the file includes:```
auto lo
iface lo inet loopback
```If it contains other text, you can leave it. Save and close. If you had to amend *interfaces*, then I would restart networking:```
sudo /etc/init.d/networking restart
```

---

### Post by kmc77 on 2008-05-14
```
auto lo
iface lo inet loopback
```is the only thing contained in the file.  No changes were made.

---

### Post by unutbu on 2008-05-14
Please post
```

sudo lshw -C network
```

---

### Post by kmc77 on 2008-05-14
Output:
```
kevin@kevin-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 02
       serial: 00:90:96:59:b3:86
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,12/22/2004, 3.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 01
       serial: 00:03:25:08:6d:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.100.1.107 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

```

---

### Post by unutbu on 2008-05-14
I am very perplexed. You say after a fresh install eth0 works fine -- the problem only starts after you've installed ndiswrapper and bcmwl5.

Yet if you blacklist ndiswrapper and reboot, the problem remains. Hm. Very strange!

---

### Post by kmc77 on 2008-05-14
> **unutbu said:**
> I am very perplexed. You say after a fresh install eth0 works fine -- the problem only starts after you've installed ndiswrapper and bcmwl5.

Yet if you blacklist ndiswrapper and reboot, the problem remains. Hm. Very strange!

This got me thinking again.  You're right blacklisting ndiswrapper should have fixed the problem as it was the only thing that I changed from a clean install.  I decided to try blacklisting it again.  And again it had no effect, but then, I noticed that Network Manager was still seeing wireless AP's, which, with no ndiswrapper, shouldn't be happening.  So, I went back over everything done to get ndiswrapper up and running, and I realized that the ndiswrapper file contained this line
```
install ndiswrapper modprobe -r b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS;
```
So, I commented that line out, and rebooted.  This time no wireless, but the wired problem is fixed.  So, for the moment, I'll just have to go in and edit the ndiswrapper file when I switch between home and work.  This is a start.  At least I can function.  Now I just need to figure out why it was screwing up.  If anyone has any ideas, I'd really appreciate the help.

---

