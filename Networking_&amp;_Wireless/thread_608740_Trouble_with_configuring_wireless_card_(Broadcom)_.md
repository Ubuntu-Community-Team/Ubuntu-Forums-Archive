---
title: "Trouble with configuring wireless card (Broadcom) on Ubuntu 7.10"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by hiflyact on 2007-11-10
Hello all,

I am new to Linux and have recently installed Ubuntu 7.10 on my Dell E1405 laptop.  It has a Broadcom 4311 wireless card in it.

My wired internet works in Ubuntu, however the wireless does not.  I was able to use the restricted drivers manager to use the firmware for the card.  

When I run a lspci, the card is visible there in the output, the card is also visible under device mgr.

When I run a scan for wireless networks from the cmd line I get a "No scan results" message.  There are wireless networks around my area but it doesn't pick them up, let alone pick mine up.

When trying to use the network mgr for wireless I didn't have any luck getting that to work either.  

I figured that if I could scan for wireless networks, then I would know that cardr was "working", but since I can't do that, something must be wrong. 

 I feel like I am just one step away from getting this to work, but am stuck on where to go next.  Can anyone help me out, maybe someone has the same laptop as me and has been through this already with 7.10?

Thank you in advance for any help.

---

### Post by kevdog on 2007-11-10
Your many steps away from getting the card to work.  You need to install and setup ndiswrapper.  There are many guides available.  Here are two guides that might help you.

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by nartooki on 2007-11-10
you could also try wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) 
you would have to uninstall network-manager though.

---

### Post by kevdog on 2007-11-10
You need to get the wireless driver module setup first before resorting to configuring network manager or WICD to configure your wireless connection paramaters.

---

### Post by hiflyact on 2007-11-10
Thank you for the help.  I was able to get my wireless card working from this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Even though I have 7.10 it still worked.



Does the following look right to you?  I've read in some articles that it should be wlan not eth1.  


~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"my_place"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:CE:6F:C7   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0


~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:75:BF:D7  
          inet6 addr: fe80::215:c5ff:fe75:bfd7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2202 (2.1 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1A:92:14:59:58  
          inet addr:192.168.149.101  Bcast:192.168.149.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe14:5958/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21133645 (20.1 MB)  TX bytes:4525581 (4.3 MB)
          Interrupt:17 Memory:efdfc000-efe00000 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:75:BF:D7  
          inet addr:169.254.10.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:686 (686.0 b)  TX bytes:686 (686.0 b)

---

### Post by kevdog on 2007-11-10
It doesnt matter if its wlan1 or eth1 or something else.  Its just an interface name that was arbitrarily chosen.  If you want to change it you can do so - you need to edit the appropriate file:

/etc/iftab (Feisty and pre-releases (Edgy, etc)) - /etc/udev/rules.d/70-persistent-net.rules (Gutsy) - File which assigns logical names (eth0, wlan0, etc) to MAC addresses

---

