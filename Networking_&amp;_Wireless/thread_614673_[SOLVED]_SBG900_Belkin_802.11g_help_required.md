---
title: "[SOLVED] SBG900 Belkin 802.11g help required"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Partyboi2 on 2007-11-16
I am trying to setup a new modem + router for my desktop. 
The modem is a SBG900 Motorola Wireless Surfboard
The router is a Belkin wireless 802.11g (F5D7230-4)
My NIC is a Realtek RTL8139/810x Family fast ethernet.

I am at a loss at where to start, as I know very little about networking.
I have managed to set it up and get it working on my Xp partition. I have looked around on google, but most of them seem to be pointing to connecting wireless to wireless. I am trying to hardwire my Desktop to the router.
Is anyone able to point me in the right direction of some good how to guides?
Thanks...

---

### Post by Partyboi2 on 2007-11-17
Still can not connect gusty to the internet. I have unplugged the Belkin router and focusing on trying to get internet connection.
The other day I replaced my broadband cable modem with  the wireless modem. I use to connect via usb to the old one with no problems at all, but the new one I am using ethernet and cannot get it to connect.
The light on the wireless modem for PC activity is not lit up like the rest of them. 
I have tried lspci -v to see if my Nic card is installed
lspci -v  
 

 

```
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)  
         Subsystem: Realtek Semiconductor Co., Ltd. RT8139  
         Flags: bus master, medium devsel, latency 32, IRQ 20  
         I/O ports at e800 [size=256]  
         Memory at e7005000 (32-bit, non-prefetchable) [size=256]  
         [virtual] Expansion ROM at 40000000 [disabled] [size=64K]  
         Capabilities: [50] Power Management version 2  
 
```My /etc/networking/interfaces only say:
```
auto lo
 iface lo inet loopback
 

 

 

 

 

 

 iface eth0 inet dhcp
 

 auto eth0

```My debug log says:
```
 debug
 media 10.  
 Nov 17 15:52:40 karl-desktop kernel: [  754.947333] eth0: Tx queue start entry 4  dirty entry 0.  
 Nov 17 15:52:40 karl-desktop kernel: [  754.947336] eth0:  Tx descriptor 0 is 0008203c. (queue head)  
 Nov 17 15:52:40 karl-desktop kernel: [  754.947340] eth0:  Tx descriptor 1 is 0008203c.  
 Nov 17 15:52:40 karl-desktop kernel: [  754.947342] eth0:  Tx descriptor 2 is 0008203c.  
 Nov 17 15:52:40 karl-desktop kernel: [  754.947345] eth0:  Tx descriptor 3 is 0008203c.  
 Nov 17 15:52:55 karl-desktop kernel: [  769.929620] eth0: Transmit timeout, status 0d 0000 c07f media 10.  
 Nov 17 15:52:55 karl-desktop kernel: [  769.929627] eth0: Tx queue start entry 4  dirty entry 0.  
 Nov 17 15:52:55 karl-desktop kernel: [  769.929630] eth0:  Tx descriptor 0 is 0008203c. (queue head)  
 Nov 17 15:52:55 karl-desktop kernel: [  769.929634] eth0:  Tx descriptor 1 is 00082156.  
 Nov 17 15:52:55 karl-desktop kernel: [  769.929636] eth0:  Tx descriptor 2 is 0008203c.  
 Nov 17 15:52:55 karl-desktop kernel: [  769.929639] eth0:  Tx descriptor 3 is 0008203c.  
 Nov 17 15:53:10 karl-desktop kernel: [  784.911903] eth0: Transmit timeout, status 0d 0000 c07f media 10.  
 Nov 17 15:53:10 karl-desktop kernel: [  784.911909] eth0: Tx queue start entry 4  dirty entry 0.  
 Nov 17 15:53:10 karl-desktop kernel: [  784.911913] eth0:  Tx descriptor 0 is 0008203c. (queue head)  
 Nov 17 15:53:10 karl-desktop kernel: [  784.911916] eth0:  Tx descriptor 1 is 0008203c.  
 Nov 17 15:53:10 karl-desktop kernel: [  784.911919] eth0:  Tx descriptor 2 is 0008203c.  
 Nov 17 15:53:10 karl-desktop kernel: [  784.911922] eth0:  Tx descriptor 3 is 0008203c.
 
```And my Syslog:
```
 Syslog
 Nov 17 15:42:52 karl-desktop kernel: [  167.457830] NETDEV WATCHDOG: eth0: transmit timed out  
 Nov 17 15:42:55 karl-desktop kernel: [  170.454303] eth0: Transmit timeout, status 0d 0000 c07f media 10.  
 Nov 17 15:42:55 karl-desktop kernel: [  170.454309] eth0: Tx queue start entry 4  dirty entry 0.  
 Nov 17 15:42:55 karl-desktop kernel: [  170.454313] eth0:  Tx descriptor 0 is 00082046. (queue head)  
 Nov 17 15:42:55 karl-desktop kernel: [  170.454316] eth0:  Tx descriptor 1 is 000820c6.  
 Nov 17 15:42:55 karl-desktop kernel: [  170.454319] eth0:  Tx descriptor 2 is 0008206f.  
 Nov 17 15:42:55 karl-desktop kernel: [  170.454322] eth0:  Tx descriptor 3 is 0008203c.  
 Nov 17 15:42:55 karl-desktop kernel: [  170.454334] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Nov 17 15:43:07 karl-desktop kernel: [  182.440119] NETDEV WATCHDOG: eth0: transmit timed out  
 

 
```I have pinged 127.0.0.1 and it is working
Don't know where to go from here.
Do I need to use ndiswrapper to get this to work?
So any help would be grateful.

---

### Post by Partyboi2 on 2007-11-19
I have finally got internet up and running, the problem was this:

>  Nov 17 15:43:07 karl-desktop kernel: [  182.440119] NETDEV WATCHDOG: eth0: transmit timed out The Netdev watchdog timeout error was caused by windows xp. What happened was that the realtek 8139 NIC was set to shut off when windows shutdown. For some reason Ubuntu can't wake it up. So to fix it, in windows I went to driver settings for the NIC and under Advance setup for the NIC I enabled "wake on lan" then rebooted into ubuntu. It worked for me.
Might work for someone else with same problem.

---

