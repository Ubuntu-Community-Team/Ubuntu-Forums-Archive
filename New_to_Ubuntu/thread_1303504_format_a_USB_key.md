---
title: "format a USB key"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by jrev on 2009-10-28
Hi all,
By which command can I discover the name of my USB key in order to format it in ext3 ? /dev/sdx or something.
Should I format it by a command in my gnome terminal ?
i never did it before...

Thank you for this basic information :p

---

### Post by hellblazer on 2009-10-28
I've always used gparted to make any changes to partitions, install and give it a try

---

### Post by martrn on 2009-10-28
> **hellblazer said:**
> I've always used gparted to make any changes to partitions, install and give it a try

+1

```
sudo apt-get install gparted
sudo gparted
```

---

### Post by alphaniner on 2009-10-28
Have you heard of [Google]("http://www.google.com/#hl=en&q=partition+usb+stick+linux&aq=f&aqi=&oq=&fp=8ec9ea851cee2c5b")?

---

### Post by clive littlewood on 2009-10-28
Hi

I've formatted many sticks just using the Gnome commands.

Just right click on the desktop stick icon and choose format.

You will be given the choice of file system and voila !! 

Clive

---

### Post by jrev on 2009-10-28
> **clive littlewood said:**
> Hi

I've formatted many sticks just using the Gnome commands.

Just right click on the desktop stick icon and choose format.

You will be given the choice of file system and voila !! 

Clive

When I click on the USB icon on my Desktop the menu format doesn't exist

---

### Post by XDevHald on 2009-10-28
jrev, remove the USB and put it into another slot. You can always right click on the drive on your desktop and choose format. I.E mine is fat32 and in this case I would select this drive to format. Hope this helps.

P.S to find out the drive type of the USB, right click the drive icon on your desktop and choose Properties and it will display what drive it is.

---

### Post by clive littlewood on 2009-10-28
[HTML]When I click on the USB icon on my Desktop the menu format doesn't exist[/HTML]

Hi

This must be a netbook thing !!!

Give gparted a try and remember to unmount from gparted before formatting.

Clive

---

### Post by jrev on 2009-10-28
> **clive littlewood said:**
> [HTML]When I click on the USB icon on my Desktop the menu format doesn't exist[/HTML]

Hi

This must be a netbook thing !!!



Yes it is eeebuntu netbook remix 3.0 but on my Ubuntu 9.04 it's the same no menu format under the right clic...
I will try gparted :p

on my Debian Lenny I can only mount or umount this USB key

---

### Post by clive littlewood on 2009-10-28
Hi

Just to make sure I'm not going mad see attathed !!!!

---

### Post by jrev on 2009-10-28
thanks !
on which version of Ubuntu are you ? 

I will install it :p

that's my Desktop :

[http://www.zimagez.com/zimage/capture940.php](http://www.zimagez.com/zimage/capture940.php)

---

### Post by Zoot7 on 2009-10-28
> **hellblazer said:**
> I've always used gparted to make any changes to partitions, install and give it a try
+1 I've been using gparted for years to format hard drives/usb sticks/external hard drives and to resize/move/copy partitions. Never had any problems with it.

---

### Post by ChildOfMana on 2009-10-28
+1 for gparted.

If you just want to see details about your USB drive though (e.g. where it's mounted, partitions, filesystem etc) the open a Terminal (Applications > Accessories > Terminal) and type:

```
sudo fdisk -l
```

Note that's a lower case L at the end, not a number 1.

---

### Post by clive littlewood on 2009-10-28
Hi jrev

I'm using 9.10 Karmic (testing)

I would wait a few days to download Karmic, it will be manic tomorrow, fried servers !!!!!

good luck

Clive

---

### Post by jrev on 2009-10-28
> **Zoot7 said:**
> +1 I've been using gparted for years to format hard drives/usb sticks/external hard drives and to resize/move/copy partitions. Never had any problems with it.

Me too !

my PC refuses to format my USB drive :
> Code:
jean@jean:~$ umount /dev/sdf
umount: /dev/sdf n'est pas monté (selon mtab)
jean@jean:~$ mke2fs -j /dev/sda
mke2fs 1.41.4 (27-Jan-2009)
/dev/sda est le périphérique en intégralité, pas seulement une partition !
Procéder malgré tout ? (o,n) o
mke2fs: Permission non accordée lors de la tentative de détermination de la taille du système de fichiers
jean@jean:~$

Sorry my computer speaks french ;)

---

### Post by Zoot7 on 2009-10-28
> **jrev said:**
> my PC refuses to format my USB drive
Have you tried out using one of the command line tools?

**[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")**

---

### Post by jrev on 2009-10-29
thanks zoot7 you found it !  ;)

It works with this command on the umounted key :

sudo mkfs -t ext3 /dev/sdf 

Bravo :p

---

### Post by Zoot7 on 2009-10-29
Excellent! Glad to hear you're sorted now. :)

---

### Post by Living2007 on 2009-10-29
I would definetly use Gparted, but be careful not to remove your HDD partitions!

---

### Post by jrev on 2009-10-30
* have done it with gparted as well*

So all is fine

---

