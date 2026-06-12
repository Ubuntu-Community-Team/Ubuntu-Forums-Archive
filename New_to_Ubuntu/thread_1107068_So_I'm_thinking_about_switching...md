---
title: "So I'm thinking about switching.."
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Break-Formula on 2009-03-26
I currently have a Dell Inspiron something.. I forget. It'a s single core 3.4ghz processor with 2gigs of ram and a 320gb hard drive..
 I want to keep the 320gb in it and run windows.. but I want to try Linux out because it's so much more efficient and no viruses.. 
I have a 40gb laptop hd not being used..Is there anyway to convert that to use?? or what I need some ideas and help please, thank you.

---

### Post by bwhite82 on 2009-03-26
Yes, it can be installed on that HD. If its installed in the machine already, its as simple as popping in an Ubuntu CD and selecting it as your install drive.

---

### Post by azmo35 on 2009-03-26
Hi, you have this options available to you first, you can use [wubi]("http://wubi-installer.org/")or becaose you have a big HD you can make room for the Linux distro by follow the steps of the live CD.

---

### Post by spcwingo on 2009-03-26
If I were in your position I would defrag the win partition and resize it to leave open ~50MB.  Then hit up ebay for a 2.5" HDD enclosure, when that came in slap in the old 40GB HDD and partition it with about 2GB swap and the rest to the linux native filesystem of you choice.  When installing you're offered to do manual partitioning.  Choose to format the 50MB partition on the internal to the linux native filesystem of your choice and select the option to mount it as /boot.  Lastly, choose the linux native partition on your new external and select the mount point of / (root).  The reason I would do it this way is so the machine will boot no matter if the external is plugged in or not.  Alternately, you could just resize the win partition and free up enough space to install to the internal and just use the new external as shared NTFS storage.

---

### Post by nothingspecial on 2009-03-26
> **Break-Formula said:**
> I currently have a Dell Inspiron something.. I forget. It'a s single core 3.4ghz processor with 2gigs of ram and a 320gb hard drive..
 I want to keep the 320gb in it and run windows.. but I want to try Linux out because it's so much more efficient and no viruses.. 
I have a 40gb laptop hd not being used..Is there anyway to convert that to use?? or what I need some ideas and help please, thank you.

320gb is plenty of room to run both ubuntu and windows as a dual boot - you only need a few gigs for each operating system.

Follow [COLOR="Magenta"][this guide]("http://www.psychocats.net/ubuntu/dualboot")[/COLOR] to set up your system.

When you boot your pc you`ll be asked weather you want Ubuntu or windows.

Oh yes and

[SIZE="5"][COLOR="Red"]BACK UP ALL YOUR DATA[/COLOR][/SIZE]

Just in case.

---

### Post by mhh91 on 2009-03-26
you won't need more than 10 gigs of your HD for ubuntu :)

---

### Post by raymondh on 2009-03-26
Another option is  Virtualization.  VMware has a free player as well as an "appliance center" that gives you OS apps to download ind install.  You can try this to learn which linux distro you'll want to use.

I have VMWare fusion in my Mac so I can run just a few windows' apps/websites.   I have not tried the free player in my MSI Wind as it is already 3-boot OSX, Ubuntu 8.10 and XP.  Again, the XP only for a few those darn educational sites that require IE.

Good luck.

---

### Post by Break-Formula on 2009-03-26
Well.. I would like to keep my desktop hdd from being used.. And the laptop is broke anyway (It's 40gb hd still works just fine).. So is there anyway I could just erase that hdd and use it on my desktop.. But w/ ubuntu??

---

### Post by markharding557 on 2009-03-26
dell is well supported on ubuntu and its installer will preserve windows so don't worry install and give it a go,you will never look back i didn't and have been using ubuntu and debian for four years now.

---

### Post by spcwingo on 2009-03-26
> **Break-Formula said:**
> Well.. I would like to keep my desktop hdd from being used.. And the laptop is broke anyway (It's 40gb hd still works just fine).. So is there anyway I could just erase that hdd and use it on my desktop.. But w/ ubuntu??

The only other way is if you have an adapter to mount the 2.5" HD in an open 3.5" bay.  Just make sure that you reset the jumpers on the Win drive to slave and set the Ubuntu drive to master and install accordingly.  Those adapters can be found here:

[http://www.geeks.com/details.asp?invtid=HD-108&cat=HDD]("http://www.geeks.com/details.asp?invtid=HD-108&cat=HDD")

That way if you decide you don't like Ubuntu (I highly doubt that you won't) just remove the 2.5" HDD set the Win Drive jumpers back to master, adjust IDE cable arrangement (assuming both are IDE), and your Win only again.

---

### Post by Break-Formula on 2009-03-26
Sorry if I sound like a total noob.. 
So I can't like just put the 40gb in an enclosure.. and use it from there?? 
It's a normal Laptop hdd.. and it isn't being used. and I wanted to try ubuntu.. soooo.
I want to try and keep my desktop hdd on Win. 
And the Laptop hdd on Ubuntu. Bc it's more efficient and no viruses.
Just whatever you think is best for me to run Ubuntu. and enjoy all the elegances of Ubuntu. Just tell me and I'll try to get it done. I have a boot cd.. its 7.1...
I have 41gb left on my desktop. and the Laptop i can fully erase and have all of it.. But whatever ya'll think is best..
Sorry I sound so. "noobish"

---

### Post by markharding557 on 2009-03-27
trying to use a laptop hd in a desktop is not simple because the laptop hd is smaller.
so i would recomend you allow the ubuntu installer to divide your existing hd,it will recognize and configure the boot loader so you can still boot windows.
this has been done by vast numbers of people without any problems.

---

### Post by kanikilu on 2009-03-27
> **Break-Formula said:**
> So I can't like just put the 40gb in an enclosure.. and use it from there?? I haven't done this myself, but it's possible, here's a guide to installing on an external USB drive: [http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/) (it refers to 7.04, but I don't see why you wouldn't be able to use hardy or intrepid).

Also, another option would be to use VirtualBox or VMWare and just keep the disk image file on your external hard drive so you don't take up space on your main HD.

---

