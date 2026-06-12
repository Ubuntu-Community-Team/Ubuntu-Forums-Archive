---
title: "Printer Sharing Via SAMBA - Not Working"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by majortomm on 2007-11-04
I installed samba so I can share some network drives and networked printers with my Windows XP laptops.  The drives and printers are all connected to my desktop which is running Ubuntu 7.10 Gutsy Gibbon.  After much fiddling around I was able to add the Ubuntu box so that the XP machines could see it.  I setup samba to share the printer and set the printer to be shared as well.  When I access the printers folder from the XP machines it shows the printers folder but there are no printers listed.  How do I get the printers to be listed and able to be shared by the XP machines?  

I am also in need of figuring out how to share the network drives.  I am a Ubuntu newbie so I am sure this is probably easy.  The drives are 2 physical HDD's partitioned into 6 seperate drives.  The kicker is that they are al NTFS setups from my XP days (still running dual boot).  How do I setup these drives to be visible to the XP machines?

---

### Post by davenaus on 2007-11-04
My friend,

I can't help you with your situation because I'm new but, how did you get your printer to work? I've got ubuntu 7.4 and I'm trying to get my canon ip6700d to read the microsoft XP box which I'm sharing it off of. No matter what I do, can't get the thing to print? Will it only work if I'm plugged into the Ubuntu box?

Thanks,

---

### Post by majortomm on 2007-11-04
I have the printer (usb) plugged directly into my ubuntu machine.  I am not sure how to fix your situation but it sounds like you are trying to print to a printer that is connected to a windows machine.  I have installed samba and I remember seeing under the printer configuration -> New Printer -> Windows Printer via SAMBA -> Browse and then I select the windows computer it will show the printers installed on it and I can then select that printer and it will add it to my printers in ubuntu.  I hope this helps.

---

### Post by willz06jw on 2007-11-11
I am having about the same problem: but I can't even see the printer folder under XP.  

Man I wish there was a howto or ubuntuguide article on how to setup a network printer for sharing to an XP computer using samba (or GSAMBAD).

---

### Post by leifwi on 2007-11-14
I have similar problem. I have Suse 10.2 machine as a file and printer server. Printing from a Windows XP works fine, but with my Ubuntu 7.10 laptop it seems impossible. I can see the printer in the printer configuration tool, but I cannot print to it. With my earlier Ubuntu 7.04 it took me a week to finally get the printer installed, and it was working. I guess I should not have updated to 7.10. If it works, dont fix it, they say. 
It seems very difficult to get any answers or advise here on how to solve printing problems, so if someona has a howto guide, plese let us know about it.

---

### Post by willz06jw on 2007-11-15
jfinkels told me to go here in another post:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

