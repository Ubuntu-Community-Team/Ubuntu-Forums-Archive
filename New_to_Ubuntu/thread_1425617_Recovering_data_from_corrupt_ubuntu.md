---
title: "Recovering data from corrupt ubuntu"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by brijraj22 on 2010-03-09
i have somehow managed to corrupt my grub. i want to copy the data from my harddisk onto another portable hard disk. i booted ubuntu using the live CD but i cannot copy the files as it says 'u'r not the owner of this file'. please advice on how i may proceed.

---

### Post by audiomick on 2010-03-09
From the live CD, if you start the file manager from the terminal using
```
sudo nautilus
```
you should be able to do what you need to do.

_I am not sure_, but this may mean that the file copies will belong to root. This will mean that you would have to use the same process to put them back when you get your problems solved (the command works just as well from a real install as from the live CD) and to change the permissions appropriately.

As far as your grub goes, you should be able to repair it, if it is just grub that is broken.

---

### Post by bumanie on 2010-03-09
Can you provide more information about the grub problem -as suggested, it may be easier to fix grub, but we need to know more information about the grub error/corruption and which version of grub you are using, ie is it grub-legacy or grub 2?

---

### Post by brijraj22 on 2010-03-09
(nautilus:5246): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:5246): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5246): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5246): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



This is what i get

---

### Post by brijraj22 on 2010-03-09
i'm not sure whether the problem is with the grub. i had earlier posted  threads twice to help solve the problem but i didn't get much help, so i thought that i'd just recover the data and install ubuntu again.here's the thread though.

[http://ubuntuforums.org/showthread.php?t=1405951](http://ubuntuforums.org/showthread.php?t=1405951)

---

### Post by bumanie on 2010-03-09
I get those same messages when I start nautilus with root privileges (I just tried it), but a window pops up and I can navigate where I want to. So...those error messages aren't necessarily as bad as they look.
To confirm information from your original post, you have karmic on a portable hard drive and windows on the computer and you have not installed grub to the windows mbr. Is that correct?
The output from the other post indicates that although you are running 9.10, you have a /boot/grub/menu.lst as well as a /boot/grub/grub.cfg Do you have any idea how that occurred? Did you upgrade to 9.10 from 9.04? 9.10 should be running grub 2, which the /boot/grub/grub.cfg directory pertains to. I would tend to think that getting rid of grub-legacy and reinstalling grub 2 via a live cd should work. 
But if you want to retrieve your data first, can you tell me whether you can copy files from a live cd by going to terminal and typing > sudo -iand then going to Places --> Computer --> Filesystem and entering the directory named home - that's where your stuff should be.
If that works, you can then decide whether to do a fresh install or try to fix grub.

---

### Post by audiomick on 2010-03-09
Yes, it is "normal" that starting nautilus with "gksu" produces error messages. Sorry, should have mentioned that. If a file manager window opens, all is fine. If not, obviously something is wrong...

---

### Post by brijraj22 on 2010-03-09
There is some slight problem remaining. although i can access the files, i'm still not able to copy those files. when i copy them, and later right click after opening my pen drive, there is no paste option.

it was a clean install, no upgrade.

---

### Post by audiomick on 2010-03-09
What happens if you try and drag and drop onto the pen drive?

---

### Post by brijraj22 on 2010-03-09
sorry bout that, it was some issue with my pen drive.have created backup of the data. can you assist me in reinstalling the grub?

---

### Post by audiomick on 2010-03-09
I am looking at the other thread, and will see if I can help there.

---

