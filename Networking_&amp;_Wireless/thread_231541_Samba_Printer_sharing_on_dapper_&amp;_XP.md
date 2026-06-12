---
title: "Samba Printer sharing on dapper &amp; XP"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by disector88 on 2006-08-07
I have an HP DeskJet 3740 printer connected to my desktop running dapper and it works fine. There are 2 XP laptops in my household which I want to share the printer with. The printer is currently visible from 'My Networking Places' when I navigate to my desktop host from the XP boxes. However, when I try to print, I get the "could not find suitable driver" error message. 

From the  guides,etc. I read online,
[http://linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/IX.CUPS-Samba/IX.Samba-HOWTO-Collection-Chapter-7.html](http://linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/IX.CUPS-Samba/IX.Samba-HOWTO-Collection-Chapter-7.html)

[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)

I understand that I have 2 options - 
(1) to install CUPS PPD, and download & install Adobe postscript driver on the XP clients. 

(2) Set up a "raw print queue" using CUPS on the server, and set up the XP boxes by adding the printer by adding it as a URL & installing the driver from the driver CD that came with the printer.

I am leaning towards option (2) because I do not want to have to have the clients go out and do some downloading themselves. I had these questions:
 - Using option (2), is it possible to host the XP drivers (currently on CD) on the ubuntu server, so that I can auto-push the driver (via CUPS) when the XP client finds the printer? If so, how? 
 - How do I verify whether the printer is being shared as a "raw queue"?

---

### Post by sitedesign on 2006-08-07
The easy way is indeed option2

Add the printer in cups as a raw printer queue (simply add a printer - and select the raw driver). Then on the XP clients connect to the printer and install the windows driver when prompted which driver to use.

Hope that helps.

Post back and I will check the folow-up in a few days and add info if required.

---

### Post by disector88 on 2006-08-08
Thanks.

So is it possible to push the driver from ubuntu when XP prompts for which driver to use?

---

### Post by Mooie on 2006-08-08
I have a HP printer connected to an XP box which is networked with my ubuntu (Kubuntu 6.06 dapper 64-bit) box.  The Xp box has file and printer sharing enabled, how do I access it from my linux machine?

---

### Post by sitedesign on 2006-08-08
Mooie
you need to set-up samba on your Kubuntu box then use the samba client utilities (I think you have some nice GUI ones in Kubuntu) to connect to the printer.

---

### Post by sitedesign on 2006-08-08
disector88
Yes that is possible, it needs a bit of fiddling with your samba config to do it. I find it easier to just connect to the printer on the linux box from the XP client then when XP prompts for the driver just use the CD or downloaded driver.

If the printer driver uses some silly install program then just install it as if it is local on LPT1 then another printer by connecting to the linux shared one and use the newly installed driver which should now show up in your printer drivers list in XP.

That should get you going.

---

### Post by disector88 on 2006-08-10
Thanks,

What do I need to fiddle with in the samba.conf file to push the XP drivers of the printer ?

---

### Post by sitedesign on 2006-08-11
This bit

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

---

### Post by disector88 on 2006-08-23
Thanks for all the input!

I finally went with the adobe post script driver option.

---

