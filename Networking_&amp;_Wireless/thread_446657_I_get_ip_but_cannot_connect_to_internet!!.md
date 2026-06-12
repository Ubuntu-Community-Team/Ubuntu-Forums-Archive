---
title: "I get ip but cannot connect to internet???!!"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by kondax on 2007-05-17
Hi all !!!!!!

I have a laptop and installed recently kubundu feisty fawn!!
also i have dsl connection in greece and i connect with SAGEM 800 E4!!

When i give the followings:

mike@mike-laptop:~$ sudo modprobe pppd
mike@mike-laptop:~$ sudo modprobe pppoatm

My computer gets ip, subnet mask,etc but i cannot surf in world wide web!!!
see for yourself :

mike@mike-laptop:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol
          inet addr:83.212.47.79  P-t-P:83.212.27.230  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:9178  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1508 (1.4 KiB)  TX bytes:1407 (1.3 KiB)

I will be greatfull for your replies mates 
Thank you !!!:)

---

### Post by Wim Sturkenboom on 2007-05-17
Try [http://64.233.167.99](http://64.233.167.99) in the address bar of your browser. It should take you to google. If so, you have a problem with the DNS (resolving of name to IP address). If not, something else is wrong (maybe firewall).

---

### Post by kondax on 2007-05-17
Thank you Wim Sturkenboom for the help but it didn't work!!!
also i do not have a software firwall in kubundu..!!

Any other thought of the problem??

---

### Post by eentonig on 2007-05-17
if you do 

tracepath 64.233.167.99 

What do you get as output? It could be that you didn't get a default gateway.

---

### Post by kondax on 2007-05-17
when i typed [http://64.233.167.99](http://64.233.167.99) it said that could not find the host!!!

Any ideas of what is wrong???

---

### Post by Randy R on 2007-05-21
If you don't have this fixed yet, start the connection and do an 'ifconfig ppp0', then do a 'route' and post the results

---

### Post by kondax on 2007-05-23
Thank you Randy R for your help but i fixed it!!!!

---

### Post by toylas on 2007-05-23
kondax! maybe you could post you solution here...

---

### Post by Chappy7777 on 2007-05-23
> **toylas said:**
> kondax! maybe you could post you solution here...
Yea, please let us know what you did to get it working.

Thnx, Chappy

---

