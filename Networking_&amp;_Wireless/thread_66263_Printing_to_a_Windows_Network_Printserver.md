---
title: "Printing to a Windows Network Printserver"
date: 2005-09-16
forum: Networking &amp; Wireless
---

### Post by Rick@aflac2 on 2005-09-16
New to Linux, setup 2 machines with Ubuntu 5.04 as a trial, they are part of a Workgroup network of about 10 machines running Win 2000 and XP pro. Linksys 54g wireless & wired router acting as the DHCP server, TCP/IP protocol. Both Linux machines have a local Laserjet 1100 configured and working. They both see the network and have an actine internet connection through it and they both see the printserver. I have tried everything I can think of to get them to print to the printserver/with no luck. Printserver is a Trendnet TE100 and the printers on it are a Laserjet5 on a parallel link and a Deskjet 952c on a usb link. The Lj5 & Djet952 drivers are installed on the linux machines. Status shows: printing   network host"IP address" is busy will retry in 20 seconds
Any help would be greatly appreciated as I have fooled with this for over a month. I would consider switching more over to linux if I could figure this out

---

### Post by mlomker on 2005-09-16
That's almost too much detail there.  Is the question how to print from linux to the network printer device that you have?  Does it support standard LPR printing or just Windows?

Almost all of the print devices at my office are HP-brand JetDirect interfaces and they work very easily...I just point at the IP address.

---

### Post by detochka on 2005-09-16
i had a similar problem and what solved My problems was:
System-> Administration-> Printing

Network Printer -> UNIX Printer
Host: ip address of the printer
queue: leave blank

It worked for me, try it!

---

### Post by mlomker on 2005-09-16
[QUOTE=detochka]i had a similar problem and what solved My problems was:
System-> Administration-> Printing

Network Printer -> UNIX Printer
Host: ip address of the printer
queue: leave blank

It worked for me, try it![/QUOTE]

Yup.  That's the LPR method that I mentioned.  If the device supports that then it's the easy way.

---

### Post by Rick@aflac2 on 2005-09-16
Thanks to all for the help, I will give it a try.!    Sounds like it should work

---

### Post by cvmostert on 2005-11-09
hi there, i also have a router with a print server, cant get it to work on windows or ubuntu! what a bummer... i can see the printer with the software given, but when i want to set it up in winxp, it hangs! and i have not gotten round to figure it out under linux.

i get the printer working as local printer on boath though.

what am i dong worong? i tried the lpr method. i have a canon s820

---

### Post by cvmostert on 2005-11-10
i figured out to get it working on the linux machine, but windows hangs on me... :-(

thanx fot the help you all

---

