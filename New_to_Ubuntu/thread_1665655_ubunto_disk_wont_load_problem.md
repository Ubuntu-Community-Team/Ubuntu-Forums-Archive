---
title: "ubunto disk wont load problem"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by acein1 on 2011-01-12
hi im trying to load the "ubunto" cd from the computer active mag,i get as far as "try ubunto or install ununto" it then stops and nothing happens.
my p/c is running "pclos" as the _only_ o/s on my hardrive, the dvd burner is working fine, as is the disk,(ive tried it on other p/c,s) my p/c is "acer aspire" and i have gone into th bios using "f12" and changed the boot order to c/d, 
for the moment i just want to "try it" but ive also tried to install it , still no joy and help appreciated thanks:confused:

---

### Post by Rubi1200 on 2011-01-12
Hi and welcome to the forums :)

What are the specifications, especially RAM and graphics card?

From the terminal in PCLOS, post the output of the following command:

```
sudo fdisk -lu
```

Thanks.

---

### Post by Hippytaff on 2011-01-12
hi and welcome

I've found not clicking either option (install/try) and closing the window by clicking on x works when this has happend to me.

How much ram does the machine have?

---

### Post by acein1 on 2011-01-12
3 gb ram + 640gb h/d
the sudo command came back with something like "this will bE reported"

---

### Post by Hippytaff on 2011-01-12
so you can use the live environment? 

what causes the message to appear? closing the install/try window?

do you have an Nvidia/ati graphics card?

---

### Post by acein1 on 2011-01-13
sorry for delay in getting back.
nividia geforce 8200+ 3 gb rm  and 640gb h/d thanks

---

### Post by Hippytaff on 2011-01-13
Nvidia can sometimes cause problems because the driver needs to be installed. try this [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)
Then install the Nvidia driver by either dropping into commandline with networking or try (once ubuntu is installed) highlighting ubuntu in the grub menu, pressing e and changing 'quiet splash' to 'nomodeset' then ctrl+X to boot. Once your in you can install the Nvidia driver.

---

### Post by acein1 on 2011-01-13
thanks to all.
hippytaff,i tried again and again,and for some reason it worked,without updateing the "nivida  drivers",i am now dual booting with pclos and ubuntu 10.10 many thanks to all for the help.

---

### Post by Hippytaff on 2011-01-13
Excellent :-D

Glad you got it sorted!!!

Edit -> just one thing, can you expand on how you sorted it, for my curiosity and for others in the same boat? :-)

---

