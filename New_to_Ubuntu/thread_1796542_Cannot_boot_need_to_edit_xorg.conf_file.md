---
title: "Cannot boot: need to edit xorg.conf file"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Darth_Sy on 2011-07-03
I was recently attempting to setup a dual screen by editing the xorg.conf file, but now when I restart, before I get to the logon screen, I get the message 'mountall: plymouth is disconnected'. I can get to the bios menu and boot from a usb however (as I'm doing right now). I'm 99% sure that the plymouth error is due to my meddling with the .conf file, and at this point I just want my computer back. Of possible note: I can still type after the plymouth error but so far no commands I've entered have sparked a response.

I'm right now running off of the 'Try Ubuntu' from a usb drive, and I notice that if I head to /etc/X11/xorg.conf, it's the same edited file, and in addition, the backup I created, xorg.conf_backup, is also there. However, as this is the from-boot-cd version, it looks like everything is read only or locked or something.

In any case, I want to solve this by finding someway to restore my xorg.conf to its former glory, meaning that I'm looking for a way to edit text files from 'outside' my system.

---

### Post by Darth_Sy on 2011-07-03
Solved the problem on my own; although it seems the GUI versions of the files were locked, I accessed the hd (listed as as external, as I was running from USB), then ran 'sudo cp' and put back the original.

Thanks for listening!

---

### Post by jtarin on 2011-07-04
Mark it solved Darth_Sy.

---

