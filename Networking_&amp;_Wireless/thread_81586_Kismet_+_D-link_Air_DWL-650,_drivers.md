---
title: "Kismet + D-link Air DWL-650, drivers?"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by ninja on 2005-10-24
I have a D-link air dwl-650 with a Prism2 chip (11mbit card), what driver should i use? my network interface is eth0, on most drivers on kismet documentations it says WlanX. Does that change automaticly from ethX to WlanX after driver installation?.

Should i use HostAP drivers?

---

### Post by shartrec on 2005-10-24
I have been working through this one for the last few days.  Basically:
[LIST]
[*]Ubuntu by default uses the Orinoco driver for this card.  Other distributions do as well, such as OpenSuse.
[*]The orinoco drivers call the interface eth0 (or eth1 etc) but you can set it to another name by editing /etc/iftab.  You may want to do this if you use both a wired and a wireless connection at different times as the kernel may assign different names to the interfaces depending on what is plugged in when you boot.
[*]The Orinoco drivers, as supplied, don't support wireless scanning and so don't work with Kismet.  There are patched ones available but I don't know any more about them.
[*]You can try to install the wlan-ng pcmcia drivers, but you will need to compile the kernel modules.  I tried this but could not get them to work on ubuntu (I previously used them very successfully on Mandriva)
[/LIST]

---

