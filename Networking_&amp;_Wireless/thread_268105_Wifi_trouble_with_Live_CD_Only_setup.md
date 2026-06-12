---
title: "Wifi trouble with Live CD Only setup"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by Dobbs5578 on 2006-09-29
I am a linux newbie. The setup I have will be run from the Live CD only, no HDD installation.

The first time I ran the Live CD, everything worked great. I had to go to the network control panel and disable my wired eth connection (not used) and enabled my wireless connection. My AP was listed, it is setup as open with MAC filtering. This all worked fine, and I was online and enjoying Ubuntu and was very impressed.

The second and onward (I've booted with Live CD about 6 times now) I cannot get an IP Address. My wireless card is recognized and it does find my AP, just does not obtain a DHCP IP Address.

It is a little frustrating since I know it worked already (this is all over a 3 day period, no system changes). Since I can't install or change boot settings, what options do I have? Also, I have a neighbor with totally open wifi and it won't obtain DHCP from that AP either.

I apologize I do not have any output to share. Besides using the GUI interface for network administration, what commands are there to manage network settings that can perhaps help me reset the connection. Can I run a command that will rescan my hardware as is done on boot from Live CD?

Thanks for the help
- Dobbs

---

### Post by x64Jimbo on 2006-09-29
try running this from the command line:
sudo dhclient <interfacename>
it forces the device to go looking for a DHCP server. Also, you might try resetting your router since sometimes the DHCP service craps out.

---

### Post by Dobbs5578 on 2006-09-29
:KS Thank you! That worked!

---

### Post by x64Jimbo on 2006-09-30
Which one? :D

---

