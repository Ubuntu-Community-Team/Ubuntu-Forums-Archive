---
title: "Facebook won't open just on one PC at home network"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by galmeida on 2013-12-10
My computer, running ubuntu 10.04,  is connected via ethernet to a router(DLink DI-524) I used to create a wlan.

There is only another computer using the wireless network - and that computer is able to load facebook page normally.

On my computer, **I can load any page I've tried so far, except facebook**, whose page request seems to be completely ignored(I don't get even a 'page not found').

So:

 1. 1 router,  2 PCS, - one using wireless, the other using ethernet.
 2. Internet on wireless PC runs normally.
 3.  On the ethernet PC everything, **except facebook(which doesn't
    open)**, works normally.

Can anyone help me to fix this?

I'm willing to post output of any commands you guys ask.

Thanks

PS: When I disable the router as 'middleman'(dismantle the wlan) and use just the modem connected via ethernet to my PC I can load facebook normally. I guess this is an extra clue.


[SIZE=3]**Update 1:** [/SIZE]I found that facebook apparently does not work only when I'm already logged in.
If I'm logged out the initial page for login loads normally. Then I login and for that moment on nothing loads.
[U]Also I found out that I cant POST anything here at these boards when logged at the wlan, neither can post anything in askubuntu

[/U]
[SIZE=3][B]Update 2 : 
 [/B][/SIZE]1)Just something I forgot to add: the pc for which the wireless works is using windows 7
