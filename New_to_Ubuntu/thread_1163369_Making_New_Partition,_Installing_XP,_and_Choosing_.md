---
title: "Making New Partition, Installing XP, and Choosing OS on Startup?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by LikwidSteel on 2009-05-18
I'm sure that there is a way to do this. I want to make a new partition, install XP on the new partition, and then have the option to choose which OS to boot to on startup like when you install Windows first. Can anyone describe how to do this step by step so I don't screw anything up, thank you. =] I don't even know how to create a partition in the first place, so any help is welcome. BTW, I need to do this to get VB6 installed, and I would like to play games without all the hassle of Wine.

---

### Post by billgoldberg on 2009-05-18
The first thing to do is back up any data you can't replace, just to be on the safe side.

Now you will have to download a copy of Super Grub Disk, to easily repair the Grub after you are done installing Windows. 

If you don't have a spare cd lying around, you could use a flash disk and use the application Unetbootin to copy the iso to the flash drive.

If that is impossible, you can always use the Ubuntu live cd to repair Grub, but that will involve some terminal commands.

Now on to the partitioning.

Grab your Ubuntu live cd and boot into it.

Press "alt+f2" and in the application launcher, enter 

```
gksu gparted
```

Gparted is an paritioning tool.

Here is a youtube video explaining the process of partioning a hdd with gparted:[http://www.youtube.com/results?search_type=&search_query=gparted+new+partition](http://www.youtube.com/results?search_type=&search_query=gparted+new+partition)

Just make sure you don't format your linux partitions.

After that is done, you can install Windows.

Make sure to install it on the partition you created with Gparted.

If you didn't format the new partition as NTFS, you can still do so in the Windows installer.

After it's done, you can use the Super Grub Disk to repair the grub. It's easy to use, don't worry, you'll figure it out.

Dualbooting should work straight OOTB box, if that isn't the case, let us know.

If you can't use the Super Grub Disk, let us know for manual instruction to repair the Grub.
--

Tip:

It's a good idea to make sure you get the drivers for windows you'll be needing before you install it.

After it's installed, just pop in the cd/usb drive with the drivers so you don't have a super small resolution while surfing to the various sites you'll need to get them from.

---

### Post by LikwidSteel on 2009-05-18
> **billgoldberg said:**
> The first thing to do is back up any data you can't replace, just to be on the safe side.

Now you will have to download a copy of Super Grub Disk, to easily repair the Grub after you are done installing Windows. 

If you don't have a spare cd lying around, you could use a flash disk and use the application Unetbootin to copy the iso to the flash drive.

If that is impossible, you can always use the Ubuntu live cd to repair Grub, but that will involve some terminal commands.

Now on to the partitioning.

Grab your Ubuntu live cd and boot into it.

Press "alt+f2" and in the application launcher, enter 

```
gksu gparted
```Gparted is an paritioning tool.

Here is a youtube video explaining the process of partioning a hdd with gparted:[http://www.youtube.com/results?search_type=&search_query=gparted+new+partition](http://www.youtube.com/results?search_type=&search_query=gparted+new+partition)

Just make sure you don't format your linux partitions.

After that is done, you can install Windows.

Make sure to install it on the partition you created with Gparted.

If you didn't format the new partition as NTFS, you can still do so in the Windows installer.

After it's done, you can use the Super Grub Disk to repair the grub. It's easy to use, don't worry, you'll figure it out.

Dualbooting should work straight OOTB box, if that isn't the case, let us know.

If you can't use the Super Grub Disk, let us know for manual instruction to repair the Grub.
--

Tip:

It's a good idea to make sure you get the drivers for windows you'll be needing before you install it.

After it's installed, just pop in the cd/usb drive with the drivers so you don't have a super small resolution while surfing to the various sites you'll need to get them from.
Okay, thank you very much, one question, will any problems arise if I don't install Windows into the C: ? I know that I've had Windows install into the I: and H: before and while trying to install the drivers it gave me an error of not having a C: to install to, does a lot of software need to install to the C: ? I plan on making this the D: and installing there.

---

### Post by billgoldberg on 2009-05-18
> **LikwidSteel said:**
> Okay, thank you very much, one question, will any problems arise if I don't install Windows into the C:? I know that I've had Windows install into the I: and H: before and while trying to install the drivers it gave me an error of not having a C: to install to, does a lot of software need to install to the C:? I plan on making this the D: and installing there.

Any partition you install Windows on will be called C.

---

### Post by LikwidSteel on 2009-05-18
> **billgoldberg said:**
> Any partition you install Windows on will be called C.
You just made me feel stupid... =[ lol, I really do feel like an idiot, thanks.

---

