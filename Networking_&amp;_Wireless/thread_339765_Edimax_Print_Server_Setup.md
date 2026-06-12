---
title: "Edimax Print Server Setup"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Andy17MB on 2007-01-16
I am trying to get my Edimax 3205UWg print server set up and am struggling.  I connect to it with wired ethernet.  It works under windows XP and I can see it in eclipse with Samba enabled in the windows workgroup.  I can ping the printserver from linux and see the configuration page in the web browser.  IPP and LPD are enabled (the printserver is Based on BSD).  I can connect the Samsung ML1510 laser printer to the linux box and print ok.  When I connect the Samsung printer to it and set up a printer connecting via LPD nothing happens..  

In the Gnome Printer configuration I enter the IP address (fixed & not dynamic) in the host field and the the printer queue name appears to be correct (it's taken from the printserver config page).  The printer properties show:
Ready: Network host '192.168.0.5' is busy, down, or unreachable; will retry in 30 seconds...

I suspect I need to do something to configure CUPS, but I can't figure out what even after trying the CUPS website](*,) 

Thanks for reading this and I hope you can help...

---

### Post by mooscape on 2007-06-12
I am having the same problem: 

> Ready: Network host '192.168.1.104' is busy; will retry in 30 seconds...

My print server is running Dapper and the guest is Feisty.  Could there be compatibility issues? (Dapper stores printer .config different to Feisty...) I see the printers in the list on the guest machine but when I look at properties there seems to be much information missing!  I can print from the server with no problem, just not over the network.

---

### Post by mooscape on 2007-06-12
Attached screenshots of the problems I described:

---

### Post by CHFFriday on 2007-07-05
Did you get a fix for this problem?

CHFFriday

---

### Post by ugach on 2007-12-12
I have another model, edimax BR6104KP print server but it also supports IPP. 

I know that this answer may be late for you but this for all others who may land here via google like me.

I have disabled LPR and enabled IPP. My two USB ports are named prt1 and prt2. Currently I only have printer connected to prt1. The default ip of the router/print server is 192.168.0.1. In printer properties/connection tab I select network printer and use following URI

Note that this port 631 although same as cups admin port was mentioned somewhere is edimax docs on the web. 

Device URI: ipp://192.168.0.1:631/prt1



I was also able to setup this printer through cups [http://127.0.0.1:631](http://127.0.0.1:631) and using above mentioned uri

HTH YMMV

---

