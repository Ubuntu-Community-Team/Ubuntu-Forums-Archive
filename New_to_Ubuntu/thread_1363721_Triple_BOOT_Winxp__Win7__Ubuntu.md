---
title: "Triple BOOT Winxp / Win7 / Ubuntu"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by Kozzmozz on 2009-12-24
Hi all!

I'm trying to build a system that triple boots Winxp_x32 / Win7_x64 / Ubuntu.

I have a Asus laptop with one HDD split up into 4 partitions:

1. Winxp with 100 gb
2. Win7 with 65 gb
3. Storage with 280 gb
4. Linux with 20 gb

Now XP and 7 play along just fine, but when booting the Ubuntu cd and arriving to the partitioning stage it says: Ubuntu didn't detect any OS on your HDD.
So I am unable to install it on my L:\ Linux partition. Only option I have is to format the entire HDD, which is not an option. I can select advanced partition but it still doesn't detect my partitions.

Any ideas how I can install Ubuntu alongside winxp and win7?

Greetz

---

### Post by RedSingularity on 2009-12-24
When you boot from the Linux CD and choose to install it will give you an option to install side by side a windows partition.

---

### Post by Kozzmozz on 2009-12-24
Thanks for the reply!

hmm I didn't see that... It doesn't recognise any partitions I have so the only option is to format the whole HDD.

---

### Post by RedSingularity on 2009-12-24
Which version of Ubuntu are you dealing with?

---

### Post by Kozzmozz on 2009-12-24
ubuntu 9.10 and I'm using sata in bios if that makes any difference as opposed to ide

---

### Post by RedSingularity on 2009-12-24
Hmmm it should be detecting your other installs.......does it give you an option for a "manual" install?

---

### Post by Kozzmozz on 2009-12-24
It does say something about advanced or manual partitioning under the full format but when trying to click or move the bar I still cannot choose or see my partitions.

---

### Post by Sef on 2009-12-24
Try to install with the [alternate cd]("http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors"); it is a text-based installer.  It is not hard to use, but manually partitioning the first time can be a little nervewracking.

---

### Post by Kozzmozz on 2009-12-24
ok, thank you, I'll try it tomorrow when my slow connection has finished downloading it.

It's getting late here.

Thanks for the help!

---

### Post by 4Orbs on 2009-12-24
The screen that has the "Full" "Side by Side" and "Manually" selectors, is more of a splash page and not the actual partitioning tool. If you click the "Manual" option it will open gParted and you'll be able to see all the partitions as they really exist.

---

### Post by holastickboy on 2009-12-25
As long as you dont overwrite another installation of an OS, ubuntu will show the other OS's in the grub menu automatically when you install it to its own partition.

---

### Post by Kozzmozz on 2009-12-25
So if I manage to install it to it's dedicated partition I will be able to choose between

Xp
win7
Ubuntu

at the boot screen without installing anything extra?

It's somewhat confusing because I read that I had to install Ubuntu first, then format partitions with a program called gparted, then Install winxp and win7 to be able to have Ubuntu installed alongside winxp and win7 and be able to tripleboot

---

### Post by drs305 on 2009-12-25
> **Kozzmozz said:**
> So if I manage to install it to it's dedicated partition I will be able to choose between

Xp
win7
Ubuntu

at the boot screen without installing anything extra?

It's somewhat confusing because I read that I had to install Ubuntu first, then format partitions with a program called gparted, then Install winxp and win7 to be able to have Ubuntu installed alongside winxp and win7 and be able to tripleboot

After you install Ubuntu, sometimes Grub 2 initially fails to see your other systems. If so, run "sudo update-grub" in a terminal (Applications, Accessories, Terminal) to allow Grub to find your other installations. 

Here is a link that may prove useful if you aren't able to boot into your other installs even after Grub 2 sees the other OSs:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Kozzmozz on 2009-12-25
Thanks for the help :)

4Orbs was right, I had to click proceed first...
Anyway, have some more questions for you :P

I made the partition for Ubuntu under windows at the end of the drive so I should look for the last 20gb?
 
And what would be the better choice: ext3 or ext4 ?

EDIT: Read that ext4 could bring problems so will choose ext3 

