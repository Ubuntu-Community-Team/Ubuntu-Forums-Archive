---
title: "Ubuntu print server with Windows &quot;clients&quot;?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by VenisonMogambi on 2008-07-29
Hi,

I just got Ubuntu set up on my desktop PC, and I'd like to hook my USB HP All-in-One printer up to it and use it as a print server for two Windows laptops that we use in our house, via our wireless networks. First off, is CUPS the appropriate tool to set this up? And secondly, should I set up SAMBA first, or will CUPS work independently of SAMBA networking?

Thanks.

---

### Post by Rich930 on 2008-07-29
cups is the print service - samba is for filesharing and has nothing to do with print serving. i think :P

---

### Post by superprash2003 on 2008-07-29
printing is possible using samba.. firstly setup samba and then share printer through samba.. this would be easier to setup up the network printer..
For reference:Samba setup [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)
Printing Setup : [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by linux6994 on 2008-07-29
Printing from Windows to your Ubuntu is really easy to setup and use. My family all have XP & Vista laptops and I run Ubuntu on my dektops sharing printers and external usb storage drive. 

Install system-config-samba and set up the access on it for all to use. Its easy. Allow all users. You will see that after it is installed that the printers are already shared and ready to go.

---

### Post by masonfoley on 2008-08-24
> **linux6994 said:**
> Printing from Windows to your Ubuntu is really easy to setup and use. My family all have XP & Vista laptops and I run Ubuntu on my dektops sharing printers and external usb storage drive. 

Install system-config-samba and set up the access on it for all to use. Its easy. Allow all users. You will see that after it is installed that the printers are already shared and ready to go.

Not so fast...  :)

I am not able to get most apps from Vista to print.  Firefox, oddly, will print but MS Office Apps, Adobe Acrobat Reader, MindMapper, Paint Shop Pro, etc. will not print to this HP Laserjet 1100.

It's as if the print job gets swallowed up in the ether.  I never see the job spool on the Linux side however I don't see any errors on the Vista side either.

Printing from XP boxes appear to never have any issues.

My post on it is here:  [http://ubuntuforums.org/showthread.php?t=899616](http://ubuntuforums.org/showthread.php?t=899616)

---

