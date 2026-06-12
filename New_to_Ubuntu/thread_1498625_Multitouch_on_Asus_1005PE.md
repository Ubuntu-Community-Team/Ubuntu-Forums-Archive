---
title: "Multitouch on Asus 1005PE"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by makuab on 2010-06-01
How can I get multi-touch with 10.04?
also is there a way to make the fn keys work (i.e. Disable/enable wireless)

---

### Post by NUboon2Age on 2010-06-01
Here's some info about getting Multitouch to work in 9.1 on another model of Asus.  Maybe it will help.

[http://blog.mfabrik.com/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.mfabrik.com/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/)

---

### Post by drkages on 2010-07-15
> **makuab said:**
> How can I get multi-touch with 10.04?
also is there a way to make the fn keys work (i.e. Disable/enable wireless)

Did you get any progress with the multi-touch in 10.04 for your netbook.

---

### Post by martin.bartlett on 2010-08-09
FN keys are activated by adding "acpi_osi=Linux" (without the quotes) to the GRUB_CMDLINE_LINUX_DEFAULT variable value found in /etc/default/grub

Once done you must execute 

sudo update-grub2

and then reboot

---

