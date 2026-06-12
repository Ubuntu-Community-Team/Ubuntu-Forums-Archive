---
title: "installing wifi drivers block wifi (insteado of enhancing it)"
date: 2022-12-30
forum: Networking &amp; Wireless
---

### Post by ksso on 2022-12-30
Hi. in a  hp AMD Ryzen 5 5500U by default the wifi is working but is too slow
last week I could install the drivers through gui of ubuntu
however, I have tried new installations of ubuntu and know when I install the driver, it blocks the wifi instead of enhancing it (if I deactivate through gui and restart the wifi is recovered but is pretty slow)
by the way, the wifi card is working well through windows, 
Indeed it looks like some new builded package doesnt allow any more to install the driver like before
please help

thank you very much

---

### Post by jeremy31 on 2022-12-30
Moved to Networking
What is the result of this command in terminal ```
mokutil --sb
```

---

### Post by ksso on 2022-12-30
it showso if secureboot is enabled or disabled., in  both cases there is no wifi with the driver mounted

indeed *sometimes* at installation., along side with the check option of third parties drivers appears an option for a password to secure  boot (8 digits)., but not always appears
in that cases after mounting for first time the driver at restart it asks a password, in  the past it worked but now not

---

### Post by jeremy31 on 2022-12-30
If you want to use the rtl8821ce-dkms driver, you have to disable Secure Boot and install rtl8821ce-dkms and reboot.  Since it is not signed like the kernel driver, Secure boot will prevent it from loading and I would bet that installing the rtl8821ce-dkms prevents the kernel driver from loading and that is why you had no driver loading

---

### Post by ksso on 2022-12-31
Hi, 
I have tried unchecking and checking the secure boot changing after first installation of drivers and didnt work
I installed ubuntu with secure boot and that is when ask a password after installing, enrolling a mok (with secure boot checked, the wifi is better, but not like if driver were mounted)
however checked or unchecked the driver isnt mounted like before, and when is mounted (or gui checked), it *blocks* all wifi

---

### Post by ksso on 2022-12-31
Hi
Finally could use it
at a dual with w11 and enabled the secure boot )(to aslk the password enroll mok)
so., it  seems  that if internet fails while installing the driver  the  mok  will not  recognize it (**difficult**, bug?)
also needed to bypass the first mok (linux kernel driver) 
idk if dual installation also participate or  is a factor
thank you!

---

