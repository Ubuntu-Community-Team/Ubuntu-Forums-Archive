---
title: "ATI Drivers"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Token B. Luntz on 2010-03-24
I have recently installed Ubuntu 9.10 on my pc. I have an ASUS EAH5670 Graphics card.
Its amd and i cannot get it to work in Ubuntu. Last night i was able to see 1600 x 1200 just fine. But after crashing my system (im a noob at Linux) i had to reinstall ubuntu. 

I dont know how i had it working but in the right bottom corner of my screen i had a watermark that said Unsupported AMD Hardware. But atleast my system wasnt 800 x 600 on a 32" screen.

I have read that some people have had some success, atleast getting a higher resolution, with using "radeon" drivers over the  "fglrx" proprietary ones. How do i find the "radeon" drivers they are referring to?

any help would be appreciated

---

### Post by cogier on 2010-03-24
Follow this link it may help [http://www.tomshardware.co.uk/forum/283121-15-asus-eah5670-linux-drivers]("http://www.tomshardware.co.uk/forum/283121-15-asus-eah5670-linux-drivers")

---

### Post by jaycee23 on 2010-03-24
I am using ATI driver 10.2 for my ATI graphics card (you can see which one in my sig).
Instructions for installation are on the AMD website

It works well apart from an issue in compiz which means it reverts back to none in visual effects every time you log on

---

### Post by halitech on 2010-03-24
which video card do you actually have? Depending on the model, there may or not be an ATI driver for you to install and it might be a case of creating and tweaking an xorg.conf file for you

---

### Post by Mark Phelps on 2010-03-25
There were lots of problems with the Catalyst 10.2 drivers, to the point that some folks had to go back to 9.12.

ATI just released their Catalyst 10.3 drivers.

Suggest you install them.  They may have fixed the problems in 10.2.

---

### Post by jaycee23 on 2010-03-26
Just installed 10.3 - removing 10.2 was a bit hairy - had to go into recovery mode and install from there but it worked!  :p

Anyone know how to check which version is installed?

Also so far seems more stable that 10.2 with regards to compiz

---

