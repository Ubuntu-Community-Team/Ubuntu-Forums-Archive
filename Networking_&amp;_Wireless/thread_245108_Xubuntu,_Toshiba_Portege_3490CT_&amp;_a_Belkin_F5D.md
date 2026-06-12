---
title: "Xubuntu, Toshiba Portege 3490CT &amp; a Belkin F5D7010"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by Flamekebab on 2006-08-27
I've recently got a Toshiba Portege 3490CT and after much messing around with floppy disks and net installs, I've Dapper up and running, using XFCE. I've bought a Belkin F5D7010 from [The Linux Emporium]("http://www.linuxemporium.co.uk/") and it works OOTB. However, when I'm using the card it randomly crashes the system. It appears to only do it when I'm online (It happens when I use Firefox) and it seems to mostly happen when I'm using it running on battery. I've got to experiment to see if that's the case though.

When the card works, it works wonderfully (ie, just plug it in and use, no configuration required). However, when the system crashes, I reset it and the card acts as if its not plugged in. Sometimes it shows up, other times not. After restarting, leaving the system alone, etc. it starts working again. I'm unsure why that is.

Is anyone able to help?

I can provide /var/log/syslog and kern.log if you like.

It might also be worth mentioning that Suspend and hibernate seem to work flawlessly.

---

### Post by funchords on 2006-08-27
I don't know what's causing the crash.  That is usually a hardware conflict of some kind.  The below addresses your temporary lack of connectivity afterward.

Are you using WPA or WPA2? If so, it could be that the AP is temporarily blacklisting your BSSID (MAC address) because it did not authenticate properly, it could also be that your client is blacklisting the AP due to a incorrect authentication.  

One hint that this is the problem is that you are immediately able to reconnect if you:
1.  Shut off power to the AP, then restore it (thus clearing its blacklist), OR
2.  Clear the blacklist in wpa_supplicant by restarting it (depends on how you are starting the wpa_supplicant, you may have to restart NetworkManager, for example)

---

### Post by Flamekebab on 2006-08-27
> **funchords said:**
> I don't know what's causing the crash.  That is usually a hardware conflict of some kind.  The below addresses your temporary lack of connectivity afterward.

Are you using WPA or WPA2? If so, it could be that the AP is temporarily blacklisting your BSSID (MAC address) because it did not authenticate properly, it could also be that your client is blacklisting the AP due to a incorrect authentication.  

One hint that this is the problem is that you are immediately able to reconnect if you:
1.  Shut off power to the AP, then restore it (thus clearing its blacklist), OR
2.  Clear the blacklist in wpa_supplicant by restarting it (depends on how you are starting the wpa_supplicant, you may have to restart NetworkManager, for example)
No, I live out in the countryside, so my AP has no security whatsoever!

---

