---
title: "my wireless is really really slow."
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by salvador dali on 2007-06-01
i've been using edgy for a month or two. edgy's wireless manager detected by card and i was able to connect to the internet, but my broadband internet connection began behaving like a 26k modem. I have a standard dsl modem feeding into a belkin wireless router that previously had worked excellent with my windows xp system. when i switched to linux however everything slowed down. any help or advice would be appreciated.
Intel PROset Wireless card on a Dell Inspiron E1505 Laptop. 
1.833 GHz Intel Processor
1 Gb RAM

thanks!

---

### Post by cornsnap on 2007-06-02
can you post you lspci output?

---

### Post by salvador dali on 2007-06-02
sure. i think this is what you asked for:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by dfreer on 2007-06-02
I have had problems with my belkin router at home (don't have model number at the moment), and I also use an Intel PRO 3945 A/B/G wireless card. Don't know if you are having the same problems, mine would take forever to resolve DNS querys. So basically, you would navigate to a webpage, it would take ~20 secs, and then load the webpage at a normal speed (pretty fast on my fiber optic line). Also, downloads would take forever to start, but once they started they downloaded at the max speed my bandwidth would allow. 

My solution? It seemed once I disabled IPv6 in firefox and by blacklisting it in the kernel, it worked much better. You might want to give that a try.

---

### Post by salvador dali on 2007-06-03
Thanks so much for your help. I know to disable it in Firefox. What terminal commands should I use to blacklist it?

Edit: Never mind I did a little googling and found it. Thanks for your help!

---

### Post by dfreer on 2007-06-03
did it improve wireless speed at all salvador dali?

---

### Post by salvador dali on 2007-06-03
Loading time went from around 20-25 seconds to about 5 seconds max. Thanks so much! It was pretty easy to do. I disabled IPv6 in about:config in firefox. Then i followed this thread:

[IPv6 Thread]("http://ubuntuforums.org/archive/index.php/t-6841.html")

---

### Post by MyR on 2007-07-15
I discovered that the actual problem is that the network manager sets 192.168.2.1 as the first dns server.
you can edit /etc/resolv.conf (even though it says not to) and move "nameserver 192.168.2.1" to the bottom so it querys the other servers first.
after saving you can now connect at normal speeds.

i also use a local dns cache to speed up browsing.

---

