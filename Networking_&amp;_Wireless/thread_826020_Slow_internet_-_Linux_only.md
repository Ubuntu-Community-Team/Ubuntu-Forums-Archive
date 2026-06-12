---
title: "Slow internet - Linux only"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by robz0rz on 2008-06-11
Dear community


I've been having the feeling that my internet connection is much slower on Ubuntu Hardy than it used to be on Windows XP. I did some Googling and found out that disabling IPv6 helped improve many peoples connection. I'm not sure wether it was a placebo effect, but I get the feeling my internet has become slightly faster. Still, my downloads never exceed ~24kb/s.


I decided to put it to the test. I used [www.speedtest.net](www.speedtest.net) to do a test on my PC, and then one on my brothers PC (using Windows XP). The results were shocking:


Ubuntu:
Download: 253kbps
Upload: 65kbps

Windows:
Download: >2000kbps
Upload: >500kbps


There must be something wrong in a configuration file somewhere. Please help me bring my internet back to good speed! Thanks.



Details:
RT2500 card
using network-manager
WLAN network using WEP ASCII key
Connection strength always around 40% (used to be 70-80% in Windows)

---

### Post by rbolio on 2008-06-11
Similar problem.... BUMP! ha!

---

### Post by robz0rz on 2008-06-11
In a private message:

[QUOTE=Dizzle7677]here's a handy network tweaking link...
[http://www.zdnetasia.com/techguide/opensource/0,39044899,62038105,00.htm]("http://www.zdnetasia.com/techguide/opensource/0,39044899,62038105,00.htm")[/QUOTE]

I tried editing my configuration as the link suggested. It only made things worse, speedtest doesn't exceed 200kbps anymore even. It's depressing.

Why is the internet on my PC so much slower on Ubuntu Hardy than on Windows XP? (factor 10)

---

### Post by newmo on 2008-06-11
No idea - I have both XP and Hardy on one machine and there is not the slightest difference.

You are using two different machines though - use a Live CD on both your brothers machine and your own and see what results you get. 

Also bypass Firefox, I had issues with the IPV6 in the past, and just compare ping results.  Open terminal write 

ping [www.ebay.com](www.ebay.com) -c 6

That's what I would probably do.

---

### Post by robz0rz on 2008-06-12
I tested the internet speeds on my own machine (still an XP installation on it). The internet speeds on this machine on XP are over 2000/500, just as on my brothers machine. Ubuntu Hardy still not fast, I got speeds today of 350/60.

I think it might be a simple setting wrong somewhere, that caps my speeds at dial-up speeds. The reason I for this suspicion is that the System Monitor Panel Applet shows full network usage when I reach the speeds of 350. Could this be because my system is set somewhere that 350kbps is the maximum downspeed? Shouldn't the scaling on the applet be different otherwise? Just a thought...

---

### Post by robz0rz on 2008-06-19
I spent all of yesterday trying to fix my internet connection. I decided to reinstall Ubuntu using the alternate cd (I was pretty desperate). As always with reinstalling, I forgot to backup half my stuff, and I also found out that programs don't necessarily store ALL their preferences in ~/.program/ ...

Anyhow, I managed to get fast ineternet speeds yesterday night! I had been googling all night and I tried pretty much every solution that I saw. I had fast internet! The keyword here is "had". This morning, when I booted up, I was back to my 250kbps. I went through my firefox history and retired every solution, and what do you know! I have fst internet again!

[[IMG]http://www.speedtest.net/result/285793333.png[/IMG]](http://www.speedtest.net)

I'm not sure which solution did it, and I'm not sure how I'm going to make sure I don't have to redo it every time I reboot. But I thought I'd post my findings here for everyone to see.


**1. - Disable IPv6**
I didn't have to redo this after my reboot.


**2. - Do some sysctl.conf magix**
> [http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804](http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804)

sudo gedit /etc/sysctl.conf

Scroll to the bottom and just add these lines to it.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

run the sysctl to take effect.

sudo sysctl -pThe lines were still present in my configuration file, but I reran sysctl after reboot.


**3. - Do some iwconfig magix**
> sudo iwconfig wlan0 rate 54M 
Reran that after reboot.


---

I don't really know what I did and how exactly this fixed my internet speeds, but I'm thankful :) I hope this helps someone.

**Edit**
It's the third step that boosts my internet to great speeds, I found out after some testing. How can I make it so that that command (with sudo) runs ate very startup?

---

