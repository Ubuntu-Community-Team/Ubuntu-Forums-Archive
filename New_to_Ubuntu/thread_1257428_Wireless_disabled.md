---
title: "Wireless disabled"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by lewstherin01 on 2009-09-03
My wireless went down earlier today and when i type in sudo lshw -c network it says my network is disabled. I dual boot and it works on vista. Please help!!

---

### Post by mbzn on 2009-09-03
Right click the network icon > Enable Networking & Enable Wireless has to be checked

---

### Post by lewstherin01 on 2009-09-03
The enable wireless bit is gone.

---

### Post by mbzn on 2009-09-03
Does your computer have a switch to turn of the wireless?
If that's all fine post the output of ifconfig.

EDIT: ifconfig would be in the terminal

---

### Post by lewstherin01 on 2009-09-03
The switch for the wireless is on but the light is out when i'm in ubuntu.  I would dude but I'm not on my laptop i'm on another computer.

---

### Post by k33bz on 2009-09-03
> **lewstherin01 said:**
> The switch for the wireless is on but the light is out when i'm in ubuntu.  I would dude but I'm not on my laptop i'm on another computer.

depending on what wireless card you have in your laptop the light will not come on. Can you tell me what wireless card is in your laptop?

---

### Post by mbzn on 2009-09-03
If your laptop is nearby, check that when you type ifconfig it should give you 3 interfaces eth0 is usualy your LAN, eth1 your wireless and lo would be your loopback. check that they're all there

---

### Post by lewstherin01 on 2009-09-03
ralink rt73 I think.

---

### Post by lewstherin01 on 2009-09-03
> **mbzn said:**
> If your laptop is nearby, check that when you type ifconfig it should give you 3 interfaces eth0 is usualy your LAN, eth1 your wireless and lo would be your loopback. check that they're all there
 
Only eth0 and l0

---

### Post by lewstherin01 on 2009-09-03
The computer is an EI system ei3103 if that is any use.

---

### Post by k33bz on 2009-09-03
> **lewstherin01 said:**
> ralink rt73 I think.

try loading up one of these drivers:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

---

### Post by lewstherin01 on 2009-09-03
Tried that mate but no joy.  :(

---

### Post by lewstherin01 on 2009-09-03
Any ideas guys?  :(

---

### Post by Dlobster on 2009-09-03
I am not able to get my wireless card working since I installed ubunto 9.04 on my Dell Inspironyesterday
I am a real newbie to Linux so help must be basic.

I saw a post to " click the network icon > Enable Networking & Enable Wireless has to be checked"
I found the net work icon, enable networking was checked, but ther was no enable wireless option.
Any Ideas?
Dan

---

### Post by Dlobster on 2009-09-03
Ok well I seem to have gotten it going.  No light but it seems to work.
I needed to enter in all info. It does not search for available networks.  Is this normal?

---

### Post by lewstherin01 on 2009-09-04
Bump.  Any solutions guys?

---

### Post by lewstherin01 on 2009-09-04
I reinstalled ubuntu and everything seems to be working now.  Cheers to anyone who helped.  :D

---

