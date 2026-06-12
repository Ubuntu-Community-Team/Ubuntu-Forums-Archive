---
title: "Installing Ubuntu to an External Hard Drive"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Videogameavatar on 2008-12-25
Hi Im very new here as this is my first post. Here is what I want to do: I want to install Ubuntu to an external 750gb Hard Drive. I do not want to physically disconnect the Internal Hard Drive while I install Ubuntu to the External Hard Drive. I do not want to Partition the External Hard Drive. I want to know how to tell which Hard Drive is the 750gb External Hard drive before I proceed with the installation so I do NOT erase my Windows installation. In other words does the "a" in sda mean the internal hard drive and the "b" in sdb mean external harddrive? I need specific step by step instructions on how to tell which hard drive is my external hard drive.

I have search the Ubuntu Forums and found that no threads are helpful.
I have read through all of the recommended guides such as:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.ginad.org.uk/Frameset.html](http://www.ginad.org.uk/Frameset.html)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by mapes12 on 2008-12-25
> In other words does the "a" in sda mean the internal hard drive and the "b" in sdb mean external harddrive?The answer is yes. With regard to the rest of your post all the Howto / Tutorials are in the psychocats web site which you have already found.

---

### Post by Videogameavatar on 2008-12-25
So how do I select "sdb" instead of sda when installing ubuntu on my external hard drive? The psychocats tutorial does not go over that.

---

### Post by mapes12 on 2008-12-25
As you go through the installation routine you will get to a section called **Partitioning**. Select **Manual** then select sdb1 for your ubu installation. But look at [this]("http://www.psychocats.net/ubuntu/partitioning") if you want to fine tine your partition configuration.

---

### Post by logos34 on 2008-12-25
At Step 7 "Ready to install' screen, click 'Advanced' lower right and change the Grub boot loader from default '(hd0)' to '/dev/sdb' -- this will write grub to the MBR of the external usb drive rather than the internal hdd.  After it's installed, toggle the Bios hard disk boot order to choose either OS. (If you leave the default, you will be unable to boot when the usb drive is disconnected.)

---

### Post by Videogameavatar on 2008-12-25
Thank you so much both of you!!! Now I finally know for sure that "hda" is my internal hard drive and "sdb" is my external hard drive!

So i select Manual install, make it so the entire hard drive is for ubuntu.

Then At Step 7 "Ready to install' screen, click 'Advanced' lower right and change the Grub boot loader from default '(hd0)' to '/dev/sdb

Thanks =)

---

### Post by Luphrid on 2009-01-08
Thank goodness!  I am so glad someone could finally offer a valid solution to this problem without doing a bunch of unnecessary steps.  

Just installing to external drive presented the Error 21 during grub loading.  There were people instructing to disconnect the internal drive so the grub would install on the external drive.  However, doing this got rid of Error 21 and brought us to Error 2.  Wow.  A lot of work for nothing.

I am currently installing Ubuntu Ultimate Edition 2.0 for Gamers on my external Western Digital My Book, 400 GB.  The instructions provided in this thread will be used, except my external is showing up as sdc, so I will be changing option in Advanced to /dev/sdc.  

When this process has completed, I will let you know whether it was a success or a failure.  I am assuming success.  It has to, or at least should, be this simple.  :)

---

