---
title: "Getting Rid of Vista Partition"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-14
my vista gets a bsod upon startup even in safe mode today.  i am fed up completely with it and want to go to ubuntu as my main os and maybe install vista inside virtualbox just for the occasional use.  is there a way i can delete my vista partition and give it all to ubuntu?

---

### Post by stevoo on 2009-01-14
you can reformat the drive and keep that as another partition. 
I am not sure if you can merge them again .... but someone else might be sure.

---

### Post by mamamia88 on 2009-01-14
is there a simple way of restoring ubuntu to the exact configuration i have now if i was just to reinstall ubuntu over the entire drive?

---

### Post by Captain_tux on 2009-01-14
Be careful with Vista in virtual environments... unfortunately, it doesn't always behave very well.

---

### Post by mamamia88 on 2009-01-14
you think it would be worth buying a copy of xp from my college bookstore for $35 than?

---

### Post by dccrens on 2009-01-14
From within ubuntu you can use the partition editor to delete the vista partition. You can then recreate/format it for a partition under ubuntu. You can assign it a name like /data, or something else. If I remember correctly, you can also "grow" an existing ubuntu partition into the space left by vista. Look under System --> Administration --Partition Editor. It will run a program called GParted. Read the man page, or help first.

---

### Post by mamamia88 on 2009-01-14
thanks sounds simple enough i'll give that a try when i get home

---

### Post by drs305 on 2009-01-14
> **mamamia88 said:**
> is there a simple way of restoring ubuntu to the exact configuration i have now if i was just to reinstall ubuntu over the entire drive?

Don't know if you would consider it simple, but you could move your /home folder to it's own partition and then keep it during a new install of ubuntu. Here is a link to creating a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Unless you have a great deal of customization it may take longer to do this, and then move all your partitions around, than to do a new install and recreate your settings. You might consider creating a separate /home partition in your new install for future flexibility.

One note on repartitioning. If the ubuntu install is in an extended partition (in gparted, within the light blue bordered area) you will not be able to directly expand the ubuntu partition to claim any free primary partition space. You will first have to either move ubuntu into a primary partition or expand the extended partition to claim the free space, *then* expand the ubuntu partition.

As always, back up your important data files before doing any of this!

---

### Post by newbee70 on 2009-01-14
> **mamamia88 said:**
> is there a simple way of restoring ubuntu to the exact configuration i have now if i was just to reinstall ubuntu over the entire drive?

have you looked at remastersys?

---

### Post by mamamia88 on 2009-01-14
i think i will just reinstall ubuntu when i get home. think i will just make a copy of the desktop background i use and write down all the settings i have and install on the entire drive

---

### Post by drs305 on 2009-01-14
You can run the following commands to copy your installed app list and then import it to the new install. It won't carry over the personal settings but it will bring over the installed programs. The downside is that if there are apps that you have installed but don't really want on a clean install they will be present as well.

Create list and copy it somewhere that won't be reformatted during the new install:
```

dpkg --get-selections | grep -v  'deinstall'   > ~/Desktop/installed_packages.txt

```

Copy installed_packages.txt to the new install Desktop, then run:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections < ~/Desktop/installed_packages.txt 
sudo apt-get update 
sudo apt-get dselect-upgrade 

```

---

### Post by albinootje on 2009-01-14
> **mamamia88 said:**
> my vista gets a bsod upon startup even in safe mode today.  i am fed up completely with it and want to go to ubuntu as my main os and maybe install vista inside virtualbox just for the occasional use.  is there a way i can delete my vista partition and give it all to ubuntu?

As a complete Linux beginner I would recommend going for the dual-boot option, *and* first boot from a recent Ubuntu installation cdrom to check what works and what does not yet work on your machine with Ubuntu.

[http://releases.ubuntu.com/](http://releases.ubuntu.com/) Try both 8.04.1 and 8.10

What are the specifications of your machine ?
Processor, RAM, disk space, video card.

---

### Post by albinootje on 2009-01-14
> **mamamia88 said:**
> is there a simple way of restoring ubuntu to the exact configuration i have now if i was just to reinstall ubuntu over the entire drive?

Use CloneZilla or other disk cloning software.
The interface of CloneZilla is a little primitive looking, and it has a learning curve, but i like it very much for whole disk cloning and restoring.

[http://clonezilla.sf.net](http://clonezilla.sf.net)

---

### Post by RichardLinx on 2009-01-14
mamamia88 you could always just backup your home partition. If you do a reinstall you should put your /home folder on a seperate partition. That way you wont have to reinstall everything  when you reinstall.

---

