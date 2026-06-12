---
title: "[SOLVED] XP Home Laptop wont Print to Ubuntu Desktop"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by Hawaiisnowstorm on 2008-02-29
Hello, I am new to the world of Linux but I am the network/computer guy for my roommate and I as well as our friends.

I would like to be able to print from the laptop to the printer that is hooked up to the desktop.  
The printer is a HP Photosmart C4100 
The laptop is XP Home Service pack 2 
The desktop is Ubuntu 7.10

I can access the laptops shared folder from the desktop.  However, I cant  access the desktop from the laptop, which I would like to do so the laptop can print.  I can see my desktop in the windows work group on the laptop, but it says I do not have permission to access the desktop.  

I followed the network set up I found on this form for getting the two computers on the same workgroup, just not sure where to go from there.

Thanks for reading my post :) and any help is grateful

Edit:  Both the XP and Ubuntu 7.10 can see each other and access each others shared folders, still not sure how to get the XP to print to the Ubuntu.

---

### Post by maulakai on 2008-03-01
have you tried

security = share

in your smb.conf?

and done an apt-get install smbfs?

---

### Post by Hawaiisnowstorm on 2008-03-01
> **maulakai said:**
> have you tried

security = share

in your smb.conf?

and done an apt-get install smbfs?

Says files do not exist and I get this erros message for the apt-get
"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

:confused::confused: I take it i need to be in root? if so how I do that?? 
accorrding to my snypts pack manager I have all the samba files installed

---

### Post by Hawaiisnowstorm on 2008-03-03
bump bump de bump bump:guitar:

---

### Post by The Cog on 2008-03-03
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)
It's much the same from XP.

---

### Post by Hawaiisnowstorm on 2008-03-05
never mind I got it myself..

---

### Post by pliukait on 2008-03-08
Hello, what was your solution?

---

