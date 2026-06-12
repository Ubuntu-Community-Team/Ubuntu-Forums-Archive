---
title: "NetworkManager"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by don_pucci on 2007-09-05
I am running 7.04 on a IBM Thinkpad T42.

I am wondering why my Network Manager looks nothing like the one on [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

In fact, I only have Manual Configuration Option when i click on the NetworkManager icon.

I would like to be able to browse and connect to available wireless networks.

Any ideas or suggestions?

---

### Post by Breathe on 2007-09-05
That may be because thats the KDE skin while you have the GNOME skin. Don't hesitate, NetworkManager works great in GNOME while KDE users would prefer another aplication such as Wifi Radar.

---

### Post by Breathe on 2007-09-05
Try this:

$ lspci

If one of those lines has something like:

Network controller: Broadcom Corporation ....

Then i can help you, XD

Download this file:
[http://mural.uv.es/alacer/wl_apsta.o](http://mural.uv.es/alacer/wl_apsta.o)

And save it to /home/<user>/Desktop

$ sudo apt-get install bcm43xx-fwcutter

Say no to the option fetch and extract firmware

$ uname -r

Copy the line that says something like "2.6.20-16-generic"

$ sudo bcm43xx-fwcutter -w /lib/firmware/<Paste the line>/  /home/<user>/Desktop/wl_apsta.o

---

### Post by don_pucci on 2007-09-05
> **Breathe said:**
> That may be because thats the KDE skin while you have the GNOME skin. Don't hesitate, NetworkManager works great in GNOME while KDE users would prefer another aplication such as Wifi Radar.

Thanks for the reply.  THe problem is, that none of those KDE options are available.  I have no option to search for wireless networks or anything, just manual network config.

---

### Post by don_pucci on 2007-09-05
> **Breathe said:**
> Try this:

$ lspci

If one of those lines has something like:

Network controller: Broadcom Corporation ....

Then i can help you, XD

Download this file:
[http://mural.uv.es/alacer/wl_apsta.o](http://mural.uv.es/alacer/wl_apsta.o)

And save it to /home/<user>/Desktop

$ sudo apt-get install bcm43xx-fwcutter

Say no to the option fetch and extract firmware

$ uname -r

Copy the line that says something like "2.6.20-16-generic"

$ sudo bcm43xx-fwcutter -w /lib/firmware/<Paste the line>/  /home/<user>/Desktop/wl_apsta.o

output of lspci is: 

Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by Senathon on 2007-09-06
When I run 

#sudo apt-get install bcm43xx-fwcutter

I get an Error 1 which I know is related to a non existant page on Googlepages.com and I notices this is happening to alot of my installs.

I have found out it is my DNS name servers but I can not change the name servers(/etc/resolv.conf) due to Network manager overwrites them when I update the network adapter through manual configuration.

Any Suggestions?

---

### Post by don_pucci on 2007-09-06
> **don_pucci said:**
> output of lspci is: 

Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

SOLUTION:  Enable Roaming Mode...this disables manual config and then u can see multiple wifi networks and choose one to connect to.

---

