---
title: "Network and Shared folder permissions"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by Wee Aldo on 2007-05-31
Hello all :->

Still a newbie to Linux/Ubuntu... especially networking... my problem is that I have two installations of Ubuntu across a wireless network, both machines can see each other, I have Samba sharing enabled, the properties of both the shared folders have the read only tick box unchecked, but I cannot transfer files between the shared folders, when I try to configure the properties of my Ubuntu\UbuntuAth icons in the Places\Network section of the GUI I can't alter the settings as it tells me in the permissions tab that the owner is unknown. The only problem I might have, is that I have set my smbpasswd user  to the same settings on both shared folders on both machines.

All help gratefully appreciated.

---

### Post by bigken on 2007-05-31
try this in a terminal

sudo smbpasswd -e (your name) 


sudo smbpasswd -a (your name)

---

### Post by Wee Aldo on 2007-05-31
Thanks bigken for the quick reply :->

Done as you asked regarding enabling and adding my Samba account/password...I can now copy and past to my desktops or home folders on both machines but still no joy copying and pasting directly between the shared folders...  I have never tried to copy and paste between shared folders before..always between my home folders on the different machines...but thanks for the tip.;)

---

