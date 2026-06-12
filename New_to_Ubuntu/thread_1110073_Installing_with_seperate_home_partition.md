---
title: "Installing with seperate home partition ?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by lightnin on 2009-03-29
ok, so I've use ubuntu for about a year or so and like it.

I'm upgrading to 8.10 with a fresh install.

This time I want to keep my home seperate, but didn't see the option in the installation.

at the moment, I have a 10Gb drive to play with, and have installed 8.10 on it.  

I still have my old drive with my old home on it.

Can I just point my new 8.10 setup to use my old 7.10 home foldr on the other drive ?

Thanks

Rich

---

### Post by cariboo on 2009-03-29
When you get tot the partitioning section of the install you have to manually create a home partition. With only 10Gb I would suggest at least 5Gb for / and split the rest between /home and /swap.

You can mount the home partition on your other drive as /home, but if you still have 7.10 configuration files in you home directory you may run into a few problems.

For example to mount you /home partition in your new installation you would mount it like this in fstab:

```
# /home was on /dev/sdb2 during installation
UUID=7c109a7f-b7fd-402d-aec5-0ee7dd30d37a /home           ext3    relatime        0       2
```

To find the uuid of you /home partition in a terminal run:

```
blkid
```

Jim

---

### Post by lightnin on 2009-03-29
Thanks Jim 

the 10 Gb is just for me to 'play' with wihlst I am learning :)

ah - set the partition in manual mode ! thats why I didn't see it.


now you have made me think ... I want a seperate home partition / drive - so I can keep all my files settings and 'stuff' every time I uprade ubuntu.

if it is going to cause problems, maybe I have the wrong idea ???

what should I be doing ?

---

### Post by philinux on 2009-03-29
It's easier to start from fresh.

If you want to do this make a backup of all important stuff.

Reinstall and choose manual partitioning. Delete existing partitions then create three

/  about 6 gig is enough. Mine is set to 12 as i have a large disk.
/swap
/home will be the rest of the available space.

These are located under mount point and there is a drop down to choose them. I'd stick with ext3 for now to. Once installed copy back your important stuff.

---

### Post by lightnin on 2009-03-29
so each time I 'upgrade' (with a fresh installation)  - I need to re load all and any programs / bookmarks / passwords / etc 

that doesn't sound very efficient ???

isn't there a 'correct' way to keep your setup how you want it ?

---

### Post by philinux on 2009-03-29
For a reinstall you can use synaptic to create a list of installed files and then use that to reinstall, file>save markings as> ticking save full state. Dead easy. Or back up apt's cache. Aalso when doing a reinstall you select NOT to format the home partition thereby all program settings are prerserved.

Upgrading is not a problem no need to reinstall anything.

---

### Post by SuperSonic4 on 2009-03-29
bookmarks will be stored in ~/.mozilla so all your bookmarks and extensions and saved passwords should stay if you use firefox. You do have to install your programs again but you could make a script to install your favourite programs looking through Synaptic and marking the ones you've installed.

never mind, the guy above me has better advice XD

---

### Post by lightnin on 2009-03-29
cool ! useful info ! :D

I kept my old drive intact so I can go back and do it properly when I know how !

the reason I didn't just 'upgrade' is that I tried 7.10 to 8.04 upgrade and it didn't work.  When I asked - I got the answer that it was best to start again, but keep your home directory.

---

