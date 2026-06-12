---
title: "Unable to print to Windows 10 SAMBA shared printer"
date: 2019-04-04
forum: Networking &amp; Wireless
---

### Post by peyre on 2019-04-04
My wife leaves her computer on 24/7, so I made her computer our print server.  In the past, with Windows XP and 7, I could simply share her printer and then connect to it from my Xubuntu machines, no problem.  It always *just worked*.  However, when we bought her a computer upgrade several years ago (which came with an upgrade to Windows 10), I could no longer connect to her printer.  I've had to use sneakernet: save whatever-it-is to a flash drive as a PDF, and print it from her machine.

I can print over the network from her Windows laptop, and I can install the printer on my Xubuntu machines.  However it always fails to actually print to them, saying the share is inaccessible.  If I enter her credentials I'm able to browse to the printer share and select it, but the Verify fails and printing never goes through.  I don't understand what's going on here; anyone have an idea?

---

### Post by him610 on 2019-04-05
Is it connected with USB cable to spouse computer, or is it connected through your LAN?

---

### Post by peyre on 2019-04-06
Oh, sorry, should have clarified.  No, it's through USB.  The P1102w has wireless capability, but not ethernet.

---

### Post by peyre on 2019-04-09
Well, I haven't managed to solve the problem, exactly, but I've found a way around it.  The printer has wireless capability so I hooked it up temporarily via USB port and run **hp-setup** from the terminal.  To my surprise that let me set up the printer so I could print to it from my desktop, which doesn't have a WiFi card.  It must be that the signal goes through ethernet to my router and from there to the printer over WiFi.  I've just printed a page direct from my desktop for the first time in years.  Wonders never cease...

Now, Ubuntu users will also have to run the following to get hp-setup to work:

[FONT=Courier New]sudo apt-get install python3-pyqt4
sudo apt-get install python3-pyqt5[/FONT]

---

### Post by peyre on 2019-07-15
Humph.  Well, it set up fine, but it still wouldn't print.  Didn't think til now to come back and mention it, but I'm still stuck with printing to PDF, dropping it onto flash drive, and printing whatever-it-is on my wife's computer.  That works, but it's a very poor workaround for this issue.

---

### Post by peyre on 2019-07-16
How 'bout that?  The very evening I wrote the above, I seem to have managed to fix printing from *buntu to Windows 10.  It seems the key was to first install python3-smbc and smbclient in Synaptic.

---

