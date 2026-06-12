---
title: "Deleting partition NFTS partition, New install. Older Ubuntu 9.10 present"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by cowcow1212 on 2009-11-07
I assume, when installing from a live CD, you will do hard disk formatting prior to formatting.  

What can I expect, if I were install from a Live Ubuntu CD - using the install file on desktop - while trying to reformat an old Windows partition, after the install is complete?

What format should I make this newly formatted (old NTFS) Partition?

[INDENT]I already have an older installed version of Ubuntu 9.11 (which was from an upgrade) that I cannot fix; therefore, are there any ways to designate that partition as the data partition?  ( ext3(data) /oldNTFS(sys) )


ext3 (old_Ubuntu 9.10 place)  ---> Data partition 
Old_NFTS                              --->New Ubuntu system partition                         [INDENT][RIGHT][INDENT][INDENT][INDENT](the ext4 partition, if you upgraded from 8.04)
[/INDENT][/INDENT][/INDENT][/RIGHT]
[/INDENT][/INDENT][INDENT]
Then have this newly formatted free space from NTFS, to the **yet unknown** partition, become another needed file system.

What would I check to allow the use of the old data partition? 
When and how do I specify this during the install? (When doing a "dry run", clicking everything but pushing the final button it didn't seem possible.)

[/INDENT]Conversely, is there a way to make a new ubuntu on this newly reformated disk space (***NTFS*** --> **New format??**)?  


                                     Old_NFTS --(holds)--> ext4(data)/ext4(sysdata)
                                  [INDENT]However, what would happen to the other partitions, including GRUB, old data partition and the broken Ubuntu file partition (ext0.. I think, ext3 and ex4, respectfully)? 
NTFS= ext1


[/INDENT]Finally, is there a way to use the old system file partition of ext4, from the upgrade, and make NFTS partition the data partition?
[RIGHT]
[/RIGHT]
[INDENT][INDENT]  
Would doing so cause my issues (unable to see the log-in screen,  from disabling my monitor/screen (my only working screen!)) to cross over to this fresh install?


[/INDENT][/INDENT]

---

### Post by Yvan300 on 2009-11-07
Seriously, you need to explain yourself a little better. If you want to use a previous partition then when it is insatalling and the partitioner shows up. Click manual or advanced and then select what each partition should be used for. If your old partition had your documents etc on it, then use that one for your home partition. Hope i helped.

---

### Post by LewRockwell on 2009-11-07
it's five o'clock **SOMEWHERE**

[http://www.youtube.com/watch?v=ib8nH4kHjxk](http://www.youtube.com/watch?v=ib8nH4kHjxk)

.

---

### Post by SuperSonic4 on 2009-11-07
> **cowcow1212 said:**
> I assume, when installing from a live CD, you will do hard disk formatting prior to formatting

Yep although the cd can largely do it for you or you can specify manually. Your choice

> What can I expect, if I were install from a Live Ubuntu CD - using the install file on desktop - while trying to reformat an old Windows partition, after the install is complete?

I'd expect an installed ubuntu and a removed windows (including files)
> 
What format should I make this newly formatted (old NTFS) Partition?

Depends what you want to use it for. For linux only ext4 is a good idea IMO. For shared data with windows use ntfs

> I already have an older installed version of Ubuntu 9.11 (which was from an upgrade) that I cannot fix; therefore, are there any ways to designate that partition as the data partition?  ( ext3(data) /oldNTFS(sys) )

Yes, if you manually partition you can point it to be a data partition which will be mounted using the fstab file. You can also manually edit fstab after the install if you like

> ext3 (old_Ubuntu 9.10 place)  ---> Data partition 
Old_NFTS                          
Then have this newly formatted free space from NTFS, to the **yet unknown** partition, become another needed file system.

I don't get it, what are you trying to say?

> What would I check to allow the use of the old data partition? 
When and how do I specify this during the install? (When doing a "dry run", clicking everything but pushing the final button it didn't seem possible.)

You can do this manually - from a live cd it is well explained to you. To check what's on a partition you can use the live cd to take a look around before partitioning if that's what you mean.

> Conversely, is there a way to make a new ubuntu on this newly reformated disk space (***NTFS*** --> **New format??**)?  

You can install ubuntu onto the old ntfs, even if you've reformatted it (a good idea since ntfs sucks for an OS)


> However, what would happen to the other partitions, including GRUB, old data partition and the broken Ubuntu file partition (ext0.. I think, ext3 and ex4, respectfully)? 
NTFS= ext1

When installing from the live CD grub should sort all that out for you

> 
Finally, is there a way to use the old system file partition of ext4, from the upgrade, and make NFTS partition the data partition?

Yes. Install manually

> Would doing so cause my issues (unable to see the log-in screen,  from disabling my monitor/screen (my only working screen!)) to cross over to this fresh install?

No idea, that's hardware dependent

---

### Post by cowcow1212 on 2009-11-07
> **Yvan300 said:**
> Click manual or advanced and then select what each partition should be used for. If your old partition had your documents etc on it, then use that one for your home partition. Hope i helped.

Well I have grub installed, and when I was going to reformat the windows partition, it said I was going to erase over that area too. (Would I just select this partition to be the boot area?)


Will I still have all my old programs' various dependencies installed? Or, will I have to select another partition for those? Did the update move the dependencies (because they used to be all together)?

---

### Post by LewRockwell on 2009-11-07
honestly, we don't think you should do ANYTHING until you've done more research on what you really want to do...and learn more about what you decide to do

and, of course, it goes without saying that you should always maintain good back-ups and secure data storage(both short-term and long-term)

we use Clonezilla

.

---

### Post by seenthelite on 2009-11-07
Regarding the formating prior to a new install, I may be wrong but I have done a lot of installs and have found that the installation disk or whatever method you are using will take care of this as the installation proceeds and indeed you get to choose the system.

---

