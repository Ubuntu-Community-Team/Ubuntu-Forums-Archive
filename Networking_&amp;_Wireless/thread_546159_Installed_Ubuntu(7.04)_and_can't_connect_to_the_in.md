---
title: "Installed Ubuntu(7.04) and can't connect to the internet...."
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by ShawnStovall on 2007-09-08
I just installed Ubuntu on a desktop PC alongside Windows Vista and XP and I can't connect to the internet.  The connection works on XP and Vista, just not Ubuntu...  I'm conneceted through a router that routs to one other computer and the computer I instelled Ubuntu on is the main computer connected directly to the router.  Help please!!!

Thanks!:popcorn:

---

### Post by noob12 on 2007-09-08
Can you indicate whether this Is this a wired connection or wireless?

When booted in Ubuntu, please run the following commands in a terminal window and post the output
```

lspci -nn

sudo lshw -C network

```

---

### Post by thorwood on 2007-09-08
I had a similar problem, with my wireless card. When I install ubuntu updates, it doesn't let me connect to the internet.

---

### Post by Don_S on 2007-09-08
I just installed 7.04 too and cannot figure out how to get the network stuff working. I am connected by wired network to a router. I have set the Ubuntu network settings to obtain an IP address automatically (DHCP). When I place a check in the box next to the network adapter, I get a message (when I hover my mouse cursor on the network icon) stating "obtaining IP address...." and after several seconds I get the message "you are now connected to the wired network". However, I cannot connect to the internet or see other (MS Windows) comps on the network. When I right-click on the network icon (on the top right near the date and time) and select "display network info", no IP address or other network information shows up (only 0.0.0.0). Any ideas are welcome. :confused:

---

### Post by ShawnStovall on 2007-09-08
> **Don_S said:**
> I just installed 7.04 too and cannot figure out how to get the network stuff working. I am connected by wired network to a router. I have set the Ubuntu network settings to obtain an IP address automatically (DHCP). When I place a check in the box next to the network adapter, I get a message (when I hover my mouse cursor on the network icon) stating "obtaining IP address...." and after several seconds I get the message "you are now connected to the wired network". However, I cannot connect to the internet or see other (MS Windows) comps on the network. When I right-click on the network icon (on the top right near the date and time) and select "display network info", no IP address or other network information shows up (only 0.0.0.0). Any ideas are welcome. :confused:

That is what is happening!! I'll get the test results up later.

---

### Post by ShawnStovall on 2007-09-08
Here is the results:
shawn@shawn-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7600 GS [10de:02e1] (rev a2)
02:02.0 Modem [0703]: Broadcom Corporation BCM4212 v.90 56k modem [14e4:4212] (rev 02)
02:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
shawn@shawn-desktop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:11:5b:bd:4a:6e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a400-a4ff iomemory:fb001000-fb0010ff irq:21

Wired by the way.:)

OFF TOPIC:  Do regular Linux drivers work with Ubuntu?

---

### Post by noob12 on 2007-09-09
OK.  You may be seeing the problem solved by this thread:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

It is known to  affect Realtek 8168/69 cards and has recently been reported by a couple of users to affect 8139 cards.  Try the solution there.  Post back if this doesn't address the issue or you have questions.

OFF TOPIC RESPONSE:  Generally speaking, yes, but they need to be compiled for the same kernel version; if you have sources you would generally build with your specific kernel.  In your case your card has a perfectly good driver shipped with Ubuntu.  No need to.

---

### Post by ShawnStovall on 2007-09-09
hmmmm... Neither work.:confused:

---

### Post by Don_S on 2007-09-09
I tried the above too, but no cigar! Any other tips? BTW I have the Realtek 8139 card too.. I'll switch it out with another network adapter and see if it helps..

---

### Post by Don_S on 2007-09-09
I'm happy to report that my problem has been solved! in my case it turned out to be a bad connection between my Ubuntu machne and my router. Because I do not have a network port in the room where the Ubuntu machine is, I had initially tried to connect using one of those powerline ethernet thingies (which did work as advertised on Windows machines but obviously didn't on Ubuntu). So, on a whim, I used a long (100') ethernet cable and voila! instant internet! :guitar: So, Shawn, I would try a different ethernet cable and see if it works.

---

### Post by noob12 on 2007-09-09
Shawn, assuming you've checked your ethernet cable, can you see if you are getting a link light on your card and on the port on the switch to which you are connected.

The following output will help
```

sudo ethtool eth0

ifconfig -a

grep dhclient /var/log/syslog

dmesg

```

Also, if you know your router's address and the local subnet mask (typical ones would be 192.168.1.1 and 255.255.255.0), you can try configuring manually and seeing if you can ping your router, which narrows the problem down.

---

