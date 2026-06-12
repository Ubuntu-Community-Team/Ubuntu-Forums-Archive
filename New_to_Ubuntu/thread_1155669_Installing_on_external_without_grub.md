---
title: "Installing on external without grub"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by roxuresox on 2009-05-11
Ive installed Linux on a different laptop before, on a 4g flash drive, the problem i always had was that when i booted without the drive, i would get the error, i think it was 21 or something like that, basically grub was on the flash drive so if i tried to boot without it on the system would just give me the error and stop.

what i plan on doing now on my new laptop is installing jaunty on my 1TB eSATA drive so that when im at home and have access to my external i can run it, what i want to make sure is that when i do install it, i dont have to worry about Grub errors. 

what i would like to know is their some way i can install it so that grub is loaded on to my main drive
Or preferably to install it without grub so that i can just set my computer to boot from the external first and load jaunty

tried searching around for how to do this, but so far haven't found any answers, so sorry in advance if this is a common question, just want to get this installation right the first time around and not have to worry about getting grub errors every time i dont have my external

thanks

---

### Post by logos34 on 2009-05-11
Your problem was that grub (stage1/IPL) was installed on the MBR of the internal drive, but /boot/grub (menu.lst, etc) is on the usb/external, so that when you disconnect it grub can't find the boot files, and you get error message).

Follow [this guide ]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/")(principle is the same for eSata)

---

### Post by roxuresox on 2009-05-11
awesome, using that guide worked great, considering reinstalling it on my desktop using that method, no problems with grub or anything if the drive isnt attached.

however the only cons are, it was a pain in the rear to remove my main drive, acer really knows how to shoe horn it in there, and my bios wont allow me to boot from an eSATA drive, but my drive did come with a USB connection that it will boot to, so i just have to deal with a slightly slower drive, but hopefully it wont make much of a diffrence and i can get it to let me mount the internal drive

thankyou

---

### Post by logos34 on 2009-05-11
too bad about the eSata...but from my experience the slower speed of usb is not all the noticeable for the most part (at least it wasn't for me when used to run feisty from a internal Maxtor connected via usb enclosure to my desktop.) of course your mileage may vary depending on your usage

---

