---
title: "usb ethernet connection"
date: 2021-12-21
forum: Networking &amp; Wireless
---

### Post by nicolaskarges on 2021-12-21
Hi I'm new to Linux. I have ubuntu 20.04.03

After booting the pc I'm always stuck with attempts to connect to a usb-ethernet device which doesn't exist (message : connection failure).
It turns out that the usb-ethernet connection is active when I check in the network settings. If I turn it down I get rid of the messages, but the problem will reappear at the next boot.
It doesn't prevent the pc to connect through wifi or regular ethernet.

Any idea ?

Thank you so much for your help

---

### Post by TheFu on 2021-12-21
Did anyone put the adapter into a network config file?  Until that file is modified to remove the device, the messages will keep happening.

Can you be more specific about the version of ubuntu 20.04.03? Is it a server or a desktop install?  Which DE?  Did you manually screw around with network settings? If so, which tool was used?  There are probably 5 different ways to do this.

6 questions asked.

---

### Post by nicolaskarges on 2021-12-21
It used to be my wife's laptop (windows) but since it is mine and I installed ubuntu nobody put any adapter. 
It is a desktop install.

nicolas@Nico:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal

The problem was there from the beginning, and I didn't change the network settings I don't think so. I only tried to understand with "ip a" commands for example.

---

### Post by nicolaskarges on 2022-02-13
Hi it's me again. So I struggled with that and found no solution. I eventually reinstalled ubuntu from scratch  to make sure it wasn't because of one of my initial settings, but the problem is still there. Any idea ?

---

### Post by morrownr on 2022-02-14
Are you talking about something like this?

amazon.com/dp/B00AQM8586

We really need more details. How does internet access come to your computer? Ethernet cable?

---

