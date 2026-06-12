---
title: "[SOLVED] Wireless Network problems"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by BallTongue50187 on 2008-06-23
I am having issues with wireless networking. I have the Linksys wpc54g v5 pci card and the correct driver is installed. On perviouse Xubutu versions i never had problem but with 8.04 i can not connect to any router. This is the output of the log

Jun 23 11:31:45 ronald-laptop kernel: [ 1821.091127] pccard: CardBus card inserted into slot 0
Jun 23 11:31:46 ronald-laptop kernel: [ 1821.271877] ndiswrapper: driver lsmvnds (Linksys,10/13/2004,3.1.0.36) loaded
Jun 23 11:31:46 ronald-laptop kernel: [ 1821.273473] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Jun 23 11:31:46 ronald-laptop kernel: [ 1821.281828] ndiswrapper: using IRQ 10
Jun 23 11:31:46 ronald-laptop kernel: [ 1821.556973] wlan0: ethernet device 00:13:10:ae:02:be using NDIS driver: lsmvnds, version: 0x3000031, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
Jun 23 11:31:46 ronald-laptop kernel: [ 1821.557030] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jun 23 11:31:48 ronald-laptop kernel: [ 1823.415291] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 23 11:36:25 ronald-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 23 11:36:25 ronald-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 23 11:36:25 ronald-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

Can someone please help

---

### Post by BallTongue50187 on 2008-06-23
bump

---

### Post by BallTongue50187 on 2008-06-30
here is iwconfig output

ronald@ronald-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

here is ifconfig output

ronald@ronald-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:86:4a:30:57  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:170890 (166.8 KB)  TX bytes:21993 (21.4 KB)
          Interrupt:10 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:10:ae:02:be  
          inet6 addr: fe80::213:10ff:feae:2be/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:90 (90.0 B)
          Interrupt:10 Memory:24010000-24020000

---

### Post by BallTongue50187 on 2008-06-30
It seems like its connecting to the router but its not getting an ip address. I looked thru the log file and the rate is 1mb i tried changing it but it will not change. It still shows 1mb. PLEASE SOMEONE HELP ME.

---

### Post by Lisanels on 2008-06-30
What applet are you using to connect?  Does it show your wireless network as available?  If so, start with no security on the wireless.  

I'm surprised you have to use ndiswrapper?  I've run several cards with the default drivers that are installed, and my BCM43XX is the only one I had to use drivers for, and they were not through ndiswrapper.  

Lisa

---

### Post by BallTongue50187 on 2008-07-21
Thanks lisa for your response. I was using the gnome applet. I manually setup the connection with network admin to my router and low and behold it worked. I have since tried gnome applet with roaming mode again to see if it would work and no go. Seems strange i can't use it but i don't mind i am just glad it works.

---

