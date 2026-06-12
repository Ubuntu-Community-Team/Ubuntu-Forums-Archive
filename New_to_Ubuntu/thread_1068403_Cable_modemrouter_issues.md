---
title: "Cable modem/router issues"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Lopezadl2ian on 2009-02-12
Hello to all,

I am very new to the Linux OS so please have patients while I am at the bottom of the learning curve. I just switched from Windows and I am having trouble getting the  Ubuntu 8.10 (64-bit) OS connected to the internet. My current configuration consist of a Cable modem I believe it is a Motorola supplied by Time Warner Cable and that feeds to a router in which another data cable feeds of a Netgear router and connects to my computer. I read online that the cable modem should configure it self and I would not have to configure anything. I clicked on the Network browser applet. and I don't see anything connection. I am not sure what to do at this point. I have search online with a computer at work to and tried running some commands in terminal mode but still I have no Ethernet detection. I am wondering if I have a driver issue or maybe I am doing something completely wrong. Any help would be appreciated. Thanks.

---

### Post by cerealtx on 2009-02-12
most cards will work out the box, open terminal and get some info for me
```
ifconfig
```
and post what ya get

---

### Post by jrusso2 on 2009-02-12
While your at it run lspci unless you have usb ethernet or wireless?

---

### Post by cerealtx on 2009-02-12
> **jrusso2 said:**
> While your at it run lspci unless you have usb ethernet or wireless?

he said cable from his netgear to comp so should be ethernet :P

---

### Post by Lopezadl2ian on 2009-02-12
> **cerealtx said:**
> most cards will work out the box, open terminal and get some info for me
```
ifconfig
```
and post what ya get

Will do. I dont get of work until around 10:30pm so i wont be able to provide that information until around 11:30pm. Thanks!

---

### Post by Lopezadl2ian on 2009-02-13
> **cerealtx said:**
> most cards will work out the box, open terminal and get some info for me
```
ifconfig
```
and post what ya get

This is what I got as an output when I typed the command ifconfig:



ubuntu@ubuntu:~$ ifconfig
lo         Link encap:Local Loopback
           inet addr:127.0.0.1 Mask: 255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:536 errors:0 dropped:0 overruns:0 frame:0
           TX packets:536 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:35404 (35.3KB) TX bytes:35304 (35.3 KB)

---

### Post by hellion0 on 2009-02-13
Post what happens when you issue
```
sudo ifconfig eth0 up
```
to the Terminal. Also, issue
```
lspci
``` to the Terminal if ifconfig doesn't work, and post what you get back from it as well.

---

### Post by Lopezadl2ian on 2009-02-13
> **hellion0 said:**
> Post what happens when you issue
```
sudo ifconfig eth0 up
```
to the Terminal. Also, issue
```
lspci
``` to the Terminal if ifconfig doesn't work, and post what you get back from it as well.

When i type the command [COLOR="Blue"]sudo ifconfig eth0 up[/COLOR] I get the follwing output:

eth0: ERROR while getting interface flags: No such device


I ran the other comman lspci and i get a very very long output. I am using a laptop with windows on it so its very difficult for me to copy and paste. I tried pasting to Microsoft Word and I get chicken scratch. Is there an specific data you need? I can type it in the message. Thanks!

---

### Post by hellion0 on 2009-02-13
The most relevant bit would start with "Network controller", "Ethernet controller", or anything else sounding network-related.

---

### Post by Captain_tux on 2009-02-13
Could it possibly be a Layer 1 problem...? What you should have is a coax cable connected to the modem that Time Warner provided, then a Cat-5 cable (the connector looks like a giant telephone connector) from the modem to your router, and then another Cat-5 from your router to your PC or laptop. Make sure all those connections are correct (the correct cable to the correct slots, etc.). At the very least, you should have the activity lights blinking from the router and the modem. Check to see if the modem came with a diagram depicting a typical home network connection.

Once all the connections are properly made, as others have mentioned, Ubuntu should automagically recognize your network card and you should be good to go.

---

### Post by Lopezadl2ian on 2009-02-13
I checked the configuration from phone-line to the cable modem, from the cable modem to the Netgear router, and then from the router to my computer. All connections are perfect. I even went ahead and rest both the modem and the router to the manufacturing settings with the rest button. : /

---

### Post by Lopezadl2ian on 2009-02-13
Just wanted to mention that I am running off the CD, does that make a difference? The reason why I am running off the cd is because I am trying to setup a raid0 configuration with my HDD and the Ubuntu distro does not have the supportive drivers needed to setup this array. I need to get online so I can download a raid driver from synaptics package manager.

---

### Post by Lopezadl2ian on 2009-02-13
> **hellion0 said:**
> The most relevant bit would start with "Network controller", "Ethernet controller", or anything else sounding network-related.

I dont see anything network related : /

---

### Post by Lopezadl2ian on 2009-02-14
I was referencing another website online and it told me to type the following command: [COLOR="Blue"]dmesg | grep eth[/COLOR]
After typing that command I got the following output

First line: [COLOR="Red"][    5.002180] Driver 'sd' needs updating - please use bus_type methods[/COLOR]

Second line: [COLOR="Red"][    6.737344] Driver 'sr' needs updating - please use bus_type methods[/COLOR]

What does it mean by driver 'sd' and driver 'sr' as well as bus_type methods? Thanks.

---

