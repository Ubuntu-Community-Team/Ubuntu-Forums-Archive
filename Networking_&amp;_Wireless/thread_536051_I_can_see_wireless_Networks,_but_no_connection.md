---
title: "I can see wireless Networks, but no connection"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by stuismad on 2007-08-27
I am using Knetworkmanager with Ubuntu Feisty 7.04, and have current internet connection via 'eth0'. (wired ethernet connection)

I am able to see the wireless networks available to connect to, however when I try and connect to them _they stall at 28%_. Obviously there is some sort of connection there, but I cant for the life of me figure it all out.

When I take a look at System>Administration>Network...I see that the eth0 is there and active, and there are two Wireless Connections. **_wlan0 and wmaster0_**. Both are in roaming mode.

I've noticed that when I try to connect via wireless, it uses wlan0 and not wmaster0.

here's some prompt info.

**IFCONFIG**
> 
eth0      Link encap:Ethernet  HWaddr 00:03:0D:66:D1:A7  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe66:d1a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8957801 (8.5 MiB)  TX bytes:1010003 (986.3 KiB)
          Interrupt:17 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1508 (1.4 KiB)  TX bytes:1508 (1.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:A1:3E:13  
          inet6 addr: fe80::210:60ff:fea1:3e13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:28904 (28.2 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:10:60:A1:3E:13  
          inet addr:169.254.4.11  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-10-60-A1-3E-13-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



**IWCONFIG**
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"<G604T_WIRELES>"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



All help appreciated in advance.

---

### Post by stuismad on 2007-08-27
Anyone able to offer some help?

---

### Post by stuismad on 2007-08-28
Earth to friendly support team....
...are you alive?

Anyone? :(

---

### Post by wobwill on 2007-08-28
Hi Stuismad,

Firstly I am unable to help you with your issue - sorry. However I saw your frustration in your posts and thought some friendly support was called for. 

In a 12 step style - my name is Will, i've been trying to connect to the internet wirelessly for 2 weeks now using ubuntu v7.04. I've reinstalled 3 times and had a working connection for about 2 days. 

Sorry I don't have an answer or am even able to point you in the right direction. You are not the only one suffering.

Will.

---

### Post by will71110 on 2007-08-28
If you dont want it to use wmaster0 you can shut it down.  Do this by,

ifconfig wmaster0 down

That will disable wmaster0.  See what that does for you.

ifconfig wmaster0 up

will turn it back on

---

### Post by lisati on 2007-08-28
Just a guess: have you had any success when you physically disconnect your wired connection? It might be that the way your machine is setup the presence of the wired connection might be pre-empting the wireless connections.....

---

### Post by stuismad on 2007-08-28
Thank you for the reply's guys.
I know there are a lot of people with Wireless connection issues, so thanks for taking the time to reply to me. Much appreciated!

Wobwill  -  i hope you get your problems sorted soon too, and thanks for the friendly omment! :)

Will71110  -  I am currently at work, but as soon as I get home I'll give your advice a shot. I'll report back my findings later this evening.

Thanks again.

---

### Post by stuismad on 2007-08-28
**update**

So I got home, unplugged the thernet wired conenction and booted. no luck, wireless has same problem as before.

so then I ran the *_ifconfig wmaster0 down_* command and nothing again. I tried running it under Sudo, and the only difference was it asked for my root admin password. No  change.

Any advice?

---

