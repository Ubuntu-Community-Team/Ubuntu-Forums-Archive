---
title: "Configure wireless on Raspberry Pi with Ubuntu Server"
date: 2019-12-25
forum: Networking &amp; Wireless
---

### Post by richie-moore123 on 2019-12-25
Hey..


Just bought the Pi4 and having trouble with the setup. Complete newbie at this !

I am trying to install the Ubuntu server for pi4 from the below website:
[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)

Done the installation process as per the requirements and even flashed my SD based on the below website:
[https://ubuntu.com/download/iot/installation-media](https://ubuntu.com/download/iot/installation-media)

However after the installation has been completed and i put my username and password. I am not able to issue any apt-get commands (to update / upgrade) used command (sudo apt-get install xubuntu-desktop).. it doesn't seem to fetch the repositories, i guess its cause i am not getting an IP address and not connected to the internet.

I was under the assumption, it would pick up an address directly (setup --> ethernet port of Pi4 directly connected to router)

Do you think there is a problem with NIC card ? or is there something i am missing out. Please help !!!

---

### Post by yancek on 2019-12-25
> i guess its cause i am not getting an IP address and not connected to the internet.

The software is downloaded from servers in various parts of the world so yes, you will need an internet connection.  Have you configured it?  Do you have  an ethernet or wireless connection?

---

### Post by richie-moore123 on 2019-12-25
Sorry to get back to you late, but I want to use wireless

---

### Post by yancek on 2019-12-26
> but I want to use wireless 		

Well, OK.  If you are having trouble configuring your wireless, posting some detailed information on wireless hardware and telling us what you have tried and what the results of your efforts were would be useful.  You might start by reading the info at the Ubuntu site below on wireless networking. 

[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html.en)

---

### Post by howefield on 2019-12-26
Thread moved to the "*Networking & Wireless*" forum and inane thread title changed.

---

### Post by chili555 on 2019-12-26
Let's first see if you have an ethernet interface. If so, that would indicate that you have a driver that is appropriate for the hardware. Please run and post the result of the terminal command:

```
ip addr show
```

Networking in recent Ubuntu versions is handled by netplan. Let's see what your file reveals. Please run and post:

```
cat /etc/netplan/*.yaml
```

---

