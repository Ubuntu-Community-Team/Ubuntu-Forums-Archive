---
title: "How Do (Can) I install Linux on my external Hard drive?"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by tonkatsu89 on 2011-07-06
I have an iomega external harddrive. I have 10 GB of unallocated space I was thinking about using for an emergency operating system such as Ubuntu. This is the one I intend to use unless anyone has a better suggestion. I just wanted to know how to do it if I can. Please let me know and if you have any suggestions don't be shy to say so. The only reason I don't want to install it on my computer itself is I'm just so used to using Windows. I might eventually install it on my computer but that's all in good time. Thanks for your eventual help!

-Dave.

---

### Post by Perkins on 2011-07-06
The simplest way to do it for the inexperienced user is to disconnect the internal hard drive so there are no mistakes.  Just open the case and take the data or power cable or both loose from the back of the drive.  That way you don't accidentally mess up your current system.

Then just plug in your USB drive and pop in the install CD and it should work as normal.

Of course, it doesn't do a lot of good to install to a USB device if your computer can't  boot from a USB device, but most modern machines can.  And it's possible to create a boot CD that will start up and then load the OS off of the USB drive.  So go ahead and give it a shot.

---

### Post by oldfred on 2011-07-06
Since it is an external you want to be sure to install grub2's boot loader to the MBR of the external drive. The absolute way is as Perkins mentioned in unplugging drive. But if you cannot unplug drive you have to use manual install (Something Else in Natty) to have a choice on where to install the boot loader. You just need to choose / (root) and swap. You only specify a format for / and swap can be 2GB.

Lots of detail, not as difficult as it may seem as Herman explains everything.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")


I prefer Ubuntu, but you could do this also:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by tonkatsu89 on 2011-07-07
Ok I'm going to check out that site that you linked me, Oldfred. I'm going to have to wait until tomorrow so I can get a blank CD.

I forgot to mention that I'm on a laptop Perkins, I'm not entirely sure of myself about removing the hard-drive and I really don't want to void my warranty.

Thanks for the help. I'll get back to you tomorrow once I've got an install disk.

---

