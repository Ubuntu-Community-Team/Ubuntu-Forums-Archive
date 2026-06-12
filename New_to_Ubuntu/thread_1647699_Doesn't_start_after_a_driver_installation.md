---
title: "Doesn't start after a driver installation"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Ramy89 on 2010-12-17
Hi,I have a notebook with dual-boot, windows 7 and ubuntu 10.10.
I have ubuntu in a different partition than windows,It was working fine  since I activated the broadcom STA wireless driver,it was present but  not active (I also activated nvidia driver).
The I selected restart to complete updates,and when I restart I find out  that after loading ubuntu's writing,instead of starting the GNOME  session I am in a sort of recovery mode.
It asks me the password,I log and it says:"Your cpu appears to be  lacking expected security protections.Please check your bios settings,or  for more information,run: /usr/bin/check-bios-nx --verbose".
Doing as it says I get:
"This cpu is family 6,model 37,and has capabilities but is unable to use  these protective features because the bios is configured to disable the  capability.Please enable this in your bios."
It also gives a link:  
[http://wiki.ubuntu.com/Security/CPUFeatures](http://wiki.ubuntu.com/Security/CPUFeatures)
But I don't have any idea of how changing that flag,I also tried  ctrl+alt+7 but it sticks at something like "enabling sensors" or  something like this,It blocks and GNOME doesn't want to start.
A solution would be to reisntall ubuntu,but if I reinstall will I get  that problem if I activate the driver again,or anyone know a solution to  change that flag to permit the execution of non-executable memory?
And since I work with C programming,will this get any problem with an  eventual stack overflow caused by the programs I compile and run?

Thanks previously for the answers (I hope).

---

### Post by Wobblybob on 2010-12-20
not promising anything here but can you tell us what netbook you have exactly and if you have managed to get into the BIOS setting yet usually pressing F2 or DEL or Esc during boot up.

---

### Post by Ramy89 on 2010-12-22
I have an acer aspire 5745G,yes I can enter boot menù by pressing f2.

---

### Post by Wobblybob on 2010-12-22
ok I've done a bit of a search and found this thread [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1592626[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1592626") looks like you need to get into your bios [as you say with F2] screen and amend the graphic mode to discrete graphics only.  

Good Luck

---

### Post by Ramy89 on 2010-12-23
Thanks man,I am now typing from ubuntu,thanks again :P

---

### Post by Wobblybob on 2010-12-24
excellent :p please mark thread as solved.

---

### Post by Ramy89 on 2010-12-24
> 
please mark thread as solved.

How to do this?

---

### Post by Wobblybob on 2010-12-28
Hi mate, check out the options under [Thread Tools] at the top of page..

Happy New Year

---

