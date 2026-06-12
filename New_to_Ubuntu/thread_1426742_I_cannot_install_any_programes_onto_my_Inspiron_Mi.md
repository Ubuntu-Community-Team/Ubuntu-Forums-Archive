---
title: "I cannot install any programes onto my Inspiron Mini 10."
date: 2010-03-10
forum: New to Ubuntu
---

### Post by nina777 on 2010-03-10
Hi there, 

I recently purchased Dell Inspiron Mini 10. It uses Ubuntu. 

I tried to install Skype today, and it downloads the file fine, but when it comes to Installing I am being asked for an administrative password. There was no password set up when I purchased the laptop, so I dont know what it may be.  

Any suggestions?

Thanks

---

### Post by J V on 2010-03-10
Its what you use to log in...

If your computer automatically logs in, you will need to reset your password ([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword))

---

### Post by nina777 on 2010-03-10
Yes it logs me in automatically. I was previously told to reset using the recovery mode but I cant seem to get into it. Sorry I am total beginner. :)

When I press ESC to get into it, nothing happens. The only options I have is F2-Set up and F12-Boot.

---

### Post by J V on 2010-03-10
If you are on karmic koala (9.10) you will need to hold shift to get into it (Read the link I sent you)

If not, you need to rapidly tap escape (its just after the bios menu which contains the F2/F12 options you see)

---

### Post by nina777 on 2010-03-10
I've tried both. No luck. Thanks anyway. 

After the F2 and F12 options I get a black screen with MBR at the top...I tried all options but cannot find recovery mode.

---

### Post by J V on 2010-03-10
Try tapping faster then xD

Or else install startupmanager and edit some settings to make it require you to choose your OS which will give you the menu you need...

---

### Post by RasterBurn on 2010-03-10
being your laptop was purchased with Ubuntu pre-installed on it there is a chance that the password is either written down in the user manual or else the password was left blank when the system was setup, try leaving the password blank when you install something (who knows, it might just work)

---

### Post by J V on 2010-03-10
afaik, linux won't let you have a blank password on install (of course, who knows, dell might have changed the password and then imaged the drives for speedier production)

---

### Post by RasterBurn on 2010-03-10
there is always the chance that Dell has disabled the password security requirement allowing them to leave it blank (unlikly but possible) anyways, those are the only 2 suggestions i could offer, afterall without knowing the password, installing anything using synaptic, apt-get, or the software center is impossible as well as installing anything that requires root privilages to install (pretty much everything including updates)

---

### Post by snowpine on 2010-03-10
[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

> Booting into Recovery mode

If you have an original Dell Mini 9 with Ubuntu pre-installed, you may have a hard time entering the GRUB menu as the default delay is zero. This is particularly problematic if you're trying to reset your password using the passwd command.

You can enter the recovery mode following these steps:

   1. Boot the mini 9 while pressing ESC every second
   2. When you see the "MBR 2FA:" prompt or similar, the boot process is stopped.
   3. Press ENTER and ESC very fast one after the other.
   4. You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode. 

---

