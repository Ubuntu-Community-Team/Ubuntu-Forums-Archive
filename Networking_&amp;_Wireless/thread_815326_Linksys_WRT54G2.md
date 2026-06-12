---
title: "Linksys WRT54G2"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by Mgiacchetti on 2008-06-01
I want to make this a bridge.
 
Is there anyone out there that has [this]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175242886869&pagename=Linksys%2FCommon%2FVisitorWrapper") router and has been successful at installing a 3rd party firmware that supports the conversion into a bridge?
 
 
ANYONE?

---

### Post by kevdog on 2008-06-01
Yes dd-wrt.  Google for it -- its capable of a lot!!

---

### Post by lethalfang on 2009-07-11
I want to get wake-on-LAN to work. Installing a 3rd party firmware like DD-WRT may be the way to do it.
Anyone has experience installing DD-WRT onto WRT54G2 and would like to share the details how HOWTO?

Thanks!

---

### Post by senor_smile on 2009-07-11
I have the wrt54g ver 6(a fairly old one) with dd-wrt ver 23 installed and set up as a bridge.  It works fabulously. 


For installing firmware: 
[http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G2]("http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G2")

For setting up the bridge: 
[http://www.wi-fiplanet.com/tutorials/article.php/3639271]("http://www.wi-fiplanet.com/tutorials/article.php/3639271")

---

### Post by lethalfang on 2009-07-14
> **senor_smile said:**
> I have the wrt54g ver 6(a fairly old one) with dd-wrt ver 23 installed and set up as a bridge.  It works fabulously. 


For installing firmware: 
[http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G2]("http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G2")

For setting up the bridge: 
[http://www.wi-fiplanet.com/tutorials/article.php/3639271]("http://www.wi-fiplanet.com/tutorials/article.php/3639271")

Thanks for the link.
I have zero experience installing 3rd party firmware to routers, and I have this dumb question:
What is tftp.exe? What does it do? 
How do I set my PC to a static IP of 192.168.1.10?

---

### Post by superprash2003 on 2009-07-14
> How do I set my PC to a static IP of 192.168.1.10?
are you talking about a windows or ubuntu machine?

---

### Post by lethalfang on 2009-07-14
> **superprash2003 said:**
> are you talking about a windows or ubuntu machine?

Ubuntu, of course! :biggrin:

---

### Post by superprash2003 on 2009-07-14
you could use the network manager for this..

for reference : [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by lethalfang on 2009-07-14
> **superprash2003 said:**
> you could use the network manager for this..

for reference : [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

Thanks for that. 

Now do you know how to work with TFTP?
I downloaded and compiled linksys-ftfp.bar.bz2. The README file instructs:
```

./linksys-tftp [router]
linksys-tftp> put [firmware image] [password]

```

The question is what do I type in for [router]? 
I'm assuming the [firmware image] is just the micro.bin file I find on DD-WRT, and I should have this .bin file in the same directory that I run tftp.exe. 
Can anyone give me an example of commands?


ifconfig -a yields:

```

eth0      Link encap:Ethernet  HWaddr 00:11:22:33:AA:BB  
          inet addr:192.168.1.2  Bcast:192.168.1.127  Mask:255.255.255.128
          inet6 addr: fe80::213:20ff:fe17:d5be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8599192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5526587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1573188508 (1.5 GB)  TX bytes:1032522517 (1.0 GB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13314 (13.3 KB)  TX bytes:13314 (13.3 KB)

pan0      Link encap:Ethernet  HWaddr 1a:af:ed:64:5b:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

---

