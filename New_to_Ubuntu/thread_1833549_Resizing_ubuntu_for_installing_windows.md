---
title: "Resizing ubuntu for installing windows"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by ronsci on 2011-08-26
I would like to install windows on a separate partition of my hard drive because I have to upgrade my BIOS. But I don't know how to resize ubuntu when it is installed on a single partition.
Kindly help me out of this.

---

### Post by androssofer on 2011-08-26
> **ronsci said:**
> I would like to install windows on a separate partition of my hard drive because I have to upgrade my BIOS. But I don't know how to resize ubuntu when it is installed on a single partition.
Kindly help me out of this.

best way wud prob b this:

get an ubuntu live cd(or usb), and boot into it... 

then open up "gparted" and it will show a nice GUI with your HD and its partitions etc... 

then you can right click on the ubuntu partition and select resise, then drag it to the size you want... then your good!

put in windows and use the empty space you just created

***note***:you may need to recover GRUB tho once u put windows on, as windows screws up the grub menu on ya....

and with everything on computers. back up your data before doing this. "if you dont back up important data, it mustn't be that important"

---

### Post by ronsci on 2011-08-26
But how can I make the live usb? And can I recover the grub?

---

### Post by androssofer on 2011-08-26
> **ronsci said:**
> But how can I make the live usb? And can I recover the grub?

why ronsci i'm glad u asked...

get ur fav ubuntu iso and then open "usb-creator", think thats its name anyway..

if ur on natty search for "usb" it will come up.

on 10.10 and earlier its in System >> Admin >> usb sumthing or System >> preferences >> usb sumthing

(as u may hav guess i'm not at my ubuntu comp atm)

then select the usb drive(make sure its the usb u select and not the HD!) in the menu and then select the iso.. select how much room etc u wanna use for storage.. i generally use all of it :-)

then when its done, reboot, go into your bios, and select the usb to b the main boot device. then save and exit the bios. and it will load :-)

---

### Post by coffeecat on 2011-08-26
> **ronsci said:**
> But how can I make the live usb? 

Or live CD. You must have used one or the other when you installed Ubuntu. Or did someone else install Ubuntu for you?

> **ronsci said:**
> And can I recover the grub?

Yes, with the live CD or USB, but we can come back to that.

Another idea. Do you have a spare hard drive? Take out your Ubuntu hard drive and put in the spare one, install Windows to it, do your BIOS upgrade, and then put your Ubuntu drive back in. This would be far quicker in the long run. Resizing an Ubuntu partition can take a very long time and risks the possibility of something going wrong with data loss. If you use another drive for Windows you won't have the hassle of repairing grub.

Creating a live CD:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Creating a live USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by androssofer on 2011-08-26
ooo and to recover GRUB... borrowed the info from [this thread]("http://ubuntuforums.org/showthread.php?t=1285499")

> Hello everyone,

I faced the same problem as some of you might have. Windows 7 install after Ubuntu 11.04 and Grub disappeared. I tried reading up many of the solutions around including booting off a live cd and trying to reinstall grub - easier it may sound, I had to struggle for a few hours before coming up with the solution.

1. Boot off a Live CD
2. Mount the ubuntu partion to the OS. I did this by sudo mount /dev/sda1 /mnt
3. A series of commands as follows

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

4. Once you have entered into the root mode 

grub-install /dev/sdx

sdx=your hard drive.. Mine was sda

Restart and Bingo !!!

***note*** this isnt mine, nor have i ever tried this, so if it doesnt work i will b of little help. but u can start a new thread if it doesnt and some1 else will now :-)

also look at [this thread]("http://ubuntuforums.org/showthread.php?t=1014708") as it might help also

---

### Post by coffeecat on 2011-08-26
> **androssofer said:**
> ooo and to recover GRUB... borrowed the info from [this thread]("http://ubuntuforums.org/showthread.php?t=1285499")

@androssofer, you are describing chroot-ing. That is a valid way of re-installing grub but is unnecessarily complicated. Here is the community documentation on this:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

The "Copy LiveCD Files" method is quick and easy.

---

### Post by androssofer on 2011-08-26
> **coffeecat said:**
> @androssofer, you are describing chroot-ing. That is a valid way of re-installing grub but is unnecessarily complicated. Here is the community documentation on this:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

The "Copy LiveCD Files" method is quick and easy.

thanks. will use this in future ;-)

---

