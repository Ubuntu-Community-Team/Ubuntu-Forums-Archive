---
title: "Network Manager can't find network"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by tbear2 on 2010-01-02
Ubuntu 9.04
Network Manager cannot detect network (wired).

Would someone please talk me through some changes???

Should I remove Network Manager?
Should it be replaced with wicd?
If so how do I do that without internet connection?

Everything works in Windows 2000 (how I am connected now.)

Thanks in advance.
tb2

---

### Post by Methuselah on 2010-01-02
Maybe you have a network card that doesn't have drivers in Ubuntu?
I think it is rare for wired internet not to work right away for supported hardware.
It has never happened to me. I hope someone else can help you.

If you can post the output of
```

lspci

```

that might be helpful to others reading this.
[You need to open a terminal with (Accessories->Terminal) type the above then hit enter and copy the result out]

---

### Post by tbear2 on 2010-01-02
I am on an old machine.
K7S5A MB with on-board "SIS 900  fast PCI Ethernet Adapter"

Never had network problems before...

---

### Post by tbear2 on 2010-01-02
Here ya go...



:~$ lspci
  00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
  00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
  00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
  00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
  00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
  00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
  00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
  00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
  00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
  00:0d.0 USB Controller: NEC Corporation USB (rev 43)
  00:0d.1 USB Controller: NEC Corporation USB (rev 43)
  00:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
  01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)




Now what??

---

### Post by waspbr on 2010-01-02
hmmm,not great haven't heard many good things about SIS cards, tho what kind of connection do you have? are you connecting to a router?


longshot,open a terminal window and try this


```
sudo dhclient eth0
```

if that doesn't work, then paste this

```
ifconfig
```

please post the results then

---

### Post by tbear2 on 2010-01-02
[FONT=&quot]Here are the results, as you suggested:
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]:~$ sudo dhclient eth0[/FONT]
  [FONT=&quot][sudo] password: [/FONT]
  [FONT=&quot]Internet Systems Consortium DHCP Client V3.1.1[/FONT]
  [FONT=&quot]Copyright 2004-2008 Internet Systems Consortium.[/FONT]
  [FONT=&quot]All rights reserved.[/FONT]
  [FONT=&quot]For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)[/FONT]
  
  [FONT=&quot]SIOCSIFFLAGS: Cannot assign requested address[/FONT]
  [FONT=&quot]SIOCSIFFLAGS: Cannot assign requested address[/FONT]
  [FONT=&quot]Listening on LPF/eth0/00:00:[/FONT][FONT=&quot]00:00:00:00[/FONT]
  [FONT=&quot]Sending on   LPF/eth0/00:00:[/FONT][FONT=&quot]00:00:00:00[/FONT]
  [FONT=&quot]Sending on   Socket/fallback[/FONT]
  [FONT=&quot]receive_packet failed on eth0: Network is down[/FONT]
  [FONT=&quot]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4[/FONT]
  [FONT=&quot]send_packet: Network is down[/FONT]
  [FONT=&quot]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5[/FONT]
  [FONT=&quot]send_packet: Network is down[/FONT]
  [FONT=&quot]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11[/FONT]
  [FONT=&quot]send_packet: Network is down[/FONT]
  [FONT=&quot]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16[/FONT]
  [FONT=&quot]send_packet: Network is down[/FONT]
  [FONT=&quot]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9[/FONT]
  [FONT=&quot]send_packet: Network is down[/FONT]
  [FONT=&quot]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10[/FONT]
  [FONT=&quot]send_packet: Network is down[/FONT]
  [FONT=&quot]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6[/FONT]
  [FONT=&quot]send_packet: Network is down[/FONT]
  [FONT=&quot]No DHCPOFFERS received.[/FONT]
  [FONT=&quot]No working leases in persistent database - sleeping.[/FONT]
  
  
  [FONT=&quot]Code:[/FONT]
    [FONT=&quot]ifconfig[/FONT]
  
  [FONT=&quot]:~$ ifconfig[/FONT]
  
  [FONT=&quot]lo        Link encap:Local Loopback  [/FONT]
  [FONT=&quot]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
  [FONT=&quot]          inet6 addr: ::1/128 Scope:Host[/FONT]
  [FONT=&quot]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
  [FONT=&quot]          RX packets:12 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=&quot]          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=&quot]          collisions:0 txqueuelen:0 [/FONT]
  [FONT=&quot]          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)[/FONT]


I don't see eth0.
Does this mean eht0 is not detected?

---

### Post by tbear2 on 2010-01-02
Oh!
I forgot to mention, I am on a router, [FONT=Arial]Linksys WRT54G, wired connection.
[/FONT]

---

### Post by Pascal11110 on 2010-01-02
I've had problems pretty much identical to this and it took me ages to figure out that it was just that ubuntu didn't have the drivers for my card in the kernel, so if you have access to another card I would suggest trying that at least before you went way to deep in the network manager. Also, something you might try when all else fails is statically assigning it using the interfaces file.

Also, if you click the network manager button in the upper right and eth0 pops up, does it say disabled or device not managed under it?

---

### Post by tbear2 on 2010-01-02
Hi Pascal...
Thanks for the suggestion.  
I tried installing another card and bypassing / disabling the built in SIS900 card on this motherboard.  Network Manager still couldn't make a connection, and Windows  wouldn't play nice, so I removed the extra network card and re-enabled the built in card.

Too bad. :sad:

Thanks anyway...

---

### Post by tbear2 on 2010-01-03
On a hunch, I downloaded Ubuntu 9.10 and burned a CD.  Then I tried it on live CD.  It connected to my network, and to the Internet.

I have installed Ubuntu 9.10 in a dual boot with windows and everything seems to be working again.

Thanks to everyone who tried to help!  This forum is a great resource and I am sure I will be back to learn more!

All the best, :P
tb2

---

