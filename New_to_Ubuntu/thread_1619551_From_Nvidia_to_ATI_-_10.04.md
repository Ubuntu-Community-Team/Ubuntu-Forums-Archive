---
title: "From Nvidia to ATI - 10.04"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by D3SI on 2010-11-11
I've got Nvidia 8600GT at the moment in my system....

I've just ordered **XFX HD 4870 1Gb ATi VGA Card** what drivers will I Need to install and remove to get this working properly?

Thank You

---

### Post by endotherm on 2010-11-11
officially, it is best to uninstall the proprietary nvidia driver before installing the ati card. its cleaner certainly. I have skipped it in the past, and it didn;t cause any problems that I am aware of, but who knows.

I would uninstall the proprietary driver via System -> Administration -> Additional Drivers (or Hardware Drivers), by selecting the enabled driver, and clicking 'disable'.
then reboot to clear the old driver, and promptly shutdown.

install your ati card, and boot up. once you are in, go back to Additional Drivers, and see if there is one for your ati card. there should be, so enable it, and your good to go. if you don't like the performance of the default proprietary driver, go to atis site and download their latest. this is a pain however, because every time you get an X or kernel update, you will have to reinstall their driver again. in lucid and maverick, the default driver has been pretty good for my 3870, so I haven't needed to install the ati one.

have fun, and good luck!

---

### Post by ccsCoder on 2010-11-11
> **endotherm said:**
> officially, it is best to uninstall the proprietary nvidia driver before installing the ati card. its cleaner certainly. I have skipped it in the past, and it didn;t cause any problems that I am aware of, but who knows.

I would uninstall the proprietary driver via System -> Administration -> Additional Drivers (or Hardware Drivers), by selecting the enabled driver, and clicking 'disable'.
then reboot to clear the old driver, and promptly shutdown.

install your ati card, and boot up. once you are in, go back to Additional Drivers, and see if there is one for your ati card. there should be, so enable it, and your good to go. 

have fun, and good luck!

If you intend on using Lucid, you'll end up getting disappointed. ATI/nVidia, both of these haven't launched any prop drivers yet for the version of X server that ships with Lucid. The open driver, isn't good.

---

