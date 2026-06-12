---
title: "Add a hard drive 500 gb"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by bicyclerider on 2009-12-26
I have a system running with Ubuntu 9.10 and here is what I would like to do.
current setup,
2.6.31-16-generic (#53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009)
Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
ATA Hard drive 140 gb
wolfdale 1333 D667 motherboard
razor baracuda sound card
voltec video card GeForce 8500 GT
Samsung Syncmaster T260 monitor
2 gb ram
Apache server
Mysql
PHP
UltraEdit 

I would like to add a dvd reader burner/cd burner and a additional 500gb hard drive.
I read the mob instructions and currently the hard drive is plugged into the sata of the motherboard.
which there is two plugins for that.
Can I use the current ribbon cable connected to the dvd drive and install the dvd/cd burner with the black connection, then the 500gb hard drive to the grey. and to the board with the blue. Will the startup find the orginal installed hard drive an boot from that?
I'm new to all this and so far I have migrated this setup from a xp pro software enviroment.

---

### Post by halitech on 2009-12-26
if this is your motherboard, you should have 4 sata ports and 1 IDE port

[http://www.asrock.com/MB/overview.asp?Model=Wolfdale1333-D667](http://www.asrock.com/MB/overview.asp?Model=Wolfdale1333-D667)

If you mean can you remove the dvd drive (I'm assuming dvd rom and that it is being removed) then add 2 new IDE devices, then yes it should work as long as you set the jumpers on the drives properly. Personally, if you haven't bought the devices yet, I'd go sata for the new drives, transfer speeds will be faster and no need of worrying about proper configuration.

---

### Post by leef on 2009-12-26
It should do, usually the bios is set to boot the first drive on the sata bus which should be the hdd that was originally installed unless you removed it or changed the order. Either way there is no harm in booting to find out.

---

### Post by bicyclerider on 2009-12-26
Thats the motherboard. it also points out the ata connection supports two devices. the dvd rom and the 500gb hard drive? I have two extra hard drives that need homes a 140 and a 500. So the 500 is my first choice. Any recommendations for cd/dvd burner??

---

### Post by halitech on 2009-12-26
If you already have the 500gig IDE drive then yes, you can put it and the dvd rom on the ata connection. Just make sure you jumper them correctly. As far the dvd/cd burner, pretty much any should work. I've got an LG GH22NS30 that has been working properly for over a year now and has burned probably over 200disks easily.

---

### Post by bicyclerider on 2009-12-26
Well I attached the drive to the previously mention location. At first the drive didn't show up. I took off the jumper completely and rebooted. documentation for the hard drive explained that it would show up as master unless the jumper was removed. Everything then showed up. I'm a little confused, I now show two diffrent master boot record hard drives. Of course I had previously installed a version of ubuntu 9.10 on the 400 gb hard drive but decided not to use for system drive but for data storage. So what steps should I do to rename and erase all the data on the device and have it register as a storage device?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141310&stc=1&d=1261887589[/IMG]

---

