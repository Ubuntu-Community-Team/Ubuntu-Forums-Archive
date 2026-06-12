---
title: "firefox doesnt load some web pages"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by basilwatson on 2009-01-14
Now this is getting annoying , My laptop ( Gos Os ) Load the pages fine , no problem , with restricted media all ok 

My main desktop  running 8.10 doesnt load the page( s)   the difference ..
Os  and firefox version,  I have tried opera , ( loads but doesnt render properly , seamonkey , and firefox 2  same problems 

I was listening to the bbc last nite , now it wont connect ..same desktop

pentium 4 1 gig ram Nvidia 5200 card 


I am not sure if its the desktop , Ubuntu , or internet provider 


Any Ideas 


Stephen

ps 200th click it connected

---

### Post by Paqman on 2009-01-14
Just certain sites, or the whole internet? If it's just certain sites, what were they?

---

### Post by superprash2003 on 2009-01-14
try changing your DNS servers to  opendns [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by basilwatson on 2009-01-14
> **superprash2003 said:**
> try changing your DNS servers to  opendns [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)


whoooooooo it does make the web faster !  Big thanks for that !  but it didnt change the web pages ,,,

My laptop works fine and that is wireless to a router , this is the main desktop cable from the same router 

The sites are such as [www.stuff.co.nz](www.stuff.co.nz) , the bbc , and letsjapan ,,, they just time out 

the only difference between the two systems are 

the operating Hardware , OS , and restricted drivers ...

but what is causing the page not to open I dont know , 

Stephen

---

### Post by w7kmc on 2009-01-14
Running UB 8.10 with Firefox 3.05 and have not problem opening the BBC or the news site in NZ.

---

### Post by superprash2003 on 2009-01-15
then there is one more thing to try.. try changing MTU values [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by basilwatson on 2009-01-19
> **superprash2003 said:**
> then there is one more thing to try.. try changing MTU values [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)


I wonder what it is , the bbc works slowly but does open , [www.stuff.co.nz](www.stuff.co.nz) , just times out ,,, but on the laptop its fine 

I gave up with me Mtu file its set to 1500 but I couldnt find the file in which to add that line to ... 

Ill try again later 

Stephen

---

### Post by basilwatson on 2009-01-19
auto lo
iface lo inet loopback

This is the output from my network file my ifconf is as follows
eth0      Link encap:Ethernet  HWaddr 00:10:dc:cd:c7:89  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1448248 (1.4 MB)  TX bytes:391799 (391.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10404 (10.4 KB)  TX bytes:10404 (10.4 KB)


I added mtu 1492 in the network file but it didnt make a difference 


also changed it to 1454 no joy ...

those pages just wont open 


Stephen

---

