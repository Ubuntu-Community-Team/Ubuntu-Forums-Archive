---
title: "Wireless not installed (worked in installation)"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by PreseliComputing on 2006-11-20
I have an Acer laptop, and the live cd shows the minipci wireless atheros card perfectly, but the system did not have enough memory to install from the live cd, so I downloaded the alternate installation disk.

During installation, the program sees the atheros card, and even connects to the wireless network, but post-install, the wireless card is not shown in the network panel, and when I checked the hardware using the terminal, I saw that the atheros card was listed, but drivers were not installed (Does this make sense?)

Can someone please help me ASAP, as I am currently removing ALL Micro$oft operating systems from my businesses systems, and I am just stuck with this one (Well, also a laptop without CD/FDD or Network)

---

### Post by FrodoB on 2006-11-20
You need the linux-restricted-modules for your kernel.  These are not installed in the alternative CD install, but they are available through apt-get if you are on the internet, or off of a normal Ubuntu install CD.

Here is the apt-get command: (just cut and paste the commands if desired)
$ sudo apt-get update
$ sudo apt-get install linux-restricted-modules-`uname -r`

If you insert the Ubuntu install CD into the system when it is up and running the system should find the CD and ask you if you want to open Synaptic, say yes and enter your password. Search for linux-restricted select the correct one for the kernel that you are running. You can see the correct kernel name at a prompt with:

$ uname -r

Good luck, after installing these and rebooting it should just work again.

---

### Post by PreseliComputing on 2006-11-20
I have inserted a 6.10 standard installation disk into the CD-RW drive, and it just opens the CD-ROM folder.  When I go to Synaptic, and select the restricted modules, it sends up an error saying that the server canot be reached.

Is there any way to force the package manager to just use the 6.10 installation disc as the only available source (temporarily)

---

### Post by FrodoB on 2006-11-20
Well I looked and I cannot see that they are all there, so that is probably the issue. Is there no way to move this machine to a location where it can be wired to an internet router while you get these installed?

---

### Post by PreseliComputing on 2006-11-20
I forgot to mention that the RJ45 ethernet port is also not working (The only device listed in the network panel is the loopback)

I can probably transfer files from another system, but I need to know which files these are

(Thanks for the quick response)

---

### Post by FrodoB on 2006-11-20
The are all in:

/var/cache/apt/archives

---

### Post by PreseliComputing on 2006-11-20
I have downloaded and transferred the files, but the package managers will not accept the files.  Instead they see them as straight text files (when they are .deb)

Do you have any other ideas, or will I have to install fedora ](*,)  (I really dont want to, as I prefer ubuntu)

---

### Post by FrodoB on 2006-11-20
You just need to use dpkg -i at a prompt in the directory that you copied them over to:

$ cd my_archives

$ sudo dpkg -i sudo dpkg -i linux-restricted-modules-*.deb

That should install them.

---

### Post by Princey on 2006-11-20
I too have the very same issue with the wireless card not listed in the network listings (did when I booted using the live cd but had to use the alternate as the partition manager had problems during install). I do have an ethernet working port and downloaded the modules, do I simply reboot as it still isn't showing up after installation of the restricted modules.

---

### Post by FrodoB on 2006-11-20
Princey;

Yes, that is the theory.

---

### Post by Princey on 2006-11-20
Thanks, will do after I'm through downloading updates.

---

### Post by FrodoB on 2006-11-22
Here is the procedure for getting wireless back after and install from the Alternate CD for Edgy, having no internet connection.

1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

---

