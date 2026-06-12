---
title: "Internet Connection Problems"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by colsandurz on 2007-03-24
Hi, 

I'm dual booting windows xp pro and Ubuntu 64 bit.  Recently, I booted into windows and did some mainly to do internet browsing.  I then rebooted into ubuntu and now I can't connect to the internet in any way.  However, I can still boot into windows and use the internet fine.  
Any help would be appreciated.

---

### Post by fdrake on 2007-03-24
in the terminal type ifconfig and show us its output

---

### Post by colsandurz on 2007-03-24
sudo: ipconfig: command not found
devin@dkelly:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:4F:9C:35  
          inet6 addr: fe80::216:17ff:fe4f:9c35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2178 (2.1 KiB)
          Interrupt:225 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Note: I am using a wired  connection, not wireless

---

### Post by colsandurz on 2007-03-24
Also, I can successfully ping my localhost and 127.0.0.1 However I cannot successfully other computers on my network

---

### Post by fdrake on 2007-03-24
from what i see the interface isn't been properly activated.you don't have an ip address  associated.try this:
go to networking and un-check the wired connection
type:
sudo ifconfig eth0 down
sudo ifconfig eth0 up
now reconfigure networking  check the wired connection.

---

### Post by fdrake on 2007-03-24
ah.. btw which ubuntu version are you using?

---

### Post by colsandurz on 2007-03-24
I'm using 6.11.

I ran those commands and now instead of realizing that I can't load a webpage and getting a 404 type error it just endlessly tries to load the page.

---

### Post by fdrake on 2007-03-24
did you try to unplug and plug your Ethernet cable before activating the last networking change. what's the out put of route -n

---

### Post by colsandurz on 2007-03-24
I tried unplugging the ethernet cable with no luck...

Here's my routing table
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
130.215.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         130.215.168.1   0.0.0.0         UG    0      0        0 eth0

```

---

### Post by fdrake on 2007-03-25
we need more info about the type of your Internet connection.
- do you use an user name and  pass to connect to the Internet or is a straight cable connection.

---

### Post by colsandurz on 2007-03-25
No I don't need a user or pass.  I'm at a univeristy and my computer connects to a certain port and is verified by it's MAC address.

---

### Post by fdrake on 2007-03-25
can you connect to your gateway using firefox? [http://130.215.168.1](http://130.215.168.1)

i found this thread looks similar to your case. you said that your mac address is verified.
[http://ubuntuforums.org/showthread.php?t=392422&highlight=internet+university](http://ubuntuforums.org/showthread.php?t=392422&highlight=internet+university)

it's 1am and tomorrow(i mean today) i have to wake up early . hope you'll find a solution soon. just don't let this thread to die so other people can help you with the prob. 

bye and goodnight.  ;)

---

### Post by colsandurz on 2007-03-25
I meant that the school verifies my computer by it's MAC address.

Thanks the help.

---

### Post by colsandurz on 2007-03-25
hmmm, interestingly I do get an error message when trying to connect to my default gateway. Unlike anything else I try to access which endlessly tries to refresh.

---

### Post by Alex&amp;Linux on 2007-04-30
Hey, Im Alex

Just finished adding Ubuntu 6 to my HP vista machine, I am very excited to learn more about this operating system in particular, and the community that helps it grow!

Upon booting into this for the first time, my internet connection was indeed active, and my Windows installation damaged because I had forced a partition of my disk to make way for Ubuntu.
After booting into windows recovery to fix the error, and establishing an internet connection using Vista, I noticed also that there was no connectivity in Ubuntu!

I have tried all that had been recommended thus far with no success, no IPv4 address showing!
Using another computer to log into router shows that its picking up my ethernet adapter's (Nvidia  nforce) MAC and delivering its proper private IP, which I tried to hardcode with more failure!

Using the network utility, when selecting the ethernet interface (instead of the loopback) there is no IPv4.

One thing that I noticed is that when booting into Vista, I was given a pop-up message saying "drivers have been successfully reinstalled" possibly referring to my network adapter?
It was after this point that Ubuntu lost its connectivity!

---

