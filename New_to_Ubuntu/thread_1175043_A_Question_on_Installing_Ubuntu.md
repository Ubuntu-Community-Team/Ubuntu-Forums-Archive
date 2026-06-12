---
title: "A Question on Installing Ubuntu"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by tcoffeep on 2009-05-31
Alright. This is a little different, and, despite my attempts of finding an answer, I've been unable to find one. My question : Is it possible, as it is with Gentoo and Arch Linux ( which I've recently done both ), to install Ubuntu via one partition on another distro to another?

My set up is this :

sda1 /boot
sda2 /swap
sda3 /home
sda4 nil
sda5 /gentoo
sda6 /arch

and i want sda7 to be ubuntu.

Is this possible? I looked for a guide, because I figure it would easily be found, but, alas, it was not.

---

### Post by nhasian on 2009-05-31
you can install as many operating systems as you like on each partition but i recommend against sharing the /home partition amongst various linux distros.  Each linux distro should have its own /home.  You could always make a /data volume to share the data between different operating systems.

I should also note that you can only have four primary partitions on a hard disk so you should make one be an Extended Partition that can contain the logical partitions inside of it.

---

### Post by tcoffeep on 2009-05-31
sda4 is the "extended", and everything thereafter is the logical partitions. Why is it not recommended to have multiple distros share a singular home? It just makes it easier for me, when it comes to disk space as I only have a 300GB hd.

Right now, my set-up is :

/boot - 100MB
/swap - 4GB
/home - 150GB
/gentoo - 50GB
/arch - 50GB
unused - 40GB

Also, the question I was asking was : Is it possible to install Ubuntu via one partition to another, as it is with Gentoo and Arch. I installed Gentoo via a temporary cd drive I was lent, and Arch through Gentoo, and I'm wondering if I can do the same with Ubuntu.

---

### Post by Diabolis on 2009-05-31
> **nhasian said:**
> you can install as many operating systems as you like on each partition but i recommend against sharing the /home partition amongst various linux distros.  Each linux distro should have its own /home.

I disagree. I've had 4 distros using the same partition as /home, of course each installation had its own user folder. You shouldn't have any problems with that.

Conflicts may arise if you create a user with the same name for all the different installations. Not because the OS can't handle it, but because each OS uses different versions of different programs that will install configuration files in your home folder.

About installing Ubuntu from a running OS, I've never tried it. I just did a quick google search and I didn't find any clues. Why would you want to do that? Just boot up from a Live CD and in 30 minutes you'll be done, probably faster than trying to find a rare tutorial.

---

### Post by tcoffeep on 2009-05-31
Sorry, but it's been awhile since I've used an installer =\.

When setting up the partitions, like in the Arch livecd, is the formatting forced? This is what caused me to do it from terminal rather than from the cd installer.

---

### Post by Bradtek on 2009-05-31
When installing from the CD you can choose what partition to use and weather or not you want to format it.

---

### Post by tcoffeep on 2009-06-01
Fixed. Installed via debootstrap. I missed that, for some reason. :)

---