2) Links to super user and wireshark questions
[http://superuser.com/questions/686738/home-wlan-wont-let-me-do-very-specific-thingslog-in-facebook-post-on-some-for](http://superuser.com/questions/686738/home-wlan-wont-let-me-do-very-specific-thingslog-in-facebook-post-on-some-for)
[http://ask.wireshark.org/questions/28028/can-wireshark-help-me-with-my-home-wlan-problemcant-login-or-post-things-on-forums](http://ask.wireshark.org/questions/28028/can-wireshark-help-me-with-my-home-wlan-problemcant-login-or-post-things-on-forums)

wireshark:
A) Logging on facebook while connected directly to the modem: [http://s12.postimg.org/cph9ybpb1/facebook_wo_wlan.png](http://s12.postimg.org/cph9ybpb1/facebook_wo_wlan.png)
 B) **Trying**(didn't work) to log on facebook while connected to the router: [http://s30.postimg.org/8makj4is1/facebook_w_wlan.png](http://s30.postimg.org/8makj4is1/facebook_w_wlan.png)
 I see a difference (apparently a lot of bad checksum packages) but I don't know if that's the problem or how to fix it





3) traceroute -  I noted nothing different, just the expected extra hop between the router and the modem

With working configuration ---------------------------------------------------------------------------------
$ traceroute facebook.com
traceroute to facebook.com (173.252.110.27), 30 hops max, 60 byte packets
 1  192.168.254.254 (192.168.254.254)  1.114 ms  1.581 ms  2.068 ms
 2  200-217-90-91.host.telemar.net.br (200.217.90.91)  44.663 ms  46.606 ms  49.707 ms
 3  xe-6-2-0.0-mpi-mg-rotn-j01.telemar.net.br (200.164.13.91)  51.749 ms  53.683 ms  56.564 ms
 4  so-0-1-0.0-gua-sp-rotn-j01.telemar.net.br (200.164.197.213)  76.728 ms  81.827 ms so-9-1-0.0-bot-rj-rotn-j01.telemar.net.br (200.223.44.161)  71.750 ms
 5  BA199060242.user.veloxzone.com.br (200.199.60.242)  197.539 ms 200.223.41.246 (200.223.41.246)  198.533 ms BA199060242.user.veloxzone.com.br (200.199.60.242)  202.593 ms
 6  xe-5-0-1.br01.mia1.tfbnw.net (103.4.96.12)  201.588 ms  178.859 ms  172.916 ms
 7  ae7.bb02.atl1.tfbnw.net (204.15.23.252)  204.205 ms ae14.bb02.atl1.tfbnw.net (31.13.29.74)  207.960 ms  210.873 ms
 8  ae13.bb04.frc1.tfbnw.net (204.15.20.75)  229.908 ms ae10.bb04.frc1.tfbnw.net (31.13.27.114)  209.036 ms ae16.bb01.frc1.tfbnw.net (31.13.27.118)  239.212 ms
 9  ae1.dr01.frc1.tfbnw.net (31.13.24.15)  227.713 ms ae1.dr04.frc1.tfbnw.net (31.13.27.80)  209.803 ms ae39.dr02.frc1.tfbnw.net (31.13.27.57)  205.937 ms
10  * * *
11  * * *
12  edge-star-shv-13-frc1.facebook.com (173.252.110.27)  186.110 ms  184.008 ms  191.134 ms


With non working configuration-----------------------------------------------------------------------

$ traceroute facebook.com
traceroute to facebook.com (173.252.110.27), 30 hops max, 60 byte packets
 1  192.168.0.33 (192.168.0.33)  0.428 ms  0.440 ms  0.489 ms
 2  192.168.254.254 (192.168.254.254)  1.608 ms  2.029 ms  2.455 ms
 3  200-217-90-91.host.telemar.net.br (200.217.90.91)  45.727 ms  47.704 ms  48.647 ms
 4  xe-6-2-0.0-mpi-mg-rotn-j01.telemar.net.br (200.164.13.91)  51.746 ms  54.589 ms  56.472 ms
 5  so-0-1-0.0-gua-sp-rotn-j01.telemar.net.br (200.164.197.213)  73.683 ms ge-6-3-0.0-arc-rj-rotn-j01.telemar.net.br (200.223.46.195)  80.787 ms xe-14-0-0.0-bot-rj-rotn-j01.telemar.net.br (200.223.46.193)  72.711 ms
 6  xe-7-1-0.0-mia-us-rotb-j01.telemar.net.br (200.223.46.142)  210.554 ms BA199060242.user.veloxzone.com.br (200.199.60.242)  206.759 ms xe-5-0-0.0-mia-us-rotb-j01.telemar.net.br (200.223.154.158)  174.927 ms
 7  xe-5-0-1.br01.mia1.tfbnw.net (103.4.96.12)  178.767 ms  179.626 ms  182.737 ms
 8  ae7.bb02.atl1.tfbnw.net (204.15.23.252)  211.780 ms  213.683 ms be25.bb02.dca1.tfbnw.net (173.252.64.90)  207.889 ms
 9  ae13.bb04.frc1.tfbnw.net (204.15.20.75)  227.732 ms  238.767 ms ae16.bb01.frc1.tfbnw.net (31.13.27.118)  246.646 ms
10  ae1.dr02.frc1.tfbnw.net (31.13.24.19)  198.745 ms ae40.dr02.frc1.tfbnw.net (31.13.27.69)  219.685 ms ae1.dr02.frc1.tfbnw.net (31.13.24.19)  212.584 ms
11  * * *
12  * * *
13  edge-star-shv-13-frc1.facebook.com (173.252.110.27)  186.997 ms  192.703 ms  191.748 ms

---

### Post by 7182818 on 2013-12-10
While connected to the WLAN, can you run 'nslookup facebook.com' and post the output?  Also, what is the output of ifconfig?

---

### Post by galmeida on 2013-12-10
[SIZE=3]**Update:** [/SIZE]I found that facebook apparently does not work only when I'm already logged in.
If I'm logged out the initial page for login loads normally. Then I login and for that moment on nothing loads.
_Also I found out that I cant POST anything here when logged at the wlan_


-----------------------------------------------------------------------------
~$ nslookup facebook.com
Server:        192.168.254.254
Address:    192.168.254.254#53

Non-authoritative answer:
Name:    facebook.com
Address: 173.252.110.27
-----------------------------------------------------------------------------
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 54:04:a6:68:ed:73  
          inet addr:192.168.0.144  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe68:ed73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:329590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:385714067 (385.7 MB)  TX bytes:35999681 (35.9 MB)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:798189 (798.1 KB)  TX bytes:798189 (798.1 KB)

---

### Post by Bucky Ball on 2013-12-10
Just an off-topic note: 10.04 LTS is no longer supported (hasn't been since April). You will receive neither regular updates or, more importantly, security updates. I would advise upgrading to a supported release (12.04 LTS is supported until April 2017).

Good luck.

---

### Post by 7182818 on 2013-12-11
That's good that your DNS is working then.  This is definitely a weird issue!

When confirming that the webpages work or not, make sure you refresh by holding down the 'Ctrl' key and then hitting 'F5'.  That way you won't be seeing any copies of old webpages that your browser saved.

Can you try doing 'traceroute [www.facebook.com'?](www.facebook.com'?)  Also, run traceroute to a website that you haven't had issues connecting to previously.  Is there any difference there?  You can also try tracerouting to facebook when you are both logged in and logged out, although it seems like a stretch to think that they would be different!

---

### Post by galmeida on 2013-12-11
I posted the traceroute on update 2. I can't see anything wrong. I thought maybe wireshark could give a clue, but I don't know what to look for(and I'm not a network expert..).  posted a link to the wireshark 'stackoverflow' question I created,  together with screenshots of both working and non working configurations

---

### Post by bapoumba on 2013-12-12
Any specific browser plugins or extensions on this computer ? If using noscript, I had to recently add an exception to one of FB stuff otherwise the page would appear blank.

---

