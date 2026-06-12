---
title: "[SOLVED] partition and directory issues after re install"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-11
hi everybody.  i lost the /home directory on my original installation (ubuntu 8.10 no other operating system) and had to re install from live disk which i did using guided partition.  i now have the system set up as follows
```
nigel@nigel-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x939aab47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6238       12525    50508360   83  Linux
/dev/sda2               1        6237    50098671   83  Linux
/dev/sda4           12526       19457    55681290    5  Extended
/dev/sda5           12526       13112     4715046   83  Linux
/dev/sda6           19169       19457     2321361   82  Linux swap / Solaris
/dev/sda7           13113       18914    46604533+  83  Linux
/dev/sda8           18915       19168     2040223+  82  Linux swap / Solaris

Partition table entries are not in disk order
nigel@nigel-laptop:~$ 

```
/dev/sda1  is  /media disk 1   seems to be a backup of orig install
/dev/sda2  is  /media disk     my data files
/dev/sda4  is  extended partition includes
    /sda5  is 4.5 Gb resized original system
    /sda7  is  /  (root?)
    /sda8  is  linux-swap
    /sda6  is  linux-swap original

i recall i used to have sda 1, 2, and extended consisting of 4, 5 and 6 which were backup, data, (ext), /, and swap respectively  but now the parts 1 and 2 are referred to as above - media instead of data etc.
i want to know whether i should delete partition sda5 and absorb the space into another eg sda7.  or whether it is possible to re create the original system that is on sda5.  whatever, i need to be rid of one or the other.  i have succeeded in copying all my data files over to sda2 so i could easily do this, but if i do will i get my full root authorizations back that i had before, as i only seem to have limited authority at present on the new installation.  i just want to get things clear again as they were before.  
thanks for any help you can give me
nigel
ps
1.  i thought this had failed so i re entered but i marked the later one solved cos this is better worded i think.
2.  this is what i get when i go (sudo nautilus) in a terninal  ```
 nigel@nigel-laptop:~$ sudo nautilus
[sudo] password for nigel: 
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:7146): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> trash:///
--> file:///root
--> file:///
--> file:///home

(nautilus:7146): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 4 elements at quit time (keys above)

(nautilus:7146): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time
Segmentation fault
nigel@nigel-laptop:~$ 

```
thanks for anyhelp - this is more an irritation than a major problem but i would like to sort it as its not sensible at present and it bugs me.  thanks all
nigel

---

### Post by blueridgedog on 2009-01-11
Perhaps you will get some other advice, by if this were my rig, I would re-install and manually format the drive.  I would use gparted on the live CD to delete everything but sda2 and then enlarge sda2 to 100gig.  Create an sda1 of 50gig for / and /swap equal to your memory.  Tred lightly as you need to know what partition is what when you start adjusting/deleting.  It would be easier if you could back up your data and just format everything (that is what I am doing tonight...)

---

### Post by capnthommo on 2009-01-12
thanks blueridgedog. you may be right but i think i would need leading a little more closely as i am not really that technically minded.   now i have slept on the problem a little i think i have an idea where i want to go.  so here goes
it looks to me as if i now have 
sda1              backup    (a tar of my old system which i dont know how 
                                to restore)
sda2              data
sda4              extended partition that includes
    sda5          the resized (shrunk) old root directory
    sda6          linux-swap   for the above (sda5 etc)
    sda7          /   (root directory for my new installation which 
                       appears to have very little authority eg 
                        lacks permissions to do much at all)
    sda8          linux-swap relating to sda7

i think what i would like to do is to restore the tar on sda1 and then get rid of sda 7 and 8.
my problem is that i cant seem to do anything with sda1 or the old inst in geneal cos i dont have authority (or knowledge) to access/edit it.  i can only perform limited functions in the new setup   and if i try to boot into the original system, after user/password i get error message about 
```
home dir listed as /home/nigel not appearing to exist would i like to log on with / (root) dir. 
```
 when i ok this i get ```
 
$HOME.dmrc file is being ignored this prevents default session and language being saved.  file should be owned by user and have 644 permissions.  users $HOME dir must be owned by user and not writable by other users.
```
i made the tar backup using instructions on a very nice help thread on this forum (its also somewhere else too) but now i cant find it and cant access my old bookmark to it either.  so in brief what i have is: a new usable system that regards me as almost a 'guest user' and a perfectly good system and a backup of it which i can't access to restore.  
i am afraid i need leading through this by the hand if you dont mind - (anybody)
again i apologise for the length of this post but as i said elsewhere i need to put it in a form i can understand so i am sure i have it right.
again, many thanks
nigel

---

### Post by capnthommo on 2009-01-12
hi again.  still trying to define the problem so i thought i'd try seeing if a change of post title might help - maybe my title was hindering.  i cant access the first ubuntu i had set up and used before i had to reinstall (still not sure what i should call it (root? directory? so as to distinguish from the present / that has no privileges) sorry im just trying to make this more understandable.  i have found the how to on backup/restore tar but it doesn't want to work.  if somebody can help me please let me know what you need to know and i'll post any info. just let me know what/how.  
i'm really sorry to whittle on about this but i don't understand whats happening and i want to get things back working like they originally were.  why for instance do i suddenly have no ability to access nautilus with root privileges.  and is ist possible to restore thgings somehow.
thanks again to anybody who can help - really grateful 
cheers
nigel

---

### Post by capnthommo on 2009-01-12
Okay folks.  in the end it got so complicated i decided to reinstall and re partition from the start.  so now i have a nice simple setup and whats most important all my permissions and stuff back.  i have lost my data for now but thats no problem as its all recoverable from original sources - and there really wasn't all that much of it.  so no worries.  and i think its an external drive asap.  main point is, if this had happened on windows i'd have been up the well known creek.  nothing i could have done except BUY more stuff.  with this i not only got to fix/improve it myself but i also learned from it.  every step is forwards.  next time i bust it i shall know a bit more.
gods, i love this o/s!
cheers everyone
nigel
):P

---

