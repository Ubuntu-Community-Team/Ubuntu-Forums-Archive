---
title: "NewB with a couple of questions"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Ernesto RD on 2009-07-21
Hi all, after trying out suse, fedora and debian, i installed ubuntu 9.04 a couple of weeks ago, and i absolutely love it!.
Its the only linux distro ibe seen that doesnt require you to be a computer mega-guru to use.
Thanks developers! :)

NE way, i have a couple of small issues with it and i hope some one can help me out...

1 - i installed the compizConfig manager (for desktop FX), and want to use the Shift Switcher or the Ring switcher to switch windows, but with either one of those, when i use it, ubuntu logs me out!, if i have say 3 or 4 windows, and i repetedly press SUPER - Tab to switch between windows, the screen turns black for a second, and then im at the login screen. its as if gnome crashed or something.
¿Any idea of what might be wrong? BTW, all other FX including cube desktop work perfectly.
FYI i have a ATI Radeon 9000 video card, and glxgears works perfectly (over 1000 fps)

2- I have 2 hard drives, on my computer, one (160GB) is for data storage, formatted in NTFS, and the other one (80GB) is the OS one, half of it is used by Windows XP (NTFS of course), and half by ubuntu. And i want to automatically mount both the NTFS partitions automatically at startup, so i installed the Disk manager package, and so i see both the drives (sda, and sdb) the 160GB NTFS is sda, and the 40GB windows partition is on sdb.
The problem is that if i go and configure the one in sda, say to mount on /media/IDE160 and use the wizzard, when i switch to sdb to configure the other partition on sdb, i get the same settings that i had for sda! (eg mount on /media/IDE160), and if i change these setting to say mount on /media/IDE40, when i go back to see the settings for sda, i see the configuration i made for sdb!
in other words, the program seems to want to treat both partitions as if they were the same.

3- I noticed you can have some sound effects in gnome, like beeps for message dialogs, a sound for emptying the recycle bin, etc. And i turned those on, but nothing happens. when a dialog box pops up with a message, or i empty the recycle bin, i get no sound at all. Even tho the sound system seems to work ok, i get sound on movies, rhytmbox, the login screen etc.
¿what im i doing wrong?

Any help appreciated.

---

### Post by Tman5293 on 2009-07-21
1. Change your key combination for switching windows.

2. Try using gparted to partition your drives. (cause I have no idea what this "Disk Manager Package" you installed is. 

3. IDK

---

### Post by acreech on 2009-07-21
> **Ernesto RD said:**
> Hi all, after trying out suse, fedora and debian, i installed ubuntu 9.04 a couple of weeks ago, and i absolutely love it!.
Its the only linux distro ibe seen that doesnt require you to be a computer mega-guru to use.
Thanks developers! :)

NE way, i have a couple of small issues with it and i hope some one can help me out...

1 - i installed the compizConfig manager (for desktop FX), and want to use the Shift Switcher or the Ring switcher to switch windows, but with either one of those, when i use it, ubuntu logs me out!, if i have say 3 or 4 windows, and i repetedly press SUPER - Tab to switch between windows, the screen turns black for a second, and then im at the login screen. its as if gnome crashed or something.
¿Any idea of what might be wrong? BTW, all other FX including cube desktop work perfectly.
FYI i have a ATI Radeon 9000 video card, and glxgears works perfectly (over 1000 fps)

2- I have 2 hard drives, on my computer, one (160GB) is for data storage, formatted in NTFS, and the other one (80GB) is the OS one, half of it is used by Windows XP (NTFS of course), and half by ubuntu. And i want to automatically mount both the NTFS partitions automatically at startup, so i installed the Disk manager package, and so i see both the drives (sda, and sdb) the 160GB NTFS is sda, and the 40GB windows partition is on sdb.
The problem is that if i go and configure the one in sda, say to mount on /media/IDE160 and use the wizzard, when i switch to sdb to configure the other partition on sdb, i get the same settings that i had for sda! (eg mount on /media/IDE160), and if i change these setting to say mount on /media/IDE40, when i go back to see the settings for sda, i see the configuration i made for sdb!
in other words, the program seems to want to treat both partitions as if they were the same.

