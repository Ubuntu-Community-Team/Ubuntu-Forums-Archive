---
title: "WPN111 wireless adapter"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by ziadoz on 2007-01-25
I've got the drivers for my netgear wpn111 installed using ndiswrapper. It says the hardware is present, but the device doesn't appear to be lit up when plugged in, or show up in network devices? Am I doing something wrong?

---

### Post by Metaljaz on 2007-01-25
did you install the windows drivers based on the name of the card or drivers based on the chipset of the card.
What version of Ubuntu are you using?

---

### Post by ziadoz on 2007-01-26
I installed the drivers on the disk that came with the adapter (which is USB btw). I'm running Ubuntu 6.10 btw.

---

### Post by Metaljaz on 2007-01-26
ok you have to find the chipset of your card and then install the drivers for the chipset, still using ndiswrapper.

Try running the below command from the terminal window:
lshw

scroll to the bottom under *network. The product should be the name of the card and vendor should
be the chipset. Once the chipset is identified find the driver for it. Then install it with ndiswrapper.
You should then remove or blacklist the other driver installed. 

if you need help finding the drivers for the chipset post back.

---

### Post by axio720 on 2007-01-29
i have the same problem.  the thing is this adapter is usb so i doesn't appear in the *network section.  its in the usb section.  so should that change what we do to get the device working??  its just really frustrating posting and reposting the same output.  thats all.  i believe there is another driver(stated on the ndiswrapper site.) athfmwdl.inf  i think its the firmware but i believe it is required also.  the thing is i cant find my install disc for the adapter either.  so im lost.

thanks,
nathan

---

### Post by Metaljaz on 2007-01-29
It looks like you got as far as configuring the driver for ndiswrapper. Now you have to actually load the driver;

sudo depmod -a

This adds the ndiswrapper module to the kernel depmod. Then do;

sudo modprobe ndiswrapper

This loads the actual ndiswrapper module configured with the Windows driver.
Now that the module is loaded, do;

sudo iwconfig

You should see an entry for wlan0 with some output.

---

