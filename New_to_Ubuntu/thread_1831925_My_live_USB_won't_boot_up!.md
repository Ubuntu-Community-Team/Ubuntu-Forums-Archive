---
title: "My live USB won't boot up!"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Chocolated on 2011-08-24
Hi I'm completely new to the Linux world and I have set my BIOS to boot from USB first and it won't boot for me. It's plugged in and I really want to use Linux back but it's a bit hard when you can't even boot it up!

Help would be appreciated very much.

---

### Post by psylencer on 2011-08-24
You're really going to have to give us a few more details.  First of all what happens when you try to boot up, does the USB stick start loading then fail?  do you get any messages on screen?  How did you create the USB stick?  Did you just extract the files from the ISO onto it or did you use software like LinuxLive?

---

### Post by Chocolated on 2011-08-24
I'm using unetbootin and nothing comes up at all, it just loads straight to Windows.

---

### Post by raja.genupula on 2011-08-24
create live usb using USB start up disk creator which already existed in ubuntu . have you checked md5sum of your ISO ? is it good .

---

### Post by psylencer on 2011-08-24
If you system boots straight into windows - your problem is almost certainly to do with your BIOS settings.  Ensure USB is set to the First Boot device.   Some systems such as the one I am working on have 2 different options for this.  One is to set the boot device order and the other is to set the boot device priority.  

IF the BIOS settings are correct and your system IS trying to boot from USB - then you should atleast see an error to the effect of "Cannot boot from disk"  or "Please insert disk and press any key"  (That IF you USB device is not OK).

---

