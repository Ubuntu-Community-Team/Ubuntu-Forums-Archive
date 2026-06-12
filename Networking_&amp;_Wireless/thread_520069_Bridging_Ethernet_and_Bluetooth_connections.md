---
title: "Bridging Ethernet and Bluetooth connections"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Asix on 2007-08-07
On my laptop computer there is an Ethernet connection with my DSL modem, and that is the only network interface that connects my laptop to the Internet.
I recently added a Bluetooth dongle so I could share the DSL connection with my Symbian - based cell phone so I don't get charged for GPRS. The problem is that I don't know how to bridge the Bluetooth connection with Ethernet connection. I have bridge-utils package installed, but I do not know how to bridge there two connections once I pair my cell phone with the laptop. I have never done this before in GNU/Linux. I've searched both the Internet and these forums but didn't find a solution. Does someone have an idea how to do this? Any link or something? Thanks in advance.

---

### Post by zero-9376 on 2007-08-07
you might be better off / more likely to succeed by looking at sharing the connection through firewall rules and making your computer a gateway, not sure how this would go with the bluetooth but if your system sees is as a network device it could work. have a look at firestarter, its a firewall configuration tool and makes ICS easy

---

