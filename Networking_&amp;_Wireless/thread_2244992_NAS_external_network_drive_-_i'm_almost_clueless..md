---
title: "NAS external network drive - i'm almost clueless."
date: 2014-09-20
forum: Networking &amp; Wireless
---

### Post by Opti_Rick on 2014-09-20
I bought a NAS (Zyxel NSA-210), I thought it would be the easiest way to offer storage to the 3 PCs in the office.

It's plugged into the router, I can see the IP address in the router settings, I can ping that IP address and that's where i'm up to. 

I was rather hoping I would be able to 'see' it on the network and connect to it (yeah, I know!) but that's plainly not the case.

Any help would be appreciated.

This is probably useful info

rick@rick-GA-MA78GM-S2H:~$ sudo blkid
/dev/sr0: LABEL="ZyXEL_NSA210" TYPE="iso9660" 
/dev/sda1: UUID="773f32a4-d9f5-4a5c-a9b7-848b62477274" TYPE="ext4" 
/dev/sda5: UUID="368ec99c-d880-44ea-8191-ad4cb243c108" TYPE="swap" 
rick@rick-GA-MA78GM-S2H:~$

---

### Post by tgalati4 on 2014-09-20
Open a browser on another computer on your LAN and put in the IP address.  You should see a configuration page and go through all of the settings.  You may need to refresh the file manager (F5) to see the network share.  If that doesn't work, then go to Nautilus or Caja and type in smb://192.168.1.125 in your location bar.  Put in the correct IP address.

It's possible that you have a bad unit.  The reviews show some wonky performance.  Open it up and make sure it is not made of cat food.

---

### Post by Opti_Rick on 2014-09-21
> **tgalati4 said:**
> Open a browser on another computer on your LAN and put in the IP address.
That was getting me nowhere, i've taken it home since and attached it to a windows PC and run the installation disk which has helped though it pains me that it's necessary.
> smb://
This was the vital chunk of info I was missing, I was just using the IP address and wodering why the 'connect' button was staying greyed out. 
Many thanks.

---

