---
title: "Booting choices?"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by TAspr on 2011-08-13
Hello, I am using Natty 11.4, and even through I go into the system settings, and choose Windows 7 by default, it still goes into a recovery mode by default.  How do you make it so that it boots into windows 7 by default?  My wife likes windows 7 and it's the geek in me that wants Ubuntu.

---

### Post by Zimmer on 2011-08-13
Edit /etc/default/grub

GRUB_DEFAULT=0 specifies the default entry. It counts from 0, like any geeky menu. Change to anything you like. If you set the entry to GRUB_DEFAULT=saved, it will boot the last selected option from the previous boot.

This is according to this tutorial
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId205199](http://www.dedoimedo.com/computers/grub-2.html#mozTocId205199)

I have changed my wife's computer some time ago to boot WinXP instead of the Linux distro in this way.. will just double check to make sure this is how I did it

EDIT: Yes, thati s how I didi it... good luck.

---

### Post by drs305 on 2011-08-13
For users not accustomed to modifying the boot system files, I recommend Grub Customizer. It's a GUI app that can do a lot of Grub tweaking, including setting the default OS. 

Click the "Customizer" link in my signature line for a thread explaining how to install and use it. If you prefer working with the files manually, click the "Tasks" link.

---

### Post by TAspr on 2011-08-13
Thank You, I will try that.  I believe I was using the Grub customizer, but I will check into it.

Thanks guys.

---

