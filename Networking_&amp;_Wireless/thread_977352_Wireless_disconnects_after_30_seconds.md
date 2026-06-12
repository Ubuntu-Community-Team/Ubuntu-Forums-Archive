---
title: "Wireless disconnects after 30 seconds"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by MasterSander on 2008-11-10
Since kernel .27 my wireless is supported but after doing a fresh install of ibex I try to download some software and my wireless connection drops after 10 seconds, although it says I'm still connected. Anyone can help me?

---

### Post by MasterSander on 2008-11-10
I found out it does it only when I download, not while surfing the net.

---

### Post by MasterSander on 2008-11-11
When I reconnect it works again, but after 6 times I can't even connect anymore and when I switch to XP it's screwed up there as well.

---

### Post by MasterSander on 2008-11-21
I found out this only happens when I'm at home weird enough, could it possibly have to do anything with the SSID name of my network, it's rather long.

---

### Post by MasterSander on 2008-11-21
This and my sound problem is what is preventing me from switching.

---

### Post by MasterSander on 2008-11-21
This the ouput of iwconfig and ifconfig

sander@sanderpc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"LAN1-AP017088"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:D0:D6:08:BD:0A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=96/100  Signal level:-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sander@sanderpc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:82:fb:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25795 (25.7 KB)  TX bytes:25795 (25.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:07:ca:05:f2:50  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:caff:fe05:f250/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15616423 (15.6 MB)  TX bytes:1815829 (1.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-07-CA-05-F2-50-32-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by MasterSander on 2008-11-21
Using windows right now, here everything is allright. I'd rather be on ubuntu though.

---

### Post by MasterSander on 2008-11-22
Now it just connects at startup weird enough then disconnects after a minute or two. My computer even crashed just now, possibly because of my wireless card.

---

### Post by s6pnj on 2008-11-22
I have the same or a very similar issue.  When I first boot into Ibex, my wireless conenction works fine.  I then start browsing / downloading and after a short time, the wifi disconnects and then wont let me reconnect unless I restart the computer.  It is a clean Ibex install, running Wicd, output of my iwconfig after the wifi has disconnected is

wlan0     IEEE 802.11bg  ESSID:"MYNETWORKNAME"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'll now reboot and post my iwconfig when the wifi is working.

So, following a reboot (wifi is now active) I get:

wlan0     IEEE 802.11bg  ESSID:"MYNETWORKNAME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:**:**:E9:5E:**   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality=100/100  Signal level:59/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by MasterSander on 2008-11-22
the only difference I see there is the frequency, but could that be the problem?

---

### Post by s6pnj on 2008-11-22
I don't think the freq is important, as once it has disconnected, the wifi dongle is effectively 'searching' and hence could be on any freq.  I think it's something to do with a 'pwer down' feature that is happening but I've been unsuccessful in using 
iwconfig wlan0 power off 
or
iwconfig wlan0 power on
to try and solve the issue.

---

### Post by MasterSander on 2008-11-22
I tried dmesg to check for the problem during boot.

sander@sanderpc:~$ dmesg | grep "wlan0"
[   42.257910] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.124998] wlan0: authenticate with AP 00:d0:d6:08:bd:0a
[   45.128832] wlan0: authenticated
[   45.128852] wlan0: associate with AP 00:d0:d6:08:bd:0a
[   45.131144] wlan0: RX AssocResp from 00:d0:d6:08:bd:0a (capab=0x421 status=0 aid=2)
[   45.131157] wlan0: associated
[   45.131601] wlan0: disassociating by local choice (reason=3)
[   73.209380] wlan0: authenticate with AP 00:d0:d6:08:bd:0a
[   73.377377] wlan0: authenticate with AP 00:d0:d6:08:bd:0a
[   73.377744] wlan0: authenticated
[   73.377753] wlan0: associate with AP 00:d0:d6:08:bd:0a
[   73.382393] wlan0: RX ReassocResp from 00:d0:d6:08:bd:0a (capab=0x421 status=0 aid=2)
[   73.382406] wlan0: associated
[   73.383233] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   83.568074] wlan0: no IPv6 routers present

and seems no IPv6 is detected and once it connects it exits for reason 3 whatever that may be.

---

### Post by MasterSander on 2008-11-22
bump

---

### Post by MasterSander on 2008-11-23
bump

---

### Post by MasterSander on 2008-11-23
I think it means I don't have an IPv6 router at home, but ofcourse that doesn't explain why it exits

---

### Post by MasterSander on 2008-11-24
bump

---

### Post by MasterSander on 2008-11-24
would reinstalling intrepid or installing hardy solve the problem?

---

### Post by MasterSander on 2008-11-26
bump

---

### Post by MasterSander on 2008-11-30
I seem to have no problem when the network is WEP encrypted

---

### Post by MasterSander on 2008-11-30
I think I found my answer :P

[   20.363442] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your hardware

---

