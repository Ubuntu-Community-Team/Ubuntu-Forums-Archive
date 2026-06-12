---
title: "Acessing Ubuntu Shared Printer From WinXP"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by dj_penguin on 2007-11-10
Hi all,

I have a newly installed Linux Box running Gutsy Gibbon.  I want to share my HP Deskjet F300 (connect to my Linux Box) with the rest of my wireless network (running WinXP SP2); I've followed the instructions detailed at [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) but when I enter the URL of the printer in WinXP [[http://dansnotebook:631/printers/Deskjet_F300_series]](http://dansnotebook:631/printers/Deskjet_F300_series]) windows says that it can't find the printer.  Any suggestions?

Thanks in Advance.

P.S. I'm a linux newbie but I'm fairly confident with the Terminal.

---

### Post by dj_penguin on 2007-11-10
[Bump]

Sorry guys, but this is fairly urgent.

Edit:  Just another piece of information, when I try to access the printer using the URL [http://dansnotebook:631/printers/Deskjet_F300_series](http://dansnotebook:631/printers/Deskjet_F300_series) from my linux box, I get the 403 Forbidden message returned.

---

### Post by dj_penguin on 2007-11-11
#Bump# Anyone?

---

### Post by SpiritIsReality on 2007-11-11
howdy
I had the same trouble 
[http://ubuntuforums.org/showthread.php?t=608738](http://ubuntuforums.org/showthread.php?t=608738)
trails
have you tried replacing hostname with ip address?
I'm sorry I missed the relevance of your link in the op. I just skimmed past it thinking it was 
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by SpiritIsReality on 2007-11-12
howdy
I finally found a way that worked for me. Please see *** toward the bottom of the page at
[http://ubuntuforums.org/showthread.php?t=608738](http://ubuntuforums.org/showthread.php?t=608738)
trails

---

### Post by dj_penguin on 2007-11-12
Thanks Spirit, I'll try that tonight when I get home.  RE the IP address, I have my IP addresses assigned dynamically by the router and I'd prefer to keep it that way if possible.

Thanks again.

---

### Post by SpiritIsReality on 2007-11-12
howdy
on the xp box I didn't have to type in any ip address. Just click on icons.
trails

---

### Post by kamasabi on 2007-11-12
Another solution I used for my deskjet 3745 is just using samba.  I use it for transferring files as well, but you don't need to add in any sections for sharing files if you don't want to, but it should pop right up.  I think by default it adds a section for your printer that it can be browse-able by anyone.

---

### Post by SpiritIsReality on 2007-11-12
howdy
dj_penguin ... do you mean this part? > (I'll try printing from another xp box on the network)
Different xp box static dhcp of 192.168.0.101, and ubuntu printer server can ping each other. Start > Control Panel >
Add Printer > Next > A network printer or a printer attached to another computer > Next > Browse for a printer > Next
Printer ..name ..click on ubuntu server name > Next > Same Error message as above.
If you do I guess I should just delete that part. Done. Thanks.
trails
links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)

---

### Post by SpiritIsReality on 2007-11-12
howdy
> **dj_penguin said:**
> Thanks Spirit, I'll try that tonight when I get home.  RE the IP address, I have my IP addresses assigned dynamically by the router and I'd prefer to keep it that way if possible.
Thanks again.
That xp box is assigned it's  ip address by dhcp from a DI-524 d-link router. On the dhcp page there is a Static IP option, which is set to assign a static ip address to that computer, but it is not necessary.
I do believe there will be no problem if you leave your dhcp settings the way they are.
All the Best
trails

---

### Post by SpiritIsReality on 2007-11-12
howdy
> **kamasabi said:**
> Another solution I used for my deskjet 3745 is just using samba.  I use it for transferring files as well, but you don't need to add in any sections for sharing files if you don't want to, but it should pop right up.  I think by default it adds a section for your printer that it can be browse-able by anyone.Thankyou for your post.
trails

---

### Post by SpiritIsReality on 2007-11-12
howdy
The ubuntu print server I am using has a static ip address.
THAT's what you saw. Please try to share your Ubuntu printer server with your dhcp settings the way they are, and if you would post your findings here and at [http://ubuntuforums.org/showthread.php?t=608738](http://ubuntuforums.org/showthread.php?t=608738) I would be truly grateful. Then we will know if it works on your network settings as well. Thanks in advance.
trails

---

### Post by dj_penguin on 2007-11-21
**_New Development_**
I made some changes to my cupsd.conf file following the instructions at [http://ubuntuforums.org/showthread.php?p=163882](http://ubuntuforums.org/showthread.php?p=163882) and found that my WinXP box can now access the printer.  However, when I try to install the printer on my XP box, Windows hangs while 'connecting to the printer'.  Does anyone have any suggestions?

---

