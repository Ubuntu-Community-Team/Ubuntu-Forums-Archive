---
title: "problem with wireless"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by mayta on 2010-07-09
Hi,

I have a problem with my wireless connection.
I live in China and i have a router that doesn't allow me to change settings.
Basically i cannot save my adsl (provider) user name and password in the router settings (i mean when i go to 192.168.1.1). 
My problem is: where can I write that user name and password when i want to use wireless? 

In Window I used to connect manually (like dial-up) to the adsl. 
And if i wanted to use the wireless, i first connected manually to adsl (even without cable) and then to the wirless. The technician who install my Internet told me to do so and it always worked. 

What can i do in ubuntu?

my modem/router is ZTE zxv10 h608b


thank you!

---

### Post by cariboo on 2010-07-09
Can you not enter your user name and password when clicking on the DSL tab when you go to Network-Manager->Edit->DSL?

---

### Post by mayta on 2010-07-09
> **cariboo907 said:**
> Can you not enter your user name and password when clicking on the DSL tab when you go to Network-Manager->Edit->DSL?
Thanks.

Yes, i can and i did it already. 
My problem is when i want to use it wireless.

---

### Post by mayta on 2010-07-10
Maybe i didn't explain well my problem. :(

In the router settings i cannot save my provider username - password. I heard that chinatelecom block the modem-router settings so that users cannot mess with them.

When i want to connect any wireless devices (mobile phone, other computers) I cannot. Because usually the devices only let you enter the WPA etc. password, and not the internet provider's and WPA. 

As i said before, in Windows i can connect to my dsl AND to the wireless. Both at the same time, with or without cable.

But in ubuntu, if i don't plug in the cable, i cannot select my DSL (where i saved my internet provider username and password) as it appears in light-grey and is not active.

---

### Post by anewguy on 2010-07-11
If you are saying you want to have a hard-wired internet connection and a wireless internet connection at the same time, I don't think that's possible with Ubuntu.

---

### Post by mayta on 2010-07-11
> **anewguy said:**
> If you are saying you want to have a hard-wired internet connection and a wireless internet connection at the same time, I don't think that's possible with Ubuntu.

Actually, I just want to use my **wireless**.
I said i connect both in windows, because i, apparently, had no other choice.

---

### Post by bumanie on 2010-07-11
You you post the output of > sudo lshw -C network and also > rfkill listAre you doing this on a laptop or desktop? If a laptop, maybe the wireless button is off. May be [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") will help.

---

### Post by mayta on 2010-07-12
> **bumanie said:**
> You you post the output of  and also Are you doing this on a laptop or desktop? If a laptop, maybe the wireless button is off. May be [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") will help.
I am using a laptop and the wireless button is ON. I can connect to the wireless but then i get "server not found". That's because i can't (or couldn't find how) change  the router settings.

This is the output:

PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:82:f5:19
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:3000(size=256) memory:b0106000-b01060ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:61:94:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:22 memory:b0107000-b0107fff


"rfkill list" doesn't give me any output.

---

### Post by mayta on 2010-07-22
nobody can help me? :(

---

