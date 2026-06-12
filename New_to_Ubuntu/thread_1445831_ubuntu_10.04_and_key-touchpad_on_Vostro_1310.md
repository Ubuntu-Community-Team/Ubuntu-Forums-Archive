---
title: "ubuntu 10.04 and key-/touchpad on Vostro 1310"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by al.adab on 2010-04-03
hello

I've been on Ubuntu 9.04 (Dell Vostro 1310) after fixing a key-/touchpad issue (please see [http://ubuntuforums.org/showthread.php?t=1164008](http://ubuntuforums.org/showthread.php?t=1164008)). 

When Ubuntu 10.04 (stable edition) is available, I'd like to upgrade to it. Is it safe to assume that the above trick at will work with Ubuntu 10.04 too?

Thanks.

---

### Post by 1991sudarshan on 2010-04-03
the final release of 10.04 lts is on 29th of April! you got to wait!! otherwise you try the beta version of 10.04:D

---

### Post by ajgreeny on 2010-04-03
You could always try it but you will not have a menu.lst file to work on, but will need to edit the /etc/default/grub file to add those boot parameters:-
> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Red] i8042.reset[/COLOR]"
GRUB_CMDLINE_LINUX=""

---

### Post by al.adab on 2010-04-06
Thanks both. I'm looking forward to trying it out.

---

### Post by eocansey on 2011-06-15
Dear all,

I just installed ubuntu 11.04 on my Vostro 1310 laptop and noticed that the mouse touch pad does not respond. This is what I have done so far which still doesn't work. I edited the **"/etc/default/grub"** file by changing 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Red] i8042.reset[/COLOR]"

And this still does not solve the problem as it did for some in ubuntu 10.04 - lucid. Can anybody help.

---

