---
title: "Network problems for some or all ??"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Healey on 2008-11-01
HI

I have had a problem with the Intrepid Ibex 8.10 which is unable to connect to the internet via a wired connection and a router. This setup works fine in Hardy Heron BTW

After doing some research it appears that I am NOT alone and this section contains a lot of people looking for answers to this problem

So my question is :-

Its this a problem for all or just some - Surely if it is a bug then it should effect all of us

Just a thought !!

---

### Post by whoop on 2008-11-01
My ibex connects fine through my router. The only thing is allot of people (all?) are unable to setup static ip.

---

### Post by Healey on 2008-11-01
Hi

Thanks for the reply

Perhaps you could explain how you - set it up, in order to connect via a router

Thanks in advance

---

### Post by lugburz on 2008-11-01
I've update from 8.04 to 8.10 and I cannot connect to a wired connection using DHCP, so the problem exists also for not static connection.

---

### Post by trumpcouptimmy on 2008-11-01
I have a problem after doing the update-manager -d. Everything seems to be OK except now I can't obtain an IP from my DSL router. I've tried by wired ethernet, usb, and 2 different usb wireless devices. The wierd thing is that there is no problem with anything when I boot up the Intrepid live cd so the hardware works. It seems like some setting somewhere that prevents getting an IP address by dhcp. It isn't particular to a user-another user on the same machine doesn't work either. I've had 2 posts asking for help and haven't had a single reply. This is probably something simple but I don't have the linux expertise yet. For the first time I see I'm not alone with the problem.

EDIT. This worked for me. I kept looking and tried the following:
sudo ifconfig eth0 192.168.0.14
sudo dhclient eth0

and I'm up. At least I'm on the net. I don't believe it would hurt anyone else who is having a problem to try it. I was so desperate-I was willing to try anything.

---

