---
title: "Not connecting to Vista system"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by DaveyBaby on 2007-07-26
Newbee here, and I just installed Ubuntu. I want to move to Linux, but will need to use Vista until I learn Linux.

I need to connect to a Vista box accessing files and printers. I've searched and cannot find how to do it. When I try to open a file on Vista, I get a message saying "Nautilus cannot display smb//desktop/working_files/documentation". "Please select another viewer and try again."

I cannot ping the vista system, but I can ping the Ubuntu system. Both systems are attached to a router and both can access the internet.

---

### Post by Jamie Jackson on 2007-07-26
These are from my notes. I think you might need WINS to be able to hit the machines by hostname:

#WINS for ubuntu (so you can browse windows network by machine name)
#[http://ubuntuforums.org/showpost.php?p=2632252&postcount=3](http://ubuntuforums.org/showpost.php?p=2632252&postcount=3)
sudo apt-get install samba smbfs smbclient winbind
sudo gedit /etc/nsswitch.conf
#find the following line (it may not be exactly that)
#hosts:          files dns mdns
# add " wins" to the above line

For mounting windows shares in Ubuntu, take a look at [this]("http://ubuntuforums.org/showthread.php?t=501575")

---

### Post by reckless2k2 on 2007-07-26
yeah you kinda got a 2 part issue. the vista side is a pain to get netwokring going. you've got a better chance of connecting from vista to ubuntu than from ubuntu to vista. wins setup as suggested will hlep with pinging but samba is a different story. go to network menu and see if you can even browse your network and see the vista machine.

---

