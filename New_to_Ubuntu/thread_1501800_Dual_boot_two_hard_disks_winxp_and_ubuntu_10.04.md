---
title: "Dual boot two hard disks winxp and ubuntu 10.04"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by AOB on 2010-06-04
I had two hard disks one with win xp and the other ubuntu 10.04. I wish to have the ubuntu as C drive and winxp D. How do I configure to have dual boot arrangement when I put them together? I am new to ubuntu 10.04.

---

### Post by zpletan on 2010-06-04
I'm not sure it's possible (at least practically possible) to switch them such that Ubuntu is c: and winxp is d: on Windows.  On Ubuntu, the concept of drive letters is not used.

If you wish to access your winxp data on ubuntu, you may go to Places->"Pick the size of your winxp hard disk" Partition.  If you wish to access your ubuntu partition from winxp, probably the easiest thing to do is copy the stuff you want under windows to the windows partition.

---

### Post by zpletan on 2010-06-04
Hmmm.... I posted twice.  Sorry.

---

### Post by louieb on 2010-06-04
The short 
plug the drives in so Ubuntu boot 1st.
now fix GRUB so it will boot windows too.
open Applications>Accessories>terminal and run
```
sudo grub-mkdevicemap
sudo update-grub
```
more info on the above commands [IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")  

Don't get confused by how Windows uses c: or d: - you might call it the c drive, but its really  a partition on a hard drive.

---

### Post by mapes12 on 2010-06-05
This may help you out:-

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by wilee-nilee on 2010-06-05
The way the OP describes this I think it is a wubi install. C and D drives sounds like wubi to me.

---

### Post by AOB on 2010-06-05
> **louieb said:**
> The short 
plug the drives in so Ubuntu boot 1st.
now fix GRUB so it will boot windows too.
open Applications>Accessories>terminal and run
```
sudo grub-mkdevicemap
sudo update-grub
```
more info on the above commands [IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")  

Don't get confused by how Windows uses c: or d: - you might call it the c drive, but its really  a partition on a hard drive.

Thanks Louibe. It works just two lines of command with 10.04! Much appreciate.

---

### Post by Zeppfan on 2010-06-05
> **louieb said:**
> The short 
plug the drives in so Ubuntu boot 1st.
now fix GRUB so it will boot windows too.
open Applications>Accessories>terminal and run
```
sudo grub-mkdevicemap
sudo update-grub
```more info on the above commands [IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")  

Don't get confused by how Windows uses c: or d: - you might call it the c drive, but its really  a partition on a hard drive.

I tried this and grub will not recognize my 2nd hdd that has my Windows XP installation on it. When I boot the computer, I don't even get the option of choosing an OS...it just boots straight to Karmic. Any help here?

This is what I get in Terminal:

xxxxxxx@xxxxxxx-desktop:~$ sudo grub-mkdevicemap
[sudo] password for xxxxxxx: 
xxxxxxx@xxxxxxx-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
xxxxxxx@xxxxxxx-desktop:~$

---

### Post by takisan on 2010-06-05
Are there two seperate drives or two seperate partitions? That's the question. (sorry programming attack!)
if(num(drives) == 2)
{
    // Try switching the jumpers around.
}
else
{
     //You have to repartition the hard drive. Sorry
}

---

### Post by Zeppfan on 2010-06-05
I have 2 separate hard drives. I installed XP first to one hdd then Karmic on the other.

---

### Post by louieb on 2010-06-05
The reason to run grub-mkdevicemap was to let grub know there are 2 hard drives. 
Then update-grub should have found the XP install - it did not - the output would have listed it. 
I does kind of sound like a hard drive connection install problem.

What kind of drives are they **SATA? **- which should not be a problem - pretty much plug them in and go.

Or **ide/pata**? (wide flat ribbon connector) - can be a problem -  jumpers must be set for the correct master/ slave / cable select setting.  The type of cable you have will determine   how you jumper the drives - some cables don't support cable select.  
Also its fairly easy to plug the flat cable in backwards - the colored wire (pin #1) goes closest to the power connector. 

Or one of each?  the sata just gets plugged in and the ide/pata should be configured as master or cable select and be plugged in to the end connector.

BTW: one way to tell if both are plugged in correctly is to run ```
sudo fdisk -l 
```(lowercase L at the end) - see if both drives get listed.

---

### Post by wilee-nilee on 2010-06-05
Good responses here for fixing but without the whole picture; it is flailing in the dark. OP plugin both drives and run the boot script and post it in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Jerry N on 2010-06-06
I am not sure this is what the OP needs but on my secondary computer I have the default boot order for 3 drives set in the BIOS.  When I want to boot on a different drive I press "F12" during the boot process (Gigabyte MB) and from there I can choose which drive to boot from.  Works fine, only slightly more time consuming than selecting the operating system to boot in a grub menu, and actually quite a bit more versatile since I have a fixed drive, an IDE mobile drive rack, and a SATA mobile drive rack on that computer.  Other MBs might have a different boot drive selection key or key combination.

Jerry

---

### Post by AOB on 2010-06-08
Now I am done with the dual boot which is working fine for me. I bought a Brother DCP145C 3-in-1 printer but I do not know how to make it work with my Ubuntu 10.04 desktop. Any help? I am new to Ubuntu.

---

