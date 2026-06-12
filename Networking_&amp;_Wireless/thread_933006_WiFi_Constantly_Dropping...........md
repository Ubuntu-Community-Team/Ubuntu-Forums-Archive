---
title: "WiFi Constantly Dropping.........."
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by Nylo on 2008-09-29
I can connect but after about 10 to 30 minutes I loose my wifi connect.  When I open Network manager my password has about six more characters than it should.  I then retype my password and hit ok.  Most of the times I have to click ok about three or four times before it connects again.

Any ideas whats causing this and how to fix it.

---

### Post by frankleeee on 2008-09-29
With the network manager on my laptop I have to do a restart after putting in the info in the manual setting in order for it to work and work every time I turn it on. I can set it to roam and work immediately but under the manual setup I have never gotten a connection just putting the info in then hitting ok.

---

### Post by Nylo on 2008-09-29
> **frankleeee said:**
> With the network manager on my laptop I have to do a restart after putting in the info in the manual setting in order for it to work and work every time I turn it on. I can set it to roam and work immediately but under the manual setup I have never gotten a connection just putting the info in then hitting ok.

Im new to Ubuntu (Linux) so bear with me.  What Im calling Network manager is actually Network settings which I have set to automatic configuration.  Like I said it works but I get dropped between 10 to 30 minutes but restarts with re-entering my password.  Im not even sure how to set to roam.

---

### Post by frankleeee on 2008-09-29
> **Nylo said:**
> Im new to Ubuntu (Linux) so bear with me.  What Im calling Network manager is actually Network settings which I have set to automatic configuration.  Like I said it works but I get dropped between 10 to 30 minutes but restarts with re-entering my password.  Im not even sure how to set to roam.

I think we are talking about the same thing the icons on the top panel that look like two little monitors. you can set it to roam in the area of the password and name, but if you have a regular wifi source connecting with the manual setting is better in my opinion. Roaming, when I turn my computer on asks for a log in to get that working. Try setting your computer in manual with the connect name and password then do a restart this is what works for me, but I have my own connection which is always there with a strong signal. I don't have a loss of wifi problem, due to running off my own router.

---

### Post by Tom--d on 2008-09-29
> **Nylo said:**
> Im new to Ubuntu (Linux) so bear with me.  What Im calling Network manager is actually Network settings which I have set to automatic configuration.  Like I said it works but I get dropped between 10 to 30 minutes but restarts with re-entering my password.  Im not even sure how to set to roam.


What is your wireless card and what driver are you using for it. When connected, right click the Wireless Signal and go to connection information and see where Driver: your_driver 

Post it here, thanks :)

---

### Post by Nylo on 2008-09-29
> **Tom--d said:**
> What is your wireless card and what driver are you using for it. When connected, right click the Wireless Signal and go to connection information and see where Driver: your_driver 

Post it here, thanks :)

On my wireless signal icon Im not getting "connection info."

Card= Netgear WG511U
Driver= e100
Driver version=3.5.23-k-NAPI

*-network DISABLED 
description: Ethernet interface
product: 82801BA/BAM/CA/CAM Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth0
version: 03
serial: 08:00:46:40:ac:61
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
*-network
description: Wireless interface
product: AR5212/AR5213 Multiprotocol MAC/baseband processor
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wifi0
version: 01
serial: 00:0f:b5:34:f7:75
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11a

---

### Post by Nylo on 2008-10-01
> **frankleeee said:**
> I think we are talking about the same thing the icons on the top panel that look like two little monitors. you can set it to roam in the area of the password and name, but if you have a regular wifi source connecting with the manual setting is better in my opinion. Roaming, when I turn my computer on asks for a log in to get that working. Try setting your computer in manual with the connect name and password then do a restart this is what works for me, but I have my own connection which is always there with a strong signal. I don't have a loss of wifi problem, due to running off my own router.

The only thing I can get out of that icon is properties.  When I click configure a window pops up and says, "The interface does not exist."

---

