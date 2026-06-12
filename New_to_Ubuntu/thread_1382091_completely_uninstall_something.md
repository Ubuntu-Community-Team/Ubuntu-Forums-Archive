---
title: "completely uninstall something"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-01-15
hi, how do you COMPLETELY uninstall wine from your system

yes, COMPLETELY

i think theres a bug in it preventing it from opening windows apps when i right click on them and its getting on my nerves

so i want to delete it from my system

and also can you teach me how to reinstall a good version of it without any errors :)

:KS:KS:KS:KS:KS:KS:guitar:

---

### Post by doas777 on 2010-01-15
sudo apt-get purge wine

purge is differant from remove, in that it cleans up config files too.
after running it, look in your home folder, for a folder called .wine (it is hidden, so ctrl+h) and if it is still there, destroy it.

then just 

sudo apt-get install wine

---

### Post by marshmallow1304 on 2010-01-15
```
sudo apt-get --purge remove wine && sudo apt-get --purge autoremove
```

Go [here]("http://www.winehq.org/download/deb") to get the latest version which usually works better than the version from the Ubuntu repositories.

---

### Post by vnpifhf on 2010-01-15
right, when i right click on me windows hard drive and find a program under program files, i double click and it gives me an error, and when i right click and click on open with wine it does absolutely nothing!!!

and this is becoming a pain!!!!
also i did the command via alt=f2 and when i right click i still get the option of open with wine even after putting the command for uninstalling it and its driving me crazy grr lol

also i have another issue with this ubuntu as you will see with the screenshot below
...

[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/Screenshot.png[/IMG]

for above ^ ^ ^ why do these random things come on my desktop when i havent put them there?!?!

[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/Screenshot-1.png[/IMG]

for above ^ ^ ^ what are all these discs for especially the first one which says 1gb??




first of all i want to COMPLETELY remove wine/snaptic package monitor (are they the same thing?)

because i have done the purge thing by command prompt but when i right click on win apps its still there!

---

### Post by vnpifhf on 2010-01-15
bump

---

### Post by vnpifhf on 2010-01-15
bump (im goin bed soon )

---

### Post by howefield on 2010-01-15
I think you have wine all wrong.

It won't help you open programs already installed inside your windows partition/disk.

Wine is intended to help you install windows executables inside linux.

---

### Post by vnpifhf on 2010-01-15
no i am on ubuntu and have 2 drives, the linux part and the vista part, i am going into the vista partition hard drive in ubuntu and trying to open microsoft office 07 lol

i have even tryed downloading windows live messenger and using wine to upen it but it will not work after i right click it, i think im using an unstable version of it and want to completely uninstall it but dont know how to :/

and reinstall it with a more stable version without bugs

what i am trying to concentrate now on is how to uninstall it lol!
help!!

---

### Post by Sir Jasper on 2010-01-15
If you want Office 2007 use Vista. 

Good night and some may say lol (lots of love) to you too.

---

### Post by vnpifhf on 2010-01-15
oh lol i shall not be going to bed for another couple of hours
and the other thing is i want to phase vista alltogether

i dont like it and wanna forget about it lol!

just answer me questions lol


too much lol i know lol

---

### Post by Cheesemill on 2010-01-15
If you use the latest version of wine from [here]("http://www.winehq.org/download/deb") instead of the one supplied with Ubuntu then Office 2007 works fine. You have to run the installer in Ubuntu though, not try to use the copy that's already installed on your Windows drive.

---

### Post by doas777 on 2010-01-15
wine will not help you run win apps on your windows drive. it will allow you to run windows apps installed into ubuntu using wine though.

---

### Post by mattbutsko on 2010-01-15
to go into detail, there's stuff on Windows that office will need to run properly that wine can't really use.

Like others have said, if you want Microsoft Office, go to Microsoft Windows. We'll use OpenOffice.

---

### Post by kenuf on 2010-01-16
Jahangir,

The things that appear on your desktop.  Those appear to be drives that got mounted.  The 3 connect looks like a CD or DVD drive and the others are partitions of drives that you have accessed this session.

The Windows partition would likely be the Acer (guess), and the 1.1 GB is likely some removable media (Memory card in a reader or USB flash drive?).

They will likely disappear upon reboot, or if you are done with the resource you can right-click on them and click Unmount.

On the second screenshot, it appears that Ubuntu has detected a multiple card reader, perhaps built in or connected via USB.

---

