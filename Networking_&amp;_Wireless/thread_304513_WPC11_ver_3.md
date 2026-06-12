---
title: "WPC11 ver 3"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by lcaley on 2006-11-21
Hello everyone. I'm trying to get Ubuntu Dapper installed on an extremely old laptop using a WPC11 ver 3 PCMCIA wireless card. The OS recognizes the card, shows it running ip4 and accepts a static address without any problems. It even tells me that I have a 74% signal strength to my AP, but it just won't pass any data. Any ideas?

I'm fairly new to Linux, but I do know a little bit, also keep in mind that the only way I am able to put files onto this machine is with a flash drive, as I don't have any other way to connect to the network at this time.

Thanks

---

### Post by ingo on 2006-11-22
it would be nice if you could post the output of the following commands (a pain, I know):

sudo ifconfig
sudo iwconfig
cat /etc/network/interfaces

also, you using wep or wpa?

---

### Post by lcaley on 2006-11-22
I don't have access to the computer right now, but I'll post that output as soon as I do. Thanks for the reply.

---

### Post by lcaley on 2006-11-22
here's the output:

sudo ifconfig:



eth0     

Link encap:Ethernet  
HWaddr 00:02:B3:05:EF:D0
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



eth1      

Link encap:Ethernet  HWaddr 00:06:25:10:5C:F8
          
inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
   UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          
Interrupt:3 Base address:0x100



lo        

Link encap:Local Loopback
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          
RX bytes:2640 (2.5 KiB)  TX bytes:2640 (2.5 KiB)




sudo iwconfig



lo
no wireless extensions.



eth0      
no wireless extensions.



irda0
no wireless extensions.



eth1      

IEEE 802.11b  
ESSID:"caleynet"  Nickname:"Prism  I"
          
Mode:Managed  Frequency:2.412 GHz  Access Point: 00:06:25:7F:A2:CB
 
Bit Rate:2 Mb/s   Sensitivity:1/3
          
Retry min limit:8   RTS thr:off   Fragment thr:off
          
Encryption key:off
          
Power Management:off
          
Link Quality=46/92  Signal level=-54 dBm  Noise level=-141 dBm

Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          
Tx excessive retries:0  Invalid misc:0   Missed beacon:0



sit0      
no wireless extensions.




cat /etc/network/interfaces:



auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet static

wireless-essid caleynet

address 192.168.1.12

netmask 255.255.255.0

gateway 192.168.1.1



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp



No, I am not using wep or wpa at this time, I turned it off temporarily to make this a little easier.

Thanks so much.

---

### Post by ingo on 2006-11-22
Ok, so you got a prism card on eth1, your router is on 192.168.1.1,  your fixed ip is 192.168.1.12 and your bit rate is 2Mb/s (pretty low).

I suppose you can't ping anything since you got 0 TX packets.

My only suggestion would be to have your router on dhcp and see whether your card will get an ip address (in which case you'd have to adjust your /etc/network/interfaces entry for eth1 to the same as eth0).

If that succeeds you know what to do, if not I don't :(

HTH

---

### Post by lcaley on 2006-11-22
Ok, my router is set up to have half of its addresses be dhcp and half of them to be statically assigned. I gave this a static address, to eliminate another place for a networking error. Do you think it would be better if I used dhcp? If so, what would I have to change other than telling the network card to look for a dhcp server?

---

