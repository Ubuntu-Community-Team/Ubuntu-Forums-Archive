---
title: "HP printer driver"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by jwalters on 2011-01-14
Hi . . . . just purchased an HP deskjet 2050 printer. Does anyone know how to install a driver for this thing. I did all the regular stuff, but it seems I need a generic one.

I downloaded a generic driver to my desk top, but can't get it to open.....help?

I'm Ubuntu 10.04

---

### Post by Kirboosy on 2011-01-14
Did you try adding the printer using the Ubuntu CUPS service?

System-->Admin-->Printing

---

### Post by jwalters on 2011-01-14
yeah I did all the usual stuff, but when I downloaded a driver from HP it said

Could not open the file /home/jim/Desktop/hplip-3.10.9.run.

---

### Post by Kirboosy on 2011-01-14
You shouldn't have to download the driver. Ubuntu should be able to fetch the driver automatically.

I'm gonna download the package and see if there are any requirements needed for the package installation.

Actually you can try installing the package via Synaptic.

(System --> Admin --> Synaptic Package Manager --> "hplip" in the quick search box.)

---

### Post by JC Cheloven on 2011-01-14
> **jwalters said:**
> yeah I did all the usual stuff, but when I downloaded a driver from HP it said

Could not open the file /home/jim/Desktop/hplip-3.10.9.run.

So you installed manually hplip 3.10.9? 
The [main site]("http://hplipopensource.com/hplip-web/supported_devices/index.html") is down in this very moment, but I found a [reference in debian lists]("http://www.linux-archive.org/debian-user/475981-hp-dj-2050-a.html") as for your printer being supported since hplip 3.10.6 (the previous version)
> HPLIP 3.10.6 Release

Added Support for the Following New Printers:
---------------------------------------------------------------
- HP Deskjet 2050 j510 All-in-one Printer

---

### Post by jwalters on 2011-01-14
I downloaded hplip-3.10.9. off the site, but now that it's on my deskto0 thats as far as i can go with it as it refuses to open

Could not open the file /home/jim/Desktop/hplip-3.10.9.run.

In synaptic they don't have this version and I'm pretty sure that this is what it takes to run the printer......... I know how to use the terminal, i don't know the commands :-(

---

### Post by jwalters on 2011-01-14
I downloaded hplip-3.10.9. off the site, but now that it's on my deskto0 thats as far as i can go with it as it refuses to open

Could not open the file /home/jim/Desktop/hplip-3.10.9.run.

In synaptic they don't have this version and I'm pretty sure that this is what it takes to run the printer......... I know how to use the terminal, i don't know the commands :-(

---

### Post by JC Cheloven on 2011-01-14
Mmmm... I guess you should uninstall 3.10.2 (the default in lucid), before attempting to install 3.10.6 (which should suffice for you) or 3.10.9. 

I was about to suggest you to enable backports in foftware sources, but I tried myself and it didn't help: only 3.10.2 appears. Also you can try to find a ppa for lucid which has the updated hplip (just visited that and the whole thing seems to have changed, I don't find myself a suitable ppa).

Finally: you could consider upgrading to maverick. It has 3.10.6 as default.

---

### Post by jwalters on 2011-01-15
thanks . . . . I'm upgrading now

---

### Post by Kirboosy on 2011-01-18
Bump. Did the Distro update fix your issue?

---

### Post by oldos2er on 2012-03-13
Closed. Please do not bump old threads.

---

