---
title: "E: dpkg was interrupted, you must manually run 'dpkg"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by billysmash on 2010-08-11
What´s wrong with this?
Everytime I try to install any program by the add/remove tool, i get this error message
     .ExternalClass .ecxhmmessage P {padding:0px;} .ExternalClass body.ecxhmmessage {font-size:10pt;font-family:Tahoma;}   
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  E: _cache->open() failed, please report.

---

### Post by r_s on 2010-08-11
*dpkg --configure -a*  run this on the terminal and look for any errors.

---

### Post by billysmash on 2010-08-11
and I keep on getting this dpkg: requested operation requires superuser privilege

shouldnt I be able to, since im the only user running this OS?

---

### Post by r_s on 2010-08-11
use *sudo dpkg --configure -a,*, it will ask for your password and then continue.
It is asking for root privileges so that you don't mess up with your system,.

---

### Post by asavetheuniverseclub on 2010-08-13
when I run it goes wilf@asavetheuniverseclub:~$ sudo dpkg --configure -a
[sudo] password for wilf: 
Setting up linux-image-2.6.24-28-generic (2.6.24-28.73) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-28-generic
eval: 1: array_iscan-data=udev: not found
eval: 1: array_iscan-data=: not found
eval: 1: array_iscan-data=: not found
eval: 1: array_iscan-data=: not found
eval: 1: array_iscan-data=: not found
PANIC: Circular dependancy. Exiting.

---

### Post by YenTheFirst on 2010-08-15
> Setting up linux-image-2.6.24-28-generic (2.6.24-28.73) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-28-generic
eval: 1: array_iscan-data=udev: not found
eval: 1: array_iscan-data=: not found
eval: 1: array_iscan-data=: not found
eval: 1: array_iscan-data=: not found
eval: 1: array_iscan-data=: not found
PANIC: Circular dependancy. Exiting.


I've been getting the exact same error message, I'm still trying to figure out what exactly is wrong. Are you also using 8.04?

I've opened a bug report, but there's no response yet.
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/616479](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/616479)

---

### Post by YenTheFirst on 2010-08-15
I think I've figured it out!

I think the 'iscan-data' package has some sort of buggy hook that screws up update-initramfs.

if you "sudo dpkg -r <driver package> iscan iscan-data", you should be able to update the system. of course, this will uninstall your scanner driver.

coming across this bug gave me the idea:
[https://launchpad.net/bugs/602621](https://launchpad.net/bugs/602621)

---

### Post by asavetheuniverseclub on 2010-08-15
Yes 8.04 . There isn't a sound out of my machine.

---

### Post by fslezak on 2010-08-15
Boot into recovery mode, and select the DPKG option, and let it do its thing.

---

### Post by asavetheuniverseclub on 2010-08-15
I got the same error report. coincidentally the keyboard malfunctions after running the fix.  I tried to uninstall the iscan but nothing happened. I think there should be something in the scanner package?

---

### Post by 2CV67 on 2011-01-01
I am having the exact same problem & error messages with iscan when trying to upgrade from 8.04 to 10.04

I thought I would try using Synapt to remove iscan, but as soon as I open Synapt I get the error message about dpkg interrupted & needing to run dpkg --configure etc.
When I run that, it ends up with PANIC: circular dependency exiting.

Add/remove programs does not see iscan.

So I seem to be stuck with a dead 8.04 & no way out.

Is there a way out?

Thanks!

---

### Post by Jonam on 2011-04-08
I suffer the same problem everytime there is a kernel update. I have an Epson V300 scanner that requires iscan.

If my computer hangs after a kernel update with the PANIC message, I reboot and after Ubuntu starts, I open a terminal window and enter (as in post #7):

$ sudo dpkg -r esci-interpreter-f-720 iscan iscan-data

This uninstalls all of iscan including the driver (esci-interpreter-f-720). I then run:

$ sudo dpkg --configure -a

This finishes the install of the kernel which crashed previously with the PANIC message. A reboot is usually required after this stage.

After this completes, I go back to the avasys.jp website and reinstall iscan, iscan-data and the driver.

Hope this helps.

---

