---
title: "Problem installing"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by lepel on 2009-07-10
I'm trying to install Ubuntu 9.04. I downloaded the file, checked the md5 hash, mounted and burned to a cd: it all worked. But when I reboot my laptop, with windows xp home, Ubuntu won't install. I get the screen where you choose a language, then I get the main menu. Every option I choose, Install Ubuntu, Try Ubuntu without installing, Check Disk, fails. I get a few flashes and the screen turns black. It stays like that untill I manually
 turn off my laptop.
What is wrong??

---

### Post by IHeequ5i on 2009-07-10
Please post your system specs.

If check disk doesn't work, it sounds like your iso file was damaged - or maybe the burning process failed.

---

### Post by lepel on 2009-07-10
Pentium dual core 2,00 Ghz, 3 Gb RAM, 300Gb HD.
Could it make difference when I burn it to a cd in stead of a DVD?

---

### Post by IHeequ5i on 2009-07-10
DVD vs CD shouldn't make any difference - I burned it to a CD when I did my install two days ago.

Try burning to another CD and set your burner to the slowest possible speed.

---

### Post by Old_Grey_Wolf on 2009-07-10
lepel,

I've had problems with laptops that have CD/DVD drives that will not burn a CD/DVD at 4X speed. They show that they are actually burning at 10X no matter what speed I select below 10X. I have given up on CD/DVD installs. I now do installs from USB disks/sticks. See [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) for a program to create bootable USB disks. Not all computers can boot from a USB though.

I have Desktops that burn at 4X just fine. I'm starting to think that Laptop manufactures are including hardware that supports multimedia where some data errors are acceptable. That doesn't work with data/iso CD/DVDs.

Try burning the CD/DVD at 4X speed, and observe the actual speed that it uses. If it is above 4X, then I would recommend that you look into using a USB disk.

---

### Post by LewRockwell on 2009-07-10
***Note: this post is more for general reference and future viewers of this thread***

During the time it has taken you to read this thread, dozens of CD-ROM Drives have been discarded. You can't give them away. I have over a dozen here right now(mfg. dates vary from 2005 back to 1995).

So the optical drive part of this project should be at no cost to you.

The other part you'll need is one of these:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

[http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=features&subcategory=converter&category=converter](http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=features&subcategory=converter&category=converter)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

You should note that not only will this device work with ATA(IDE) and SATA hard drives(both 2.5 and 3.5) but it will also work with optical drives as well!

and, along with:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007](http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007)

and, depending on your budget, this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16899887102](http://www.newegg.com/Product/Product.aspx?Item=N82E16899887102)

or THIS:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007](http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007)

your next Newegg order should be a real technician's and hobbyist's treat!


****The reason I point out a simple, effective, and inexpensive solution to provide optical drive read/write ability where either no previous drive existed(netbooks) or where the drive in question has failed or is failing and cannot be easily replaced(laptops)...is because you can burn and pass out MANY more *nix distro CDs for the same costs associated with passing out thumb drives(not to mention the optical media being impervious to alterations/corruptions)***

.

---

### Post by lepel on 2009-07-10
> **Old_Gray_Wolf said:**
> lepel,

I've had problems with laptops that have CD/DVD drives that will not burn a CD/DVD at 4X speed. They show that they are actually burning at 10X no matter what speed I select below 10X. I have given up on CD/DVD installs. I now do installs from USB disks/sticks. See [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) for a program to create bootable USB disks. Not all computers can boot from a USB though.

I have Desktops that burn at 4X just fine. I'm starting to think that Laptop manufactures are including hardware that supports multimedia where some data errors are acceptable. That doesn't work with data/iso CD/DVDs.

Try burning the CD/DVD at 4X speed, and observe the actual speed that it uses. If it is above 4X, then I would recommend that you look into using a USB disk.
Thank you for this response. This is very helpful.

---

### Post by earthpigg on 2009-07-10
some burners, for some reason, also dont work well if you try to burn a bootable cd-r ISO (such as the ubuntu one) to a anything but a cd-r (such as a dvd).

---

