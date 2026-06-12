---
title: "why and how should I partition when I do a fresh Ubuntu install?"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by hanzj on 2010-10-16
We read [http://www.channelregister.co.uk/2010/10/11/ubuntu_10_10_review/](http://www.channelregister.co.uk/2010/10/11/ubuntu_10_10_review/) and now we're thinking of partitioning our hard drive when we do  fresh install of Ubuntu 10.10.

Why should we partition?

How should we partition?

---

### Post by TNT1 on 2010-10-16
Bump. Please help, I'm thinking of redoing my laptop 64bit, and I usually just select use the entire disc at install time, but I'm reading more and more here about guys having /home on a separate partition and all sorts of stuff. 

What's recommended?

---

### Post by A_M_S on 2010-10-16
I use a different partition for my home folder.

You can easily upgrade your system without loosing your personal data.

---

### Post by msandoy on 2010-10-17
I have been trying out various distros over the last couple of years, and my default partitioning is 2GB swap, 10GB / (root) and the rest for /home. When I install a new distro, I only format the root partition and remove settings from my home folder. 
But, if you have had a computer running for a while, you probably have it set up s certain way, and this way, your new distro keeps the settings from your old one.

---

### Post by diablo75 on 2010-10-17
> **msandoy said:**
> I have been trying out various distros over the last couple of years, and my default partitioning is 2GB swap, 10GB / (root) and the rest for /home. When I install a new distro, I only format the root partition and remove settings from my home folder. 
But, if you have had a computer running for a while, you probably have it set up s certain way, and this way, your new distro keeps the settings from your old one.

This.

However, if I do reinstall (replacing the / partition but using the /home as it is, and making sure it's not marked for formatting) I just leave the contents of /home as they are.  Firefox (for example) and Thunderbird store all their settings and cache data in a hidden folder called .mozilla.  After a reinstall, it's like the everything is exactly the way I left it (sans software not included with the default install; you just have to mark packages off in Software Center or Synaptic for installation).

---

### Post by Rinzwind on 2010-10-17
I have 2 discs in my notebook:

/ 10Gb
swap 5 Gb
/home/ 5 Gb
/discworld1/ remainder

/discworld2/ all 160 Gb


I remove ~/Desktop and create a symlink to /discworld2/Desktop/.
That way I can store my video en ebook files on my desktop and have them back immediately after an installation.

I can choose to not format home and keep settings or to format home without thinking about needing to save important files in my home dir: since there are none...

Post-install I have a script that does lots of apt remove and apt install's to get me all my needed software.

---

### Post by Megaptera on 2010-10-17
Useful guide with screenshots of a basic partitioning scheme:

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

---

### Post by amjjawad on 2010-10-17
> **hanzj said:**
> 
Why should we partition?

1) [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
2) [https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

> 
How should we partition?[/QUOTE]
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

The best tool to do this job is: [GParted]("http://gparted.sourceforge.net/documentation.php")
It's available by default in Ubuntu's Live CD/USB. 

If you're planning to install Ubuntu ONLY without dual booting with Windows or any other Operating System > then I recommend to let Ubuntu handle that job and choose : Erase and use the entire disk ([https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall))

If you're planning to install Ubuntu and dual booting with another Operating System, then that's another story. If this is your case, let us know so that we could walk you through the steps.

In general, if you decided to do it manually, you need minimum TWO Partitions:-
1- ROOT Partition (/)
2- SWAP Partition (SWAP)

The most recommended scheme is having 3 partitions:-
1- ROOT Partition (/)
2- SWAP Partition (SWAP)
3- HOME Partition (/home)

Please note that the size of SWAP partition should be [YOUR RAM SIZE] by [2] = [YOUR SWAP Partition].
[U]Example: 
[/U]if your RAM is 2GB then your swap partition should be 2*2=4GB.
if your RAM is 1GB then your swap partition should be 1*2=2GB.
and so on.

If you need more information, please ask :)

---

