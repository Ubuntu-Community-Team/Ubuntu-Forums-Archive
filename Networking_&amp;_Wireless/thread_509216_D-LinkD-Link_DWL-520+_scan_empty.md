---
title: "D-Link
	

D-Link DWL-520+ scan empty"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by SergeiFranco on 2007-07-25
Hello there, I have decided to fix my wireless network which was not working since day one (after switching to Linux).I have fixed the firmware problem (now there is no complaint in dmesg log).
iwconfig returns this:
```

wlan0     Link encap:Ethernet  HWaddr 00:40:05:CF:E3:D6
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:936 (936.0 b)
          Interrupt:20 Base address:0xb000

```
iwevent returns this:
```
Waiting for Wireless Events from interfaces...
22:48:06.671338   wlan0    New Access Point/Cell address:Not-Associated
22:48:08.002576   wlan0    New Access Point/Cell address:Not-Associated
22:48:09.334309   wlan0    New Access Point/Cell address:Not-Associated
22:48:10.666322   wlan0    New Access Point/Cell address:Not-Associated
22:48:11.996732   wlan0    New Access Point/Cell address:Not-Associated
22:48:13.328116   wlan0    New Access Point/Cell address:Not-Associated
22:48:14.659705   wlan0    New Access Point/Cell address:Not-Associated
22:48:15.990886   wlan0    New Access Point/Cell address:Not-Associated
22:48:16.670306   wlan0    Set Mode:Managed
22:48:16.695576   wlan0    New Access Point/Cell address:Not-Associated
22:48:17.322266   wlan0    New Access Point/Cell address:Not-Associated
22:48:18.653654   wlan0    New Access Point/Cell address:Not-Associated
22:48:19.985039   wlan0    New Access Point/Cell address:Not-Associated
....

```

I have tried Wireless Assistant, KWifi, SWscanner and none of them find any networks.
It looks like scanning does not work.
BTW I use Feisty with KDE.

What am I doing wrong?

---

### Post by Mark_in_Hollywood on 2007-07-25
I'm sorry to ask you without having something to contribute, but I have a D-Link WDA 2320 and the output of my dmesg is:

[  163.963545] ath_pci: Unknown symbol _ath_hal_attach
[  163.964019] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  163.965405] ath_pci: Unknown symbol ath_hal_computetxtime
[  163.966595] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  163.967039] ath_pci: Unknown symbol ath_hal_detach
[  163.969046] ath_pci: Unknown symbol ath_hal_probe
[  163.971595] ath_pci: Unknown symbol ath_hal_init_channels
[  163.972569] ath_pci: Unknown symbol ath_hal_getwirelessmodes

If the foregoing is similar to your problem, what did you do?

---

### Post by SergeiFranco on 2007-07-26
Mine one is of different chipset, I do not have any errors in dmesg.

---

### Post by SergeiFranco on 2007-08-01
Anyone? I am puzzled why it does not pick up anything - I have Linksys Router, + I usually pick up my neighbours as well. It looks like the radio side does not work properly. I will try to see if it is broadcasting anything tonight.
Any help appriciated.
Thank You.

---

### Post by fredj on 2007-08-01
Open a terminal and type 'sudo lshw -class network'. Post the output from that here.

---

### Post by SergeiFranco on 2007-08-01
```
sergei@sergei:~$ sudo lshw -class network
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth1
       version: 13
       serial: 00:16:e6:d9:c1:49
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:f8000000-f8003fff ioport:a000-a0ff irq:16
  *-network
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 2
       bus info: pci@05:02.0
       logical name: wlan0
       version: 00
       serial: 00:40:05:cf:e3:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=192.168.1.20 latency=32 multicast=yes wireless=IEEE 802.11b+
       resources: ioport:b000-b01f iomemory:f9110000-f9110fff iomemory:f9100000-f910ffff irq:20

```
Right I have compiled ACX100 driver from here [http://acx100.sourceforge.net](http://acx100.sourceforge.net)
But it resulted in exactly same problem, I still don't get any results from scan...
I had a laptop (win XP) in my room + my router, with laptop I was picking up my router (trough which laptop is connected) and my neighbour, but it was not picking up my D-link card. I have tried to scan (which should of picked up my laptop, router and neighbour) but it did not.
If I set it to Ad-hoc mode it will connect to itself :confused: WTF is going on?
Now I have really solid head ache - another couple of hours down the drain....

---

### Post by SergeiFranco on 2007-08-01
Ok, let me look at the problem other way: What model and brand of Wireless card will work out of the box and has linux support from manufacturer (as not reverse engineered drivers)? I will just buy one that works straight away. This way I will suport manufacturer that supports linux at the same time I will have hassle free experience.

---

### Post by fredj on 2007-08-02
I don't know which cards work out the the box because I don't know anything about your wireless
network. This is because you haven't given us  any information about it. You have to decide if
you really want to get this card to work or if you want to try something else. If you want to get this
card to work then post again.

---

### Post by SergeiFranco on 2007-08-02
It will be good to get this card working... But if there an easier route then I am happy to take it.

My network is simple one. I have an cantenna at my end and other one at my friends end (about 100m away) we had this setup work really well under Windows. It is 802.11b adhoc network with basic security (no internet sharing and passworded accounts on shares). Cantennas are very narrow so no wardrivers.

I was using my Linksys router as an test (also laptop aswell).

It does not appear that the actual card is not trying to send or receive the signal.
I use firmware from windows driver. The firmware was missing in Feisty folder (tiacx100c11), so I renamed windows file into appropriate name. It was complaining before in dmesg about missing firmware, and when I place a wrong one it also complained.

---

### Post by SergeiFranco on 2007-08-03
Ok, here is an update:
```
sergei@sergei:~$ cat /var/log/dmesg | grep acx
[   16.926000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[COLOR="DarkRed"]**[   16.926004] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them**[/COLOR]
[   16.926108] acx: found ACX100-based wireless network card at 0000:05:02.0, irq:20, phymem1:0xF9110000, phymem2:0xF9100000, mem1:0xf893a000, mem1_size:4096, mem2:0xf8a60000, mem2_size:65536
[   16.927100] acx: loading firmware for acx100 chipset with radio ID 11
[   17.959431] acx: === chipset TNETW1100A, radio type 0x11 (RFMD), form factor 0x00 (unspecified), EEPROM version 0x04: uploaded firmware 'Rev 1.9.8.b' ===
[   17.959509] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-16-generic
[COLOR="DarkRed"]**[   18.084017] usbcore: registered new interface driver acx_usb**[/COLOR]

```

Is it normal?
Also my card is not usb....

---

### Post by SergeiFranco on 2007-08-06
bump

---

### Post by Permafrost91 on 2007-08-07
I have had the hardest time getting my DWL-520+ (acx100 chip) to work under Feisty ... and it's still not working. The card is not even recognized anymore (PCI card) so I can't even begin to troubleshoot under Linux (the card works under Windows on the same machine so the hardware seems to be fine). Any help would really be greatly appreciated!

---

### Post by SergeiFranco on 2007-08-10
anyone?

---

### Post by MadeR on 2007-10-21
yes:
acx111 drivers do not work.
they never worked with this card. NEVER.
 
This is known and they never add ndiswrapper among the preinstalled packages.
 
Your only (and working) solution is replacing acx with ndiswrapper.
 
and remember to blacklist acx.

---

