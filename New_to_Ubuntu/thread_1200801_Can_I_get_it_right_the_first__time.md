---
title: "Can I get it right the first  time ?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Chris J.S. on 2009-06-30
Hello 

  I am as green as can be ... but look forward to learning from anyone willing to teach some one as new to LINUX as I am .

 I am ready to evolve. Before I attempt to partition my freshly wiped hard drive and install XP media center on one partition and UBUNTU one another what do I need to have ready ( drivers and ??? ) 

 I do not even know where to start and have had little success with searching the forum. 

Should a complete newbie use the new release ( ( JJ  ) or an older version ? 

 What can I use to partition the drive ( prefer freeware but am not opposed to buying something if that is the smart move )...  I am thinking of having three partitions . one for XP ... one for UBUNTU and one to play with other distro's . How big should the partition for UBUNTU be . 


Will I be able to create a ready to use CD with UBUNTU on it that I can use ( am unable to open  any CD that I burned with Nero , have burned three so far )  Is there some freeware I can use to open the download . i tried to use Wubi but had no success with that either ... lol 


 Having the needed drives on a ready to use CD seems like the smart thing to do  , but I do not know where to even begin to gather this info . 

My comp is a Gateway OEM 

  Processor-  AMD Athlon 64 X2 4200+ / 2.2 GHz


  Main board - NVIDIA GeForce 6100 / nForce 410

  Ram - PC3200 / 400.0 MHz / DDR SDRAM .. 1 gig

  Hard drive - 1.0 x 250.0 GB - Standard - 7200.0 rpm
 
  Optical Storage - 48x (CD) / 16x (DVD)

  Graphics - NVIDIA GeForce 6100

  Sound card ( integrated ) - AC '97 5.1 channel surround

Monitor - gateway 22 inch LCD ( fp2275W)

Printer - Epsom CX800F

(  know I am missing  something ) 

 I have no knowledge on dual booting , have never ha a drive with multiple partitions .... and little experience of command line use ... but am not afraid to learn . 

 where do I start ? 

 Thanks for any help I receive  , as my knowledge and experience grow I will be more than happy to help those who may benefit from any help I may be able to offer . 

  Chris

---

### Post by LowSky on 2009-06-30
install windows first, makes thing much easier... you will need drivers and such for that, as windows doesn't do the work for you

then install ubuntu, any version you like. the Live CD has a partitioning program on it already, no need to find one. you shouldnt need any drivers, as ubuntu will take care of everything, you will have to enable the graphic drive but its a one click process and a quick reboot, nothing crazy.

I dont know if you printer will work, you will need to google around for the info, just use epson model number and linux.

---

### Post by oldos2er on 2009-06-30
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

[https://help.ubuntu.com/9.04/switching/index.html](https://help.ubuntu.com/9.04/switching/index.html)

---

### Post by mcduck on 2009-06-30
Like suggested, install Windows first and use the Windows installer to create the Windows partition. Leave the space you are planning to use for Ubuntu as empty, unpartitioned space.

After installing windows just pop in the Ubuntu CD and boot the computer from it, Ubuntu's installer will detect the unpartitioned disk space and offer you option to use it fro Ubuntu. It will create Ubutnu partitons for you automatically.

And I'd definitely recommend going for the latest release, and only trying the older ones if you have nay compatibility problems with the latest version.

What comes to burning the CD, just make sure that you don't extract the .iso file you downloaded, and that you burn it as disk image, not as data CD or bootable CD.

---

### Post by Bucky Ball on 2009-06-30
Great resource:

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

8.04 LTS is the Long Term Release version and stable. 9.04 was released in April and 'teething' but sounding good and improving all the time (I use 8.04 so can only go by what folk are saying). Anything beyond that (Karmic Koala) your would be 'testing', valuable but something for later. 

Gotta say, Love your attitude! Good luck with it and welcome to the learning curve! :)

---

### Post by magh-87 on 2009-06-30
You can check this out, it's opensource (so it's free) and I use it whenever I convert a Windows computer to Ubuntu, or whatever other needs I have. [Burn ISO]("https://help.ubuntu.com/community/BurningIsoHowto")

Make Windows your first partition. M$ set it up in such a way that if you don't go with them first, it won't work properly. So create your 3+ partitions using a M$ Windows installation disk,  install windows then Ubuntu then your distro's of choice.

---

### Post by Bucky Ball on 2009-06-30
> **magh-87 said:**
> 
Make Windows your first partition. M$ set it up in such a way that if you don't go with them first, it won't work properly..

Yes and no. MS made it so Windows wants primary partition (not logical) number 1, disk 1; so not ideal for a new OP to install anywhere else as problematic if newbie. But it will work properly with some coaxing if for some reason you really want or need to install Windows somewhere other than on numero uno.

> **magh-87 said:**
> So create your 3+ partitions using a M$ Windows installation disk,  install windows then Ubuntu then your distro's of choice.

I would think about what you are going to require here. I advise sit down with a paper and pencil and figure them out. Any partitions you want NTFS, do them with Windows installer. Leave the space for your Ubuntu install and everything else do with the partitioner in the Ubutnu install (Gparted).

One really important reason for thinking about this is that Linux uses EXT3 for it's partitions (you can use other things but this is standard) which Windows will not do anything with (doesn't natively recognise them AT ALL but can with appropriate software, unsure how successfully as never tried it). 9,04 uses EXT4 and Windows has no recognition of that, no software for this combination.
 
So, any partitions you want to share between OSs: NTFS or FAT. Any you don't (unless you are sharing with an OS that understands them), EXT3.

---

### Post by Chris J.S. on 2009-06-30
Thanks for the help !  

 Two things that I really needed right .

 First MCDUCK  telling me to burn an image instead of a data file. Burn the image and was in business . 

 Second .. the first thing I did was forget the password I used during the install .. and ***oldos2er*** posted this link [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)   where I found a way to correct that . 

I wanted to send a personal message to them to say TY , but I do not have 75 posts = so thanks to you two ..=D>



[]("http://psychocats.net/ubuntu/index.php")

---

