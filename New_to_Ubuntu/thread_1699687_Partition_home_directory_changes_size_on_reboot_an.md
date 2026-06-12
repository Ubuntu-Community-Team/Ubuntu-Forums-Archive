---
title: "Partition home directory changes size on reboot and files missing"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by FreeFromWindows on 2011-03-04
I am a real noob.  I did a complete new install of Maverick 10.10 a few months back and must have screwed something up maybe with the partitions table.  I have an 300Gb HP-Pav 2 cpu, dual boot system with Ubuntu and Windows XP.  However, I haven't logged into Windows since setting up Ubuntu.

Not realizing what I was doing, I accidentally sized my /home directory at ~3Gb.  I used a live cd and "fixed" it to a more realistic size of ~127Gb, which it was for a while.  That was months ago, however, something isn't working.  

1.  Last night I saved some pictures to my picture folder.  This morning I went to find them only to see that they disappeared.  I was also getting a message that I only had 12Mb available on my /home directory.  I knew that wasn't correct. 

2.  I checked the file systems with Gparted and saw the larger /home directory (/dev/sda8) and a smaller partition (/dev/sda7) and noticed they shared the same UUID #.  I don't know if that's an issue or not...

3.  Additionally, Gparted did not match the file system section of the System Monitor.  

4.  I didn't make any changes with Gparted, just rebooted the computer. 
 
5.  When I logged back in after the reboot, the missing pictures had returned to my pictures folder, AND my /home directory had over 100Gb (like it should). Not knowing what caused this, I ran a few commands in terminal, copied and pasted the results into OpenOffice writer just in case something weird happened again, so I'd have something to compare it to.  

6.  Update manager prompted for updates, so I did that and rebooted...  The pictures are once again missing.  The files I saved in Writer are missing.  I have a /home directory with a size of ~3Gb again.

What did I do wrong?  It's almost like I have two separate /home directories but I cannot control what one I get on rebooting.

More info that may or may not be helpful (or related...)  while rebooting.  I had a few things flash across the screen.  One was stating that Firestarter wasn't starting.  The other was related to ClamAv not working.  I can't get Firefox to work but that is probably related to AppArmor profiles I downloaded. 

Lastly, sometimes when I log in, I get a brief glimpse of my desktop and then I get sent back to the log in screen and have to log in again.

I'm afraid I've created a mess.  :confused:

I RAN THE FOLLOWING IN TERMINAL:

fdisk -l

 Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3669    29467066+   7  HPFS/NTFS
/dev/sda2           35327       36481     9277537+   c  W95 FAT32 (LBA)
/dev/sda3            3669       35326   254287873    5  Extended
/dev/sda5            3669       18082   115774464   83  Linux
/dev/sda6           34599       34848     2000000   82  Linux swap / Solaris
/dev/sda7           34848       35326     3843072   83  Linux
/dev/sda8           18082       34599   132667392   83  Linux

Partition table entries are not in disk order

sheila@StevensHP:~$ sudo blkid
[sudo] password for sheila: 
/dev/sda1: LABEL="HP_PAVILION" UUID="BC184BD2184B8A7A" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="7EC1-2D87" TYPE="vfat" 
/dev/sda5: UUID="2d926f4f-c303-423f-9db2-f30f9d116b80" TYPE="ext4" 
/dev/sda6: UUID="4a93c00b-9eeb-4983-a83d-62e15438a4c2" TYPE="swap" 
/dev/sda7: LABEL="Extra" UUID="dc55377e-8714-40cc-9900-cea3f84425c9" TYPE="ext4" 
/dev/sda8: UUID="dc55377e-8714-40cc-9900-cea3f84425c9" TYPE="ext4" 


sheila@StevensHP:~$ df -h | grep "/dev/sd"
/dev/sda5             109G  5.9G   98G   6% /
/dev/sda7             3.7G  3.3G  149M  96% /home


I would appreciate any help.

Thanks.

---

### Post by aaryansh on 2011-03-04
Hey there,
You can change the uuid of the disk by doing

```
tune2fs -U random /dev/sda7
```

---

### Post by mcduck on 2011-03-04
Two partitions with a same UUID would definitely be a problem, as the UUID is what the system uses to detect which partition to mount and where. With the same UUID it can't tell the partitions apart and just probably mounts the one that happens to respond first.

I'd say the first task would be to check what the small partition with same UUID as your home partiton actually is, and what it contains. Most likely the second step would be moving whatever you have there into the real home partition, and then removing the offending partition or giving it a new UUID and mount point.

I can't really say how the partition might have ended with the same UUID as your home, considering that UUID's are randomly generated and it's extremely unlikely to get the same UUID by that random process. More likely it's a result of some error when editing your partitions.

---

### Post by Dutch70 on 2011-03-04
Welcome to UF :)

 I really hate to be the one to break this to you, but you really need to repartition your hdd anyway, but given your other problems, that may just be a good thing. 

 You're wasting about 90-95 GiB with the set up you have. "/" or (root) only needs to be about 10-20 GiB if you have a /home that you keep your files in. Yours is a whopping 110 GiB & I doubt if you'll ever use much more than 10. I'd make it 20 GiB for good measure.

Here is the process **I** would use...But I'm no guru so you may want to see what others think before trying it.

1. Shrink sda5 down to about 20-GiB. 

2. Take all the stuff from sda7 & sda8 that you don't want to lose and back it up. Alternatively, you may be able to store it in a temporary folder in windows, or sda5.

3. Delete sda6, sda7 & sda8. 

4. Recreate /home & swap

5. Move your files to /home

6. Reinstall Ubuntu to sda5, make sure your files aren't stored there before reinstalling.

Sounds like a lot, but really it's not. It could probably be done in less than an hour.

---

### Post by egalvan on 2011-03-04
Your **/home **is still sized at 3gb, according to your listings.

**/dev/sda7 34848 35326 3843072 83 Linux**
[COLOR="Red"]/dev/sda8 18082 34599 132667392 83 Linux
[/COLOR]

**/dev/sda7: LABEL="Extra" UUID="dc55377e-8714-40cc-9900-cea3f84425c9" TYPE="ext4"**
[COLOR="Red"]/dev/sda8: UUID="dc55377e-8714-40cc-9900-cea3f84425c9" TYPE="ext4"
[/COLOR]
The partition [COLOR="Red"]/sda8 [/COLOR]seems to be the "enlarged" home partition, correct?

Exactly HOW did you "fix" your /home to a larger size?

Duplicate UUID's will happen when you "clone" a partition.

---

### Post by vanadium on 2011-03-04
Make this easy. Remove all logical partitions (sd5 and above) and reinstall Ubuntu. Let it automatically use the available space. This will take you less than one hour and you will end up with a clean system.

Make sure all your user data are backed up before you attempt this.

---

### Post by FreeFromWindows on 2011-03-07
Thanks everyone for your help.  I will probably start from scratch and reinstall based on the suggestions.

I feel pretty confident that it was **user** error somehow with regards to the same UUID number, although I couldn't tell you how I did it.  

However, I have been able to figure out that every time I restart the computer, the home directories (3gb vs ~100g) alternate.  Like now, for example, I have the larger directory.  Next time I reboot, I'll have the smaller one.  I figured someone may find that interesting or helpful to know...

I think I do know what the smaller partition is.  It think it was my original home directory that was set up when I was installed Maverick.

Lastly, I really appreciate finding out how much space I was wasting ~90gb.  See how badly a noob can mess things up!  Thanks also for letting me know how large root needs to be.  I will set up at 20gb.

---

