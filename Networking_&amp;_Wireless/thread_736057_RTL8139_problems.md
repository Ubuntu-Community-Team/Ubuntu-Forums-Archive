---
title: "RTL8139 problems"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by post_scriptum on 2008-03-26
Hi,

I read this topic: [http://ubuntuforums.org/showthread.php?t=206185](http://ubuntuforums.org/showthread.php?t=206185) regarding problems with the RTL3189 network card.
Here's my poor attempt at troubleshooting this
```
jason@jason-desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:06.0 SCSI storage controller: Adaptec AHA-2940U2/U2W / 7890/7891
00:09.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (Worldwide) (rev 08)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
jason@jason-desktop:~$ lsmod | grep 8139
8139too                27776  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
jason@jason-desktop:~$ sudo dhclient eht0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eht0: ERROR while getting interface flags: No such device
eht0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
jason@jason-desktop:~$ sudo modprobe 8139too
jason@jason-desktop:~$ sudo modprobe 8139cp
jason@jason-desktop:~$ sudo ifconfig -a
eth0      Lien encap:Ethernet  HWaddr 00:08:54:B2:BA:26  
          adr inet6: fe80::208:54ff:feb2:ba26/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:18 Adresse de base:0xe000 

eth0:avah Lien encap:Ethernet  HWaddr 00:08:54:B2:BA:26  
          inet adr:169.254.6.109  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:18 Adresse de base:0xe000 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:16 erreurs:0 :0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:1184 (1.1 KB) Octets transmis:1184 (1.1 KB)

jason@jason-desktop:~$ dmesg|tail
[  223.570170] eth0:  Tx descriptor 3 is 00082070.
[  223.570192] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  235.567977] NETDEV WATCHDOG: eth0: transmit timed out
[  238.567471] eth0: Transmit timeout, status 0d 0000 c07f media 00.
[  238.567489] eth0: Tx queue start entry 4  dirty entry 0.
[  238.567501] eth0:  Tx descriptor 0 is 000820bb. (queue head)
[  238.567512] eth0:  Tx descriptor 1 is 000820bb.
[  238.567522] eth0:  Tx descriptor 2 is 00082046.
[  238.567531] eth0:  Tx descriptor 3 is 000820bb.
[  238.567553] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
jason@jason-desktop:~$ sudo dhclient eht0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eht0: ERROR while getting interface flags: No such device
eht0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```

Please take note that the link light on my network card is "OFF" on Ubuntu but it is "ON" under Windows XP (I'm posting this on WinXP).

Is there something I can do?
I found the drivers for my network card, I'll try installing them, we'll see.

---

### Post by dstew on 2008-03-26
What trouble are you having? It seems your card is connected. Are you having problems with a specific program (like Firefox) or with all network traffic? That thread is almost two years old, probably things have changed. What distribution do you have?> jason@jason-desktop:~$ sudo dhclient eht0It should be```
jason@jason-desktop:~$ sudo dhclient **eth**0
```

---

### Post by post_scriptum on 2008-03-26
Dang, anyway the problem was with the card not being recognized correctly in Ubuntu.
I didn't get any IP address so I was unable to browse the net, etc.

I replaced the card with a more recent one (still same chipset, the RTL 8139) and it works now...

Anyway, thanks :)

---

### Post by oldham03 on 2008-04-11
I having a problem getting my internet to work with RTL8139C+ chipset. I am trying HardyHeron Beta (cutting edge). Card is recognised by lspci. Activity light is on. 
Getting an error when I:
sudo /etc/init.d/networking restart

Get message:
SIOCSIFADDR: No such device
eht0: ERROR while getting interface flags: No such device
eht0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

Thanks.

---

