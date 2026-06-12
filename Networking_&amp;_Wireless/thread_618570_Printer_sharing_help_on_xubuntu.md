---
title: "Printer sharing help on xubuntu"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by dinonet on 2007-11-20
Hi, I know there are many threads about this and I've looked through tons and tons and I never seem to be able to find the right combination of things to get this working right. I have a xubuntu box that I hooked up an epson stylus color 880 printer on. I added it using CUPS and can get it to work there but there is nowhere that I can see to enable printer sharing. I've seen many posts that it's in system > administration > printing etc but I don't see that in my xubuntu menu. I can go to settings ? printing and add the printer there too. But still nothing about sharing. If I want to share the printer how do I install it on the xubuntu box first? Should I just connect it locally or add it using IPP? Also through CUPS I was able to set it up to print and could access it using localhost:631 but when I try to add this printer from a winxp laptop it never can find it. Should I be able to access the CUPS web interface from another machine on the network? If I go to <hostname>:631 it can't access anything. At first I thought my firewall was blocking but I disabled guarddog and the same thing happened. 

Sorry if this stuff has been explained before. I would appreciate any help on this. Thanks!

---

### Post by lintoon on 2007-11-20
Check out Samba to share your printer.

---

### Post by lintoon on 2007-11-20
Check this page:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by dinonet on 2007-11-20
Ok thanks, is this a better way than just setting it up as a network printer with CUPS only?

---

### Post by dinonet on 2007-11-21
> **lintoon said:**
> Check this page:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Ok I set up a samba share and can map the drive from my winxp pc. Can you point me in the right direction on how to allow all the windows pcs to access the printer? I can actually see the printer when I search for it in "search network printers" but it says Access denied can't connect. I don't know if I have a user set up correctly for this but the howtos I used got me nowhere. Thanks!

---

### Post by lintoon on 2007-11-22
FYI - CUPS is the unix printing system and Samba is used for sharing files and printers to smb clients (Windows).

I must hold my hands up before I go any further and tell you I'm not a linux expert, but the more information we get posted here the more chance you will have of getting a fix. 

Anyway, you say you can connect to the shared folders from windows so that must mean your users have been added correctly to samba.  Can you post the contents of your smb.conf file.  
It is located in the directory /etc/samba

It's been a long time since I set up my printer but I seem to remember I didn't add it by just selecting the printer icon either in Network neighbourhood or by browsing for a network printer in the add printer dialogue box.  This is probably not the fix but it's worth a try.

When you add your printer in windows select network printer and type in the url as follows:

[http://servername:631/printername](http://servername:631/printername)  

-where servername is the name of your ubuntu box and printername is the name your printer.

---

