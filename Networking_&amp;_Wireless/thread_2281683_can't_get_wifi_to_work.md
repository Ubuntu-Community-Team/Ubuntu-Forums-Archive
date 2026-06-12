---
title: "can't get wifi to work"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by houmingc on 2015-06-08
i did
nmcli d wifi connect HUAWEI-E5776-853E password 7Y168E40 iface wlan0
Error: NetworkManager is not running.


i did 
sudo killall -9 NetworkManager
NetworkManager: no process found


i did
nm-applet
Could not initialize NMClient .org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files. 
nm-applet-Warning: Error connecting to ModemManager

i did
sudo /etc/init.d/NetworkManager start
sudo: /etc/init.d/NetworkManager: command not found

---

### Post by grahammechanical on 2015-06-08
What computer operating system are you using? What User Interface? If it is Ubuntu, then what version?

When we install Ubuntu we usually need to have an internet connection to install updates as part of the installation process. Network Manager should be installed by default and when we load Ubuntu we should see a Network Manager icon in the top panel towards the right side of the screen because Network Manager will start even before we get to the login screen.

What do you see when you click the Network Manager icon? Do you see a tick mark against Enable WiFi? If there is a tick mark then do you see a list of available in range wireless access points. We should be able to use the Network Manager's graphical user interface to select our wireless access point and use the dialog box to set up a connection.

Is this a server edition?

Regards.

---

### Post by sandyd on 2015-06-08
Moved to *Networking & Wireless*

---

### Post by houmingc on 2015-06-09
lsb_release -a

Description: Ubuntu 14.04.2 LTS.

Do i need to reinstall ubuntu?

---

### Post by Brandon_Morris on 2015-06-09
Can you give any more details? Particularly, what hardware are you using?

I had an issue with wifi when I tried to boot Ubuntu onto a MacBook Pro. Turned out to be a device driver issue. I was able to get online with a tethered connection to my phone (though a wired connection would work just as well) and install the driver I needed.

---

