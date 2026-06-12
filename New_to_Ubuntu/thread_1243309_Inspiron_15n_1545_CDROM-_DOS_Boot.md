---
title: "Inspiron 15n/ 1545 CDROM- DOS Boot"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by OooBuntuRox on 2009-08-18
Hello everyone,
 
It has been ages since i've made any type of boot disk. I am trying to make a floppy boot disk that can then be used to create a bootable CD/ DVD.
 
I can create the boot floppy without problems. It is the DVD rom disk drivers i seem to be missing. I really need a walk-through on creating a boot floppy with dvd support for the Inspiron 15n/ 1545
 
I can boot from a floppy or a CD right now, but all I can access on the Cd is the boot portion or the A:\ Drive. So, I need a hand locating and installing the CD rom drivers for the Inspiron 15n/ 1545 laptop.
 
I have a win98SE boot disk but it does not recognize the DVD. I think that it may be a SATA drive or scsi. But the drivers included with WinSE don't recognise the drive and no support is installed.
 
I would much prefer CD/ DVD support. The USB installs are much to SLOW.
 
Thanks, OooBuntuRox :guitar:

---

### Post by am256 on 2009-08-18
I don't know if this is really going to help you or not, but [M$'s database]("http://support.microsoft.com/kb/188513") lists what types of DVD adapters work.

[Dell Inspiron 1545 Drivers Download Page]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&ServiceTag=&SystemID=INSPIRON1545&os=WLH&osl=en&catid=&impid=")  <---maybe that is helpful


And as far as I know, I thought Win98 boot discs only contains the basic drivers for most CD-Rom drives, but not DVD.   I don't know if you're using Win98 for any particular reason, but I would suggest trying to install Win98 through the VirtualBox to see if you can mount the DVD drive using the VirtualBox settings.  Also, WinXP has the ability to run particular programs in previous versions of Win (in case you are installing 98 for the sole reason of running particular progs.).  I hope this helps, if not - maybe provide some more specific reasons that you are trying to install Win98 to see if I can have some more direction to my solution.

---

### Post by OooBuntuRox on 2009-08-18
> **am256 said:**
> I don't know if this is really going to help you or not, but [M$'s database]("http://support.microsoft.com/kb/188513") lists what types of DVD adapters work.
 
[Dell Inspiron 1545 Drivers Download Page]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&ServiceTag=&SystemID=INSPIRON1545&os=WLH&osl=en&catid=&impid=") <---maybe that is helpful
 
 
And as far as I know, I thought Win98 boot discs only contains the basic drivers for most CD-Rom drives, but not DVD. I don't know if you're using Win98 for any particular reason, but I would suggest trying to install Win98 through the VirtualBox to see if you can mount the DVD drive using the VirtualBox settings. Also, WinXP has the ability to run particular programs in previous versions of Win (in case you are installing 98 for the sole reason of running particular progs.). I hope this helps, if not - maybe provide some more specific reasons that you are trying to install Win98 to see if I can have some more direction to my solution.
 
Hello am256,
 
The win98SE boot disk is more like a DOS boot disk. So I would actually need a driver for the dvd drive to work with dos. I tried to install DR-Dos 7-03 and PC-DOS to see if that would fix it. But I hit problems there too.
 
Along the way,  I also found this Dell Ubuntu 9.04 factory image for download: 
[http://linux.dell.com/files/ubuntu/jaunty/iso-images/ubuntu-9.04-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/jaunty/iso-images/ubuntu-9.04-dell-reinstall.iso)
 
 So I was thinking of looking to see if Dell also offers a Dell FreeDos factory image for the 15n/ 1545.
 
What I am trying to do is create a DOS boot disk that allows access to the dvd rom drive so i can run utilities, etc from the DVD rom drive while in DOS mode. I want to be able to run/ install programs from the dos environment without having any other operating systems installed. So I can boot and image/ restore the drive, etc.
 
While it seems possible to do this from a USB stick it takes MUCH more time. What takes minutes from the DVD may takes a number of hours to transfer from the USB stick.
 
Also, I'm not familer enough with linux to be doing it that way. Basically, I want to be able to start with a clean Hard Drive and Boot from a DOS floppy. Old School :-k
 
Thanks so far. If you have any other thoughs I'd appreciate it!
 
 OooBuntuRox:guitar:

[SIZE=3]Solved:
For anyone who finds this thread, The problem turned out to be the lack of scsi drivers for dos. I went with a DOS bootable USB drive then added Utilities as needed.[/SIZE]

---

