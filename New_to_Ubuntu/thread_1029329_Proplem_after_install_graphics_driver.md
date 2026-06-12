---
title: "Proplem after install graphics driver"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Ghost M.D on 2009-01-03
Hi all

my proplem is after installing ubuntu 8.10 on my laptop

I check the drivers from Hardware drivers

& I find one for graphics & I activate it

after that I open an application (( Neverball & also in Movie player when I open a music track ))

the secren of the application was flashing which is very annoying

the rest are working without proplem

so what can I do for it 

I don't know what is my ghraphic card excpet it is ATI

my laptop is Toshiba Satellite A200-1J0

I wait for help

---

### Post by taurus on 2009-01-03
To find out your graphic card, just run this command from a terminal.
Applications -> Accessories -> Terminal
```
lspci | grep VGA
```
After you installed a driver for your graphic card, you did reboot, right?

---

### Post by Ghost M.D on 2009-01-03
Yes I reboot

the ubuntu ask for it

& the kind of my graphic card is 

01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]

---

### Post by taurus on 2009-01-03
Try turning off compiz to see if the fixes it.

System -> Preferences -> Appearance -> Visual Effects -> _N_one.

---

### Post by Ghost M.D on 2009-01-03
It fixed it

but the compiz was really cool

---

