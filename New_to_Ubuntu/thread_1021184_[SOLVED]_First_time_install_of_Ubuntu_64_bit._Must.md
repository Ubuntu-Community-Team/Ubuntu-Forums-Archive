---
title: "[SOLVED] First time install of Ubuntu 64 bit. Must be duel-boot"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by GumpTron on 2008-12-25
Hello,

I am downloading the 64bit version of Ubuntu, which I would like install on my HD with Vista 64 bit currently running on it as well.

1.)It is imperative that I be able to duel boot the two OS's without either one effecting the other. I do not want to share between the two and I hopefully I can install ubuntu in such a way that it will not jeopardize Vista.

2.)i am prepared to devote 25 GIGs to Ubuntu for this duel boot. Is that sufficient? it is overkill? I wouldn't mind making it less, as long as it wont effect me being able to take advantage of Ubuntus great effects.

thank you for your help.

---

### Post by nhasian on 2008-12-25
1) it is recommended to use Vista's partitioning tool to resize/shrink the partition to make room for ubuntu.

2) 25 gigs for ubuntu is very good.  it will give you some breathing room.  after you've shrunk the ntfs partition to free up 25 gigs, then boot off the LiveCD.  during the ubuntu installation you will need to create one partition for the root filesystem / and another for the swap file (1.5 to 2 times the amount of ram you have in your system).

---

### Post by Steve05TSX on 2008-12-25
1) I just installed 8.10 myself a second ago with Vista x64 on the same partition and it worked great.  I used the GRUB boot loader, which could be a pain if you decide to uninstall Ubuntu.  You could, on step 7 in the advanced section to not install the boot loader and use EasyBCD via Windows to customize the MBR.

2) That should be plenty enough, it's all about preference

---

### Post by GumpTron on 2008-12-25
> **nhasian said:**
> 1) it is recommended to use Vista's partitioning tool to resize/shrink the partition to make room for ubuntu.

2) 25 gigs for ubuntu is very good.  it will give you some breathing room.  after you've shrunk the ntfs partition to free up 25 gigs, then boot off the LiveCD.  during the ubuntu installation you will need to create one partition for the root filesystem / and another for the swap file (1.5 to 2 times the amount of ram you have in your system).

I think I understand what you are telling me to do. Would you mind giving it to me in steps? I am sorry but i am new to this.

---

### Post by balaknair on 2008-12-25
To safely install Ubuntu as a dual-boot with Vista

1) Within Vista
        a) Defragment the hard drive
        b) Shrink the partition using the partitioning tool on Vista to free up space for Ubuntu
Right click on the My Computer icon on the desktop or in the 'Start' menu> manage> select disk management
**or**
Control Panel> Administrative tools> disk management

Then, right click on the partition you want to resize and select 'shrink volume', and enter the amount of space you want to shrink(for 25 GB= 25600 MB), click 'Shrink'.


2) Boot into the Live CD, and at the partitioning step, opt for Manual partitioning.
If you have 25 GB free space, an advisable format would be

a) root partition of 5-10 GB(mount point /)
b) Swap partition of 1-4 GB (the swap partition is similar to the pagefile in Windows, and an easy way to determine how much space to allocate it is 1-2 x installed RAM- if you have 1 GB RAM, use approx 2 GB Swap)
c) The remaining space to be used as your home partition (mountpoint /home)

Having a seperate /home partition is useful when you want to retain settings and files when reinstalling/upgrading Ubuntu.

---

### Post by balaknair on 2008-12-25
You can find more info here(along with screenshots of each step)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

