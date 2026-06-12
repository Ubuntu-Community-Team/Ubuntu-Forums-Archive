---
title: "newb here.  help with mounting ntfs"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by lobes on 2009-03-09
**[COLOR="Red"]{SOLVED}  Please look at new problem in 2nd post. Thanks[/COLOR]**

its been a long 24 hours and im very tired so I will try to be thorough and quick.  i know little about linux so bare with me.  quick overview:

ive been running a dual boot system with latest ubuntu version and XP. ubuntu installed first. my xp has major, MAJOR issues that just cant be resolved.  I'm ready to just reload xp but the problem lies in the 300gb's of movies on that partition that i dont want to lose.  

so...i dont have an extra hdd just the 640gb sata drive im using.  I downloaded gparted and after a little work i was able to split my current 600gb ntfs partition into 2 300gb partitions.  This was so I could transfer my movies to new part. and format the old.  so far so good.

next i downloaded the ntfs partition tool so i could mount the part.  just messing around with it, and here is where my lack of knowledge shows, I mounted the partitions, one to media/windows and one to media/backup. it worked.  after restart for some updates i boot back into ubuntu and when I try to mount either of the partitions i get an error saying "you are not privleged to mount this volume"  

i tried to force the mount but no go.  I know its something simple it's just been a long day so I display my "newbness" for all to see.  any help would be appreciated. and please, pretend like your talking to a child cause the linux/teminal/sudo stuff falls very short of me.  thanks.

output of fdisk:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux
/dev/sda2            1246        1618     2996122+   5  Extended
/dev/sda3   *        1619       41137   317436367+   7  HPFS/NTFS
/dev/sda4           41138       77825   294696360    7  HPFS/NTFS
/dev/sda5            1246        1369      995998+  82  Linux swap / Solaris
/dev/sda6            1370        1618     2000061   83  Linux


---

### Post by vanadium on 2009-03-09
How did you try to mount your partitions?

---

### Post by lobes on 2009-03-09
sorry, been away.  So like i thought it was something simple.  It was just a problem mounting the ntfs xp partition because windows crashed last time i booted it.  but I have a new issue.

I was able to transfer my movies to the other ntfs partition and then I went to format the windows part.  after un mounting i tried formating it to a ntfs partition.  well it woarked for like 5 seconds and said done.  everything was still on the partition.  so i deleted the partition.  it went away and said i had 300gb of unallocated space.  but once again it only worked for like 5 seconds.  there was 290gbs of data on that part.  so i went ahead and made a new ntfs partition using the unallocated space and it worked.  it shows as an empty partition with aprox 300gbs free. 

sounds great but I fail to belive that the 290gbs of data is off the hard drive.

here is the fdisk reading:
> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00005239

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux
/dev/sda2            1246        1618     2996122+   5  Extended
/dev/sda3            1619       41137   317436367+   7  HPFS/NTFS
/dev/sda4           41138       77825   294696360    7  HPFS/NTFS
/dev/sda5            1246        1369      995998+  82  Linux swap / Solaris
/dev/sda6            1370        1618     2000061   83  Linux


---

### Post by orethrius on 2009-03-10
If you're at the Terminal anyways, you can always run **df** to confirm your suspicions.  Aside from that, the only real way to confirm that the data is really gone is to either:

(A) Boot back into Windows and check, which seems unlikely at this point if the partition holding your C: drive has been formatted, or:
(B) Boot using a LiveCD and check the partition in question.

---

### Post by lobes on 2009-03-10
hey thanks. i ran df and below is the output. once again shows me exactly what i want to see but still dont belive.  I tried booting back into windows which did not work.  my ubuntu live cd shows the same results as gparted.  i need to get my hands on a vista install disk and format it thats way.  anybody else got any ideas?  is it even possible that it did remove all 280gb's of data from the part in 5 seconds?

heres the output of df:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9843276   4246652   5096604  46% /
tmpfs                  1898720         0   1898720   0% /lib/init/rw
varrun                 1898720       300   1898420   1% /var/run
varlock                1898720         0   1898720   0% /var/lock
udev                   1898720      2796   1895924   1% /dev
tmpfs                  1898720       104   1898616   1% /dev/shm
lrm                    1898720      2384   1896336   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6              1968588     61492   1807096   4% /boot
/dev/sda3            317436364     75672 317360692   1% /media/windows
/dev/sda4            294696356 289996788   4699568  99% /media/backup


---

### Post by orethrius on 2009-03-10
If by "removed all 280gb's of data" you mean "marked the space for overwriting", then yes.  The data is still technically there, but you can overwrite that space by first formatting that partition with a different filesystem, then back to NTFS.  The upshot is that *the whole partition* is marked for overwriting, which *includes* the entirety of the system.  Booting back into Windows on a "dead" filesystem will NOT work.

---

