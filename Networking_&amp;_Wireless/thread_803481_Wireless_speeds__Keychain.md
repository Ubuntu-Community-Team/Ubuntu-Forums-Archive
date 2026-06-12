---
title: "Wireless speeds / Keychain"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by aarb00 on 2008-05-22
I have had 7.1 and 8.04 installed on both my laptop and desktop.  I have two D-Link DWA-130 usb 8011.N cards in which I used in each.  The network performance on all 4 combinations was slower than with Windows, around 12 mb/s vs 50 mb/s. 

My laptop also has an internal Broadcomm card, which I use instead of the D-Link because it works faster, even though it is a G card.

Since my desktop is used for Midi and Audio applications, I decided to try Ubuntu Studio because I wasn't having any luck getting these types of applications to work.  Anyway, after installing Ubuntu Studio, I got my D-Link DWA-130 card working with NDISWrapper as I did all the other times.  I used the same drivers, the same version of NDISWrapper, and what do you know, I get the same speeds as I get with Windows!!

Also of interest, is that I don't have to enter a keychain password during bootup on Ubuntu Studio.  On my desktop I have network shared in my fstab file.  When Ubuntu boots, it prompts for a keychain password.  It then connects to my wireless, then mounts my shares.  On my desktop, I used WICD instead of Network Manager as I don't have any shares in my fstab.  Using WICD prevents the password from being asked.  Now with Ubuntu Studio, I can use Network Manager, have a mount in my fstab, and don't get prompted for a password.

Does anyone know why?  I would like to have the option of using the USB Dlink on my laptop when I need the speed, and I would also like not to get prompted for a password every time I reboot and don't want to install Ubuntu Studio on it.

Thanks,

Brian

---

### Post by aarb00 on 2008-05-23
Bump

---

### Post by aarb00 on 2008-05-27
Bump

---

### Post by aarb00 on 2008-05-28
Does anyone know where I could possibly find out this information?  Is there a suggestion of any files, or logs to compare between the two computers to try to figure out the solution?  Any help would be appreciated.

Thanks,

Brian

---

