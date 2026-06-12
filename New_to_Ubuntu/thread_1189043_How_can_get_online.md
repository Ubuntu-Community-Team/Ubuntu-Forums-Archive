---
title: "How can get online?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by ArnoldGove on 2009-06-16
I've a fresh install of Ubuntu 9 (no other OS on the PC) and a Safecom SAMR-4112 ADSL Modem Router all wired up (but not the USB connection). The ADSL light is on, the LAN light is on, and of course the PWR light is on. What now? I've gone to the Network icon, and keyed in what I could, but I'm still offline.

---

### Post by PureLoneWolf on 2009-06-16
I am presuming that the router is configured to access the internet?  Was it working before Ubuntu was installed?  If so, your PC should get an automatic address assigned by the router.

If the router is new aswell, you will need to connect to it through Firefox and configure (almost all routers have a HTTP admin page) - I don't know that model though, so you would need have a look at the (sorry) manual.

If you have the network icon on your panel - Right click and choose "Connection Information"

This will give you the router IP address (if the PC has made a connection to it)

---

### Post by SoftwareExplorer on 2009-06-16
Possible router addresses:
192.168.0.1
192.168.1.1
10.0.0.1
192.168.10.1

---

### Post by caravel on 2009-06-18
The problem here may be the router and not the OS.  If you plug an Ubuntu box via ethernet into a correctly set up router that is connected to your ISP, the Ubuntu box should assign itself an IP address by DHCP and you should then be online.  Ubuntu usually uses an available connection during the setup to update - there is nothing to configure in Ubuntu, configure the router correctly first by logging into it's web based interface through a browser. Instructions on how to do this come with the router or are downloadable from the manufacturer's website.

If it still fails find out your router's IP and use that IP as both your gateway and primary dnns.

---

