---
title: "first time ubuntu user, can't connect to internet"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by gc1980 on 2011-03-22
Hi,

I've been wanting to have a look at linux for some time now, and have finally been given the opportunity to do so now that there is a spare computer in the house for me to play with.

The computer is an Acer aspire 5100 laptop connected to a Dlink DSL-G604T. It was running Windows XP but was really starting to slow down and have a lot of problems booting up, and with the CD/DVD drive not working anymore I decided to just wipe windows off and install ubuntu 10.10 from USB. This part all went really well, had ubuntu up and running pretty well straight away, internet was working fine, I set up evolution and did a little bit of browsing on firefox without any problems. What really impressed me was that it didn't require any fiddling at all to network with my main desktop running XP and I was able to transfer a couple of files from it to the laptop without any problems at all.

Ubuntu had updates ready to download and install but I didn't do it last night as it was getting a little late, so I fired the laptop up this morning, downloaded the updates, rebooted the computer and now for some reason I don't have internet access. The laptop can still connect to the wireless network, I can still get access to shared files on my windows computers, but I can't get access to the internet.

Anyone have any ideas?

Cheers

---

### Post by ashmew2 on 2011-03-22
Hi, 
Welcome to the Forums , 

could you post the output of 

```
ifconfig
```

Run that in a terminal (Applications > Accessories > Terminal)

---

### Post by gc1980 on 2011-03-22
Hi ashmew2,

thanks for the reply.

here it is:

```
tara@tara-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:5d:3f:a0
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
wlan0     Link encap:Ethernet  HWaddr 00:16:cf:a5:68:61  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:cfff:fea5:6861/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:342801 (342.8 KB)  TX bytes:180393 (180.3 KB)

```

---

### Post by TechWiz2100 on 2011-03-23
try ```
sudo ifconfig wlan0 down 
sudo ifconfig wlan0 up
```
if that does not work try ```
sudo /etc/init.d/networking restart 
```

---

### Post by gc1980 on 2011-03-23
> **TechWiz2100 said:**
> try ```
sudo ifconfig wlan0 down 
sudo ifconfig wlan0 up
```if that does not work try ```
sudo /etc/init.d/networking restart 
```

tried it and nothing has happened.

---

### Post by ashmew2 on 2011-03-23
Hey, 
Try this first , if doesnt work , read the part after *--------*//
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

followed by a 
```
sudo /etc/init.d/networking restart
```

Is it working ? 
If not , try rebooting your laptop

*-------------*//

If not , we'll have to reconfigure.
```

sudo pppoeconf
```

Give this a try , will reconfigure your connection. As far as im understanding , u need to configure the eth0.
It will ask u for a few things.
Did u use a static IP/DNS servers in Windows , on the same laptop ?

If yes , u can do so with pppoeconf.

Give it a try.!

---

### Post by Dutch70 on 2011-03-23
Go to System >> Administration>> Network and check your settings in there. I'm not logged-in to Ubuntu right now, So that's about all I can tell you at the moment. You should be able to find the settings in there that will fix it though.

Edit: 
> wlan0     Link encap:Ethernet  HWaddr 00:16:cf:a5:68:61  
          [COLOR="Red"]inet addr:10.1.1.3[/COLOR]  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:cfff:fea5:6861/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:342801 (342.8 KB)  TX bytes:180393 (180.3 KB)

The part in red is what I believe you need to be checking on. I'm just not knowledgeable enough to explain or advise after that.

---

### Post by d3v1150m471c on 2011-03-23
does it work with a direct ethernet connection? secondly, what did you update? does system >> hardware drivers tell you anything?

---

### Post by jtarin on 2011-03-23
Did you upgrade the kernel? Boot an earlier earlier version and check the connection. 
Can you ping your router?

---

### Post by gc1980 on 2011-03-24
> **ashmew2 said:**
> Hey, 
Try this first , if doesnt work , read the part after *--------*//
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up
```followed by a 
```
sudo /etc/init.d/networking restart
```Is it working ? 
If not , try rebooting your laptop

*-------------*//

If not , we'll have to reconfigure.
```

sudo pppoeconf
```Give this a try , will reconfigure your connection. As far as im understanding , u need to configure the eth0.
It will ask u for a few things.
Did u use a static IP/DNS servers in Windows , on the same laptop ?

If yes , u can do so with pppoeconf.

Give it a try.!

Hi,

I tried running 

```

sudo pppoeconf
```and it told me that the access concentrator of my provider did not respond. 

A quick search on google led me straight to one of the old threads on this forum that was dealing with a similar problem involving my dlink DSL-G604T router.

[http://ubuntuforums.org/showthread.php?p=423242#post423242](http://ubuntuforums.org/showthread.php?p=423242#post423242)

Post 4, option 1 has seen me get access to the web and email again(haven't tried anything else yet).

Thanks all for the help, most appreciated:D

---

### Post by gc1980 on 2011-03-24
turned out to be too good to be true, computer was recently restarted and now I have firefox working fine, but can't access email.

This whole thing is doing my head in and I've barely even had a chance to even use ubuntu:(

Anyone have any suggestions?

---

