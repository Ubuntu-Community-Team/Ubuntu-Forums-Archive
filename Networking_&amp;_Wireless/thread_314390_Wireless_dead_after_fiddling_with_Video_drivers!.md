---
title: "Wireless dead after fiddling with Video drivers!"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by HeavyAl on 2006-12-07
Hey all, first the story:

I was checking out the video forums and found some 'bleeding edge' video drivers for ati cards. Someone in there posted what looked like an indication that hte driver would work with my ATI card, and even though mine worked 'ok' I thought if I could give it a boost it would be cool so I tried installing them.

Well, the install bombed and I ended up having to work from the cl and eventually ended up removing X altogether and reinstalling from the original edgy repos to get my X server back up. That done I went on my merry way thinking that it was an interesting experience that I didnt want to have happen again but I was wiser for it none the less. Until this morning ..

I booted up and noticed that I no longer had lights on my wireless card. I tried all kinds of fiddling and the darn thing just wouldnt come back on. So I'm here now .. 

Wireless card: PCMCIA Linksys ACX 111 - WPC54G
OS: Ubuntu Edgy
Machine: IBM Thinkpad T40 (without the internal wireless)
Video: ATI 7500 (not really a problem now, it works which is sufficient)

Some stats:

sudo lshw -C network:

```

 *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:ca:f2:c9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.1.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:c0200000-c0200fff ioport:8000-803f irq:11
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:c4020000-c4021fff iomemory:c4000000-c401ffff irq:11

```

cat /etc/network/interfaces:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid linksys 
wireless-key MY128BITWEPKEY

auto eth0

auto wlan0

```

ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr 00:0D:60:CA:F2:C9  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:feca:f2c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:464327 (453.4 KiB)  TX bytes:105738 (103.2 KiB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.217.1  Bcast:192.168.217.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.111.1  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Note there is no wlan0 in the above ifconfig - it used to be there!

lspci:

```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
07:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

locate acx:

```

/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/acx
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/acx/acx.ko
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/acx
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/acx/Kconfig
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/acx/Makefile
/usr/src/linux-headers-2.6.17-10-generic/include/config/net/acx
/usr/src/linux-headers-2.6.17-10-generic/include/config/net/acx/module.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/net/acx/pci.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/net/acx/usb.h

```

.. and it appears that the drivers are installed

So what gives?

I tried sudo modprobe acx and got nothing. Rebooted and got nothing. Tried a different slot for the card (wasnt expecting this to work but anyway ..) got nothing.

Anyone know what might be going on?

Thanks in advance!

---

### Post by HeavyAl on 2006-12-07
It seems I answer my own questions more often than not in here but perhaps this information will be useful to someone else with similar problems.

Turns out that the operation to remove the video drivers during my earlier video mess ended up wiping out the firmware for the wireless card as well as the video drivers. Seemed odd to me that the two would cross paths as they did but thats what happened.

Anyway I stumbled upon this issue as I was perusing the firmware directory for my kernel and noticed that there was no acx dir listed, which is where the firware for this card is supposed to be .. for those looking into a similar issue you might want to check these dirs:

```

/lib/firware/yourkernel/

```

Look for an acx folder in there - if it's not present then chances are thats the reason you're hosed.

To fix this I used some tips from two different threads:

First, I grabbed the firmware thats noted in this thread: 

[http://ubuntuforums.org/showthread.php?t=290348&highlight=acx+111+drivers](http://ubuntuforums.org/showthread.php?t=290348&highlight=acx+111+drivers)

And after untarring them to the appropriate locations I followed the setup described in this thread:

[http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g](http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g)

Note that if you've modified /etc/modprobe.d/options to include the line regarding the acx version that its not necessary and it might even give you trouble if it exists so comment it out if you have done so.

The main part of the second thread to look at is the linking - you have to do the symbolic link so that the system can find the firmware:

```

sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16

```

After that I used modprobe

```

sudo modprobe acx

```

plugged out and plugged in the card .. and I was dismayed at first that I didn't get any flashy lights. Not to be dissuaded, I rebooted (geez, flashback to windows there!). On the way back up I was happy to see the lights begin to flash on my card.

And thats it. Wireless works again. If youre having a similar problem don't forget that you also want to make sure you have everything else in place to make your wireless work such as /etc/network/interfaces where you'll want to put your essid and key.

---