When arriving at the partition stage where I select advanced(manual) partitioning I get:

/dev/sda, the only option I have is to rightclick it and select new partition table ( it doesn't detect my existing partitions, don't know if that's normal  :?: 
"You have selected an entire device to partition. If you proceed with creating a new partition table on he device, then all current partitions will be removed.
I click proceed ( there s an option to revert)

Now I see Free space 500105 MB -> richtclick is the only option, I choose ADD

Type: *Primary or Logical ( I need to have it set to Primary right? What's the best option for triple boot?)
New parttion size: 21000MB
location: end
used as: ext3
mount point: /
No swap space; will this also affect the OS or only the installation process?

Continue ->

Warning: This will destroy all data on any partition you have removed as on the partitions that are going to be formatted.
The partition tables of the following devices have been changed:
SCSIl (0,0,0) (sda)
 :?: Is it correct to assume that the 0,0,0 are my existing partitions winxp, win7 and storage and the 0 means no changes to these partitions?

The following partitions are going to be formatted:
partition #1 of SCSIl (0,0,0) (sda) as ext3
then when I clcik advanced I get:

Bootloader install to 
(hd0) selected as default
/dev/sda
/dev/sda-1
/dev/sda 1
 :?: Again which one to choose to be able to triple boot safely  :D 

At this stage I got scared to continue to lose the data on my other partitions so I reverted and quit. To my surprise I only saw my c:\ partition in explorer  :!: 
Luckily partition magic found them after a quick scan and was able to recover them  8-) 

So could anyone spare some time to guide me through this process and reassure me this is the normal procedure and I will not lose my partitions, because am a bit sceptical after what happened.
Also tell me what are the best choices out of the above options, to maintain existing partitions with no data loss and the ability to triple boot?

Lol sorry for the long post if you read all of it but I wanted to provide as much info as possible for maximum accuracy.

Thanks!

---

### Post by Kozzmozz on 2009-12-26
I used the default xp partitioner when installing XP the first time 5 months ago, then used Partition Magic to create and resize more then one time.

Now the strange part, as you know, is that linux didn't recognise my existing partitions. 
And ended up deleting all my partitions except the one where XP was installed, no idea why not that one?

Now the good part, after recovering my partitions with partition magic and reassining the drive letters I tried once more to install Ubuntu.

Guess what... Now it said Windows 7 loader found!!  :D And it recognised my partitions and so I chose to install it to the last 20 gb partition.

However, I tried to delete that partition and create a 15 gb partition which went fine, but I then had 5gb unusable space which I wanted to use to create a swap file, but no way, except if I created the swap area first and then the ext3 partition. I thought that was weird so not to mess things up again I just created a 20 gb primary partition with ext3 and / and no swap space.

Ubuntu installed and I was able to boot into it and I can also choose to boot into winxp or win7 so it's perfect. \\:D/

Now I'm trying to install my sagem modem drivers, not easy for a windows user  ](*,)

Thanks for the help guys!

---

### Post by drs305 on 2009-12-26
Kozzmozz,

If you want to create a swap partition:

Boot the Ubuntu LiveCD.
Open Gparted (System, Administration, Gparted/Partition Editor)
Select the Ubuntu partition, Partition, Resize. Shrink by 2 GB (or as desired, but 5GB is most likely too much).
Create a new partition of 2GB and format as "swap".

Restart.
Find the UUID of the new partition and add swap partition to fstab:
```

sudo blkid | grep swap
gksu gedit /etc/fstab

```

Add the following to fstab, using your swap UUID:
> 
UUID=[COLOR="DarkRed"]*b0e26f5f-a977-4fe7-8a5f-b3c2dc1bf5c7*[/COLOR] none 	swap 	sw 			0 0

Save the file and reboot.

Check swap is working (The swap value may be 0 if not currently needed and in use, but you should see "total, used, free") :
```

free -m

```

---

### Post by walt.smith1960 on 2009-12-26
I've used BootItNG from [www.terabyteunlimited.com]("http://www.terabyteunlimited.com"). It's shareware, not freeware. It has its foibles but works okay. I'm not sure what it will do that Gparted and GRUB won't do.  Just another option and not too expensive. BootIt also contains a partition copy and paste utility.

---

