---
title: "Continuous Boot up"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by POWMS on 2009-07-20
Hello all
I have a Compaq 800 notebook running Xubuntu 9.4.
Last night after a very rare crash I re-booted only to find that the notebook would load the grub, then reboot to infinity.
I entered the BIOS and all settings are correct, except the date and time had changed. I manually corrected this, no change. Still booting to infinity.
Would this be a hardware issue or a corrupt grub?
No errors/warnings are showing.
Thanks

---

### Post by yeats on 2009-07-20
You might want to try booting into a live CD (if you have the resources).  If not the Ubuntu live CD/installation disk, then Knoppix, perhaps.

What caused the crash, do you know?

---

### Post by ~sHyLoCk~ on 2009-07-20
Do you see any error messages?

---

### Post by POWMS on 2009-07-20
Chris
I tried booting from the installation disc, the last option, I just get continuous boot. Running the live CD I cannot access the harddrive.
Shylock, no error messages initially. From the boot up line of loading Grub 1.2, it powers down and the Compaq logo shows, powers up, loads Grub 1.2 etc, etc.
I tried the Super Grub disc, which replaced the Grub 1.2 with Grub 1.5 and now I get an error message 'Error 15'.
Since I can run the live CD I'm assuming there are no hardware faults, the Grub must be corrupted from the initial crash. I was downloading photos thru Picasa at the time (Picasa is not the most stable apps on Xubuntu).
Is there a simple way to reinstate the original Grub for Xubuntu 9.4?
I don't want to go down the path of formatting and reloading the OS.
Thanks.

---

### Post by lisati on 2009-07-20
Do any of the options available through recovery mode help?

---

### Post by Sef on 2009-07-20
>  Is there a simple way to reinstate the original Grub for Xubuntu 9.4?

Download [Super GRUB Disk]("http://supergrubdisk.org") and use that to reinstall GRUB.

---

### Post by POWMS on 2009-07-22
Neither Super Grub Disc or re-installing Grub from the live CD work. I get a 'core dump' error. I have reported this bug (there is one other already logged), so I will see if an expert there can help shed some light on reinsating Grub.

---