3- I noticed you can have some sound effects in gnome, like beeps for message dialogs, a sound for emptying the recycle bin, etc. And i turned those on, but nothing happens. when a dialog box pops up with a message, or i empty the recycle bin, i get no sound at all. Even tho the sound system seems to work ok, i get sound on movies, rhytmbox, the login screen etc.
¿what im i doing wrong?

Any help appreciated.


For the beep sounds left click on the speaker icon on the top right and then click on the volume control. There will be a toggle in there for the beep. See what that level is.

---

### Post by The Cog on 2009-07-21
1: That does indeed sound exactly like gnome crashing abd being restarted automatically. Sorry I have no idea why though.

2: What is the package you are using there? Could it be pysdm? Anyway, it sounds very confused. You may have to set this up by editing the underlying configuration file /etc/fstab. Entries like this should work:
```
/dev/sda1 /media/IDE40 ntfs umask=0 0 0
/dev/sdb1 /media/IDE160 ntfs umask=0 0 0
```
**BUT** check the device numbers before using this.

You will also need to make the mount points:
```
sudo mkdir /media/IDE40
sudo mkdir /media/IDE160
```

and be careful editing that file. If you mess it up, your entire system may fail to mount and you might have to use the install disk to go back in and re-edit it. Make a backup first.

Oh, the easiest way to edit it is
```
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
```

---

### Post by Ernesto RD on 2009-07-21
Thanks for your reply.

> **Tman5293 said:**
> 1. Change your key combination for switching windows
I did, tried ATL+TAB, and a couple of others, same thing.

> **Tman5293 said:**
> 2. Try using gparted to partition your drives. (cause I have no idea what this "Disk Manager Package" you installed is. its pysdm. NeWay, i contacted the developer, and he thinks its a bug in pysdm.


> **Tman5293 said:**
> 3. IDKIDK?? :confused: :confused: :confused:

---

### Post by Ernesto RD on 2009-07-21
> **acreech said:**
> For the beep sounds left click on the speaker icon on the top right and then click on the volume control. There will be a toggle in there for the beep. See what that level is.Thanks for your reply. The left most slider on the volume controls (my ubuntu is in spanish, it sais "System speaker"), was muted and at its lowest level :redface:
Thanks!

---

### Post by Ernesto RD on 2009-07-21
> **The Cog said:**
> 1: That does indeed sound exactly like gnome crashing abd being restarted automatically. Sorry I have no idea why though.

2: What is the package you are using there? Could it be pysdm? Anyway, it sounds very confused. You may have to set this up by editing the underlying configuration file /etc/fstab. Entries like this should work:
```
/dev/sda1 /media/IDE40 ntfs umask=0 0 0
/dev/sdb1 /media/IDE160 ntfs umask=0 0 0
```**BUT** check the device numbers before using this.

You will also need to make the mount points:
```
sudo mkdir /media/IDE40
sudo mkdir /media/IDE160
```and be careful editing that file. If you mess it up, your entire system may fail to mount and you might have to use the install disk to go back in and re-edit it. Make a backup first.

Oh, the easiest way to edit it is
```
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
```Thanks for your help, it is pysdm, i contacted the developer, and he sais it might be a bug in the program.
I will give your sugestion a shot, and edit the fstab file.
Just one more question please, will those options (the umask part) give me write access to the partitions?

Thanks!

---

### Post by The Cog on 2009-07-21
> **Ernesto RD said:**
> 
I will give your sugestion a shot, and edit the fstab file.
Just one more question please, will those options (the umask part) give me write access to the partitions?

Thanks!

Yes is should do. Unless the partition is marked as not having been cleanly shut down, in which case it will be mounted read-only and you will have to chkdsk it in windows to clean it up again.

---

### Post by Ernesto RD on 2009-07-21
> **The Cog said:**
> Yes is should do. Unless the partition is marked as not having been cleanly shut down, in which case it will be mounted read-only and you will have to chkdsk it in windows to clean it up again.Perfect. Ill give it a try
Thanks for your help! :)

---

