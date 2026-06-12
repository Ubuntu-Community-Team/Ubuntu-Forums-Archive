---
title: "Toshiba external Hard drive"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by toonage531 on 2011-05-09
Hey everybody, im fairly new to Linux OS's
anyways
i got a Toshiba Canvio 500 GB external hard drive with the hope of putting Ubuntu 11.04 on it, also i am running on a HP pavilion dv6
so i downloaded the OS and burned it onto a CD and everything was fine
when i went to install it to the HD i plugged it in and clicked "something else" for the allocated drivers
ok
heres how i partitioned the HD
i had 100MG set aside for swap space and i set the type as swap area (/dev/sdb1)
then i had the rest of the HD as 
[U][U]Primary
Ext4
Beginning 
/[/U][/U]
(/dev/sdb2)
i clicked install and it went to work
but when it was all finished and i restarted the computer, the only thing it gave me was a "Read Error"
and i restarted a couple of times and thats still all it gave me

if someone could please help me out, and tell what im doing wrong it would be much appretiated!
thankyou

---

### Post by Naggobot on 2011-05-09
You are sure that you are on the correct forum :P

I have few suggestions but no absolutes. 

1. Check that the files are actually installed to the hard disk. 
2. Check that you installed to correct hard disk. 

What worries me a bit is that does the Grub know to install the boot sector to external HD with out messing the local hard drive? I remember reading some older instructions about installing to external disk and those instructions suggested removing the internal hard disk prior to installation to make sure that every thing installs to external HD. 

Also you might benefit from 

[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

So the question is that are you sure your computer can actually boot from external HD?

Good luck with your endeavors.

---

### Post by fabricator4 on 2011-05-09
> **toonage531 said:**
> it gave me was a "Read Error"


I think the problem is that grub is not being read, which could mean it isn't there, or that the BIOS is not successfully booting off the USB HDD

Please boot off the LiveCD and run the boot info script.  Leave the external HDD plugged in while you do this.

Instructions for running the boot info script [are here]("http://bootinfoscript.sourceforge.net/").

Also check your BIOS again.  Some have both a 'boot order' and a 'boot device priority' setting. Some BIOS's also let you enter a boot menu after post where you can definitively select the boot device you want.  This is often a keypress such as <Esc> or <F1>


Chris

---

### Post by northwestern on 2011-05-09
I succesfully run Ubuntu 11.04 from an external Buffalo 500gb ministation external hard drive on my HP laptop (DV5), I used the following web site for details.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
 
Best to change your boot start up selection in the BIOS to internal hard drive last.
 
Regards
Northerner

---

