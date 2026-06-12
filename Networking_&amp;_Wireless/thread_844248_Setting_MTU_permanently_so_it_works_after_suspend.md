---
title: "Setting MTU permanently so it works after suspend"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by con on 2008-06-29
I need to have my mtu set at 1440 to be able to use my internet connection. I can do this with the commands;

sudo ifconfig wlan0 mtu 1440    
sudo /etc/init.d/networking restart

I have the first command set as a start up command so networking works when I first boot my computer, but when I resume from sleep I have to run the two commands again.

I think on earlier versions of Debian/Ubuntu the file /etc/network/interfaces could be edited to set the mtu but all I have in that file is the following two lines.

auto lo
iface lo inet loopback

---

### Post by chewearn on 2008-06-30
> **con said:**
> I need to have my mtu set at 1440 to be able to use my internet connection. I can do this with the commands;

sudo ifconfig wlan0 mtu 1440    
sudo /etc/init.d/networking restart

I have the first command set as a start up command so networking works when I first boot my computer, but when I resume from sleep I have to run the two commands again.

I think on earlier versions of Debian/Ubuntu the file /etc/network/interfaces could be edited to set the mtu but all I have in that file is the following two lines.

auto lo
iface lo inet loopback


I believe the /etc/network/interfaces configuration can still be used, except you have to first disable the networkmanager (nm-applet).

---

### Post by superprash2003 on 2008-06-30
hope this helps [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by con on 2008-06-30
I'm using knetworkmanager to connect to my wi-fi network, I guess I could use kwlan instead and then the instructions superprash2003 has given would work. I'm thinking I might try to find a way to run the two commands to change the mtu settings automatically after resuming from suspend before I try kwlan.

---

### Post by con on 2008-06-30
I've tried to put a script with the two commands into /etc/acpi/resume.d but I can't get them to run after I resume. When I run sudo sh /etc/acpi/resume.d/92-change_mtu.sh it works alright. I don't really know anything about scripting so maybe its a permissions problem or something.

I tried the instructions on this page but no joy either.

[http://ubuntuforums.org/showthread.php?t=585039&highlight=%2Fetc%2Facpi%2Fresume.d](http://ubuntuforums.org/showthread.php?t=585039&highlight=%2Fetc%2Facpi%2Fresume.d)

---

### Post by con on 2008-07-01
I have the permissions set up on the script correctly and the script works when I execute it manually but it still doesn't want to work after a resume, any ideas?

---

### Post by neel148 on 2011-03-11
For me application like Evolution mail, youtube-dl, PUBKEY etc. dont work and I checked the MTU to be 1472. At my work environment the MTU is 1500 and there all these applications work. Is the problem just with the MTU? and would changing that make all of them work for me?

I am just being a bit cautious so that changing it doesn’t disrupt my present scenario!

Also I haven’t understood how to change the MTU permanently. at /etc/network/interfaces the following two lines are written:

auto lo
iface lo inet loopback

What do I change now?

---

