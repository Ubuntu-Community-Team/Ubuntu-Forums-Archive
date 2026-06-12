---
title: "[SOLVED] stop wireless at bootup"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Circus-Killer on 2007-06-26
Okay, I currently have my wireless network card setup and working well. There is only one small problem.

Currently, I am using WPA to secure my network. Now, I use gnome's network-manager to handle my connections and all that, which is all fine. The problem is that during bootup, it still tried to connect to the wireless network even though the booting part has not been set up for WPA.

I was wondering, does anybody know how I can stop the computer from trying to connect to the network during bootup? (and letting network-manager do the connection once logged in).

I tried removing the section dealing with wlan0 from /etc/network/interfaces but that also stopped gnome's network-manager from working. Any ideas how I can stop the bootup attempt without stopping gnome's network-manager?

---

### Post by chili555 on 2007-06-26
Please try removing *auto wlan0* from ../interfaces. Leave the remainder of the wlan0 wording there.

---

### Post by Circus-Killer on 2007-06-26
what you suggested didnt work, but then i tried it the other way around.
i commented the other lines out, and only left the "auto wlan0" uncommented, that did the trick. 

but thanks for your help, i wouldnt of thought of trying that until i tried your advice. ;)

---

### Post by chili555 on 2007-06-26
That's very weird, but whaever works...works!

---

### Post by Circus-Killer on 2007-07-03
okay, after doing a re-install, neither works anymore :(
any suggestions?

---

### Post by Circus-Killer on 2007-07-04
alright, since the start of the problem, i always knew what the problem was. i didnt know how to configure wpa in /etc/network/interfaces. that didnt matter because i was using network manager to configure the network. however, thats what was causing the slow boot.

last night i found this [very helpful howto]("http://ubuntuforums.org/showthread.php?t=318539") which shows you how to setup all the different security protocols in /etc/network/interfaces. after following that guide, i managed to get the network to establish succesfully on bootup. no more slow boot.

---

### Post by GrouchoMarx on 2007-07-04
If you're using Network Manager with ndiswrapper, there seems to be a boot timeout when the wireless interface is being configured before the ndiswrapper module is loaded.

Adding "ndiswrapper" to /etc/modules did the trick for me (and you can leave /etc/interfaces alone, so everything is properly configured).

This step is omitted from some HOWTOs, and on a reinstall or upgrade, /etc/modules may be wiped.

---

