---
title: "Each time I type dhcliet, I can surf the web for about 30 seconds"
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by epb613 on 2005-04-19
I have a very strange problem, I set up my wireless network card (intel 2200bg) and then entered the settings of my network (I typed, sudo iwconfig eth1 essid Gr33nG0bl1n, then sudo iwconfig eth1 key restricted DA1608B7C9). Typing iwconfig shows me:

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Gr33nG0bl1n"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:29
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-39 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

But then I tried to surf and it wouldn't work. So then I ran KWiFiManager and it told me that I was connected to Gr33nG0bl1n but I didn't have an IP address. Ok - no problem - I type sudo dhclient and get the following:

pinny@pinnys-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth1/00:0e:35:15:a6:e8
Sending on   LPF/eth1/00:0e:35:15:a6:e8
Listening on LPF/eth0/00:02:3f:07:f5:d2
Sending on   LPF/eth0/00:02:3f:07:f5:d2
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.5 -- renewal in 114267 seconds.
pinny@pinnys-laptop:~$            

And PRESTO! I can surf!

...for about 30 seconds later. For when that half minute elapses I can no longer surf, nor can I apt-get - you get the idea.

So I type another iwconfig to what's up. I get:

pinny@pinnys-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Gr33nG0bl1n"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:29
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-40 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:13

sit0      no wireless extensions.

pinny@pinnys-laptop:~$    

Well everything looks good so I decide to give KWiFiManager another go  and it tells me that I still have I'm still connected with 94% signal quality and that I still have my IP address. Yet I can't surf.

Well now that's really strange. But it get's stranger: For giggles I type sudo dhclient again and guess what - I can surf... ...for another 30 seconds. This happens each time I type sudo dhclient.

Well, I'm clueless. If anyone has any idea's I would be really grateful.

P.S. Some other info: if I plug a network cable into eth0 and type sudo dhclient again, then I can surf, and it stays connected.

Thanks in advance!

---

### Post by epb613 on 2005-04-19
Well now, although I posted this five minutes ago, it was after 2 hours of playing with it unsuccessfully. And I finally figured out the answer: typing sudo /etc/init.d/networking restart solved the problem. Anybody have any theory as to why?

And while I have your attention, does anyone know how all of this can be automated during boot-up.

In other words, where can I store my SSID and WEP key that they will automatically get read and applied during boot up. I heard something about an interfaces file - maybe that's it.

Thanks again for sticking with me.

---

