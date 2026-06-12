---
title: "grub crash"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by sundy58 on 2009-05-15
We had a thunderstorm last night and my Jaunty install can't find a way to boot. I'm writing this from the live cd. It is a clean install and the only thing I need off the hard drive is some video.

I can't find a path to my files (documents/video) though. I'm not familiar with the Linux file system so any help is appreciated.

---

### Post by Don1500 on 2009-05-15
If you saved the vedios in your user account they should be on the /home/(username) directory. Mine would be "/home/don" or a subdirectory of that.
/home/(Username)/documents/video

This is all case sensitive.

goto PLACES>HOME> then use the GUI as you would a windows file system GUI.

---

### Post by clive littlewood on 2009-05-15
Hi

Don't know how a thunderstorm can have affected grub !!!!

But anyway download the supergrub disc and run from boot you will see many menu options to reload your grub.

This is a great app and has saved me on more than one ocassion.

Hope this helps

Clive

---

### Post by sundy58 on 2009-05-15
Yeah I don't get it either. My XP and Jaunty boxen crashed but the wife's XP box is fine. My two are on the same power strip her's is a different outlet but the same circuit. (same room)

Must have been some sort of power fluctuation. None of the digital clocks needed reseting though.

Weird.

---

### Post by presence1960 on 2009-05-15
what happens when you try to boot? Do you get the loading GRUB message then an error, or just nothing? A better description of what is happening when you try to boot would be helpful.

---

### Post by sundy58 on 2009-05-16
Goes through bios and comes up 'can't find hard drive' 'press F1 to continue 2 for setup'. Dell Precision 450. I just want the video files and will reinstall. I can't find my 'user' from the live cd though. Might be toast.

---

### Post by sundy58 on 2009-05-16
I followed the instructions here: "http://www.supergrubdisk.org/wiki/SGD_Howto_make?phpMyAdmin=4d5aa646470e3977a158303759c2efde#How_to_make_a_Super_Grub_Disk_USB." After downloading this "/home/ubuntu/Desktop/super_grub_disk_slovensky_usb_0.9795.tar.gz" for a Super Grub Disk install on a USB thumb drive. Scroll down to the Gnome instructions. Seemed to work fine till the 'grub (hd3)' then nothing seemed to happen I would get 'no such place' errors.

I'm going to try to boot from it but I think I will be back for more help.

---

### Post by sundy58 on 2009-05-16
On my XP box I unplugged the hard drives turned them off in bios. Powered on let not find drives then powered off reconnected drives powered back and set to auto in bios. Found drives and booted up. I think it might be something in bios got confused. Will try on Jaunty box now.

---

