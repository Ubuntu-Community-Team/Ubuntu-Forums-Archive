---
title: "Question on - USB Startup Disk - on Ibex"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by listerdl on 2009-04-01
Hi - am I correct that I can insert any flavour of linux via CD into my machine and then that will enable me to transfer this onto a (formatted to fat32) flash drive?

-- what I am trying to do is install eeebuntu on my EEE-PC via a laptop running Ibex -- !

---

### Post by James_Lochhead on 2009-04-01
Yes, although there have been problems with the program that does this by default in Ubuntu. I suggest you use unetbootin for this task.

---

### Post by davec64 on 2009-04-01
If you want more info about Linux on USB pen drives have a look here:

[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

I've got Mint installed on my 8GB drive with the option of running it as either a Live CD version or a persistant version.

I used the Ubuntu USBcreator for this but had to copy a file from PenDrive Linux to get it to work.

---

### Post by albinootje on 2009-04-01
> **listerdl said:**
> Hi - am I correct that I can insert any flavour of linux via CD into my machine and then that will enable me to transfer this onto a (formatted to fat32) flash drive?

-- what I am trying to do is install eeebuntu on my EEE-PC via a laptop running Ibex -- !

I've answered this already in your original thread, but i'll repeat it again : unetbootin is giving me the best results for booting from usb, see here [http://unetbootin.sf.net](http://unetbootin.sf.net)

Some instructions for using unetbootin to create the bootable usb-stick :
[http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin)
[http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/](http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/)

---

### Post by listerdl on 2009-04-02
thanks very much

---

### Post by FiReSTaRT on 2011-06-25
Just a couple of notes.. I ended up using Unetbootin (performs much better at creating the USB startup disk than the built-in tool) to create a startup disk. One thing that is not well documented is that you have to turn off the boot helper options (2 of them) in the BIOS and press Esc a few times when the boot screen comes up and then select the option to boot off the memory stick.

---

