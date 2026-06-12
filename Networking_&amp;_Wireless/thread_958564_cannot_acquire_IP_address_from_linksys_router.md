---
title: "cannot acquire IP address from linksys router"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by apexofservice on 2008-10-25
Hello Forum,
I've got a Linksys BEFW11S4 Wireless-B router.  I've just upgraded to the latest firmware.  
If I plug my laptop into the router with an ethernet cable--connectivity is fine.  I get an IP address from the DHCP server on the router.  However, wirelessly I can connect, but cannot get an IP address.  I'm only having this issue with this router--that is, I have no issues connecting to other wireless networks with Ubuntu.  I should also say that I'm only having this issue with this router with Ubuntu--if I boot into windows, I can connect wirelessly without issue. 

Here's ifconfig and iwconfig outputs: 

jcrowgey@spooky2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:61:f2:d2  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe61:f2d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11477189 (10.9 MB)  TX bytes:2243569 (2.1 MB)
          Interrupt:221 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:18:de:b3:ee:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110400 (107.8 KB)  TX bytes:110400 (107.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-B3-EE-F0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


jcrowgey@spooky2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"SCIENTIST/WIZARD"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:73:8C:1E   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




Thanks for any help.  -apexofservice

---

### Post by bill516 on 2008-10-28
I am having this exact same problem.  Using WPA-TKIP under WinXP the router connects every time.  It will not connect at all under 8.04.  I have let the SSID broadcast and turned off all security so that the router now is open (gives me the creeps).  The router still will not connect, so apparently encryption is not the problem.  WICD indicates it is looking for an IP address.  It apparently never gets one and stalls out.

A hard-wire connection to the router works just fine.

So Apex and I would both appreciate a little help and we thank you.

---

### Post by bill516 on 2008-10-28
New info:

I have a number of LiveCDs so I tried several on this problem.

PuppyLinux 4.10 found that Linksys router and lashed up without a complaint.  Since you and I both have the Linksys working with Windows but not with Ubuntu, that was an interesting result.  We can say the router DOES work with Linux.  So I tried a Kubuntu 8.04 LiveCD and the original Ubuntu 8.04 LiveCD.  No luck, exactly the same situation you and I are experiencing.

On a hunch I downloaded the Ubuntu 8.10 "release candidate" iso and burned it.

First observation, it uses a new release of Network Manager, which is to say 0.7.0.

Second observation:  It found and linked up to my Linksys router without a problem.  I reverted back to my WPA security and that worked as well.

In my case -- and perhaps yours -- the problem is not the router.  I then switched out the Linksys for a Trendnet router I have and repeated the entire experiement.  I experienced exactly the same problem with the Trendnet unit.

I also experienced the same problem with the Network manager in Ubuntu 8.04 and with the Wicd net manager, which often performs better.

What has worked is the new Network manager in the Ubuntu 8.10 release candidate as noted above.

Ubuntu servers are about to go nuts with 8.10 downloads.  If you can get there and you do not want to do the full 8.10 download, upgrading to the newest Network Manager 0.7.0  might be sufficient perhaps?

I think I will do a clean 8.10 install just to see if I can step around wireless problems once and for all.  Worth it if it works.

So try a net manager upgrade if no one else comes forward to help.  BTW, keep an eye out for Pytheas22, who has helped me previously.  One very capable wireless person.

---

### Post by apexofservice on 2008-10-29
Thanks Bill.  I'll try the new network manager.  I've found it to be a really confounding problem because it only occurs at home with this linksys router--other wireless nets are no problem (at the university or even public wifis at cafe).  
-apexofservice

---

