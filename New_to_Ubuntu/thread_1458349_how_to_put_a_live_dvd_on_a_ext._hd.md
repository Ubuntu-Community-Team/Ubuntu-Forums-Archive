---
title: "how to put a live dvd on a ext. hd"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by racerrandy on 2010-04-19
Hello all, I have a netbook that I would like to put ubuntu on but no ext. dvd drive. I have a ext. hd and would like to put the disc on and boot it that way. Is this possible? I am using ubuntu on my toshiba laptop and it has usb creator and gparted on it. I am pretty new to computers and don't want to screw up and trash my music and files already on the ext hd. I could go buy a flash drive but already have the ext. hd. Thanks in advance for the help!



Randy

---

### Post by undecim on 2010-04-19
You can do with Unetbootin (from Windows or Ubuntu) or with the USB Startup Disk Creator (Ubuntu).

If the drive is already formatted as FAT, then it won't erase the drive.

---

### Post by carl4926 on 2010-04-19
or use dd

```
dd if=image.iso of=/dev/sd? bs=M4;sync
```

replace image.iso with actual .iso name

---

### Post by cuberts on 2010-04-19
> **racerrandy said:**
> Hello all, I have a netbook that I would like to put ubuntu on but no ext. dvd drive. I have a ext. hd and would like to put the disc on and boot it that way. Is this possible? I am using ubuntu on my toshiba laptop and it has usb creator and gparted on it. I am pretty new to computers and don't want to screw up and trash my music and files already on the ext hd. I could go buy a flash drive but already have the ext. hd. Thanks in advance for the help!



RandyOn net books you actually have to run a virtual machine before you can actually install it itself. Go to this link : [http://www.5starsupport.com/tutorial/install-virtual-machine.htm]("http://www.5starsupport.com/tutorial/install-virtual-machine.htm")
I hope it helped.

---

### Post by k3lt01 on 2010-04-20
> **racerrandy said:**
> Hello all, I have a netbook that I would like to put ubuntu on but no ext. dvd drive. I have a ext. hd and would like to put the disc on and boot it that way. Is this possible? I am using ubuntu on my toshiba laptop and it has usb creator and gparted on it. I am pretty new to computers and don't want to screw up and trash my music and files already on the ext hd. I could go buy a flash drive but already have the ext. hd. Thanks in advance for the help!



Randy

Take a look at [this]("http://ubuntuforums.org/showthread.php?t=1288604").

Personally I'd just get a flash drive and put it on that to install, this is because you have files you don't want to loose and I doubt you want to risk it.

---

### Post by racerrandy on 2010-04-20
Ok, I did use the usb creator and put the live dvd on my ext. hd. When I booted it with my netbook it ended up at a dos prompt that said boot_

I am assuming this is because of no grub maybe?

I will pick up a 8gb flash drive tomorrow, they are pretty damn cheap these days. 

I am not totally giving up on the ext. hd, I basically try to do stuff like this to learn more about computers. Kinda sad, I am 43 and most teenagers probably know more that I do about computers. LOL!


I will let you know how it works out. 




Randy

---

### Post by k3lt01 on 2010-04-20
Randy, I have a 500 gb Seagate ext hdd that I have setup to do this exact same thing. The difference is my hdd is for just this purpose. I can use it to boot to a LiveCD so I can install and then  use a repository folder to update with. I have nothing else on my hdd apart from Ubuntu specific materials.

I also have a 2 gb flash drive for installs as well.

---

### Post by racerrandy on 2010-04-20
> **k3lt01 said:**
> Randy, I have a 500 gb Seagate ext hdd that I have setup to do this exact same thing. The difference is my hdd is for just this purpose. I can use it to boot to a LiveCD so I can install and then  use a repository folder to update with. I have nothing else on my hdd apart from Ubuntu specific materials.

I also have a 2 gb flash drive for installs as well.


I would like to do the same thing, I will put my music in another drive and empty it out. Can you put several different distros on it then choose which one to install? Tell me how you accomplish this if you don't mind. Thank you. 



Randy

---

### Post by k3lt01 on 2010-04-20
> **racerrandy said:**
> I would like to do the same thing, I will put my music in another drive and empty it out. Can you put several different distros on it then choose which one to install? Tell me how you accomplish this if you don't mind. Thank you. 



RandyTake a look at the link I posted in my initial post. With regards to the repositories I created a repository folder after I followed that thread I linked to and put the relevant repositories in it.

---

### Post by racerrandy on 2010-04-20
> **k3lt01 said:**
> Take a look at the link I posted in my initial post. With regards to the repositories I created a repository folder after I followed that thread I linked to and put the relevant repositories in it.

Sorry I missed the link on your first post. I am going to get a flash drive for now, but will take on your tutorial as a project. I am trying very hard to learn the linux way, but there is a lot to digest. Thanks for the help. 



Randy

---

