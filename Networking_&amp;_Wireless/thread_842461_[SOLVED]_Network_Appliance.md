---
title: "[SOLVED] Network Appliance"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by e_swallie on 2008-06-27
Hello, the main purpose of this Ubuntu box is to be a network appliance.  However I did load a GUI on the system so I could try out that side of Linux as well.   I have a problem with my wireless networking at this time, so the next question sort of hinges on me finding a solution there.  However what I am after is this:
 
1. I want this device to run DHCP for my home netowrk, both over the extra 3 Gigabit ports as well as the wireless, and use the built in Gigabit port as a WAN port.  It needs to have firewall and router features, thus creating my own wireless broadband router.
 
2. I want to run basic internet services such as a Web Server, FTP Server, Mail Server, Proxy Server, VPN, etc.
 
3. I also would like to be able to remotely acess this system, both for configuring the the above features, as well as just connect as a remote desktop user. (From a windows based machine if possible)
 
With this in mind, what would you suggest doing to reach these goals.

---

### Post by superprash2003 on 2008-06-27
1) for DHCP server [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)
2)web server - apache [http://prash-babu.blogspot.com/2008/05/how-to-install-apache-and-setup.html](http://prash-babu.blogspot.com/2008/05/how-to-install-apache-and-setup.html)
 ftp server - proftpd .. also install gproftpd ( gui for proftpd)
  vpn - openvpn
  proxy server - squid proxy
3)remote access - [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html)

---

### Post by superprash2003 on 2008-06-27
mail server [http://www.hypexr.org/linux_mail_server.php](http://www.hypexr.org/linux_mail_server.php)

---

### Post by e_swallie on 2008-06-27
Thanks for the quick reply.  i have allready installed a few of those as they just seemed to be the rigt thing to do.  the rest of them ill get and see about configuring it all to work.
 
 
I am marking this as solved as the majority of the issues are taken care of to my liking.  however if anyone has input on the firewall/router issues please let me know.  otherwise i will open a new thread for these items later after i get all the server apps set up and running.

---

