---
title: "Surfing slow but download speeds high!"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-06-17
In Hardy, I have noticed Firefox (and other browsers) are slow. They are slow when opening a new link. or clicking a link. Its slow. But my download speeds are high, 800kb/s.

I've disabled ipv6 in firefox and in Ubuntu. But my surfing is still slow! 
How can I get my true speed (like in Vista)?

I'm using Ndiswrapper to run my Wireless card. RTL8187B.
Here are some outputs, if they help:
```
tom@Laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:83:60:87   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tom@Laptop:~$ 

```
Also, Network manager doesnt work. So I run a little script to establish a connection. This script runs at start up.
```
ifconfig wlan0 up
dhclient -r wlan0
iwconfig wlan0 mode Managed
iwconfig wlan0 essid "linksys"
iwconfig wlan0 key my_key open
dhclient wlan0
```


How can I speed things up??

If I remember, I had fast surfing in Gusty. (I was using nm-applet to connect me to my wireless, it will not work in Hardy).


Thanks,
Tom

---

### Post by Tom--d on 2008-06-17
Anyone?

---

### Post by superprash2003 on 2008-06-17
try changing your DNS servers to opendns 208.67.222.222 and 208.67.220.220

---

### Post by dmizer on 2008-06-17
> **superprash2003 said:**
> try changing your DNS servers to opendns 208.67.222.222 and 208.67.220.220

indeed, i'll second that.  howto here: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by Tom--d on 2008-06-18
> **superprash2003 said:**
> try changing your DNS servers to opendns 208.67.222.222 and 208.67.220.220

Why?
What will it do?
Where and who's ips are they?

---

### Post by dmizer on 2008-06-18
> **Tom--d said:**
> Why?
What will it do?
Where and who's ips are they?

1) slow browsing can be caused by a number of different things.  one thing that can cause slow browsing is slow domain name resolution.  ubuntu often defaults to your router ip address for its domain name resolution instead of defaulting to your isp's dns servers.  because of this, ubuntu has to wait for your router to time out before trying your isp's dns servers.

2) changing to opendns domain name servers will bypass this tendency.

3) read more about opendns here: [http://www.opendns.com/how/dns/turning-names-into-numbers](http://www.opendns.com/how/dns/turning-names-into-numbers)

in my previous post, i linked to the howto for setting ubuntu up with opendns servers.  most often, opendns is faster and safer than your isp's dns servers.  i highly recommend using opendns even if it does not solve your problem.

---

### Post by Tom--d on 2008-06-18
How is it safer?

Also, I did it. And I do not see a differnce. 
Do I still use my ISP?

---

### Post by dmizer on 2008-06-18
> **Tom--d said:**
> How is it safer?
take a look at this presentation for more information on that: [http://www.opendns.com/how/safer/content-filtering/](http://www.opendns.com/how/safer/content-filtering/)

summary: it prevents bad stuff from getting to your computer by preventing it from getting resolved in the first place.

> **Tom--d said:**
> Also, I did it. And I do not see a differnce. 
Do I still use my ISP?

as i indicated before, you are probably better off with opendns even if it does not correct your problem.

have you tried rebooting your router?  just unplug it, leave it unplugged for 5 seconds or so, and plug it back in.

---

### Post by Tom--d on 2008-06-18
> **dmizer said:**
> 1) slow browsing can be caused by a number of different things.  one thing that can cause slow browsing is slow domain name resolution.  ubuntu often defaults to your router ip address for its domain name resolution instead of defaulting to your isp's dns servers.  because of this, ubuntu has to wait for your router to time out before trying your isp's dns servers.


But, there are 3 DNS enteries in my Network:


212.139.132.25
212.139.132.24
and my router ip. 


How can I direct my connections straight to my isp servers?

---

