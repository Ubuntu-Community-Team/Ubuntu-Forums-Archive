---
title: "Redirect network printer to LPT"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by manudo on 2013-11-13
I have a shared printer, that works by CUPS system, but I need to redirect the printer because I need to print by the LPT port.
I've seen a net use command for Windows but it doesn't work in Ubuntu. How I can redirect the printer? Thanks. ;)

---

### Post by SeijiSensei on 2013-11-13
You need to run [Samba]("https://help.ubuntu.com/community/Samba") on the server to support Windows networking.

---

### Post by manudo on 2013-11-14
> **SeijiSensei said:**
> You need to run [Samba]("https://help.ubuntu.com/community/Samba") on the server to support Windows networking.

Well, I'm trying to do this with wine, my printer is working on a USB port in Ubuntu, I want to do that net use because I need that Wine recognizes that printer as a parallel or serial port.
Thanks for your reply.

---

### Post by SeijiSensei on 2013-11-14
You say you have a shared printer.  Is it connected to a server of some sort, or does it have native sharing code built in?  Since you were trying "net use" I presumed the printer was on a network server.  We need more details about your setup in order to help.

If the printer is connected to the computer itself, it should be recognized in Wine.  Do a google search for "wine access printer," and you'll get lots of help.

---

### Post by manudo on 2013-11-15
> **SeijiSensei said:**
> You say you have a shared printer.  Is it connected to a server of some sort, or does it have native sharing code built in?  Since you were trying "net use" I presumed the printer was on a network server.  We need more details about your setup in order to help.

If the printer is connected to the computer itself, it should be recognized in Wine.  Do a google search for "wine access printer," and you'll get lots of help.

Ok, I'll explain it all.

My printer is a CITIZEN CT-S801, it's installed in an Ubuntu PC, connected as an USB port and I use it with CUPS.
My main objective is that the printer can be recognized as a parallel or serial port in the Ubuntu computer because I need to be recognized as that "ports" in a Windows program in wine.

All of that is in one Ubuntu computer with wine. I googled and I saw that I have to share the printer to redirect, but the net use command doesn't work in Ubuntu.

If you didn't understand, I'll give more details. Thanks. :)

---

