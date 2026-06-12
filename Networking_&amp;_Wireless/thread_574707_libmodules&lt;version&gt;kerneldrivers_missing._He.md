---
title: "/lib/modules/&lt;version&gt;/kernel/drivers missing. Help"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by Darvenkry on 2007-10-13
/lib/modules/version/kernel/drivers/  . The whole file is missing. Cant remember exactly what i did as i had compiled a new kernel and done some other things before restarting the computer. After i restarted, in the boot up screen it appeared:

Warning: Could not open /lib/modules/version/kernel/drivers/xxxxx.ko
               No such directory exists

The modules missing were USB, sound and ethernet.

When i got into the system, i used the browser to have a look at the directory and its totally empty.
Now i cannot use the internet, 

ive tried    ifconfig eth0 up   but it just gives unknown interface   (internet was working before all this happedened)

Running Gentoo 2.6.16 on a :

Pentium 4
Ethernet:  Realtek Controller

Since then i have tried recompiling the linux kernel to 2.6.19 and the /lib....../kernel/driver and still nothing. One thing i have found is all the files that were in that directory except it is in /usr/src/linux/drivers  but all have  .c  or .h   instead of    .ko

Is there someway to build the  .ko files again???

---

