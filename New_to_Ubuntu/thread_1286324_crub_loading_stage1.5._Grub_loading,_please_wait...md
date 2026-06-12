---
title: "crub loading stage1.5. Grub loading, please wait... error 22"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by takis56 on 2009-10-08
My laptop HP vz5000 can not start at all. My cd drive does not start and I get the message " Grub loading stage1.5. Grub loading, please wait... error 22. I tried to boot from the cd but nothing happens. I tried windows xp proffesional black, Nothing. I don't know what to do. Somebody please help.

---

### Post by louieb on 2009-10-08
Did you use XP to delete your Linux partition? 
or has the hard drive been making strange noises lately?
Can the laptop boot from the CD drive or USB drive?

In order to find what is wrong (and possibly fix) you will need a working CD drive or the ability to boot to a USB device. 


From [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html") 
> 
22 : No such partitionThis error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.       

---

### Post by Sarai the Geek on 2009-10-08
> **takis56 said:**
> My laptop HP vz5000 can not start at all. My cd drive does not start and I get the message " Grub loading stage1.5. Grub loading, please wait... error 22. I tried to boot from the cd but nothing happens. I tried windows xp proffesional black, Nothing. I don't know what to do. Somebody please help.

Not all computers are set up to boot from a cd automatically. When your computer first boots and the splash screen comes up with the name of the manufacturer (i.e. Dell, Asus, System 76, etc) there should be a line of text that says something like "boot options" or "boot menu" with an indicated key to press. Go into that menu and make sure it's set only boot from a hard drive if it doesn't find a bootable cd first.

Once you fix that you should be able to boot into a live cd and we can get more information on the problem. Best case, you accidentally made a change that made grub "forget" where to boot from (this has happened to me) which is very easy to fix. Worst case, your hard drive is fried in which case there's not a whole lot we can do, although there are some data recovery options.

---

### Post by takis56 on 2009-10-09
Thank you very much for your response.
I only had Ubuntu in my laptop when it happened. 
The cd tries to start, then the hard drive blinks and after a few seconds stops and gives you the message. 
I don't know how to create a usb a bootable jump drive if I don't have another Ubuntu OS.
Should I try to create an xp bootable jump drive?

Thank you for your help again.

> **louieb said:**
> Did you use XP to delete your Linux partition? 
or has the hard drive been making strange noises lately?
Can the laptop boot from the CD drive or USB drive?

In order to find what is wrong (and possibly fix) you will need a working CD drive or the ability to boot to a USB device. 


From [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by takis56 on 2009-10-09
I already did all that from the bios.
The hard drive tries to start and then stops with that error 22

> **Sarai the Geek said:**
> Not all computers are set up to boot from a cd automatically. When your computer first boots and the splash screen comes up with the name of the manufacturer (i.e. Dell, Asus, System 76, etc) there should be a line of text that says something like "boot options" or "boot menu" with an indicated key to press. Go into that menu and make sure it's set only boot from a hard drive if it doesn't find a bootable cd first.

Once you fix that you should be able to boot into a live cd and we can get more information on the problem. Best case, you accidentally made a change that made grub "forget" where to boot from (this has happened to me) which is very easy to fix. Worst case, your hard drive is fried in which case there's not a whole lot we can do, although there are some data recovery options.

---

### Post by louieb on 2009-10-09
> Should I try to create an xp bootable jump drive?
Since the CD does not work. Go to the  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") site.  They have a download that will create a boot-able USB jump drive. This is a really nice rescue CD/USB.

In the documentation there are instructions for creating a boot-able USB stick for  both Linux and windows.  

Or for 15 dollars + shipping OSdisk will send you a 2GB USB flash drive with Parted Magic already installed. (There is a link on the Parted Magic site).

---

### Post by LewRockwell on 2009-10-09
> **takis56 said:**
> I only had Ubuntu in my laptop when it happened. 
The cd tries to start, then the hard drive blinks and after a few seconds stops and gives you the message. 
I don't know how to create a usb bootable jump drive if I don't have another Ubuntu OS.
Should I try to create an xp bootable jump drive?

Here, you describe that during start-up the BIOS is checking the CD/DVD/optical drive for a bootable optical disk and then moving on to check the hard drive.

This seems to imply that if you had a bootable LiveCD inserted in the optical drive during start-up then that might help with your trouble-shooting process.

.

---

### Post by LewRockwell on 2009-10-09
> **takis56 said:**
> My laptop HP vz5000 can not start at all. My cd drive does not start and I get the message " Grub loading stage1.5. Grub loading, please wait... error 22. I tried to boot from the cd but nothing happens. I tried windows xp proffesional black, Nothing. I don't know what to do. Somebody please help.

It is highly unlikely that both the CD drive and the hard drive would go bad at the same time so you will need to figure out what is and isn't working

If the CD drive has failed then you'll need to boot from an external drive of some sort...or a flash media...either one via your USB port

We use one of these with optical and IDE drives to provide external connectivity

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)
*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

You may also need to alter your BIOS settings to make sure your USB ports boot before the hard drive

Keep us posted on your progress

.

---

### Post by takis56 on 2009-10-10
Thank you very much.
I hope it works.
My bios though has only floppy disk line.
I will try it and hopefully works.
Thanks again

> **louieb said:**
> Since the CD does not work. Go to the  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") site.  They have a download that will create a boot-able USB jump drive. This is a really nice rescue CD/USB.

In the documentation there are instructions for creating a boot-able USB stick for  both Linux and windows.  

Or for 15 dollars + shipping OSdisk will send you a 2GB USB flash drive with Parted Magic already installed. (There is a link on the Parted Magic site).

---

### Post by takis56 on 2009-10-10
Would you give some more details, because I went to PartedMagicCD site and I got lost. I am not an expert in these things. 
Thank you again.

> **louieb said:**
> Since the CD does not work. Go to the  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") site.  They have a download that will create a boot-able USB jump drive. This is a really nice rescue CD/USB.

In the documentation there are instructions for creating a boot-able USB stick for  both Linux and windows.  

Or for 15 dollars + shipping OSdisk will send you a 2GB USB flash drive with Parted Magic already installed. (There is a link on the Parted Magic site).

---

### Post by LewRockwell on 2009-10-10
> **louieb said:**
> Since the CD does not work. Go to the  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") site.  They have a download that will create a boot-able USB jump drive. This is a really nice rescue CD/USB.

In the documentation there are instructions for creating a boot-able USB stick for  both Linux and windows.  

Or for 15 dollars + shipping OSdisk will send you a 2GB USB flash drive with Parted Magic already installed. (There is a link on the Parted Magic site).

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/partedmagic?ad=partedmagic](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/partedmagic?ad=partedmagic)

.

---

