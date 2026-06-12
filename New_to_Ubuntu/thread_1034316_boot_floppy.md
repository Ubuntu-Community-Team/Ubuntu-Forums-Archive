---
title: "boot floppy"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by schoolboy666 on 2009-01-08
hey there i've got a problem,

i have a cd with ubuntu 6.10 desktop but it's not bootable,
i tried to make a bootfloppy in ubuntu serve version: 8.10 

code: mke2fs /dev/fd0

that did'nt work
then i tried in windows with rawrite

it made the floppy but wen i tried booting it it did'nt work either.

can someone help me out here?

:confused:

---

### Post by kellemes on 2009-01-08
> **schoolboy666 said:**
> hey there i've got a problem,

i have a cd with ubuntu 6.10 desktop but it's not bootable,
i tried to make a bootfloppy in ubuntu serve version: 8.10 

code: mke2fs /dev/fd0

that did'nt work
then i tried in windows with rawrite

it made the floppy but wen i tried booting it it did'nt work either.

can someone help me out here?

:confused:

You probably need to enter your BIOS and change your boot-settings.
If you want to boot from a cd you may need to move it to the top of the boot-order, same thing for floppy.

In order to enter BIOS you need to find out the magic key-combination to use at boot, depends on motherboard.

---

### Post by schoolboy666 on 2009-01-08
i already did that i even disabled the cd rom and hdd but it stil wil not work

---

### Post by linux_tech on 2009-01-08
Depending on the computer manufacturer and bios, Del, F1, F2, and F10
are all possible keys to press at boot to go into bios setup. 
Look for boot order or boot priority.  Change the boot order to boot from cd before HD. Usually F10 to save and exit.
If cd is bootable, then OS setup should start.

---

### Post by schoolboy666 on 2009-01-08
i've already set the boot priority 

but i think i used the wrong image for the floppy

sbm.bin

is there another way to do this?

---

### Post by linux_tech on 2009-01-08
Did you try following all the steps here yet
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)
to make the boot floppy

---

### Post by linux_tech on 2009-01-08
As a different option, you can make a usb install stick.
This is probably your best bet if you are sure your cd is not bootable and you are trying to install ubuntu.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by linux_tech on 2009-01-08
But if you are still determined to write smb.bin to a floppy then this
shows how to do this
[https://answers.launchpad.net/ubuntu/+question/29313](https://answers.launchpad.net/ubuntu/+question/29313)
[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

---

### Post by schoolboy666 on 2009-01-08
ubuntu does not  recognize:


/dev/fd0

---

### Post by handydan918 on 2009-01-08
Try doing ```
sudo modprobe floppy
```

This will load the module that provides support for floppies, since it is no longer loaded by default.

---

### Post by schoolboy666 on 2009-01-09
i've made a usb boot stick
but my pc does'nt support booting from usb device

the floppy boots on anothrer computer and vmware but not the computer that i want it to boot on

---

