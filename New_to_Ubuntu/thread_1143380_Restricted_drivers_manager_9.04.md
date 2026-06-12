---
title: "Restricted drivers manager 9.04"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by captpicard12 on 2009-04-29
Ok, I Know that this is a really stupid question, but I'm new to ubuntu and i was wondering, how do i access the restricted drivers manager?  I need it to install drivers for my ATI graphics card so I can turn on visual effects... if anybody can help with that, that would be awesome too :)  thanks!

---

### Post by taurus on 2009-04-29
System -> Administration -> Hardware Drivers

---

### Post by captpicard12 on 2009-04-29
thanks, is there any way to specifically download something from it? I mean a lot of people say on google they got the driver i need from there, but i can't find any options for that...

---

### Post by emarkay on 2009-10-05
You can download the Proprietary driver from AMD/ATI's website:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) 
but the "Restricted Driver" here is part of the Ubuntu Repositories - it is possible to get it separate, but you don't need to.

Sorry, just noticed your post...

---

### Post by lavinog on 2009-10-06
> **captpicard12 said:**
> Ok, I Know that this is a really stupid question, but I'm new to ubuntu and i was wondering, how do i access the restricted drivers manager?  I need it to install drivers for my ATI graphics card so I can turn on visual effects... if anybody can help with that, that would be awesome too :)  thanks!

What card do you have?
The restricted/proprietary (commonly referred to as fglrx) drivers dropped support for a lot of older cards in march 09.
You need to have a radeon hd2000 or newer to use the proprietary drivers.
If the restricted drivers manager doesn't show the driver, it probably doesn't support your card.

The driver in the repos is a beta version of the 9-4 (april-09) driver. The most recent driver is 9-9 (september-09), and 9-10 is due to be released in a couple of weeks.  Each version has its share of unique bugs, and newer versions are not always better.  Some versions work better for some users and vice versa.

the open source driver for ati cards should have 3d support for newer cards in ubuntu 9.10
According to this: [http://www.phoronix.com/vr.php?view=14223](http://www.phoronix.com/vr.php?view=14223)  the open source driver has some advantages over fglrx.

---

### Post by pablolie on 2009-10-06
My experience is that, left alone, it will eventually automatically detect the drivers you need and prompt you to download them, via an icon on the top panel.

---

### Post by Mark Phelps on 2009-10-06
> **captpicard12 said:**
> Ok, I Know that this is a really stupid question, but I'm new to ubuntu and i was wondering, how do i access the restricted drivers manager?  I need it to install drivers for my ATI graphics card so I can turn on visual effects... if anybody can help with that, that would be awesome too :)  thanks!

Follow lavinog's advice... 

If you're not being offered drivers in Hardware Drivers, then there is no restricted video driver available for your card/chip that works with your version of Ubuntu.  IF you download a driver and force its installation, you're most likely going to trash your display and then will be faced with having to remove it when you no longer have a working desktop.

---

