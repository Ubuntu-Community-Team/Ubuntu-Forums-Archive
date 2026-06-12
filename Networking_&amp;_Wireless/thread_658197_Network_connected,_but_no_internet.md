---
title: "Network connected, but no internet???"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by tim558 on 2008-01-04
Im having some DNS trouble.  I know its DNS cause when i type an IP addy of google into firefox it loads the page (slowly); but it wont load 'www.google.com' 
Problem is my router setup is a little funny, i have 2 routers strung together, one has an ADSL modem which is connected to the internet (it works fine on XP) with addy 192.168.1.1.  The second has no modem but is a netgear with g wireless (the other only has b) which we need to cover the whole house.  The netgear has IP 192.168.2.1 so there is no conflict with the first router and both modems are accessable with firefox from BOTH xp and ubuntu.  The netgear is set up to force all computers into the 192.168.1.x domain however (e.g. even though connected to the netgear router my laptop atm has an IP of 192.168.1.5) and on windows this all works just fine with the internet, torrents and games connecting like a charm.

I dont think its a connection problem to the network purely because ifconfig and iwconfig are showing im connected and everything is working fine.
Interestingly iwconfig is showing these lines but i cant interpret them
"Rx invalid nwid:251 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0 Missed beacon:0"   <- im guessing thats not normal!

In System>Administration>Network under the DNS tab ive tried having both 192.168.1.1 & 192.168.2.1 as DNS servers but it doesnt seem to be working, any hints, see anything ive done wrong??

---

### Post by reckless2k2 on 2008-01-04
well you need to specify a gateway for one. i'm a little unclear what gateway you are supposed to be using. after that you need to specify a nameserver in /etc/resolv.conf. the nameserver issue will resolve your DNS prob.

---

### Post by tim558 on 2008-01-04
Thanks for the quick reply

After having a bright idea i ran ipconfig/all on XP and discovered XP uses 192.168.2.1 as its DNS server so ill try that again.  As far as nameservers im a little unclear as to what this entails...

If you could flesh out your comment there or give a link to someone who has it'd be much appreciated (I'm a bit of an Linux rookie)

---

### Post by reckless2k2 on 2008-01-04
you would have to take a look at your /etc/resolv.conf file. that houses your dns nameservers. 

open a terminal window and type:

```
cat /etc/resolv.conf
```

the output should be something like this:

```
nameserver 192.168.2.1
nameserver 68.38.175.4
```

you get the idea. if i'm not mistaken, this can be viewed and edited in the network manager as well in the properties of that network device.

---

### Post by tim558 on 2008-01-04
Well i tried looking at the resolv.conf file and it spat out 
192.168.2.1
192.168.1.1
Which are the two DNS serveres I had guessed at.  Should there be a third one, an external IP provided by my ISP??

Again a sidenote, had a look at the output from ifconfig ...
---------------------------------------------------------------------------------------------------------
inf

ath0      Link encap:Ethernet  HWaddr 00:14:6C:31:A3:A7  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe31:a3a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30045 (29.3 KB)  TX bytes:22085 (21.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:1B:FC:E4:7D:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6000 (5.8 KB)  TX bytes:6000 (5.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-31-A3-A7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4615 errors:0 dropped:0 overruns:0 frame:170
          TX packets:346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:764992 (747.0 KB)  TX bytes:38312 (37.4 KB)
          Interrupt:19 
---------------------------------------------------------------------------------------------------------
Should there really be a wifi0 connection there?? When I run iwconfig its the ath0 connection thats associated to the SSID of my routers network so im assuming there could be a conflict?
If so could this be caused with messing about with ndiswrapper (I confess I have been) and if so how do you turn of ndiswrapper?

---

### Post by reckless2k2 on 2008-01-04
i personally use 2 external DNS servers and then the last one i use is the internal DNS server for hostname stuff inside. i remember there being something about wifi0 being associated with ath0 but i wouldn't be that concerned.

---

### Post by tim558 on 2008-01-04
Uh ok, thats nice, I have no idea what the second external DNS address should be, I thought ubuntu was supposed to detect that automatically...
Is there any more information you need?

---

### Post by reckless2k2 on 2008-01-04
your router will usually have the external DNS servers. it will have the address from your ISP as well as your DNS addresses. if you have DHCP enabled inside your network, it typically will use the router as the DNS source. i just prefer external to resolve names back to internal. like if you are running a server that's excessable from the real world.

---

### Post by Lostincyberspace on 2008-01-04
Try using this site here they show how to use there server for dns it might help
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

If you cant get there I will post the steps here if you need them.

---

### Post by Al42 on 2008-01-04
Emasculate your Netgear.  (They actually give instructions for this for one of their wireless routers on their site.)

Connect the cable from the modem to one of the **LAN** ports on the Netgear and turn off DHCP on the Netgear.  The Netgear will be acitng as a **NON**-Natting-WAP - it'll give you wireless, but the modem will be giving anything connected (wired or wireless) its address.  Natting (address translation) twice causes more problems than it's worth trying to fix.

---

### Post by tim558 on 2008-01-05
Excellent Lostincyberspace, I tried that open source DNS provider and they were fantastic.

Al42, I understand what you're saying and believe me its not my ideal solution, ubuntu seems to see both subnets but I think its the crappiness of the older modem/router, it wont broadcast the DNS properly (even though XP picks it up and both my flatmates who are on macs never seem to have problems either).  Its just an interim solution until I get a new router/modem that has a decent access point in it! 

For anyone looking at this in the future, the problem was with ubuntu not picking up my ISP's DNS servers off the modem, the solution, just bypass your ISP and use open source DNS servers!!! (see link > [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu))

Problems solved, thanks to all for help :guitar:

---

