---
title: "Lost permissions on NAS when resumes from suspend/sleep"
date: 2014-08-16
forum: Networking &amp; Wireless
---

### Post by Anthony_Cunningham on 2014-08-16
Folks, 
  In the process of moving to Ubuntu and hitting a little snag with my NAS and NFS shares that I can't seem to solve and need your guidance please!

Mounts work, I was using /etc/fstab and first noticed these problems and I've been trying with autofs too but still the same issue. Everything works as
I expect until the following morning I start work again; my NAS shuts down over night and restarts in the morning. 

I was expecting - possibly incorrectly - that with NFS and autofs I could carry on and utilse the mounts to the NAS. Whilst I can see them I seem I lose 
previously working permissions on the files.  Example of ls command with all working (ignore 777 permissions, still need to fix these):-

```
ant@AntW530:/$ ls /mnt/NASMedia/Music/FLAC\ Music/Underworld/dubnobasswithmyheadman/ -l
total 423936
-rwxrwxrwx 1 1024 users 46392619 Jul 22  2010 01. dark & long.flac
-rwxrwxrwx 1 1024 users 75069245 Jul 22  2010 02. mmm skyscraper i love you.flac
-rwxrwxrwx 1 1024 users 46872186 Jul 22  2010 03. surfboy.flac
-rwxrwxrwx 1 1024 users 47438572 Jul 22  2010 04. spoonman.flac
-rwxrwxrwx 1 1024 users 20962544 Jul 22  2010 05. tongue.flac
-rwxrwxrwx 1 1024 users 63430039 Jul 22  2010 06. dirty epic.flac
-rwxrwxrwx 1 1024 users 53800395 Jul 22  2010 07. cowgirl.flac
-rwxrwxrwx 1 1024 users 31204714 Jul 22  2010 08. river of bass.flac
-rwxrwxrwx 1 1024 users 44668660 Jul 22  2010 09. m.e..flac
```

Now I restart the NAS and issue the same the same:- 
 
```
ant@AntW530:/$ ls /mnt/NASMedia/Music/FLAC\ Music/Underworld/dubnobasswithmyheadman/ -l
total 423936
---------- 1 1024 users 46392619 Jul 22  2010 01. dark & long.flac
---------- 1 1024 users 75069245 Jul 22  2010 02. mmm skyscraper i love you.flac
---------- 1 1024 users 46872186 Jul 22  2010 03. surfboy.flac
---------- 1 1024 users 47438572 Jul 22  2010 04. spoonman.flac
---------- 1 1024 users 20962544 Jul 22  2010 05. tongue.flac
---------- 1 1024 users 63430039 Jul 22  2010 06. dirty epic.flac
---------- 1 1024 users 53800395 Jul 22  2010 07. cowgirl.flac
---------- 1 1024 users 31204714 Jul 22  2010 08. river of bass.flac
---------- 1 1024 users 44668660 Jul 22  2010 09. m.e..flac
ant@AntW530:/$ 

```

I lose the prior permissions I had on the files. If I restart the autofs service (and I dont have terminals or apps using the NFS mount points) all is well again 
and I regain my permissions (similar to if I did a mount on /etc/fstab when I was using that). 

Am I expecting too much here for autofs/nfs to allow me to maintain my permissions when the NAS restarts or missing some config on the NFS client/server
for this to work smoothly with no loss of permissions? 

Thanks for the guidance

Ant

---

### Post by Anthony_Cunningham on 2014-08-17
Update:- 

For now stopped the NAS from shutting down and restarting overnight and instead set it to suspend the hard disks when not used. 

Issuing ```
mount -o remount /<mount_point(s)> 
``` will remount and provide permissions again. I could set up daemon/cron to monitor
and automatically fix if it detects permissions are gone. The change from shutdown -> hibernate works for now.

---

### Post by tgalati4 on 2014-08-17
Why do you need to restart the NAS once a day?  Does it lock up and require frequent reboots?  I would think that shutting down a NAS would leave a /etc/fstab mount in an indeterminant state.  You would need to unmount and then *mount -a* to get the mounts to correctly function.  Linux expects perfect hardware and expects mounts to always be there.  There is no framework to gracefully remount drives that disappear randomly.

I would investigate the NAS and the reason for frequent reboots--is it a hardware problem or a NAS firmware problem?  What is the make and model of the NAS?  Perhaps others are having problems with it.

Welcome to the forums.

---

### Post by Anthony_Cunningham on 2014-08-17
> **tgalati4 said:**
> Why do you need to restart the NAS once a day?  Does it lock up and require frequent reboots?  I would think that shutting down a NAS would leave a /etc/fstab mount in an indeterminant state.  You would need to unmount and then *mount -a* to get the mounts to correctly function.  Linux expects perfect hardware and expects mounts to always be there.  There is no framework to gracefully remount drives that disappear randomly.

I would investigate the NAS and the reason for frequent reboots--is it a hardware problem or a NAS firmware problem?  What is the make and model of the NAS?  Perhaps others are having problems with it.

Welcome to the forums.

Thank you for the welcome. 

I don't *need* to, I was doing so overnight and when travelling with work to be green :-) Nothing wrong with the NAS, more this is how I had in working in my Windows environment and this is something
I noticed whilst porting everything over to Linux and using NFS in place of SMB. Thanks for clearing up this appears to be working as it should. Did a lot of reading around NFS, autofs etc whilst looking into this
so I learnt much in this endeavor - including how I could easily automate a fix for this. 

Cheers!

---

