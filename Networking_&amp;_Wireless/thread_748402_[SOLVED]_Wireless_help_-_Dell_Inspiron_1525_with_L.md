---
title: "[SOLVED] Wireless help - Dell Inspiron 1525 with Linksys WRT54GL"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by BigSilly on 2008-04-07
Can anyone help me? The wifey has just bought a brand spanking new Dell Inspiron 1525 with Ubuntu 7.10 pre-installed. She also bought a Linksys WRT54GL to go with it, not because we knew about it, but simply because it was recommended to us as Linux users. Neither of us have any clue whatsoever when it comes to wireless. It's all completely and utterly new to us. Our desktop PC is Ubuntu 7.10 too with a with a wired Ethernet connection (Eth0) and Virgin Media broadband. In the laptop I believe the wireless card is an Intel.

After a bit of messing I managed to get our desktop PC to connect to the net via the Linksys, but neither one of us has been able to get the laptop to connect to it. I've looked in the Network settings, but really I haven't the foggiest.

Like I say, I am an extreme n00b when it comes to wireless - this is the first time in my life I've even used one! - so a lot of the jargon is going straight over my head sadly. We'd hoped it would work automatically, as we'd heard the Linksys is extremely good on Linux, but that was a bit hopeful. It does need some setting up clearly, and we don't even know where to start.

Please help! Thanks all. :)

---

### Post by dstew on 2008-04-07
> I've looked in the Network settings, but really I haven't the foggiest.Does the wireless interface show up in the System --> Administration --> Networking window at all, even if it is not connecting?

---

### Post by BigSilly on 2008-04-07
Yeah the interface seems to show up. It says 'linksys', and we've tried to set it but it won't have it. Honestly, I don't know what to do next....

---

### Post by dstew on 2008-04-07
Open a terminal window (Applications --> Accessories --> Terminal), and on the command line enter```
lspci
```Post the result to the forum. This will let us see exactly what hardware you have. And, while you are at it, enter these commands, and post the result also:```
ifconfig
iwconfig
```These will give some detail about the network interfaces you have, both wired and wireless. Can you get the laptop connected to the internet using a wired connection?

EDIT: Another thought: if you see a 'linksys' connection, that might be the ESSID of your router. Does your desktop connect to the router by a wired connection, or by wireless? If by wireless, you can check the properties of the connection and try to duplicate them on your laptop.

---

### Post by BigSilly on 2008-04-08
Hi there. Sorry it's taken so long to reply. I was a bit ill yesterday and had to get to bed!

OK, FYI the desktop is connected via a wired connection, and after a bit of faffing it works through the router just fine. The problem is the laptop. Though I am completely green when it comes to wireless, I did spot 'linksys' in the settings and set it accordingly, but it's made no difference.

Here's the output from those terminal commands....
```

bigsilly@localhost:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
bigsilly@localhost:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:09:4A:79:3E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1F:3C:2D:B8:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:30 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1500 (1.4 KB)
          Interrupt:17 Base address:0xe000 Memory:fe7ff000-fe7fffff 

eth1:avah Link encap:Ethernet  HWaddr 00:1F:3C:2D:B8:78  
          inet addr:169.254.6.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 Memory:fe7ff000-fe7fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3298 (3.2 KB)  TX bytes:3298 (3.2 KB)

bigsilly@localhost:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"linksys"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0
```

Thanks again for your help. We're on the phone to Dell at the moment, but it's got them stumped too sadly.

---

### Post by BigSilly on 2008-04-08
Thanks for your replies dstew. It looks like we've fixed it - fingers crossed!

Turns out we'd enabled MAC filtering by default, but not inputted the MAC address of the laptop. Once we put that in, it connected up. We're in the process of setting up the rest of the security now, so hopefully we should be sorted. Getting a really good connection too. Lovely having Ubuntu on that laptop. It looks fantastic!

Thanks again! :)

---

