---
title: "Replace Ubuntu 9.10 with Ubuntu 11.04, When window 7 is side by side."
date: 2011-07-05
forum: New to Ubuntu
---

### Post by sstextile on 2011-07-05
I have Ubuntu 11.04 in my pen drive . Now i have to replace Ubuntu 9.10 with Ubuntu 11.04. Presently Ubuntu is installed side by side Windows 7. I can not disturd Windows 7. Please help me, i am new to Ubuntu.

---

### Post by nothingspecial on 2011-07-05
Is windows 7 on the pendrive?

---

### Post by androssofer on 2011-07-05
> **sstextile said:**
> I have Ubuntu 11.04 in my pen drive . Now i have to replace Ubuntu 9.10 with Ubuntu 11.04. Presently Ubuntu is installed side by side Windows 7. I can not disturd Windows 7. Please help me, i am new to Ubuntu.

is a few ways, you could go into 9.10 and upgrade it, then upgrade again til u reach 11.04.. but tht mite b a bit flaky. 

or you could make a backup of your /home directory. then boot from usb.

on step 4 on this how-to: [http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

u see the option to get rid of 10.10 and reinstall, it should be the same for u except it will list 9.10 select "erase 9.10 and reinstall" and it should leave windows b and only erase 9.10 for ya :-)

---

### Post by Bucky Ball on 2011-07-05
Easy, during the install you will get to a section where you pick how you want to install: there is a side by side option at the top. Don't use it. Go for 'Custom' (I think it is), the bottom option (where you can setup/resize partitions, etc.).

Now, you might need to make a note of what's where from Gparted in your 9.10 install before doing this, but you want to aim the new install at the current 9.10 / partition (which should be sda? - whatever you discover it is). 

Click the partition where 9.10 is, then click 'Change'. Set to EXT4, Format = yes, mountpoint = /. 
That's it! You'll see a column in there which is 'Format?'. The only one that should be ticked is the / partition (where 9.10 is currently installed but soon to be replaced by your new OS). 

Also, if you have an existing /home *partition *- not directory - you can change that to use as EXT4 (if it is that), but don't enable to format. Set mount point as /home and your new install will not format the existing /home and consider it as its /home also and won't create a /home directory or partition as part of the install. Neat, huh? 
  
I've just installed 11.04 so fresh in my mind ... ;)

---

