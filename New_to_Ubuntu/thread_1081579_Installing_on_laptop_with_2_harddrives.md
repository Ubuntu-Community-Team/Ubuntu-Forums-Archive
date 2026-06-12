---
title: "Installing on laptop with 2 harddrives"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by tonytheviking on 2009-02-26
Newbie question:

I'm very interested in installing Ubuntu on my Toshiba laptop.

I have Vista running currently.  The laptop has 2 hard-drives (300Gb each), so I was wondering if I could install Ubuntu on the second hard-drive (which is basically empty).  Is this an easy task?

I have burnt the free installation CD.  I'm not hugely technical, but have lots of patience, and enthusiasm!

Cheers,

TtV

---

### Post by jimmy the saint on 2009-02-26
easy as pie.  just make sure you pick the empty drive when it asks you where to install.

---

### Post by tenach on 2009-02-26
Are you going to exchange the hard drives in your laptop or have one of them as a USB external hdd?  If you are going to swap them, then Ubuntu will install quite easily.  If you are going to install it as a USB drive, I suggest looking here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by smani on 2009-02-26
Is is as easy as installing on any harddrive, the only things you want to keep in mind is how to boot the system afterwads:

First option: install grub (the bootloader) on the Master Boot Record of the second drive (you will be asked during the installation where to install it), and then you will be able to choose whether to boot windows or ubuntu by choosing the first resp second drive as boot device in the BIOS.

Second option: install grub on the MBR of the first drive, it will then give you a list with the operating systems you can boot, that is linux and windows (probably the preferred method). You will need to recognise what the first harddrive is called (probably /dev/sda - but look at the output of sudo fdisk -l run from the terminal)

---

### Post by tonytheviking on 2009-02-26
thanks for the amazingly quick responses.

i understood most of them!

now, i'm interested to know if i can chose between ubuntu and vista when i boot up the computer.  could someone explain in a little more detail how to do the installation to make sure this can be done?

thanks very much

---

### Post by smani on 2009-02-26
If you choose the second approach I described above, you will get a list you can choose from. The detailed procedure is the following:
[LIST]
[*]Set the BIOS to boot from CD-ROM or USB stick (whichever you are using to install ubuntu), then boot and wait until the desktop has loaded
[*]Click on the icon on the desktop to install ubuntu on you harddrive
[*]Answer the questions, when asked about partitioning, be sure to tell the installer to use the harddrive you want to! The easiest way is to tell the installer to create a default layout on the selected drive.
[*]At the summary page, before you start the actual installation, you should notice ad "advanced" button. There you will be able to choose where to install the boot loader (who will let you choose which OS to load). Set it to the first harddrive.
[/LIST]
That should be all.

---

### Post by tonytheviking on 2009-02-26
that's great!  very clear.

now one more quick question.

since i am a new user, should i try WUBI first?  it looks pretty risk-free, and as far as i can see there are very few downsides?

thanks again.

---

### Post by smani on 2009-02-26
Well wubi is for sure the more risk-free variant - but it then sort of depends on you windows installation - I would prefer having something totally independent from windows. Btw, if you just want to give ubuntu a test-run to see if it runs okay and you like it, you can also run it from a usb stick - there are many utilities on the internet, see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) for example. Then all you have to do is plug in the stick and tell the bios to boot from it, then, if you like it, you can install it.

---

