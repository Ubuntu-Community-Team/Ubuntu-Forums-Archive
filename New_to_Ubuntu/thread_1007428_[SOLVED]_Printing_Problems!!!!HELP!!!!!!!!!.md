---
title: "[SOLVED] Printing Problems!!!!HELP!!!!!!!!!"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by DizzyEwok on 2008-12-10
Hi,
I have been using ubuntu for about 10 months now and have had no problems whatsoever apart from that I have never been able to print!
So far I have coped by transferring the files by e-mail and printing them on one of the computer's that is connected to my printer.
It has now come to the stage where I have a file which is "ubuntu-only" and I cannot print it!!!
Any ideas on how I can connect to my printer?
I have a hp-deskjet and it is connected to 2 windows computers on the network. They can both print via the network but I cannot.
About 6 months ago I tried to connect and it seemed to work but when it came to printing it simply said "Processing" and never printed.
I have tried many times since then to no avail...

---

### Post by Michael.Godawski on 2008-12-10
I guess you have to set up a samba share... but I am not an samba expert myself:

[https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers](https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers)

---

### Post by silverglade00 on 2008-12-10
What is the model number of your printer? Also, try to open up Synaptic and install HPLIP. It's the HP software and it does a pretty good job of locating and configuring your printers for you. As long as they are HP.

---

### Post by txwooley on 2008-12-10
Do you have cups installed?  I think this is the printer driver.

---

### Post by DizzyEwok on 2008-12-10
> **Michael.Godawski said:**
> I guess you have to set up a samba share... but I am not an samba expert myself:

[https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers](https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers)
Score That worked!!!!!!!!Thanks sooooooooo much!

---

