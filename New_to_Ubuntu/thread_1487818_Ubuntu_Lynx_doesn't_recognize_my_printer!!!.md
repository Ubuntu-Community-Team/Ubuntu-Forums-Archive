---
title: "Ubuntu Lynx doesn't recognize my printer!!!"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by jorgecarrillo150990 on 2010-05-19
Karmic worked great with this printer, but somehow, Lucid doesn't.
De ulusb (or something like that) command showed me that Lucid DID recognize my printer, but going to System>Administration>Printing shows an empty box.

Now, using the LiveCD, I could print the work I had to print. My laptop immeadiately recognized the printer, installed the drivers, everything worked like a charm.

I don't want to use the LiveCD anytime I want to print, so there must be a solution to my problem.

The Printer is connected to my laptop via USB port.

---

### Post by apjone on 2010-05-19
What is the printer make/model

---

### Post by jorgecarrillo150990 on 2010-05-19
Sorry, I forgot it's an HP PSC 1510 All-in-One

---

### Post by cogier on 2010-05-19
Have you installed HPLIP?

---

### Post by jorgecarrillo150990 on 2010-05-19
yes it is

---

### Post by cogier on 2010-05-19
Well I thought "mine is OK" but it wasn't. The HP printer had gone so I thought I would run through the HPLIP printer install routine as it said there was no printer (which is strange as it's been there for some time) but it could not find the PPD file.

I tried various thinks to no avail. So I uninstalled HPLIP from the Software Centre - REBOOTED (this is important) - Then reinstalled and I did not even have to get HPLIP to install the printer it was there just as it had always been.

Very strange.:confused:

Must be worth a try.

---

### Post by jorgecarrillo150990 on 2010-05-20
> **cogier said:**
> Well I thought "mine is OK" but it wasn't. The HP printer had gone so I thought I would run through the HPLIP printer install routine as it said there was no printer (which is strange as it's been there for some time) but it could not find the PPD file.

I tried various thinks to no avail. So I uninstalled HPLIP from the Software Centre - REBOOTED (this is important) - Then reinstalled and I did not even have to get HPLIP to install the printer it was there just as it had always been.

Very strange.:confused:

Must be worth a try.

Thank you!
This worked perfectly!
Weird bug eh?

---

### Post by daimaru on 2010-05-20
yeah ubuntu rules.. I still cant get my hp deskjet 6540 to work under windows 7 ... and guess what I will probably never get it to work, since its windows and you cant do **** to fix it. :)

---

