---
title: "installation of ubuntu problems... and systemrescuecd"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Sidster67 on 2010-07-27
alright so im installing ubuntu and i first want to use systemrescuecd to make a backup image of my computer.

then ill also start messing around with the partition table so that i can properly dual boot.

so what ive done so far is downloaded the iso for it and used the program on theyre site to extract the files onto my 4G flashdrive (im on a netbook so a cd isnt an option)

now ive went into the BIOS setup and placed it first in line for booting, but it just goes to this black screen and tells me that it failed. i dont see how i can boot from my flash drive and then ignore my OS... ive researched quite a bit but i just dont quite understand it.

it is formated to fat32 and what not, and all the files are on there.  what more do i need to do?

please leave a comment and let me know what you think.  thanks

---

### Post by Revolutionary101 on 2010-07-28
One thing I have noticed is that not all flash drives are able to be booted from. I have noticed this exact problem when I put Ubuntu on my flash drive and it worked perfectly. Then my friend requested I put it on his (different brand), I did the exact same process with no problems. Although, when I turned on the computer (same computer), and tried his flash drive it did not work and it failed to load. Then I put mine in and it worked perfectly.

---

### Post by Sidster67 on 2010-07-28
well i just looked mine up

mine is an hp v100w 4G, that i just bought yesterday, and its on lists of websites of bootable flash drives.

is there anything else that im missing? or is this right?

and i am trying to boot systemrescuecd onto windows right now, before i do ubuntu.  this is in preparation to boot ubuntu

---

### Post by Revolutionary101 on 2010-07-28
Try to put Ubuntu on the USB flash drive, maybe systemrescuecd doesn't support booting from a flash drive. If Ubuntu works you can backup your HDD when you run Ubuntu off of your flash drive.

---

### Post by Sidster67 on 2010-07-31
well systemrescuecd definetely supports booting from a flash drive, says so on their website.

and id like to do this first, because i doubt ubuntu will work if this doesnt.

but yeah, still just a black screen saying failed

---

### Post by oldfred on 2010-07-31
I was able to directly boot systemrescue from the ISO on my flash drive with grub2.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script but only limited ISOs, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

Have not used this but it looks like it automates the procedure:
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

grub.cfg entry for system rescue:

menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

---

### Post by Sidster67 on 2010-08-02
OOHHH!

I just looked into Grub, and it looks like this is what I'm missing.

Would I be completely unable to boot into SystemRescuecd without Grub?

Please, more information on this.

---

### Post by oldfred on 2010-08-03
You have to use some boot loader and grub2 is very good at booting a variety of systems from many different partition formats.

The other choice is just a full install of system rescue to a USB, I have not tried that as before I would just install it to a CD. Unetbootin will probalby work, but I like grub2.

---

### Post by albneon on 2011-04-10
sorry, that's NEO B4103 N

---

