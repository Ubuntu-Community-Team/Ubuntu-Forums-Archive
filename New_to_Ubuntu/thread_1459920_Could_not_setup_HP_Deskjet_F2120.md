---
title: "Could not setup HP Deskjet F2120"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by nandinibhaduri on 2010-04-22
I am on 9.04. I have a printer installed in a Windows network. Went through the steps of setting up by samba. First problem I faced was - when I had to choose the driver - there was nothing for the printer model I had - HP Deskjet F2120 All-In-One. I tried F2100 - did not work. Googled - tried D2300. Did not work. When I am trying to Print Test Page - it says that the print has been successful but actually nothing was printed.

Any suggestions?

---

### Post by nandinibhaduri on 2010-04-22
I plugged the printer directly to my laptop usb, it got installed automatically and its printing fine. But not from the network with the same driver setup and other properties settings.

---

### Post by Dezemerel on 2010-06-01
Hi nandinibhaduri,

Did you finally  solved your problem? Im having the same issue with Lucid:

Using the f2100 drivers is ok if the printer is directly plugged in the printing pc, but it doest work if I try to print when its plugged in the windows machine.

Also if some other forum member could help, Id be grateful.

---

### Post by pricetech on 2010-06-01
So this is entirely a local printer, not a network printer ??  The original post is not clear on that, but implies it's a network printer.

---

### Post by Dezemerel on 2010-06-02
Yes, its a local printer.

It works fine if its plugged directly in the ubuntu computer, however, if I try to print when its connected in a windows machine, the printer doesnt work.

Viewing the printer queue in the windows machine, I see that a "Low level document" is queued for printing, however it isn't printed.

Note: Printing from another windows machine to the windows machine hosting the printer is fine, so the setup appears to be properly done...


Thanks for your reply·

---

### Post by Fawkat on 2010-06-09
[SIZE=3]I have the same problem with my HP PSC 1310 printer connected to a windows machine. The printer shows the job but it does not print it. 
[/SIZE]

---

### Post by sydbat on 2010-06-09
Personally, I was never able to get any printer to work if it was coming from a Linux box and going through a Windows box. The other way around was never a problem.

However, in Windows, you have to enable the "unix" driver to print from non-Windows machines. Not sure exactly how to do it (have not used Windows for 3 years), but it *might* be something like this describes - [http://aplawrence.com/Unixart/ldsprintwindows.html](http://aplawrence.com/Unixart/ldsprintwindows.html)

---

