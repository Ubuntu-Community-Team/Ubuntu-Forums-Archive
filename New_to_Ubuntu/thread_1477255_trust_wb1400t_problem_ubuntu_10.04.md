---
title: "trust wb1400t problem ubuntu 10.04"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Ruben_99 on 2010-05-08
Hi, I'm new in ubuntu, and everything works perfect except two of my devices, my webcam, and my usb wifi adapter.

in system->preferences->multimedia system selector and in the video tab, using the v4l2 codec I can see myself, but, with a very poor quality, I mean, everything very dark, and I see myself yellow.

anyone knows a solution?

and with my usb wifi adapter I have another kind of problem. It connects perfectly, but the speed is very slow, in windows xp was much faster. The usb wifi adapter is an ecom EW125TGUSB

Thanks in advance, and remember, I'm a complete newbie in ubuntu, any help is useful and grateful. :)

---

### Post by cariboo on 2010-05-08
I'm not sure about your webcam problem, but could you open a terminal and type:

```
sudo lshw -C network > network.txt
```

the above command will create a file called network.txt, that you can copy to your Windows partition, you can then paste the contents in your next post. The file will contain all the details of your networking device.

---

### Post by Ruben_99 on 2010-05-09
well... but I don't have a windows partition, I only have ubuntu, anyway I will try, thanks

---

### Post by Ruben_99 on 2010-05-09
the command that you tell me to execute, gives me this.

*-network
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 12
       serial: 00:0e:a6:51:83:de
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:18 memory:ed800000-ed803fff ioport:d800(size=256)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:4f:62:1e:28:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.176 multicast=yes wireless=IEEE 802.11bg

---

### Post by no2498 on 2010-05-09
cheese webcam booth should be loaded look in sound&video
you can change settings in it

hope it works for you

---

### Post by Ruben_99 on 2010-05-10
I have installed cheese,  but I can't  get a good quality, it's true that in windows the quality was not very good, but a little bit more yes, any other ideas?

---

### Post by Ruben_99 on 2010-05-10
well I made some tests in windows again, and the problem with the lack of  light persists in windows and in linux, in windows I see the "real" colours, but in ubuntu I see very "strong" colors, the green es too green, the skin colour is very strong. Anyone knows how to configure that?

---

