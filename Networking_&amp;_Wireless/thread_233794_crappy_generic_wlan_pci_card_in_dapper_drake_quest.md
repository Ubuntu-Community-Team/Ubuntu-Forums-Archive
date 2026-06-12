---
title: "crappy generic wlan pci card in dapper drake question."
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by unixevangelist on 2006-08-10
hello i would like to know if there is a guide for installing wlan cards in general...and if so is there one for trendnet pci wlan cards....does one have to install driver then put the card in the pci slot like i have to for Windows? in windows i had to take the card out install driver put it back in the pci slot and set it up to connect to router....

---

### Post by unixevangelist on 2006-08-10
trendware tew-pci
thats what it is

---

### Post by unixevangelist on 2006-08-12
does one have to install driver then put the card in the pci slot like i have to for Windows? in windows i had to take the card out install driver put it back in the pci slot and set it up to connect to router....
Edit/Delete Message

---

### Post by Bezmotivnik on 2006-08-12
The important thing is what **chip** is on the card.  A lot of generic cards are sold under the same name even after they've been contract-built with entirely different circuits.  Device brand and model names are often meaningless.

If the card you have already has that chip supported in Ubuntu (and I don't know where you'd find that list), at least in theory all you have to do is power down your system, turn off the power supply switch and physically install the card, then power back up and boot.

Then you have to determine if the card was automatically installed.  How you do that may vary a little bit determined by which chipset it is and how Ubuntu named the device.

---

