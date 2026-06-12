---
title: "intel wifi strangeness on a thinkpad x31"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by twoblackeyes on 2007-01-23
So I just installed 6.10 on a thinkpad x31 with the standard centrino Intel 2100 wireless module. I'm seeing some odd behavior in trying to get wifi running:

In the ubuntu Network admin panel, I see my wireless card detected along with the built in ethernet. When I go to configure wifi, though, I can't browse any of the available essids with the drop down menu (like I could with an older ndiswrapper-supported card on another machine)--it's blank. When I type in my network name and WEP key, I get no connection. 

I installed Network Manager, and it can only see my wired connection. There are no wireless options in the drop-down menu of nm-applet. 

Third time's the charm, as I installed wifi-radar, which seems to be working just fine. I can browse available networks and connect just fine. 

One thing I noticed that's peculiar is that the whole time, iwconfig says I'm up and running and connected:
```
eth1      IEEE 802.11b  ESSID:"EmailFromToilet"  Nickname:"EmailFromToilet"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:30:BD:FB:A7:53   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And also weird is that ifconfig sees the eth1 as a wired connection. I'm not sure if that's normal or not:
```
eth0      Link encap:Ethernet  HWaddr 00:0D:60:80:3A:C2  
          inet6 addr: fe80::20d:60ff:fe80:3ac2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:18604 (18.1 KiB)  TX bytes:7108 (6.9 KiB)
          Base address:0x8000 Memory:c0220000-c0240000 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:05:C0:BC  
          inet addr:192.168.2.14  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe05:c0bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2184741 (2.0 MiB)  TX bytes:420961 (411.0 KiB)
          Interrupt:11 Base address:0xa000 Memory:c0210000-c0210fff 
```
 I'd really like to be able to use network manager.  Does anyone have any idea what might be happening? Thanks for the help...

---

### Post by ubuntu.daemon on 2007-03-05
well i finally got the problem covered i guess lol.  When you go to ur networking, i havent been able to get a list of ssid's either, so i just put an asterisk there *.  Though i use wifi-radar, but when i start it up it says i have an ip of 169.blah  so i disconnect, then reconnect and it gives me the proper 192.168.1.34.  I usually do sudo ifconfig eth0 down before i do all that just so it doesnt give me any issues.  So ya let me know how this goes so i can help ya out

---

