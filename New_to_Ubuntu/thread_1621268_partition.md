---
title: "partition"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by zorrofox on 2010-11-14
Hello everyone. It seems every November I get sick of Windows and come running here. I'm going to install Ubuntu on a friends laptop. The laptop in question runs XP Pro SP3 and has one physical drive, divided into two of 80GB each. He wants to run Ubuntu on it's own and so has no need for this second partition. How do we go about combining the two so that the Ubuntu install disk sees only one drive? Is this an option in the install process or is there something I must do in Windows beforehand? I'm guessing these are simple questions to answer but I'm not sure myself so thought I'd ask the experts. Thanks for taking the time to read through this plea for help.

---

### Post by spiky001 on 2010-11-14
Do you want to get rid of windows and just have 1 OS on hard drive Ubuntu?

---

### Post by zorrofox on 2010-11-14
> **spiky001 said:**
> Do you want to get rid of windows and just have 1 OS on hard drive Ubuntu?

Thanks for the quick response. Yes, we just want to have Ubuntu 10.10. Windows will be history.

---

### Post by mick222 on 2010-11-14
just choose the use whole disk option at install

---

### Post by spiky001 on 2010-11-14
Just put the disc in set machine to boot from cd load Ubuntu, I would suggest making a sepperate partition for home
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by tajiknomi on 2010-11-14
[SIZE=2]While installing ubuntu..their is an option "Erase the whole disk"

it will automatically erase your partition's and Create only 1 drive in which Ubuntu will install....
[/SIZE]

---

### Post by Verbeck on 2010-11-14
a separate /home is better, so manually partition  it during the installation
15gb = /
swap = ram size
rest = /home

---

### Post by spiky001 on 2010-11-14
When installing have eth0 cable connected run updates

---

### Post by zorrofox on 2010-11-14
Thanks for the help. It seems clear enough. Unfortunately I'm getting an error when I try to boot from either CD or USB stick.

"input/output error can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

Damn!

---

### Post by zorrofox on 2010-11-14
> **spiky001 said:**
> When installing have eth0 cable connected run updates


Do I have to connect via Ethernet? This computer is a long way from the router unfortunately. Will it make any difference if I just update it later once the wireless driver is installed, or am I missing something important here?

---

### Post by zorrofox on 2010-11-14
> **zorrofox said:**
> Thanks for the help. It seems clear enough. Unfortunately I'm getting an error when I try to boot from either CD or USB stick.

"input/output error can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

Damn!

I'm trying everything here to gt this thing to boot, nothing worked so far. I'm now trying UNetbootin to see if that will work. However I think maybe the downloaded .iso is corrupted which is a shame because files that large take all night on this very slow internet connection.

---

### Post by zorrofox on 2010-11-14
> **Verbeck said:**
> a separate /home is better, so manually partition  it during the installation
15gb = /
swap = ram size
rest = /home

Ok, the first iso I downloaded was corrupted somehow. I now have a working disc. I've moved the computer to where it is connected via ethernet so I'm good to go. For the above, we've got 2GB RAM so I put in 2GB for the swap?

---

### Post by zorrofox on 2010-11-14
> **Verbeck said:**
> a separate /home is better, so manually partition  it during the installation
15gb = /
swap = ram size
rest = /home

Sorry to be a pain. I was kinda expecting to see something similar during installation to what you've written above, but I don't. Could you maybe be more specific as to what I should be doing at this point?

---

### Post by Verbeck on 2010-11-14
> **zorrofox said:**
> Sorry to be a pain. I was kinda expecting to see something similar during installation to what you've written above, but I don't. Could you maybe be more specific as to what I should be doing at this point?
you'll have to select 'specify partitions manually'/'advanced partitioning tool' from the installation and make those partitions from unallocated space separately. click the add/new button to do so
so
1. 15 gb - file system - ext4 -mount point /
2. 2 gb swap space
3. rest X gb - file system ext4 - mount point /home

 this image might help (from google >_<)
[http://karuppuswamy.com/wordpress/wp-content/uploads/2010/09/Screenshot4.png](http://karuppuswamy.com/wordpress/wp-content/uploads/2010/09/Screenshot4.png)

---

### Post by zorrofox on 2010-11-15
Got it! That's it up & running. Thanks for all the help guys.

---

