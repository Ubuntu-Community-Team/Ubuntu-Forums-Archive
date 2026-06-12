---
title: "I'm still in troble in wireless"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by kjman83 on 2008-04-03
Hi
I use 802.11g.
I installed ndiswrapper. 
I can see the wireless when I click Manual configuration.
What I want to see is some networks.

When I used vista at the time there are 4 or 5 networks here but nothing now,

Do you think what is problem?

now I can see this screen (below)

wired network
            wireless network
------------------------------------
connect to other wireless network...
Create New wireless network...
------------------------------------
connect to 802.1x protect wired network...
Manual configuration


in ubuntu 8.04     
kjman83

---

### Post by mr.loco on 2008-04-03
You just have to type in the name (SSID) of the network you want to join.

If you want a list of those do

```
iwlist <interface name> scan
```

---

### Post by kjman83 on 2008-04-03
> **mr.loco said:**
> You just have to type in the name (SSID) of the network you want to join.

If you want a list of those do

```
iwlist <interface name> scan
```

Sorry what is exactly interface?
for example..
WAP? this things? or

---

### Post by mr.loco on 2008-04-03
The interface name is the name that the system gives to you network card.

It is probably wlan0

---

### Post by kjman83 on 2008-04-03
really thank you for your reply.
I did 

kjman83@guinness:~$ iwlist wlan0 scan
wlan0     No scan results

but not so good isn't it?

---

### Post by nathansoz on 2008-04-03
Your wireless is set to roaming mode right?

---

### Post by kjman83 on 2008-04-04
Yes exactly,
But there is nothing and  usually the blue light that means turn it on was on before, when wireless was on. 
Now I can't turn it on.

:(

---

### Post by nathansoz on 2008-04-04
Try unloading ndiswrapper, unistalling the driver, and then reinstalling the driver.

```
modprobe -r ndiswrapper

ndiswrapper -r <name of driver>

ndiswrapper -i <path to inf file>

ndiswrapper -m

ndiswrapper -ma

ndiswrapper -mi

modprobe ndiswrapper
```

---

### Post by mr.loco on 2008-04-05
What's your wireless card?

---

### Post by kjman83 on 2008-04-07
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
my laptop is hp 6515b

It's my card..
The important thing is that I can't turn on the wireless lan.
Because The wireless switch is a kind of touchpad switch(useless) not analogtic switch(I prefer analog). The switch is not working in ubuntu. It did work well in Vista. 

I  really want to turn on my wireless.
I really want to see the blue light.

---

