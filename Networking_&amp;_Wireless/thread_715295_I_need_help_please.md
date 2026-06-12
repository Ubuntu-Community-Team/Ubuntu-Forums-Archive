---
title: "I need help please"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by mdc4115 on 2008-03-04
ok i have a gateway m-6752 laptop with the marvell topdog wifi card. i have tried and tried to get the wireless to work and it just won't work. can someone help me get it work. i've tried ndiswrapper but doesn't seem to work. i finally got it so i can read and write to my windows vista partition maybe that would help in some way with getting it to work. so could someone please help me.

---

### Post by mdc4115 on 2008-03-05
bump...

i guess no one wants to help me. i wish i had some help with this.

---

### Post by chili555 on 2008-03-05
This:> marvell topdog wifi cardis unknown to most of us. Please open up a terminal and issue the following commands:```
sudo lshw -c network
iwconfig
```Jot down the details relevant to wireless and summarize them here. We'll have a much better idea how to proceed. Thanks.

---

### Post by schmildo on 2008-03-05
I'm no guru at this but try posting the results of a few commands so others might be able to assist;

ifconfig -a

iwconfig

lshw

lspci


etc...

People might not be responding yet because they may be unfamiliar with your particular type of network card. Is it a PCMCIA card?

I saw someone link to a compatability list for WiFi cards here recently but I can't find it now.

Good luck!

---

### Post by mdc4115 on 2008-03-06
lshw
```
 *-network UNCLAIMED
                description: Ethernet controller
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0

```

lspci
```

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)

```

---

### Post by chili555 on 2008-03-06
Oh, boy!!! Our very favorite:> Unknown device 2a08

Please let us see the result of the following terminal commands:```
ndiswrapper -l
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by mdc4115 on 2008-03-06
ndiswrapper -l
```

netmw14x : driver installed

```


iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

sudo iwlist wlan0 scan
```

wlan0     Interface doesn't support scanning.

```

---

### Post by mdc4115 on 2008-03-09
ok and...

---

### Post by JakobMonrad on 2008-03-10
Well, I'm a complete n00b at Ubuntu and fighting with my own connection problems, but I've noticed that your 

```
wlan0     Interface doesn't support scanning.
```

so either you don't have a wlan0 enabled or it is enabled as eth1.
Try running a sudo iwlist rth1 scan instead, if that is your wireless, you should get a list of available network i the area

---

### Post by mdc4115 on 2008-03-11
sudo iwlist rth1 scan
```
rth2     Interface doesn't support scanning.
```

---

### Post by mdc4115 on 2008-03-15
ok i think i know why its not working. the chipset is new and a driver hasn't been developed for it yet.

---

### Post by mdc4115 on 2008-03-27
got it working yay!

---

### Post by bnbliss on 2008-04-01
so what did you do to get it working.  I have the same laptop and would like to get mine running ubuntu rather than Vista.

Thanks

K

---

