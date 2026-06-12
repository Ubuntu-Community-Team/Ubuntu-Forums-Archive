---
title: "new to Ubuntu, home network question"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by nihiilist on 2008-04-12
I just installed Ubuntu today and have a couple of quick questions:

I installed Ubuntu on my laptop and also have an XP home desktop with an second harddrive used for storage.  I want the Ubuntu machine to be able to map to the second HD so I can access photos, programs, etc that I store there.  Do I need Samba installed to get out to that other drive or is Samba only needed if you want a machine to be able to access the Ubuntu PC?  

I have a Dlink DWL G630 wireless card, should Ubuntu automatically recognize this card or are there more steps involved.  I can't test it right now because I am at work.

Finally I have an HP Photosmart printer attached to the XP machine set to share, I know in an XP LAN the laptop recognized the printer and worked without having to install drivers on the laptop itself, is Ubuntu similar to this or do I have to install seperate Linux drivers on the laptop (I assume I will have to but just wanted to check)

Sorry for the newb questions but the threads I searched didn't give me the answers on Samba that i was looking for.  So far Ubuntu seems to run much faster on the old laptop than XP did so I hope the networking part works out.

---

### Post by Iowan on 2008-04-12
> Do I need Samba installed to get out to that other drive or is Samba only needed if you want a machine to be able to access the Ubuntu PC? Samba client is already installed - Samba server must be installed to share files FROM Ubuntu.

> have a Dlink DWL G630 wireless card, should Ubuntu automatically recognize this card or are there more steps involved.I don't do wireless (yet), but you can check under the "Manual network configuration" icon (two monitors - upper right corner, near date/time) to see if it has wireless configured.

> ...is Ubuntu similar to this or do I have to install seperate Linux drivers on the laptop (I assume I will have to but just wanted to check)I think I had to install something to get my HP Laserjet 5 working.  Check under System>Administration>Printing.

---

### Post by warp99 on 2008-04-12
> **nihiilist said:**
> 
Finally I have an HP Photosmart printer attached to the XP machine set to share, I know in an XP LAN the laptop recognized the printer and worked without having to install drivers on the laptop itself, is Ubuntu similar to this or do I have to install seperate Linux drivers on the laptop (I assume I will have to but just wanted to check).

The HP drivers are already installed, but you have to setup your printer. HP does have good support for Linux so everything should work fine. To set up the printer to share with the XP machine follow this guide:

[https://help.ubuntu.com/community/WindowsXPPrinter?highlight=%28xp%29%7C%28print%29](https://help.ubuntu.com/community/WindowsXPPrinter?highlight=%28xp%29%7C%28print%29)

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

