---
title: "Wireless issues"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Shayne22 on 2007-09-10
Hi I'm staying in a hostel for a few months and they've got wireless internet to which I'd really like to be able to connect.  
I'm running Xubuntu Feisty Faun on an oldish laptop.  I've been using Wicd in the past without issue to connect to several different wireless networks.  I don't know anything about the network here, even whether it is WEP or WPA except for the ssid and password.  
First times I tried to login it got stuck on the Generating PSK message and wouldn't stop.  I tried both WPA and WEP.  
I then saw something about WEP networks getting stuck there, and putting quotation marks around the password being a workaround.  I tried that and now it gets to the Obtaining IP stage, tries for a while and then gives up, returning to not connected.  

Some outputs:
From lspci -v:

02:02.0 Network controller:  Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
   Subsystem: IBM PRO/1000 MT Mobile Connection
   
From iwconfig

eth1  unassociated  ESSID:"hostel"  Nickname:"ipw2100"
Mode:Managed Channel=0  Access Point:  Not-Associated
Bit Rate=0Kb/s  Tx-power:16dBm
Retry limit: 7  RTS thr:off  Fragment thr:off Power Management:off
Link Quality:0  Signal level:0 Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  Tx excessive retries:0  Invalid misc:0  Missed beacon:0

Thanks for any ideas
Shayne

---

### Post by lbriner on 2007-09-11
Sorry to state the obvious but do you know that you are getting a good signal from the wireless access point? Especially if you have others accessing the same transmitter, the signal can drop quite low and the computer therefore doesn't have a successful conversation. Also if it is in reasonably heavy use, many routers seem to be slow at handing out IP addresses to new connections and again the connection times out. If your hardware worked before then there is a fairly good chance it is something simple like this.

Luke

---

### Post by Shayne22 on 2007-09-11
That could be the problem and I'll look into it, but I don't particularly think so.  I have been trying for almost a week now, and at different times during the day.  And I know that new users, with windows, have been able to get on without problems.  I'll give another try maybe late tonight and see if that fixes it.  Thanks for the suggestion

---

### Post by sympeltun on 2007-09-13
wow, thats the same problem i've been having.. network manager doesnt want to connect to the network at my university. (64 bit ascii or hex key) i'm hoping someone replies and helps fix this problem

---

