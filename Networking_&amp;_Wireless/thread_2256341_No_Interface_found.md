---
title: "No Interface found"
date: 2014-12-11
forum: Networking &amp; Wireless
---

### Post by devdlp on 2014-12-11
Hey guys, I had a problem today where I changed something's on my desktop through the terminal that needed a reboot afterwards. Once I rebooted and returned to the desktop I wasn't able to connect to a wifi. I put ifconfig up in the terminal to bring my interface back up and got: No interface was found. Please help me with this problem.

---

### Post by lah7 on 2014-12-11
More details will be required. What did you change on the desktop? Which version of Ubuntu are you running? Is there a message in the network menu?

If possible, try to reverse what you did. Type **history** for a list of your previous commands. For instance, if you installed a package via **apt-get install**, do **apt-get remove **instead.

You could check if your device is still functioning by typing **lsusb** and **lspci** to see if it's listed. You could try ifconfig again, but like this: **sudo ifconfig wlan0 up.**

---

### Post by devdlp on 2014-12-12
I changed my toolbar. Used nano to add network icon because I got rid of it. I'm also running xubuntu 14.10. No there are no messages.
Also I didn't download and install anything, and  nothing in my history reverses it, I tried lsusb they all seem to be working fine, then ifconfig wlan0 up and I get the same issue. But I did plug in my Ethernet cable and it connected fine if that means anything.

---

### Post by lah7 on 2014-12-12
You could try loading a guest session on your system, which might identify if there's a faulty configuration file in your home folder, or if this is a system-wide problem.
If you can connect under a guest session, you may wish to reset the [XFCE panel settings]("http://askubuntu.com/questions/224006/resetting-xfce-panels-to-default-settings") for your profile.

In "All Settings" in the XFCE menu, there is an option for Network Connections. You could try adding a Wi-Fi connection this way, where your device should be selectable from the "Device MAC Address" drop-down.

Is your wireless card built-in or plug and play (USB)? Either plug it in and out or press a 'toggle' hardware button or switch if your system has one.

---

