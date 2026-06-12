---
title: "windows xp ubuntu and fedora 10 all on same comp."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by tavati on 2009-02-08
i tried to install all three on my pc.

i have xp already installed. when i combine xp with ubuntu or fedora 10 then all is well.

but the moment i put the third OS i.e fedora or ubuntu on it, none of the linux system survives.now the details.

i have two ide disks 40gb and 300gb(slave). i have xp on 40gb(with four partitions-1 primary and three logical).

when i load fedora 10 after ubuntu is loaded then fedora boot manager totally wipes out my ubuntu from the boot list and gives only option of booting either xp or fedora. In this case both xp and fedora start successfully when choosen.

when i load ubuntu (7.10) after loading fedora then ubuntu boot manager( grub) gives all options to load xp, fedora and ubuntu. but except xp none of the OS gets loaded when choosen. When i choose fedora 10 from the list Error msg is ; Bad file or .. press any key to continue. --and then i am back to boot menu. 
if i choose ubuntu then ubuntu hangs on startup.

i have tried out all combinations of partitions like -- both ubuntu and fedora on 300gb disk on seperate partitions // ubuntu on 300gb and fedora on 40gb ( one of the logical partitions) // ubuntu on 40gb ( one of the logical partitions) and fedora on 300gb disk etc.

i want all three on my pc. help pls.

---

### Post by rolnics on 2009-02-08
To help us can you do the following command from a terminal: -

```
sudo fdisk -lu
```

Then we can go from there, you'll probably have to manually edit your menu.lst

But you might want to get yourself  [Super Grub]("http://geocities.com/supergrubdisk/")!! It's a handy disk to have around, I'm having an issue at this time. For some reason OpenSUSE won't boot so I used Super Grub to boot up.

---

### Post by hyper_ch on 2009-02-08
do you have IDE and SATA drives mixed?

---

### Post by tavati on 2009-02-08
no both are ide disks( 100% ).

---

### Post by Kellemora on 2009-02-08
Hi Tavati

I had this same problem when I was playing with multiple OS's as a learning experience more than anything else.

Most Distro's Other than Ubuntu will wipe out the bootloader on your and you will have to rebuild it by hand.
Thankfully, this is a LOT easier than it sounds!

The trick here is, install the DOZE First, since it thinks it's GOD!  Install ALL the other Distro's next, letting them place their bootloaders on their OWN partition, then install Ubuntu LAST.
Often Ubuntu will FIND all the other Distro's and build the bootloader for you, but if not, it's a simple matter to get the menu.lst from your Ubuntu install, and copy the few lines from the OTHER Distro's bootloaders to it.

You would place at the TOP of the list, the Distro you want to boot without user intervention and all the rest after it of course.

If you need to see what this looks like, just holler and I will post a menu.lst from a triple boot machine for you.

TTUL
Gary

---

### Post by tavati on 2009-02-13
thankx. isaw your reply today.  it will be good if u could paste the menu.lst for triple boot machines

---

### Post by unixeducation on 2009-02-13
Just as a heads up, even properly set up boot schemes sometimes get out of whack after updates. In cases like this, you can try using the Super Grub Disk to boot into your desired operating system and fix problems: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

