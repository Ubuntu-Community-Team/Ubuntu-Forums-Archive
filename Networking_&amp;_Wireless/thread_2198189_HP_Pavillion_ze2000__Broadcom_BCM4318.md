---
title: "HP Pavillion ze2000 / Broadcom BCM4318"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by kingfishracin on 2014-01-07
I am new to Ubuntu and just installed Lubuntu version 13.10 on an old HP Pavillion ze2000. I can connect to the internet wired but I have no wireless. I have the Broadcom BCM 4318 card which I have discovered is a common problem. I am not sure on where to start. Any help would be greatly appreicated.

---

### Post by Bucky Ball on 2014-01-07
Welcome. You can start by opening a terminal and giving us the output of this command:
```

sudo lshw -C network
```

Also check additional drivers and see if there's anything in there containing 'b43'.

You can also try opening a terminal and:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

PS: You need to be online with a cable for this last command to work. ;)

---

### Post by kingfishracin on 2014-01-07
[SIZE=3]**Thanks Bucky, here are the results from the first command.**[/SIZE]

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:d0:85:89
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=8139too  driverversion=0.9.28 duplex=full ip=192.168.1.109 latency=64 link=yes  maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:d0208000-d02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:d0204000-d0205fff

**[SIZE=3]Here is what I got from the second command.[/SIZE]**
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-installer

---

### Post by Bucky Ball on 2014-01-07
Were you online with the cable when you input the second command? Have you looked in Additional Drivers (plug in the cable and do an update then look)?

---

### Post by kingfishracin on 2014-01-07
I was online with it for the second command. (using it now). Im Not sure how to check for the drivers.

---

### Post by Bucky Ball on 2014-01-07
That is strange. Can you open Software Centre (or Synaptics) and do a search for 'firmware-b43-installer'.

Not sure where Additional Drivers is on Unity but you can do a search for it.

---

### Post by kingfishracin on 2014-01-07
Software Centre and Synaptics return 0 results for firmware b43 installer.

---

### Post by Bucky Ball on 2014-01-07
Just wondering if you have all repositories active. Can you open a terminal and do an update while online with the cable?

```
sudo apt-get update
```

Post any errors you get.

---

### Post by kingfishracin on 2014-01-07
After the update I was able to run the b43 installer. It seemed to go well with no errors. I have to go to work right now so I will see where I am at when I get home. I will let you know. Thanks for your help.

---

### Post by Bucky Ball on 2014-01-07
Excellent. As I say, you probably need firmware-b43-installer and b43-fwcutter. Install both and reboot. ;)

---

### Post by kingfishracin on 2014-01-08
Just got home and started the old HP up and BINGO!! I have wireless connection. Thanks for your help Bucky.

---

### Post by Bucky Ball on 2014-01-08
All good and happy to hear it and no problem ;)

Just out of curiousity, could you post the output of this command again and we'll see what it is now using:

```
sudo lshw -C network
```

Thanks.

PS: You can mark the thread as solved to help others by following the instructions in my thread.

---

### Post by kingfishracin on 2014-01-10
Sorry Bucky I just got back on here today. I marked this as solved and here is the command output.

```
 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:d0:85:89
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:d0208000-d02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:d0204000-d0205fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:15:51:e6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.11.0-12-generic firmware=666.2 ip=192.168.1.107 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by frodoswaggins on 2014-07-05
> **Bucky Ball said:**
> 
...

Hey there, I have the same problem as the other guy. Im quoting you because you solved the other problem, so I hope you can help me too. I hope thats fine.

Anyway I tried the things you said in this thread and it didnt work for me, so lets do it from the beginning. I will post what you asked the other guy for.

Ok so this is strange, I cant write my password in the terminal so I cant do what you asked for. I cant write numbers in the terminal, not even if I put "num lk" and try to write it with other keys.

Btw my laptop is a HP Pavilion ze2000, I dont know more about the wireless card, how can I see which model I have?

Thanks in advance.

---

### Post by Bucky Ball on 2014-07-05
Welcome frodoswaggins. 

Please start a new thread with a descriptive title for any further support requests rather than reawakening this old, dead one. Thanks.

---

