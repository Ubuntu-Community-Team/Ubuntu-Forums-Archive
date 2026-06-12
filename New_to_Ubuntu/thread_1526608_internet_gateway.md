---
title: "internet gateway"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by speedygarth on 2010-07-08
hello there i`m a newby to linux, and i managed to setup my server with ubuntu 9.04 jaunty.
i`ve managed to download all the other packages to run the system but i need help- with setting up the server as an internet/email server so that workstations on my LAN can connect to the net via the proxy service.
the problem is the modem i`m using has no linux support (i checked the installation CD manual) is there a way to add the ADSL modem/router to the ubuntu system so that the internet connection can go via the server.
the modem has two ports 

1. USB
2. Ethernet

so far i`ve tried to connect the cat5 cable to the ethernet port and then back to the Linux machine but once i do that the other machines on my network lose internet connectivity.
and the LED indicator starts flashing red.
the model name of the modem is ZISA
can someone help!! (please)

---

### Post by okplayer02 on 2010-07-08
what kind of server are you trying to make Email Proxy or Gateway ? If you looking to make a gateway you need to have 2 NIC's in the machine that will be the gateway:  I would caution if this machine will be your gateway that you do not run other types of services on this since it will be your firewall. 

here is an how to for ICS (internet connection sharing)
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by speedygarth on 2010-07-09
thanks for the reply what i`d like is to have the users connect to the internet thru the ubuntu server so i can monitor their usage with squid.

actually the setup i`m trying to achieve or create is for the users to send & recieve emails from the server using a shared internet connection on the LAN.
thanks for the useful link on ICS.

---

