---
title: "Disable bluetooth"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by yamla on 2006-08-17
I would like to disable bluetooth on my laptop.  I can't do this in the BIOS.  I'd have thought adding:
"blacklist bluetooth"
(without the quotes) to /etc/modprobe.d/blacklist would have done it but when I reboot, I do lsmod | grep bluetooth and I find the driver has been loaded.  What am I doing incorrectly?

---

### Post by ComplexNumber on 2006-08-17
> **yamla said:**
> I would like to disable bluetooth on my laptop.  I can't do this in the BIOS.  I'd have thought adding:
"blacklist bluetooth"
(without the quotes) to /etc/modprobe.d/blacklist would have done it but when I reboot, I do lsmod | grep bluetooth and I find the driver has been loaded.  What am I doing incorrectly?
thats not necessary. go to Services in your main menu (you will find it in the Administration section). go down to bluetooth, click OFF bluetooth so that it doesn't run at boot time. then select the Stop button to stop the service. see screenshot:

---

### Post by yamla on 2006-08-17
This doesn't seem to work.  It stops loading the bluetooth daemon but doesn't prevent the bluetooth _module_ from being loaded.  It's this module that I think is causing me problems.

---

### Post by heikkitoivonen on 2007-10-21
Maybe this helps: [http://kaplan-myrth.ca/Main/DisablingBluetoothInUbuntu](http://kaplan-myrth.ca/Main/DisablingBluetoothInUbuntu)

---

