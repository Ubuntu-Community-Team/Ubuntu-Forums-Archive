---
title: "Netbook very hot"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by randomafk on 2011-06-22
Hi,

I just installed ubuntu and am pretty pleased so far, but I'm having some difficulty trying to change the power management settings.

Right now, my netbook averages at ~65C according to ACPI as compared to ~30C before when i ran windows 7. I understand this may be a driver issue but my netbook had official support for opensuse so I would think it might be something else? (Unless I need to manually download the drivers)


My netbook is an hp mini 5102


Thanks!

---

### Post by 09061920 on 2011-06-25
My Acer Aspire One netbook runs 32bit Xubuntu and Fluxbox wm and it's usually at around 35C, whilst when I tried 64bit Ubuntu, according to acpi my average temperature stayed at around 55C.

Do you have Windows 7 dual booted with Ubuntu? Do you use 32 or 64bit Ubuntu?

---

### Post by Impute on 2011-06-25
You might try running "powertop". It will show what processes are waking up the CPU. If nothing looks suspicious, then you might want to search the forums for how to check the fan speed.

Powertop is a command line tool that needs to be run as root (so "sudo powertop"), but you can find and install it using Ubuntu Software Center.

---

### Post by josephmills on 2011-06-25
10.10 and lower system-->pref-->power management in 11.04 and up click on the ubutnu icon and enter power in to the search bar there you go

also could we see a screen shot of Htop 

```
sudo apt-get install htop 
``` then then just enter ```
htop 
``` and take a scrren shot and add it as an  attachment

---

