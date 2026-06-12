---
title: "Could not set my lan connection in ubuntu 14.04"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by Shopnobuzz on 2014-04-30
Hi.I am new ubuntu user.today i set up ubuntu 14.04 in my pc.But now i cant connect with my lan connection.Before using ubuntu i'm just manually assign my ip , dns server , mac into windows 7 network properties.Then it worked perfectly.What i have to do with my ubuntu now??? Thank u .

---

### Post by TheFu on 2014-04-30
Welcome to the forums. There are many options, just like Windows has at least 3 ways to accomplish this.

* Use **network manager** (the default method) - there is almost always a network button on the top panel
* Use the "Dash" to find **network manager** - hit the "super" key and type "network" when the search comes up
* Use the **System Settings** button on the desktop, find "network" in the window that comes up
* Use DHCP reservations provided by the router (just need to know the MAC address for the NIC) this way
* Use text configuration (after disabling network manager) in the /etc/networking/interfaces file.

Before you get started, is there a network device recognized?  Something named "eth0" or "em0" would be a good start. Check the output from **dmesg** for that. There is probably a GUI log file viewer too.

Ubuntu is a form of Debian, so it is safe to follow Debian instruction, if [Ubuntu instructions]("http://help.ubuntu.com/") aren't working. [https://wiki.debian.org/NetworkManager](https://wiki.debian.org/NetworkManager)

Also, don't forget that the GUI on any Linux system is just another program. You are free to select any of 20+ different GUIs and do not need to use the default.

If you don't understand something, please ask for clarification.

---

