---
title: "Instructions on how to install a windows networked printer..."
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Devilham on 2010-04-17
I have an HP Officejet j3600 series printer hosted on a windows xp machine, set to be shared.  Ubuntu can see the device, but I seem to not have the correct drivers (prints a blank page).  Anyone have good step by step instructions for installing a printer and finding the right drivers for this printer?

---

### Post by MrWES on 2010-04-17
> **Devilham said:**
> I have an HP Officejet j3600 series printer hosted on a windows xp machine, set to be shared.  Ubuntu can see the device, but I seem to not have the correct drivers (prints a blank page).  Anyone have good step by step instructions for installing a printer and finding the right drivers for this printer?

Do you have HPLIP installed? If not, do so.

---

### Post by oldsoundguy on 2010-04-17
install cups printer drivers and then run the set up and select the driver you need. (in synaptic and the programs.)

---

### Post by Devilham on 2010-04-17
thanks for the responces, and I have made some partial headway, but have encountered a new problem.  My Ubuntu laptop and the printer are communicating, just poorly now.  After installing CUPS and that other one (hplips or some such thing), I now had the officejet 3600 series of drivers, so that's good.  The bad, is when I send a test page from Ubuntu, it leaves the Ubuntu Queue at about 105k, and ballons up to 7mb on the Windows machine.  I suspect it's a driver issue, and if so, I probably have an unsupported printer, is this a correct assumption?

---

