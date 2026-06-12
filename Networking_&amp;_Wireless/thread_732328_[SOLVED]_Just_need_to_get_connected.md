---
title: "[SOLVED] Just need to get connected"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by djmoore85 on 2008-03-22
Hey yall I recently set up a dual-boot system with Ubuntu and XP, I am tired of windows and want something new. I got it installed and running great with some help from the forum, and now have just one more hurdle before I can spend the majority of my computer time in Ubuntu. I have a laptop with wireless card built in, a Broadcom 802.11b/g WLAN. I connect through a router in my home. Here's snag one: my wife threw away the cable company paper that had the network key on it. Now I know it is stored on my computer somewhere because I don't have to enter it when I connect. Where do I find this in windows? Also, the indicator light showing the card is powered up is not active while logged into Ubuntu, how do I confirm that Ubuntu sees the card and will use it to find wireless networks in the area? Thank you all for the help

---

### Post by dstew on 2008-03-22
> my wife threw away the cable company paper that had the network key on itIf you own the router, and you are willing to try, you can reset it, and configure it again yourself, putting in your own new key. If the cable company owns the router, you might have to call them to get help.> Now I know it is stored on my computer somewhere because I don't have to enter it when I connect. Where do I find this in windows?I imagine it is stored in a protected way, like other passwords. I probably cannot be recovered easily.> the indicator light showing the card is powered up is not active while logged into Ubuntu, how do I confirm that Ubuntu sees the card and will use it to find wireless networks in the areaThis may mean that the card driver is not installed. What kind of card is it? You can tell by using the command```
lspci -n
```The other command to use to see if the card has a working driver is```
iwconfig
```Or, just look in the System --> Administration --> Network window to see if it is listed there.

---

### Post by djmoore85 on 2008-03-26
Alright, I am talking to yall from Ubuntu now. I got the card up and working, indicator lights are lit up and everything. Took downloading firmware for my Broadcom 4318 card. Now have one issue: I can't get internet and I am not getting a return on pings (unless I am typing that code wrong, that could be why). It seems as though I am connected to a network, because Mozilla no longer returns a "can't find server" page, but it just sits there looking up the website I type in. I am currently hooked to internet by ethernet cable. Any suggestions from anyone?

**EDIT** Now I also have one more problem from the ethernet setup, when I go to the application add/remove from the main menu I get a window saying an internet connection is required. I don't understand how I am connected through firefox and could download the needed firmware for my wireless, but when I run an apt -get or go through the GUI for apps ubuntu says that no internet connection is available.

---

### Post by dstew on 2008-03-26
Post the output of the commands```
ifconfig
iwconfig
```

---

### Post by djmoore85 on 2008-03-27
Hope this helps yall see where any issues may be lying within my wireless/ethernet setup. I just need it to get to where I can be able to download drivers and apps for ubuntu. Also, Iam currently about a foot and a half from the router and it shows a signal strength of 68/100, and I normally have this laptop in my bedroom about 75 feet away with a room in between mine and the router. Thanx again for any help, I appreciate it a lot.

```
daniel@DJK71307:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:06:F0:17  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe06:f017/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1190639 (1.1 MB)  TX bytes:204850 (200.0 KB)
          Interrupt:19 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:61:14:3D  
          inet addr:76.107.0.56  Bcast:76.107.7.255  Mask:255.255.248.0
          inet6 addr: fe80::214:a5ff:fe61:143d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:56 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6084 (5.9 KB)
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:176 (176.0 b)  TX bytes:176 (176.0 b)

daniel@DJK71307:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"klinger"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1E:8C:02:FD:10   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=68/100  Signal level=-45 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:59  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by dstew on 2008-03-27
Seems you are having dropped packets on your wireless connection. This could be a driver issue, but also due to IPv6 interference. You can try to disable IPv6 if you don't need it. See [this article]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html").

---

### Post by djmoore85 on 2008-03-27
Not to sound naieve, but what is IPv6?

---

### Post by dstew on 2008-03-27
Internet Protocol version 6. It is like the old protocol, IPv4, except that it allows the use of 128-bit unique identifiers, instead of the 32-bit identifiers used before. An IPv4 address might be 192.168.0.0, but an IPv6 identifier can be fe80::214:a5ff:fe61:143d, to take an example from your ifconfig output. If your ISP does not require you to use IPv6, it might be better to disable it, if you are having connection troubles.

That said, it might be a driver issue. A driver issue is harder to fix than an IPv6 issue, so try that first. Then, if no joy, we will look at your driver.

EDIT: I notice that your wireless connection has been dropping packets because of invalid encryption. Are you sure you are set up properly? It still could be a driver issue, but maybe it is a configuration problem.

---

### Post by djmoore85 on 2008-03-27
Lol I feel pretty dumb here, I changed my settings from static IP (like windows) to automatic configuration and voila! it works. Alright, now my terminal window won't allow me to edit that setting for changing IPv6. Is there another way for me to get to the file to edit it?

---

### Post by dstew on 2008-03-27
If it works, don't try to fix it. If you really want to edit the setting, just use **sudo** before issuing your edit command. Sudo gives you temporary administrative privleges. But, if it works, I wouldn't bother to disable IPv6. Maybe you will need it next year!

---

### Post by djmoore85 on 2008-03-27
Thanks a bunch man. My signal strength where the computer normaly sits is at 48/100. My comp don't move, so it looks like we're all good now. Thanx a bunch for al the help!

---

