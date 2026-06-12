---
title: "How can I forward ports in VirtualBox?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by hopelessone on 2010-05-19
Hi,

I just learn't how to port forward my router works good in Deluge Ubuntu 9.10...How can I port forward using VirtualBox? 
When I boot virtualbox Ipconfig in XP gives an internet address of: 10.0.2.15
I'm trying to forward port: 52152

Any light much appreciated...

Thanks...

---

### Post by blazemore on 2010-05-19
You need to set Virtualbox to allow the guest OS to use your physical network hardware, ie. NOT Network Address Translation.

Then the guest OS will have a "real" IP on your local network, and you can forward the port in the usual way.

---

### Post by hopelessone on 2010-05-19
Hi,

Could you please help me with > You need to set Virtualbox to allow the guest OS to use your physical network hardware, ie. NOT Network Address Translation.


How can I do that? (Newbie)

---

### Post by pirateghost on 2010-05-19
> **hopelessone said:**
> Hi,

Could you please help me with 

How can I do that? (Newbie)

go into your virtual machine settings and click on NETWORK, then choose BRIDGED instead of NAT

---

### Post by blazemore on 2010-05-19
On the settings for the Virtual Machine, go to the "Network" section

Where the mode says "Network Address     Translation" (NAT)
change it to "Bridged Networking"

This is IMO the easiest way to do it, although there are ways to forward ports while still using NAT. If you want to do that, see the Virtualbox Documentation [here]("http://www.virtualbox.org/manual/ch06.html#natforward").

---

### Post by hopelessone on 2010-05-19
blazemore & pirateghost THANK YOU BOTH!!!

You know that fixed it...!!!

I'm in Korea and i don't speak the language but all you guys make it possible for me to do anything in Ubuntu...

Many Thanks from the bottom of my heart...!

---

