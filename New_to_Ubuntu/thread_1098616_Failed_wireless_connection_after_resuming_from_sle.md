---
title: "Failed wireless connection after resuming from sleep"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by marcus_c on 2009-03-17
Hi Everyone,

I've got sleep/resume working nicely on Intrepid Ibex 8.10, however my wireless connection to my home ADSL router does not resume successfully. It attempts to re-connect and after a while will ask for the WPA password again. I enter that but it still fails to connect. Only a reboot will re-establish the connection successfully.

I have a Winfast system board with NForce3 chipset. The wireless card is a Netgear (Atheros) 108mbps PCI (model WG311T I think?)

I'm so close to getting sleep/resume working perfectly, so any responses on how to resolve this would be much appreciated!!

---

### Post by Nxion on 2009-03-17
Here is the fix for it, open a terminal and type the following:

```
gksudo gedit /etc/pm/config.d/madwifi
```This will open a text editor. Next copy and paste this into it.

```
SUSPEND_MODULES=ath_pci
```Save and close the file. Now put your laptop to sleep and wake it up. This should fix the issue.

---

### Post by Nxion on 2009-03-17
> **marcus_c said:**
> Hi Everyone,

I've got sleep/resume working nicely on Intrepid Ibex 8.10, however my wireless connection to my home ADSL router does not resume successfully. It attempts to re-connect and after a while will ask for the WPA password again. I enter that but it still fails to connect. Only a reboot will re-establish the connection successfully.

I have a Winfast system board with NForce3 chipset. The wireless card is a Netgear (Atheros) 108mbps PCI (model WG311T I think?)

I'm so close to getting sleep/resume working perfectly, so any responses on how to resolve this would be much appreciated!!

Also. did you install madwifi for the wireless or are you using the ath5k/ath9k drivers?

---

### Post by marcus_c on 2009-03-18
Hi Nxion, thanks for your reply.

I'm not sure which drivers it is running on. I haven't installed madwifi myself, so I would think its using whichever driver Intrepid has installed automatically?

---

### Post by Nxion on 2009-03-18
> **marcus_c said:**
> Hi Nxion, thanks for your reply.

I'm not sure which drivers it is running on. I haven't installed madwifi myself, so I would think its using whichever driver Intrepid has installed automatically?

So since you are using the built in drivers change "ath_pci" to "ath9k" If that doesnt work cahnge it to "ath5k" Let me know if that helps.

---

### Post by drs305 on 2009-03-18
this is the thread that helped me when I had a similar problem:
[http://ubuntuforums.org/showpost.php?p=6264243&postcount=8]("http://ubuntuforums.org/showpost.php?p=6264243&postcount=8")

---

### Post by marcus_c on 2009-03-19
All fixed now!
Many thanks to you both Nxion and drs205.

I don't have a "madwifi" file in that location, but I do have 00sleep_module. Added SUSPEND_MODULES="ath_pci" to the file and the wireless connection now resumes successfully. 

Thanks again! :D

---

