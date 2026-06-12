---
title: "Problems connecting to internet"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by im420soldier on 2010-08-24
ok. new to linux. installed ubuntu 10.04 LTS Desktop. have an intergrated NIC and a PCI NIC. trying to connect to integrated NIC from comcast cable modem. running command line ifconfig shows both cards and shows eth1 (intergrated card) as haveing an active connection with an IPv6 address but no IPv4 address. when i try to connect to auto eth1 with network-manager it will not connect. any ideas?

---

### Post by LiquidMeson on 2010-08-24
If your connecting directly to the modem it might require a little setup.

Assuming internet doesn't work already, try going to 192.168.0.1 or 192.168.1.1 in the web browser. Or if there's another number located on the modem/manual. Doesn't sound like a Ubuntu problem tho, the cable company should be able to assist as well? I don't have Comcast but rather att.

---

### Post by im420soldier on 2010-08-24
Thanks for replying... 
 
Dont think i can access the modem through browser... tryed the address above and checked on the modem... nothing...
 
from what i can tell its just not acquireing an inet4 address...  
 
still lost....

---

### Post by LiquidMeson on 2010-08-24
anyway to test it on another pc?

---

### Post by im420soldier on 2010-08-24
yeah... i am connected to it right now on my win7 PC....
 
was on the phone with comcast early... the guy said he could see when i disconnected the ethernet cable from the back of the comp in question... he couldn't give anymore insight as to what was wrong other than it wasn't my connection from them...

---

### Post by LiquidMeson on 2010-08-24
a router might be an easy fix.

---

### Post by im420soldier on 2010-08-24
yeah... was hoping not to have to go that route....

---

### Post by LiquidMeson on 2010-08-24
see if it work's when you're using the live cd on either pc.

---

### Post by dtoronto on 2010-08-24
have you looked at this thread
[http://ubuntuforums.org/showthread.php?t=1560473]("http://ubuntuforums.org/showthread.php?t=1560473")

---

### Post by im420soldier on 2010-08-24
I think either of those solutions would be assuming that i have some sort of IPv4 connection... which i dont...   
 
if i am understanding this correctly, which i may not be, the problem is my NIC is only acquiring an Inet6 address but not an Inet4 address as shown with ifconfig command line....

---

### Post by im420soldier on 2010-08-24
will try running the live cd on my win7 comp...

---

### Post by dtoronto on 2010-08-24
right, I believe this thread is talking about removing the ipv6 to default to an ipv4 connection

[http://ubuntuforums.org/showthread.php?t=1560473]("http://ubuntuforums.org/showthread.php?t=1560473")

---

### Post by im420soldier on 2010-08-24
well i just booted from the live cd on my win7 PC and it recognized the network, assigned ip address and was straight on the internet...  now i just need the server tower to do that...

---

### Post by LiquidMeson on 2010-08-25
so if the live cd didn't work on the tower, linux might not like the nic. what does this give u?

terminal:
dmesg | grep -i "eth"

---

### Post by im420soldier on 2010-08-25
actually i am on the server tower now running the live cd... so it works fine off the live cd obviously... recognized it right away just like on the win7 tower...

dont know what the problem could be???

---

### Post by LiquidMeson on 2010-08-25
so something is wrong with your setting (eject the cd), try updating first.

---

### Post by im420soldier on 2010-08-25
fixed the problem by reinstalling from the live cd desktop... dont know exactly what happened with the first install, but i did a straight install without going into live cd that time....

---

### Post by LiquidMeson on 2010-08-25
Cool, I think there's a way to mark the thread solved or something.. not sure.

---

### Post by im420soldier on 2010-08-25
got it...   thanks for the help guys...

---

