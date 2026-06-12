---
title: "Migrating Install from 1 pc to another"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by wilryt2 on 2008-12-07
Hi~

I have a very unique problem, and am hoping someone here might know the best route to my end goal.   

I have a Micros Eclipse System Unit (point of sale register type machine) that I would like to load up with ubuntu.  For some reason, the machine will NOT boot from USB (be it usb thumbdrive or usb cd/dvdrom), and there is no floppy or cdrom drive built in.  Is there a way to install ubuntu on a hdd in a different computer, and then migrate the physical drive to the Micros with the install still intact?  Thanks in advance.

~Will

---

### Post by jamesrl on 2008-12-08
See installation without a cd options here:  
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
I wouldn't try your suggested method, as I don't think it would work (different hardware being autodetected).

---

### Post by Paqman on 2008-12-08
> **wilryt2 said:**
> Is there a way to install ubuntu on a hdd in a different computer, and then migrate the physical drive to the Micros with the install still intact?  Thanks in advance.

Yep, that should work. It's worth a crack anyway.

---

### Post by earthpigg on 2008-12-08
> I wouldn't try your suggested method, as I don't think it would work (different hardware being autodetected).

it autodetects hardware the first time you boot after you install...

1. install onto that hd
2. once done, instead of restarting go ahead and shut it off
3. move hd to other computer
4. start up, ubuntu autodetects for the first time at this point


think that'll work?

---

### Post by Mattventura on 2008-12-08
It should work with just moving the disk over. I have done that before even after it autodetected the hardware. The only quirks are that it will give the new network devices new names and if you have anything graphics card or screen related in your xorg.conf you will want to reconfigure that.

---

