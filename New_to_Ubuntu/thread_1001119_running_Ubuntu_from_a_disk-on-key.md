---
title: "running Ubuntu from a disk-on-key"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by is777 on 2008-12-03
I want to use Ubuntu but my computer is tiny and I don't know if the hardware requirements are ok. Its an Asus eee and according to the properties section its got an Intel Celeron 900 MHz processor with 504 MB RAM. Its currently running Windows XP home edition and its single drive is 3.72 GB in size but currently has only 279 MB free space (all taken up by pre-installed programs, no files of my own :( )  
My questions are: Can I run Ubuntu directly from a disk-on-key without downloading anything to my computer? If so, how? and how do I use other programs, such as Lyx, with it?

---

### Post by Paqman on 2008-12-03
Your eee can handle Ubuntu just fine. In fact, these even a customised version called [Ubuntu Eee]("http://www.ubuntu-eee.com/") made especially for eeePCs.

---

### Post by bobnutfield on 2008-12-03
Take a look at this site:

> [http://www.pendrivelinux.com/2008/02/13/pendrivelinux-2008-install-from-windows/]("http://www.pendrivelinux.com/2008/02/13/pendrivelinux-2008-install-from-windows/")

But, the easiest for you is to use UNETBOOTIN to install to the key.  This app will download it and install it for you to the USB stick.

[http://sourceforge.net/projects/unetbootin/]("http://sourceforge.net/projects/unetbootin/")

---

### Post by Carl Hamlin on 2008-12-03
I would strongly recommend against running Ubuntu (or any operating system) from a flash device. Flash can sustain a finite number of write/erase cycles before failure, and running write heavy processes along with swap on flash will *substantially* shorten the life of the device.

---

### Post by anjilslaire on 2008-12-03
True, but many new netboots have a flash-based SSD drive internally nowadays, so they must be making improvements in th writeability dept. 

(Yes, I know these are different from the usb flash drives in your pocket, but still...)

---

### Post by anjilslaire on 2008-12-03
> **bobnutfield said:**
> Take a look at this site:



But, the easiest for you is to use UNETBOOTIN to install to the key.  This app will download it and install it for you to the USB stick.

[http://sourceforge.net/projects/unetbootin/]("http://sourceforge.net/projects/unetbootin/")

You can also do this from the repos by installing "Create a USB startup disk" via Add/Remove programs in Ubuntu.

Sorry, too lazy to look up the packages in Synaptic, but I think its mtools and usb-creator.

---

### Post by Paqman on 2008-12-04
> **Carl Hamlin said:**
> I would strongly recommend against running Ubuntu (or any operating system) from a flash device. Flash can sustain a finite number of write/erase cycles before failure, and running write heavy processes along with swap on flash will *substantially* shorten the life of the device.

Proper SSD drives use wear-levelling algorithms, and have an MDBF well above what a magnetic hard drive has. Limited writes is only a problem on older flash media like CF or USB sticks.

If you're really worried, then there are steps you can take to [reduce writes to your SSD]("http://www.brighthub.com/computing/linux/articles/9170.aspx").

---

