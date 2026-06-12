---
title: "Atheros AR928X not working"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by firestorm10 on 2008-10-30
[COLOR="Red"]***I switched to Intrepid and that fixed it***[/COLOR]


First of all I'm rather new to linux, well lets just say I'm refamiliarizing myself with it, last time I used it before this month was 3-4 years ago.  Secondly, I know this question has been asked before numerous times and I have tried most if not all of it.

Ok, so let me state my journey and how things have changing through it, and hopefuly someone will help me finish it.

I have a toshiba m305d-s4840, I bought it with plans of making it my main pc and running ubuntu on it. Sadly, most of the devices don't work, so I'm slowly but surely fixing it, with my wee bit of linux know-how and the help of google.

A friend of mine (hes kindof a linux expert but extremely hard to get to) fixed the Lan and then by slightly mimicking what he did I got the wireless device recognized.

[INDENT]So now lspci reads:  AR928X Wireless Network Adapter (PCI-Express) (rev 01) instead of Unknown Device 002 (rev 01).  But still no connection[/INDENT]

So, in the search of my MAC address I used ifconfig to notice that I still had no wlan.  That led me to a new search which led me to this thread ([http://ubuntuforums.org/showthread.php?t=874097]("http://ubuntuforums.org/showthread.php?t=874097")) and this thread ([http://ubuntuforums.org/showthread.php?t=930667]("http://ubuntuforums.org/showthread.php?t=930667"))

I followed the intructions from Volian but I couldn't echo the wlan like the other thread said, since Volian's solution didn't work.  Finally I followed the directions from elvis on this thread ([http://ubuntuforums.org/showthread.php?t=38972]("http://ubuntuforums.org/showthread.php?t=38972")).

Now, the system sees the device not only in lspci but in Hardware Drivers and in Network Settings, but iwconfig still says no wireless.

Outputs:

uname -a:

[INDENT]2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux
[/INDENT]

lspci:

[INDENT]06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)[/INDENT]

ifconfig:

[INDENT]wlan0     Link encap:Ethernet  HWaddr 00:23:4d:03:83:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-03-83-99-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/INDENT]

iwconfig:

[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]

dmesg |grep wlan0:

[INDENT][  241.890376] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/INDENT]

dmesg |grep Atheros:

[INDENT][   34.072230] phy0: Atheros 9280: mem=0xffffc20001080000, irq=18[/INDENT]


Thanks for all your help,
David

PS: Also, if anyone has any idea why only the video and not the wireless devices are the only ones showing up in Hardware Devices, I'll apretiate your help.

---

