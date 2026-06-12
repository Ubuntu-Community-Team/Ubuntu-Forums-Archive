---
title: "Broadcom 14e4:4311 rev 01, Ubuntu 14.10"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by rob118 on 2015-02-15
Hello, I installed Ubuntu Server 14.10 today. My wired connection works great, my wireless does not. 

I did an apt-get update
Since I have a Broadcom wireless card, I used Chili555's pci.id table to see if there was a package I could install that matched my pci.id.
Mine is 14e4:4311 rev 01
The table lists 4311, but does not list 4311 rev 01. I installed firmware-b43-installer before I realized the table did not explicitly mention rev 01 for 4311.
I downloaded the wireless script mentioned in the sticky for this forum and ran it successfully. The security mode on my router is WPA-Personal. I don't see a physical switch for WiFi on the laptop.

I've attached the output from the script.

Not sure what other information I should provide. Hopefully someone can spot something in the output file that looks odd.

- Rob

---

### Post by westie457 on 2015-02-15
Hello rob118

Does the terminal command ```
sudo modprobe b43
``` make any difference?

Have you tried rebooting the system yet?

Occassionally the wireless does not/will not connect when the cable is still plugged in.

---

### Post by rob118 on 2015-02-15
Hi westie457.
I was initially trying to configure my wifi on the command line. I installed lubuntu-desktop but was unable to launch the GUI, after restarting. The messages I saw referred to no screens being found. I had to install intel drivers ```
sudo apt-get install xserver-xorg-video-intel
```
 and I was then able to launch the gui. Once there, I was able to configure my wifi connection successfully. 
I unplugged my wired connection and restarted the system. Once the desktop loaded, it took a couple of minutes for the wifi connection to establish.
I plugged the wire back in and restarted the system again. This time, the wifi connection was established as soon as the desktop loaded.

While I was trying to set up my wifi, on the command line and prior to getting the GUI working, my wired connection was plugged in the whole time.
I'll take this as a win, even if it took all evening to sort out :) I appreciate you looking into it. I'll mark this thread as solved.

Rob

---

