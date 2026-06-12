---
title: "ATI card driver not getting installed"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by joe2005 on 2010-08-27
I have a dual boot system with Windows and Ubuntu 10.04 installed.Recently installed ATI Radeon HD 4500 AGP Card.With Windows there was no difficulty at all in installing drive for the card I am not able to install sucessfully in many attempts.Most of the time after installation of the card downloaded from ATI am getting no screen display.I request some guidance please

---

### Post by psavva on 2010-08-28
> **joe2005 said:**
> I have a dual boot system with Windows and Ubuntu 10.04 installed.Recently installed ATI Radeon HD 4500 AGP Card.With Windows there was no difficulty at all in installing drive for the card I am not able to install sucessfully in many attempts.Most of the time after installation of the card downloaded from ATI am getting no screen display.I request some guidance please

Go to the Menu and select System -> Administration -> Hardware Drivers.

You should find you graphics card in the list.

Click the Enable button, and Ubuntu should automatically install the drivers for you.

---

### Post by nitinkdhiman on 2010-08-28
Hi,
I tried to install ATI driver (on Ubuntu 10.04) in same fashion but now there is no display at all. Black Screen :(
I have Lenovo Thinkpad R400 with ATI Radeon 3450. It was earlier working fine with default driver.

any ideas
rgds
nitin

---

### Post by joe2005 on 2010-08-28
Tried System Hardware drivers.After activation "Found fglrx primary device section
 Unable to find any supported Screen sections.This is the situation.PLease I am desparately in need of advice.thanks

---

### Post by clhsharky on 2010-08-28
joe2005


Mixing fglrx installers (Ubuntu hardware driver)
and ATI's installer creates a pain, to use or uninstall.
Uninstall each fglrx with the same method used to install, before using the other.

Purging fglrx and returning to default OSS radeon driver before installing fglrx is recommended.
here
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Ubuntu hardware driver installer is the preferred way with kernel upgrade benefits. And adding (ppa:ubuntu-x-swat/x-updates) will give you latest fglrx driver.

Very good howto for fglrx drivers
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

After using ATI installer use
```
sudo aticonfig --initial -f
```
to create xorg.conf file
reboot 
Will also work with Ubuntu installer if not working correctly.


Sharky

---

### Post by joe2005 on 2010-08-28
Tried as suggested .Went well as far as packages installed.aticonfig command not found
lost the screen removed fglrx reinstalled mesa ati open source drivers, got the machine working.I finally realised that installing ati driver is a rocket science subject.thanks for guidance.

---

### Post by alphacrucis2 on 2010-09-01
> **clhsharky said:**
> joe2005


Mixing fglrx installers (Ubuntu hardware driver)
and ATI's installer creates a pain, to use or uninstall.
Uninstall each fglrx with the same method used to install, before using the other.

Purging fglrx and returning to default OSS radeon driver before installing fglrx is recommended.
here
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Ubuntu hardware driver installer is the preferred way with kernel upgrade benefits. And adding (ppa:ubuntu-x-swat/x-updates) will give you latest fglrx driver.

Very good howto for fglrx drivers
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

After using ATI installer use
```
sudo aticonfig --initial -f
```
to create xorg.conf file
reboot 
Will also work with Ubuntu installer if not working correctly.


Sharky

Cool. I hadn't come across the x-swat ppa before. Do they keep fglrx up to date with each AMD release?

---

