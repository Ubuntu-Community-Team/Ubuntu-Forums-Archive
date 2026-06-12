---
title: "No wifi adaptor found in Ubuntu 18.04.1 LTS"
date: 2018-09-19
forum: Networking &amp; Wireless
---

### Post by lamashtu518 on 2018-09-19
I have a laptop - HP Notebook - 15-ac101tu and it is showing "No wifi adaptor found - Make sure you have a Wifi adaptor plugged and turned on". 
How do I resolve this? It has Broadcom chipset.

0d:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)

I also ran below commands but nothing changed.

sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source

---

### Post by jeremy31 on 2018-09-19
In terminal run ```
mokutil --sb-state
```
If it shows Secure Boot is enabled, reboot and go into BIOS/UEFI settings and disable it

---

### Post by lamashtu518 on 2018-09-19
Yes it shows SecureBot enabled. I'm kinda new to this stuff. Can you guide me how to go to BIOS/UEFI settings and disable it? / Thanks :)

---

### Post by jeremy31 on 2018-09-19
You will have to look at the HP splash screen at boot to see what key to press to change system settings, then look through until you find Secure Boot settings

---

### Post by lamashtu518 on 2018-09-19
Changed it but the issue still remains. In fact I have run into a new problem. After booting the laptop it goes straight to windows and does not give me the grub screen to choose from Ubuntu and Windows. What do I do?

svart@lamashtu:~$ mokutil --sb-state
SecureBoot disabled

---

