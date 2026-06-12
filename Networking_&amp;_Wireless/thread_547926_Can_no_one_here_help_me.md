---
title: "Can no one here help me?"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Carn Thorn on 2007-09-10
I understand that everyone comes to help people here on their own free time and out of the kindness of their hearts but I can't seem to get any help at all with my problem.  I've asked two separate questions and neither got any response at all...I'm sure someone out there knows something about my problem...

I guess I'll just try again...

I have a smartlink modem that has the hardware ID PCI\VEN_163C&DEV_3052&SUBSYS_3052163C&REV_04

So can I get this working in Ubuntu?  I've looked at the dialup modem help topic and the links but I can't make heads or tails of what modem driver I'd need...can anyone help?

Oh and if I install drivers meant to allow Ubuntu online would I still be able to go online through XP?

Thanks in advance if someone helps me...

---

### Post by Anteaus on 2007-09-10
Is this an analog modem, or a broadband one? 

If the former, PCI modems are often heavily dependent on software for their operation, the card having no 'brains' in itself. Some PCI modems can be made to work in Linux, some not. The simple answer here is to find yourself a traditional (9-pin) serial-port modem; this will work in any OS as it's standardised kit. 

If broadband, I would strongly recommend an Ethernet modem/router instead. 

The Linux drivers (if you can find any) will have no effect at all on XP. The only possible disaster I can forsee here is if you're using Grub to boot XP, and the Linux partition gets totally nuked by a bad driver.  Not very likely though.

---

### Post by stchman on 2007-09-10
> **Carn Thorn said:**
> I understand that everyone comes to help people here on their own free time and out of the kindness of their hearts but I can't seem to get any help at all with my problem.  I've asked two separate questions and neither got any response at all...I'm sure someone out there knows something about my problem...

I guess I'll just try again...

I have a smartlink modem that has the hardware ID PCI\VEN_163C&DEV_3052&SUBSYS_3052163C&REV_04

So can I get this working in Ubuntu?  I've looked at the dialup modem help topic and the links but I can't make heads or tails of what modem driver I'd need...can anyone help?

Oh and if I install drivers meant to allow Ubuntu online would I still be able to go online through XP?

Thanks in advance if someone helps me...

Winmodems have very little support under Linux.  I recommend getting a hardware modem.  They will work under Linux.  You can try:

[http://www.linmodems.org/](http://www.linmodems.org/)

---

### Post by Carn Thorn on 2007-09-10
Thank you.  That was pretty much exactly what I was wanting to hear.  I'll be getting a new modem then and I'll be sure to check to see if it's the correct type.  

Thanks for the help.

---

### Post by nowshining on 2007-09-10
if you get a external modem then before you do anything download gnome-ppp

packages.ubuntu.com and do a search for it, from there install it - go into setup and select detect wait a bit and watch the lights on the external modem - as they should lite up, if so congrats you now have a working modem, input all the info. needed and  click connect.. however it's best to go into the setup and after the modem is successfully detected to go into options and uncheck minimize and check dock into notification area which when done dialing in will do just that now you can monitor the info. going in and out.. :)

---

