---
title: "DHCP not working for wireless"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by c_forq on 2007-02-24
Okay, this problem is driving me insane.  I can scan for networks and find my local wireless network, I can assign the essid, but for the life of me I can not figure out a way to get the computer to connect to the internet, the "sudo dhclient wlan0" always fails.  Any suggestions, I sure can't figure out what is going on.  I would like to post the terminal output, but unfortunately it is a desktop in the other room, and as you might be able to guess from this post is unable to access the internet.

---

### Post by bukwirm on 2007-02-24
Suggestions: 

Make sure the network interface is actually up - try "sudo ifup wlan0".

Make sure your router is configured to allow that computer to connect.

For posting the output of dhclient, you could copy it from the terminal into a text file, then transfer the file to a computer with internet access on a floppy disk/usb key.

---

