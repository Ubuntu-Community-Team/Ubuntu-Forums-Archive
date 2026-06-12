---
title: "Printer not printing with ubuntu"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by joeshey on 2011-01-24
Hi I am new to Ubuntu and am having problems printing anything (test page etc) I have a canon pixma mp270 and am operating on ubunu 10.10 I try to print and the print info briefly states that it is processing then changes to completed. I have it set up as my default printer and can carry out a scan. Please help i feel like i am pulling teeth.

---

### Post by schwascore on 2011-01-26
I would guess this is a driver issue.

Without knowing which specific drivers you chose to use, I can't offer too much advice, but I would start by removing the printer and drivers and checking to see how other people got this printer working and looking for updated/different drivers.

[http://ubuntuforums.org/showthread.php?t=1244254](http://ubuntuforums.org/showthread.php?t=1244254)

---

### Post by nomko on 2011-01-26
For Canon drivers check these sites:
 
[http://software.canon-europe.com/](http://software.canon-europe.com/)
 
[http://support-au.canon.com.au/](http://support-au.canon.com.au/)

---

### Post by GerryB on 2011-01-26
I've downloaded .ppd files from these sites and everything worked well.
Just take note of the folder where the file is downloaded - mine is called "Download". Extract the files there. Log out and back in as root.
Move the .ppd file to your /user/share/cups/drv folder (could be /cups/drivers, depending on the version). Log out and back in under your user name. Put the printer on - it should take care of everything from there, detecting the printer, searching for the driver on your hard drive. Wait till you see the message "Printer is online". Press "Test page". Should be ready to go.

---

### Post by najRazaele on 2011-06-27
@GerryB

followed your instructions and got stuck @ moving the .ppd file... i cannot access the /user/share/cups/drv folder.. i was lacking permission... changed my account to admin.. still i the same problem.. "permission denied"... im new to ubuntu...

---

### Post by plucky on 2011-06-27
> **najRazaele said:**
> @GerryB

followed your instructions and got stuck @ moving the .ppd file... i cannot access the /user/share/cups/drv folder.. i was lacking permission... changed my account to admin.. still i the same problem.. "permission denied"... im new to ubuntu...

There is no /user folder,try /usr/share/cups/drv which does exist.

Good Luck

---

