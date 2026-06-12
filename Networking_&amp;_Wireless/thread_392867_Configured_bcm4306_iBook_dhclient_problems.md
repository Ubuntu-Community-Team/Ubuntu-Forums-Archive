---
title: "Configured bcm4306 iBook dhclient problems"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by BrunoThePug on 2007-03-25
I'm posting this from links so please excuse any formatting issues :D

I've followed various guides for getting my iBook G4 up and running with the bcm43xx firmware, I've got through all of the iwconfig steps, setting the essid, the channel and the key.

When I try to obtain an IP from the router using ```
sudo dhclient eth0
``` where eth0 is my wireless card. I just get various timeouts and eventually dhclient gives up and goes to sleep.

When I run ```
iwconfig
``` I can see my wireless card, see Broadcom in the nickname and it will even show that I'm connected to an AP, but I still get no internet connection.

The especially weird thing is that if I look at the list of local clients from my router's web interface I see a connection from the hostname of my Ubuntu iBook!

I've installed the "server" version as this will eventually be tucked away as a server so I cannot configure the wireless connection using the GUI network manager, I only have the command line (hence the use of links :D)

Thanks in advance for any help! :)

---

### Post by chili555 on 2007-03-25
Command line and links! Good stuff!

When you do sudo iwlist eth0 scan does it show that the ESSID and access points MAC address match what iwconfig eth0 show? If not, sudo nano /etc/network/interfaces to amend and then restart networking sudo /etc/init.d/networking restart and let us know.

By the way, your format looks perfect.

---

