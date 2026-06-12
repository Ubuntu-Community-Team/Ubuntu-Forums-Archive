---
title: "do i need to have internet to install testdisk?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by rasunin on 2009-12-14
hi. i am new here and totally new to Ubuntu.

i had just installed Ubuntu 9.10, the latest version.
i am able to dual boot with no problems.

Right now, i would like to install TestDisk.

However, each time i type "sudo apt-get install testdisk"
it returns with "......no package...."

i had installed Ubuntu with the choice of giving it 10GB of space,
since im not so sure what it does, in case it also implies that extra programs
will be installed.

i have went to [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
and downloaded:


[LIST]
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2"), kernel  2.6.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux24.tar.bz2"), kernel  2.4.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/rpm.png[/IMG] Linux [i386 RPM]("http://www.cgsecurity.org/testdisk-6.11.3-1.i386.rpm")
[/LIST]
i have absolutely no idea how am i suppose to install/execute those.
i did fiddle around and tried opening a few files, hoping something would happen.
but nothing so far.

can anyone help me???

---

### Post by Hetepeperfan on 2009-12-14
Hi,

In order to use 'apt-get' internet is recommended. It might be easier to connect to internet and then use :
system>administration>synaptic 
And search for for your Package. Note that this also requires internet.

---

### Post by lavinog on 2009-12-14
You need to be connected to the internet to use apt-get.
You also need to enable the universe reposistory first.

or you can download the deb file.
download it from here: [http://packages.ubuntu.com/karmic/testdisk](http://packages.ubuntu.com/karmic/testdisk)
Make sure you download the right architecture (64bit/386)

---

### Post by lavinog on 2009-12-14
Also why do you want to install testdisk?
Are you wanting to recover lost files? If so, you should be using a live cd to do that because putting anything on your drive ruins your chance at recovering the files.

---

### Post by rasunin on 2009-12-14
WOW!!! Fast replies. i never had that for a long time already.
MANY THANKS!!!

okay...so i guess i really do need internet to get it
alright!

so there's a difference in chance for running testdisk from a LiveCD then from a internal HDD? because at the moment, i am testing out Ubuntu to see if my chances of recovering my files from my external hard disk are still...well... to see if i still have a chance.

my external hard disk suffered from a very bad...Bad Blocks/Sectors.
it freezes Windows XP and even Ubuntu when i plug in my external HDD and i try to enter one of the folders.

the thing is...so far...Ubuntu was at least able to let me see the Root Directory of my Ext HDD, which Windows XP couldn't! 

i manage to LUCKILY save a very small notepad file. after that few seconds, it freezes until i disconnect the USB cable.

---

### Post by lavinog on 2009-12-14
ok if it is a external drive it should work then.
i would also get ddrescue to try and save an image of the drive, and use the image to recover from.  photorec is part of the testdisk package, and is really good at recovering files, but if the hard drive is suffering from mechanical issues it is best to recover from an image.
the command from the ddrescue package is 
```
dd_rescue /dev/sd# imagefile
```
where  /dev/sd# is the device file for the external drive (might be /dev/sdb)

Is your external drive clicking?

---

### Post by Hetepeperfan on 2009-12-14
Well if an external HD is the problem you might just as well install testdrive, on your internal HD for then you won't overwrite your data.

---

### Post by rasunin on 2009-12-14
> **lavinog said:**
> ok if it is a external drive it should work then.
i would also get ddrescue to try and save an image of the drive, and use the image to recover from.  photorec is part of the testdisk package, and is really good at recovering files, but if the hard drive is suffering from mechanical issues it is best to recover from an image.
the command from the ddrescue package is 
```
dd_rescue /dev/sd# imagefile
```where  /dev/sd# is the device file for the external drive (might be /dev/sdb)

Is your external drive clicking?

clicking as in it *beeps ...make noises?
**[EDIT]** did a research on "clicking". no...my ext hdd doesn't clicks
whenever i connect the ext HDD, its always like this in this pattern:

1st 10 secs green color
next 3-5 secs red color
2nd 10 secs green color
next 3-5 sec red color

like as though its reading and then stops reading, read again and then stops again...repeating in a cycle over and over.

that is what happens when i connect my EXT hdd for the first time in Ubuntu.
when i unplug it and plug it back for the 2nd time, it doesn't reads or detect my ext hdd.
until i restart my computer.

many thanks for those tips. an image...sounds like i will be needing it...really really needing it. :)

---

