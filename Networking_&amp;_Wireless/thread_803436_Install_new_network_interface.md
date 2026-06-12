---
title: "Install new network interface"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by slacker9876 on 2008-05-22
Hello all, I had an installation that failed (MB died) and so I took the HDD and put it in a new computer. Everything boots up fine and the interfaces indicate they loaded, however, there is no eth0 adapter in the system only a lo interface. Since the adapters are different, I would assume the driver is not loaded and I need to load it.

How do I go about configuring a brand new card in the system? The adapter in question is a 3Com 905-TX.

TIA

---

### Post by chili555 on 2008-05-22
I suggest the following steps. In a terminal:```
sudo modprobe 3c59x
sudo modprobe mii
sudo lshw -C network
```Does your 3com now appear with a driver=3c59x? Is there a logical name=eth0? If so, let's do:```
sudo ifconfig eth0 up
sudo dhclient eth0
```Did you connect?

---

### Post by slacker9876 on 2008-05-22
It appears to have worked for the first 3 steps but not that last two. Also from the output I had the adpater wrong, it shows it is a 3c900B-TPO, I am sure that is related. (sorry)

---

### Post by slacker9876 on 2008-05-22
OK so I grabbed a 3c905 from the basement ... same result. there is a logical adapter now but I cannot bring it up.

SIOCSIFADDR: No such device
eth0: error while getting interface flags: no such device
Bind socket to interface: no such device
Failed to bring up eth0

---

### Post by pseudo-random on 2008-05-22
Please post output of```
ifconfig
```
It's probably got a different name. That's why you're getting errors.

---

### Post by chili555 on 2008-05-22
I assume the logical name is *eth0*? Please:```
sudo gedit /etc/network/interfaces
```Make sure the file contains this:```
auto eth0
iface eth0 inet dhcp
```Amend and save as necessary. Sustitute the interface you found with *sudo lshw -C network* if it's not eth0. Then restart networking:```
sudo /etc/init.d/networking restart
```Did you connect?

---

### Post by slacker9876 on 2008-05-22
the logical adapter appears just as you stated in /etc/network/interfaces but I still get the same error if I try to bring it up manually. I also have since transported the server to another site, and the port is hot. should I try another adapter? It is connected with a 6' patch cord.

I think I may try another adapter even though I do not have one here. Any recommendations on those easily purchased retail.

---

### Post by slacker9876 on 2008-05-22
Argh!!! I know I must be doing somehting wrong. I just install and RTL8169 and performed 'modprobe 8139too' and the remaining steps but have the same result. I did note in the output this time that a liket that stated "*-DISBALED - network" is there a config file I need to edit?

---

### Post by chili555 on 2008-05-22
I feel like I am trying and failing to hit a moving target. Please do not buy another adapter. Are you sure 8139too goes with this adapter? I think r8169 might be the module you want. Please try:```
sudo rmmod 8139too
sudo modprobe r8169
```Now, does *sudo lshw -C network* show your device? Disabled or not? Driver? Logical name?

---

### Post by ljavierrivera on 2011-11-08
I want to say that I was looking for a solution to my problem using a VMware Linux Guest image. "installing" the network card is a sinch using VMware workstations GUI (on Windoze), but getting the Linux distro to recognize it was another issue. Chili555's solution is spot on! I know have a second virtual network card

:popcorn:

Thank You,

---

