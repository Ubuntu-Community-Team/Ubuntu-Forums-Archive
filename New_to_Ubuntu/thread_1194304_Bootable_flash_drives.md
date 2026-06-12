---
title: "Bootable flash drives?"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Logank9 on 2009-06-22
ALRIGHT, so I got linux up and running and I really love it. The only problem is that I would like to install Windows 7 on my another computer to test it out. So I just thought I'd use the 'Create a USB startup disk' tool. When I tried that it gives me the error: 'This is not a desktop install CD and thus cannot be used by this application.'

Is that tool only for making bootable flash drives with Ubuntu on them?

After that I did a little research and found that ( this may or may not be right I found it in some tutorial ) for bootable flash drives they must be the fat or fat16 file system. It said to do something like 'mkfs vfat /dev/sda'. I was going to do that, but somewhere else it said if you're not careful you could erase your hard drive. I have everything backed up, but it would be a pain to reinstall ubuntu.

So how do I format my USB to the right file system, and also write the ISO to it? Do I just extract the files in the ISO to the USB?

Any help is appreciated!

---

### Post by Cheesemill on 2009-06-22
The tool you are refering to is only for Ubuntu iso's. Check out the following link for installing Windows 7 from a USB drive.

[http://lmgtfy.com/?q=install+windows+7+from+usb](http://lmgtfy.com/?q=install+windows+7+from+usb)

(It's the top link)

---

### Post by nhasian on 2009-06-22
i know lots of people like to use the terminal but i find gparted a lot easier to use system->administration->Partion Editor (it may be labeled gparted) if its not installed you can install it with:

```
sudo apt-get install gparted
```

when your in gparted, make sure to choose your flash drive with the drop down menu.  you dont want to accidentally delete a partition from your hard disk!  delete any partitions you have on the flash drive and create a new fat32 one.

then you can put your windows 7 setup files on the flash drive.  theres a ton of howto videos on youtube on how to do extract the setup files from the windows7 iso and put them on your flash drive.

---

### Post by Sealbhach on 2009-06-22
There is another tool called Unetbootin, but again it's only for Linux - I tried but it doesn't work for Windows 7. Unetbootin is really handy though, and very easy to use if you want to look at a Linux distro.


.

---

