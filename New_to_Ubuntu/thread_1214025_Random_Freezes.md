---
title: "Random Freezes"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by mvalviar on 2009-07-15
I'm getting random lock ups again. Mouse and keyboard are not responding and can't RSEIUB. I suspect wireless because I've been in and out of it but my machine only acts up when its on wireless.```
*-network:0
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wmaster0
                version: 01
                serial: 00:14:78:ec:09:8c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=192.168.11.2 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

Plus I've been getting this message every now and then.[IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Screenshot-1.png[/IMG]

Is the a fix or a work around this. Please help me out. This is really giving me a hard time.

---

### Post by mvalviar on 2009-07-16
^^ up ^^

---

### Post by Het Irv on 2009-07-16
See if this helps you any: [https://answers.launchpad.net/ubuntu/+question/56736](https://answers.launchpad.net/ubuntu/+question/56736)

---

### Post by mvalviar on 2009-08-22
I've decided to dig up this thread because I just confirmed that it is the wireless adapter that is causing my computer to crash. 

I've booted on the live CD and the moment I tried to connect to the wireless net the system freezes.

Can anyone suggest a workaround? Would it be better if I dl the drivers from atheros and use them?

---

### Post by mvalviar on 2009-09-10
I solved my own problem. I checked under hardware drivers and there is a proprietary driver for my adapter. Everything is ok now.

---

