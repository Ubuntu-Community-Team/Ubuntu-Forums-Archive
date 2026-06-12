---
title: "Virtualization for newbie"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by patilkaustubhv on 2009-04-02
My system config is-- core2quad 6600, dg35 chipset MB, 250gb hdd, 2gb ram (will make it 4 gb soon)


I would like to install Ubuntu on it and virtualize vista or XP on it.....

Can any one suggest me _HDD partitions _and _appropriate versions of Ubuntu and virtual box _for the same????

I will be greatful.....

---

### Post by skymera on 2009-04-02
You can install Ubuntu as you normally would.
Version 8.04, 8.10 or 9.04 (Beta).
Then using virtualbox you can install XP using the DVD or an ISO.

Unless you want to install XP to the hard drive and boot it whilst inm Ubuntu, i don't know how to do that.

EDIT:
[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)
That may help. I would double check it, however my college has blocked the site.

---

### Post by patilkaustubhv on 2009-04-02
ok but 64bit version or 32bit.... heard that 64 bit versions are not well supported by various programs....


and about swap area?????? primary partition???? sec partition???
which partition should i install windows?????

---

### Post by cwmoser on 2009-04-02
I have an AMD 64 X2 6000+ processor with 4GB RAM.
I use Ubuntu 8.04 and VMWare.
I have virtualized several instances of Windows and other Linuxes.

VMware words fantastic with Ubuntu.  My PC was a Windows XP machine before I upgraded to Ubuntu.  There are only 2 applications I need to run under Windows so I used VMware Server software to create a Windows XP VM instance using the old installation disk for my PC.  Many of the VMware products are free.  After I got my VM's created, I prefer to use VMware Player to run them than Server.

Ubuntu + VMware is a great combination.

Carl

---

### Post by tarps87 on 2009-04-02
The swap area, if you want to hibernate 8GB when you have 4GB of ram (it is recommended to use 1 1/2 times the amount of ram you have). If hibernation isn't a problem I'd go for about 2GB.
Primary partition depends, do you want a separate home partition  if so:
10GB for / (the root partition, this should be more that enough)
the rest for /home (this is where the users data is store, if you reinstall/or change the OS as long as it is GNU/Linux based you can use this partition without the need to reformat or copy any data back on after)
If you don't want a separate /home partition I would just test the installer to use the entire disk and it will do it all for you.

Virtualbox will create a virtual hard drive so there is no need for a separate partition. It will be clear when you use it.

Assuming you have a 64 bit processor (I think you do) I would go for the 64 bit version. I have two computers running Ubuntu 64bit and have not had any compatibility problems. That's one of the beauties of open source :)
I believe Virtualbox will only run in 32bit mode. I.e. Even if you are using a 64bit host the guest OS will still need to be 32bit.
I may be wrong as I haven't looked into it

Hope this helps

---

### Post by patilkaustubhv on 2009-04-02
Thanks 2 you all... eased a lot for me

---

