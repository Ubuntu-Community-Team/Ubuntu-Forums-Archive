---
title: "Please help, GNOME desktop goofed up"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by neo.patrix on 2009-07-13
Hi all,

I really need help with some strange problem

My laptop starts normally, I CAN login into my default GNOME desktop through GDM. But my GNOME does not seem to startup properly. It gets hanged on Blank Screen with a mouse pointer. Same is true with KDE, but it shows desktop background and Splash Screen with all startup icons.

I am able to login to "Failsafe GNOME" , but it works normally only seemingly. On logging in , it gives me error message for .ICEAuthority overwrite. After logging , some of the applications I start with error messages

Eg : Nautilus, Evolution gives some GConf nonsense

I am not able to edit my documents with OpneOffice, again something to do with Failsafe hopefully

So, basic problem is nice blank screen with GNOME desktop, I am blank as well since I DID NOT play around with system graphics like driver or xorg.cong or Compiz. It was just a simple restart since my notebook was on for about 3 days.

Please SOS, I don't like Blank screen, I would prefer if screams some error messages.

---

### Post by philinux on 2009-07-13
If you can open a terminal use this.

```
chown yourusername ~/.ICEauthority 
```

Please post back with any message terminal gives you.

---

### Post by neo.patrix on 2009-07-13
Actually I would not play with chown untill necessary .ICEauthority might be safegaurd when using Falisafe GNOME. I am not very sure.

Anyway update on error, It might get a bit scary

> 
E: core-util.c: Failed to symlink /home/patrix/.pulse/c994bd3a85aa1130a206c9f849e4a93c:runtime.tmp to /tmp/pulse-coqtR6wfb0EC: No space left on device
E: core-util.c: Failed to symlink /home/patrix/.pulse/c994bd3a85aa1130a206c9f849e4a93c:runtime.tmp: No space left on device


Now this does not look very nice, also. I had to check few other things. but first my disk configuration 

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        1642    13141170    7  HPFS/NTFS
/dev/sda3            1643        3626    15936480   83  Linux
/dev/sda4            3627       14593    88092427+   f  W95 Ext'd (LBA)
/dev/sda5            3627        8645    40315086    7  HPFS/NTFS
/dev/sda6            8646       12214    28667961   83  Linux
/dev/sda7           12215       14354    17189518+  83  Linux
/dev/sda8           14355       14593     1919736   82  Linux swap / Solaris

```

(Ya, it is bit... well... nvm)

Now my /home is /dev/sda6 & /dev/sda7 mounted as /usr

On checking with system monitor I get /home 69% filled. The partition is 26.8GB, it shows me 17.8GB used 9.1GB Free, 7.7 GB Available. 

Now when I check , with Nautilus for my home folder /home/patrix "CTRL+H", "CTRL+A", right-click properties it get 3.7GB as file size. I am the only user, so /home contains 3 folders patrix, lost+found & recycled(since I mount this partition is Windows XP using Ext2Fsd)

Any file operation that I try to perform gives me error like "No Space left on device", which I know is not true.

1) Should I panic? 

2) Is my hard-disk going to evaporate? 

It seems that GNOME & KDE desktop startup problem might just be symptom.

---

### Post by measekite on 2009-07-13
> **philinux said:**
> If you can open a terminal use this.

```
chown yourusername ~/.ICEauthority 
```Please post back with any message terminal gives you.

 Just curious as to what .ICEauthority is and does.

---

### Post by philinux on 2009-07-13
> **neo.patrix said:**
> Actually I would not play with chown untill necessary .ICEauthority might be safegaurd when using Falisafe GNOME. I am not very sure.

Anyway update on error, It might get a bit scary



Now this does not look very nice, also. I had to check few other things. but first my disk configuration 

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        1642    13141170    7  HPFS/NTFS
/dev/sda3            1643        3626    15936480   83  Linux
/dev/sda4            3627       14593    88092427+   f  W95 Ext'd (LBA)
/dev/sda5            3627        8645    40315086    7  HPFS/NTFS
/dev/sda6            8646       12214    28667961   83  Linux
/dev/sda7           12215       14354    17189518+  83  Linux
/dev/sda8           14355       14593     1919736   82  Linux swap / Solaris

```

(Ya, it is bit... well... nvm)

Now my /home is /dev/sda6 & /dev/sda7 mounted as /usr

On checking with system monitor I get /home 69% filled. The partition is 26.8GB, it shows me 17.8GB used 9.1GB Free, 7.7 GB Available. 

Now when I check , with Nautilus for my home folder /home/patrix "CTRL+H", "CTRL+A", right-click properties it get 3.7GB as file size. I am the only user, so /home contains 3 folders patrix, lost+found & recycled(since I mount this partition is Windows XP using Ext2Fsd)

Any file operation that I try to perform gives me error like "No Space left on device", which I know is not true.

1) Should I panic? 

2) Is my hard-disk going to evaporate? 

It seems that GNOME & KDE desktop startup problem might just be symptom.


Ah ok. Well in that case what does this output.

```
df -h
```

If it shows / as full then see this.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by neo.patrix on 2009-07-13
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              15G  1.1G   14G   8% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  124K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  160K 1007M   1% /dev
tmpfs                1007M   48K 1007M   1% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6              27G   18G  7.8G  70% /home
/dev/sda7              17G  5.7G  9.7G  37% /usr
/dev/sr0              699M  699M     0 100% /media/cdrom0

```

Nope / is not full, in-fact it will not get full untill Ubuntu 500.10 :lolflag: (by that time, atleast my laptop would be long dead, if I survive somehow), actually it has long awaited repartition process, which I never did.

Still why my /home has 18G used where as Nautilus shows only 3.7GB used?

---

### Post by philinux on 2009-07-14
In post #2 chown was rejected.

Here's a screenshot of my ICEauthority permissions. Check yours are the same.

---

### Post by neo.patrix on 2009-07-14
Thanx philinux

GNOME or ICEauthority , does not seem to be THE problem. consider these thread closed atm, I am going to make new thread.

---

