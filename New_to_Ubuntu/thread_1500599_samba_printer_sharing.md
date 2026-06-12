---
title: "samba printer sharing"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by amin1990 on 2010-06-03
I have set up canon imageclass mf6540 printer on eeebox using windows xp professional.  I enable printer sharing.  I cannot connect to that printer sharing from ubuntu.  I already have samba, but I don't know how to use it. So am I missing something?  I am a noob.:)

---

### Post by lrgmmc on 2010-06-03
i think you still need canon drivers for ubuntu.

---

### Post by ScottinSoCal on 2010-06-03
> **lrgmmc said:**
> i think you still need canon drivers for ubuntu.

You do. I found directions for it here somewhere, but I'm having trouble locating it again. The Canon support files I had to install started with "bj" - presumably for their old bubble-jet support.

Canon's printer interface isn't standard, and you have to have the drivers to support it.

---

### Post by Jerry N on 2010-06-03
Go to System>Administration>Printing
Select ADD on the "Printing - Localhost" menu
Select "Network Printer"
Select "Windows Printer Via Samba"
Select "Browse"
This should bring up a list of the active computers on your network.  Select the computer that has the printer connected.  Select the name of the printer and click on "OK".  Select "Forward".  A "Searching for Drivers" box should come up.  After that goes away a "Choose Driver" box should come up.  Select the brand and the model of printer.  Select the default driver.  At this point you should be able to printe a test page.  Worked exactly this way for me a few minutes ago from Mint 9 (Same as Lucid Lynx) although my print server uses Windows 2000, not Windows XP.

Jerry

---

### Post by amin1990 on 2010-06-03
Now you mention about bj supported files.  I look on the printer list.  There are a lot of bj drivers.  I don't know which one is for canon imageclass mf6540 printer.

---

### Post by Jerry N on 2010-06-03
> **amin1990 said:**
> Now you mention about bj supported files.  I look on the printer list.  There are a lot of bj drivers.  I don't know which one is for canon imageclass mf6540 printer.

At that point I can't be of much help as I don't know a thing about Canon printer models.  If your model is not listed, possibly there is a listed model that uses compatible drivers.  I have heard that Canon is not nearly as Linux friendly as HP.

Jerry

---

