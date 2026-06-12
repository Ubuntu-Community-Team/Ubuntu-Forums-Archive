---
title: "udev persistence"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by helander on 2008-07-03
I have a minimal ubuntu (server) installed on a USB stick and I move this stick between several different computers. It works great  but one thing that I discovered early was that the network connection did not work properly since the eth0 device was not "properly discovered". I found one remedy for this via the forums and that was to delete a file in the /etc/udev/rules.d directory. 

What would be the proper action to do regarding this file to automate the prcoess of deleting this file, so that I have not manually have to access the systems to delete the file in order to get the network up an running. The thing is that one of the target machine is headless and I access it via vnc (x11vnc started at systems startup) and if the network is not working I have no means to access the machine :).

/Lars

---

