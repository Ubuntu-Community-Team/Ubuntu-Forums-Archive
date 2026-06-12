---
title: "Knetworkmanager and connecting to my University's campus Wireless"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by TheVrolok on 2007-01-24
Basically, like many universities, mine (Penn State) offers wireless internet access to the school's network at many locations on campus.  I've had no problems connecting to it under windows but I just can't seem to get my linux laptop to play nicely.  My wireless is flawless at my apartment, but attempting to connect to our network here is not so easy.  knetworkmanager reports that the network is seen and even gives me signal strength reports.  However, when I try to connect it just hangs at 28% (configuring device or activating device?  I forget which) before it gives up and returns to "disconnected."

The general procedure under windows was simply to connect to the network, then run Cisco's VPN client to log into the network.  In linux, I installed the PPTP addon for knetworkmanager and configured the VPN (obviously not tested as I can't connect) but I'm being halted by the lack of primary connection.  I was planning on just using knetworkmanager to connect to the network, and once connected using the VPN functionality.  And if that didn't work, I'd try to compile myself a working Cisco VPN client (the amd64 version just doesn't seem to want to work) or vpnc, or something else.  Bottom line is that I can't begin to troubleshoot the VPN client (if necessary) until I can actually connect to the network.

Anyone have any similar experiences or suggestions?  Maybe more verbose ways to see what exactly is going on?  It's there a better way to get connecting information from knetworkmanager than simply the "connecting.." popups?  

Thanks in advance!

---

### Post by optimarcus_prime on 2007-01-25
I'm on the Connecticut College campus having what I believe is a similar problem.  On windows setups, the computer will detect the wireless network and will ask for your network credentials, meaning your ConnColl user name and password, and then the Internet will work.  However, as far as I can see, there is no way to input this user name and password anywhere.  So, I also would appreciate some sort of workaround for this problem.

---

### Post by optimarcus_prime on 2007-01-25
This is the output from my iwlist scan for the cell that I want to connect to:
 ```
Address: 00:11:5C:0D:E6:60
ESSID:"conncollwireless"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.432 GHz (Channel 5)
Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                 48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0
```

My friend suggested that what I need to do is find a way to do PEAP authentication.  Any ideas on how to do this?

---

