---
title: "xxx-xxx-xxx Does Not Exist. Dropping"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Johnbouy on 2009-01-05
To A Shell!

Hi all. 3 days new on my new [--->EVEREX gPC3 i386- LINK To System Bought<---]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883118008") Ubuntu bought from newegg. This is my 1st experience w/ a linux system and absolutely LOVE what I saw before Ubuntu quit booting. Somehow, either in the update manager and/ or the version upgrade, something went awry. I've downloaded and attempted to install from the latest stable Ubuntu 8.10.x LiveCD and get this error on BOTH CD or no cd reboot:

> usplash: setting mode 1152x864 failed
usplash: Using mode 1024x768
Gave up waiting for root device. Common Problems:
    etc.etc.etc


Alert! /dev/disk/by-uuid/c8815cb6-c206-49c9-bae1-7bccc479208b does not exist. Dropping to a shell!


I am/was absolutely giddy over Ubuntu for both the simply fantastic OS of Ubuntu and wanting to learn linux (unix?) OS's.

What is the simplest or easiest way to remedy my problem or quickest fix for a Ubuntu idiot?

Thanks in advance and I really want to give this a try!

-John

---

### Post by Carl Hamlin on 2009-01-05
> **Johnbouy said:**
> To A Shell!

Hi all. 3 days new on my new [--->EVEREX gPC3 i386- LINK To System Bought<---]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883118008") Ubuntu bought from newegg. This is my 1st experience w/ a linux system and absolutely LOVE what I saw before Ubuntu quit booting. Somehow, either in the update manager and/ or the version upgrade, something went awry. I've downloaded and attempted to install from the latest stable Ubuntu 8.10.x LiveCD and get this error on BOTH CD or no cd reboot:




I am/was absolutely giddy over Ubuntu for both the simply fantastic OS of Ubuntu and wanting to learn linux (unix?) OS's.

What is the simplest or easiest way to remedy my problem or quickest fix for a Ubuntu idiot?

Thanks in advance and I really want to give this a try!

-John

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Oof. Tough break, there. How far into the CD boot do you get the error?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAkliJEUACgkQyLm4ydrABvcxdACbBhXynSb8n4UmkLWX408pMX0U
FtQAnj84nTo5p3KrYrXM5xDD4w7cDaDT
=LYSm
-----END PGP SIGNATURE-----

---

### Post by lazyart on 2009-01-05
Looks like the system is not even booting from CD (it's looking for a disk by uuid, and a LiveCD wouldn't do that).

Double check your BIOS settings to see if you are indeed booting from CD as the first choice.  Once the disk starts up, select Install Ubuntu and you're on your way.

---

### Post by Johnbouy on 2009-01-05
The only difference between the two boots, cd or no cd, is a > Boot from CD....

The bios has the Sony cd/dvd as priority boot device, or shows it listed anyways.

I get the Ubuntu splash screen on both instances but the same dos-style boot up I get those same messages. I had some failed upgrade errors on the update manager but still had Ubunto GUI up to try the GUI version upgrade. During that process (late into it and even on it's own reboot) is when it wouldn't boot. So I then went for the online CD and burned to a disk using powerISO/ nero burner...

Man I am depressed because my alternative is windows uuugh.

---

### Post by caljohnsmith on 2009-01-05
So are you saying that you get the same error whether booting the Live CD or booting the Ubuntu on your HDD? If so, how about booting your HDD, and when you get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of that line add:
```
rootdelay=120
```
Press enter to save the temporary change, and then "b" to boot. Please let me know if that makes any difference.

---

### Post by Johnbouy on 2009-01-05
Booted from HDD, chose the 1st Ubuntu (non generic) and followed your steps and got the same results  =(

I have nothing on it, as it is brand new, so any default restore or reinstall would be fine if that helps?

---

### Post by caljohnsmith on 2009-01-05
It seems suspicious that both the Live CD and your HDD Ubuntu install give you the same error. Have you made any changes to your BIOS between the time when Ubuntu booted OK and now that it doesn't? Have you ever tried booting a Live CD on that computer before, and was it successful or did you get similar errors? You might try downloading the Hardy Live CD and see if that results in the same behavior when you boot it, because that could give a clue whether the problem might be hardware/BIOS related or not.

---

### Post by Johnbouy on 2009-01-05
I did not see the Hardy Live CD download but did find the Wubi download and have no problem putting xp on it first then using Wubi. Dual OS boot works and would actually suit nicely if that is what Wubi allows?

All ears and open to any ideas, though I eagerly want to use Ubuntu - this is my mother's Christmas gift and she is a two-time stroke survivor and has difficulties with vision and dexterity. Ubuntu's super easy navigation and complete customization of it's environment made us both beyond giddy. You may want add that as a marketing feature because it is worth it's weight in gold for my mother.

Never had a successful CD boot and the version upgrade was done via Ubuntu GUI or overlay(?)  complete idiot here and thanks again!

---

### Post by lazyart on 2009-01-05
Put that CD in another machine and see what you get.  I think maybe the CD is not burned correctly or is corrupted.  Will the CD boot from another machine?  Or if the machine is already running, put the disk in and report back what you see?  A single .iso file or some files and folders?  If you see an .iso file on the disk then it was burned incorrectly....

---

### Post by Johnbouy on 2009-01-05
autorun on this XP box:

<hr>

[IMG]http://www.mygreenwood.net/ubuntu.jpg[/IMG]

<hr>

CD/DVD rom issues then?  Shall I try to stick my XP CD in the ubuntu machine?

---

### Post by lazyart on 2009-01-05
Ok, so the disk is burned correctly.  Hardware issue?  Sure, try booting the system with your XP disk, though I wouldn't recommend installing Windows so that you can install Ubuntu.

Do you have multiple optical drives on your linux box?  Have you tried the disk in each of them?

---

### Post by Johnbouy on 2009-01-05
Only 1 optical drive- changed up the BIOS and did get a boot disk error on the boot from cd option

I'll suppose it's the cd rom drive drivers? Might I try loading generic cd drivers? Don't know how with ubuntu though

would Wubi format/overwrite XP?

---

### Post by Johnbouy on 2009-01-05
Update:

Everex Tech Support, which has been superb so far, said to try the 8.04 Live CD as they have not upgraded to 8.10 on that computer model, gPC3, and that XP would not boot from CD necessarily anyways.

Standby for the 8.04 Live CD results...

---

### Post by lazyart on 2009-01-05
Sounds like hardware.  No reason why a 8.04 disk would work while 8.10 or XP won't.  I would have balked at tech support for suggesting that nonsense.

Have some fun.  Boot up your windows machine with the 8.10 disk, then go into LiveCD mode (try ubuntu without making changes...)

Plug in a thumb drive with 1 gb free and go to system>administration>create a usb startup disk.

once complete, plug that into your linux box and set BIOS to boot from it.  You should be able to install that way.

---

### Post by Johnbouy on 2009-01-05
Man I am liking this Ubuntu even more- Going to try exactly what you suggested!

Tech Support said sounds like hardware failure and to send it to them to fix or replace.


Trying your idea 1st then send back if all else fails.

Thanks for the help and will keep this updated as I imagine there are other Everex owners who might run into the same issue.

---

### Post by Johnbouy on 2009-01-05
No-go on the Live CD test drive/usb boot - my box is too old to pull it off. Sending their Box back. Thank you for that suggestion nonetheless!

---

