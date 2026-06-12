---
title: "connection sharing w/ 360 problems"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by dracule on 2007-06-01
I am having troubles using firestarter to share my connection.  It will work for about 2-3 minutes, and then stop until i change some random detail in eth0 connection and then it will work again and then stop. I need help


trying to do:
modem->router->desktop w/ wifi->ethernet port->Xbox 360

Wireless USB: eth1
Ethernet:eth0
router ip:192.168.2.1

eth0 configuration:
IP: 192.168.3.1
Subnet:255.255.255.0
Gateway:192.168.2.1

Xbox 360's configuration:
IP: 192.168.3.5
Subnet:255.255.255.0
Gateway:192.168.3.1
DNS:192.168.2.1




It will work for like 3 minutes, then i have to change something in eth0 to make it work again (eg change gateway to 192.168.2.100 or subnet mask 255.25.255.0)

can anyone help me?

---

### Post by golfing22 on 2007-06-01
Well, if your router IP address is 192.168.2.1 it's a good idea have your clients IP addresses be 192.168.2.xxx.    Also, on your 360s connection you have the gateway set at 192.168.3.1 when it should be 192.168.2.1.

---

### Post by dracule on 2007-06-01
Well, I did what you said and it didnt even work.

on these forums before it said you have to set your Ethernet ip 3rd number different than your wireless ip's 3rd number...

and it also said to set your xbox's gatway to your ethernet's ip address.

These were just posts that I found by searching. I have not found any tutorials on how to properly set it up.

---

### Post by dracule on 2007-06-01
just so you know, i got the ideas for setting it up that way from here: [http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)
I followed this, and as we speak I am connected to Xbox Live through my PC...  but it never lasts. It will disconnect soon and I will have no idea what to do.

---

### Post by golfing22 on 2007-06-01
Oh, I thought you were using a real router instead of a bridged connection.  Sorry about the confusion.

---

