---
title: "I have internet, but cant load websites"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by monstermudder78 on 2007-05-17
Ok, here is my problem in a nutshell:
I have a desktop that is dual booting XP/Dapper.  The Dapper was a fresh install last night because Feisty totally crashed everything (but thats another story)  When I boot Dapper I cant get firefox to load any websites, and the update manager won't connect.  When I reboot into XP everything works fine, internet messenger everything.  I also have a laptop dual booting XP/Edgy.  When I boot Edgy and open Firefox no pages will load, but forecastfox can get the weather forecasts and Kopote can connect.  All of these problems SEEM to have happened last night after I restarted both my modem and router b/c of a lighting storm that caused a momentary loss in power.  Any ideas?

---

### Post by blazercist on 2007-05-17
did you have internet before you reset the modem/router?  post to output of sudo ifconfig here.

It may be a DNS problem if some apps can connect they are probably using straight ip addresses rather than hostnames.... try setting your DNS server manually.

---

### Post by monstermudder78 on 2007-05-17
I had been using the internet earlier in the day.  After the power outage I couldn't get pages to load so I reset everything as that has fixed similar problems in the past.  Here is ifconfig for the laptop:

```
eth0      Link encap:Ethernet  HWaddr 00:0D:56:A9:14:26  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fea9:1426/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1189996 (1.1 MiB)  TX bytes:70897 (69.2 KiB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan1     Link encap:Ethernet  HWaddr 00:0E:2E:82:42:41  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe82:4241/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:646 errors:393 dropped:73 overruns:0 frame:0
          TX packets:948 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:281722 (275.1 KiB)  TX bytes:126321 (123.3 KiB)
          Interrupt:11 Memory:d8a5a000-d8a5a100 
```

I'm not exactly sure how to set my DNS server manually but I am searching for the answer now, can anyone point me in the right direction?

---

### Post by blazercist on 2007-05-17
ok first of all the problem may be that you have two interfaces up.  maybe you want to down one with 
sudo ifconfig wlan1 down

Also, can you try typing [http://64.233.167.99](http://64.233.167.99) into your browser's address bar.  If this works then its def a DNS problem.

Are you using network-manager?

---

### Post by monstermudder78 on 2007-05-17
I am not using Network Manager, but I do have wireless assistant installed, although it doesnt seem to do much. 

I did a little checking and it seems the only connection that is being used is eth0, with the cable unplugged and wlan1 up or down and lo up or down nothing happens at all, it goes straight to "server not found."

Using eth0 I can get to google using 64.233.167.99, but not [www.google.com](www.google.com).  If I can get help with the DNS issue I think I can fix the wireless prob myself.

**UPDATE** I used the OpenDNS addresses 208.67.222.222 and 208.67.220.220 instead of the old addresses 192.168.0.1 and 205.171.3.65 and it works now.  Any idea why the old addresses would suddenly stop working?

---

### Post by blazercist on 2007-05-17
well 192.168.0.1 is your router, perhaps you turned off the routers DNS server by accident?

---

### Post by thelinuxguy on 2007-05-17
What type of Internet connection do you have? Is the Internet accessible when you switch on the router or do you have to use pppoe (or rppppoe) after switching on your router. I think the router's dns server matters in the first case (and for resolving names on the LAN). In the second case, the dns server settings are stored in a configuration file. This dns server is contacted for resolving Internet domain names. The solution posted at [http://ubuntuforums.org/showpost.php?p=1364482&postcount=19](http://ubuntuforums.org/showpost.php?p=1364482&postcount=19) may help.

Does that solve your problem?

---

