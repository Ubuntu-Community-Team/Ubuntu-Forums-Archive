---
title: "help installing to an antique system"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2009-08-23
it has 256 ram 
8 meg shared memory (min 2)
but it will not let me install because 248 is less than 256
to my understanding the bare minimum is like 128 ram vs windows xp 256
how can i override the 256 requirment
the audo player even lass every now and then on xp 
[[IMG]http://i41.tinypic.com/24g0wb8_th.jpg[/IMG]]("http://i41.tinypic.com/24g0wb8.jpg")
(the thought of using the video card would give you night mares) 1 gif + mouse moving quickly = lag
unetbootin's boot menu will not even load on it
tried it with DSL and puppy linux
system does not support usb boot

---

### Post by snowpine on 2009-08-23
Ubuntu won't work well with only 248mb of ram; I would not recommend it. You could try installing using the Alternate CD I suppose (but I still wouldn't recommend it).

DSL and Puppy are good choices; what happened when you tried them?

---

### Post by pqwoerituytrueiwoq on 2009-08-23
boot failed with unetbootin
it cant be worse than windows xp with 248 ram

---

### Post by snowpine on 2009-08-23
> **pqwoerituytrueiwoq said:**
> boot failed with unetbootin

Of course it won't work if your computer can't boot from USB... what about burning a CD?

---

### Post by pqwoerituytrueiwoq on 2009-08-23
used the hard drive
did not have a cd
it has a 95 meg zip drive could not get it to boot from it (try to)

---

### Post by ajgreeny on 2009-08-23
Get another 256 or more ram and you may be OK, but 256 with shared memory will not work very well at all.
Crunchbang, based on ubuntu but with a very light DE would be worth trying, or even the minimal install CD from here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and add lxde or another lightweight DE of your own choosing.

---

### Post by pqwoerituytrueiwoq on 2009-08-23
adding ram to it crashes it 
it was built for 512 :(

---

### Post by Liolikas on 2009-08-23
Better try:
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by argos3016 on 2009-08-23
Or use an light-weight distro, than Puppy Linux or Damm Small

---

### Post by halitech on 2009-08-23
Unetbootin doesn't require you to create a bootable usb drive, its just 1 option. 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Features

> UNetbootin can create a bootable Live USB drive, or it can make a "frugal install" on your local hard disk if you don't have a USB drive. It can load distributions by automatically downloading their ISO (CD image) files, or by using existing ISO files, floppy/hard disk images, or kernel/initrd files, for installing other distributions. 

---

### Post by running_rabbit07 on 2009-08-23
> **Liolikas said:**
> Better try:
[http://www.xubuntu.org/](http://www.xubuntu.org/)

+1 Xubuntu will work fine on that.

---

### Post by pqwoerituytrueiwoq on 2009-08-23
as i said before i tried unetbootin like that

---

### Post by running_rabbit07 on 2009-08-23
If you can get a hold of an external CD drive you can use it to start the install process.

---

### Post by halitech on 2009-08-23
well, you say Unetbootin won't work, no cdrom and no usb boot. Does it have a floppy drive that works? Can you take the drive out and install it in another machine with a working cdrom then put it back? (not the best way but should work)

---

### Post by pqwoerituytrueiwoq on 2009-08-23
cd drive is good no cd advaible downloading xubuntu now over 1hr left

---

### Post by halitech on 2009-08-23
you may want to get the alt install cd and not the live cd as it has lower requirements to get things running.

---

### Post by hackerseraph on 2009-08-23
> **running_rabbit07 said:**
> +1 Xubuntu will work fine on that.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

You're just above the minimum specs. I agree with going for xubuntu although puppy is not a bad idea at all but im just trying to push the ubuntu community along :P :lolflag:

---

### Post by Hallvor on 2009-08-23
Xubuntu is not that light. It is probably the heaviest of all XFCE distros.

If you want something light, have a look at this:

[http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

---

### Post by snowpine on 2009-08-23
> **pqwoerituytrueiwoq said:**
> cd drive is good no cd advaible downloading xubuntu now over 1hr left

So just to be clear, your thread would be [solved] if you had a blank CD?

---

### Post by pqwoerituytrueiwoq on 2009-08-23
not sure how to actually make the cd for puppy/dsl
---------------------
just got the file downloaded

---

### Post by ugm6hr on 2009-08-23
> **pqwoerituytrueiwoq said:**
> 
how can i override the 256 requirment

Create a swap partition first.

PS: You have not been very clear on the situation, which makes helping impossible.  I would suggest you summarise what you are trying to do, and in what circumstances.  Screenshots not necessary.

---

### Post by oldos2er on 2009-08-23
> **pqwoerituytrueiwoq said:**
> not sure how to actually make the cd for puppy/dsl
---------------------
just got the file downloaded

 Create it the same way you would for Ubuntu: [http://psychocats.net/ubuntu/burn](http://psychocats.net/ubuntu/burn)

---

### Post by pqwoerituytrueiwoq on 2009-08-23
i installed xubuntu on it took hours
@ugm6hr
just uploaded that picture a long time a go and did not remember the the stats so i search the tags i put on it on tinypic
had to change some bios setting for it to work 
changed these settings:
installed OS:
other
has (other,windows 95, windows 98)
shared memery:
2MB
has (2MB,6MB,8MB)
something else
other
has (other,DOS)

---

