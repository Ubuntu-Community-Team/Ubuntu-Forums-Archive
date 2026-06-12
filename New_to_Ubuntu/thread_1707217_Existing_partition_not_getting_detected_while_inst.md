---
title: "Existing partition not getting detected while installing Ubuntu 10.04.2"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by panand178 on 2011-03-15
Hi,

I have a 250 GB HDD already running windows XP (~50 GB) and Ubuntu 8.04 (~50 GB) on my desktop along with 3 other NTFS partitions (~50 GB, ~48 GB and ~48 GB) and a 2GB swap. I'm planning to format the 8.04 partition and install 10.04.2 in it. 

When I'm trying to install Ubuntu 10.04.2 the installer is not detecting any of my existing partitions. The funny part is that from the Ubuntu 10.04 desktop launched from the live CD when I select ***gparted*** it shows all my existing partitions, also I am able to mount these drives as well. However it does not detect my partitions when I start installing.

Could anyone let me know how I can fix this without having to lose any of my existing partitions. Do let me know in case you require any additional information on this from my side

---

### Post by Dutch70 on 2011-03-15
Can you be more specific as to what exactly is happening when you try to install. I have an idea what you mean, but not 100% sure. 

Also, can you take a pic of your partitions in Gparted and "attach" them to your next post using the little paper clip in the toolbar. 
As shown in the pic I included just for the fun of it. :D

---

### Post by coffeecat on 2011-03-15
@panand178, was your 250GB drive once used in a RAID array? Residual raid metadata can cause this problem.

---

### Post by panand178 on 2011-03-15
@Dutch70: Sorry Disk Utility was showing my partitions properly. Gparted isn't showing my partitions. Attaching both the screenshots.

@coffeecat: My HDD wasnt used in a RAID Array. In fact I havent formatted or played around with it since I installed 8.04 around mid 2008.

---

### Post by coffeecat on 2011-03-15
Ah, the screenshots you posted tell a different story from this in your first post:

> **panand178 said:**
> The funny part is that from the Ubuntu 10.04 desktop launched from the live CD when I select ***gparted*** it shows all my existing partitions, also I am able to mount these drives as well.

In your screenshot, Gparted is saying your HD is unallocated. I read your first post to say that the installer didn't detect your partitions which often happens with RAID metadata. Forget the RAID; that's a red-herring. The empty Gparted  is almost certainly caused by an inconsistency in your partition table.

Boot up with the live CD, choose "try Ubuntu" and open a terminal (Applications > Accessories). Post the output of this command:

```
sudo fdisk -lu
```Then we can take it from there.

---

### Post by panand178 on 2011-03-15
@coffeecat: Attached *sudo fdisk -lu* output.

---

### Post by coffeecat on 2011-03-15
Yup, you have an illegal entry in your partition table. If you look at the figures, your sda4 partition (with a #4 that should be a primary partition) is sitting inside your extended partition sda3. Only logical partitions can exist inside an extended partition and gparted is choking over an impossibility. Rather bizarrely, your installed operating systems are probably carrying on as though nothing is wrong. It's only when you need to use a partitioner or installer that you run into problems.

There are two ways of fixing this: by editing the partition table with sfdisk or with a new utility called fixparts that forum member srs5694 has developed. Either way it would be useful to have your information posted in a more usable way. Please boot up with the live CD again and run...

```
sudo fdisk -lu
```... again, but this time copy and paste the output into your post, enclosing it between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the # icon on the message toolbar for this.

Also, run this:

```
sudo sfdisk -d /dev/sda > Desktop/parts.txt
```A text file called parts.txt will appear on the live desktop. Save this to a safe location. It might be needed. Also post the contents of parts.txt in code tags. The code tags are imperative for formatting. Again, we might need this.

I'm also going to call for another pair of expert eyes to look at this. This deserves care.

---

### Post by panand178 on 2011-03-15
Hi,

I had saved the output to a txt file as well the last time I did a *sudo fdisk -lu*. Here's the output (The same one that was in the screenshot).

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf43cf43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398310   205760519    51681105   83  Linux
/dev/sda3       205760520   488375999   141307740    f  W95 Ext'd (LBA)
/dev/sda4       409593303   488375999    39391348+   7  HPFS/NTFS
/dev/sda5       205776648   307194929    50709141    7  HPFS/NTFS
/dev/sda6       307194993   405496664    49150836    7  HPFS/NTFS
/dev/sda7       405496728   409593239     2048256   82  Linux swap / Solaris

```

I will now go ahead and boot using the live CD again and provide you the output for *sudo sfdisk -d /dev/sda > Desktop/parts.txt*.

---

### Post by srs5694 on 2011-03-15
> **coffeecat said:**
> There are two ways of fixing this: by editing the partition table with sfdisk or with a new utility called fixparts that forum member srs5694 has developed. Either way it would be useful to have your information posted in a more usable way. Please boot up with the live CD again and run...

I concur with coffeecat's analysis. FWIW, this is exactly the sort of problem I wrote fixparts to correct. It's still new, so I strongly recommend you run sfdisk (as coffeecat specified) and save the file on another medium (USB flash drive, floppy disk, CD-R, or whatever). That way, if fixparts trashes the disk, you can still recover your existing partitions. Similar comments apply to using sfdisk to do it manually; you want to have the sfdisk backup available in case of disaster. (Neither fixparts nor sfdisk is likely to trash data *within* your partitions, but either could theoretically make partitions disappear or create an even more illegal partition table than you've got now. A partition table backup can easily recover such losses.)

In your case, simply launching fixparts on the disk, checking that all your partitions are present (none are "omitted") by reviewing the output of "p", and writing the partition table back out with "w" should work; however, that will probably keep /dev/sda4, which is at the end of the disk, as a primary partition. There's nothing wrong with this, but it can be a bit confusing. Thus, you might want to reassign /dev/sda4 to be a logical partition using the "l" (letter L, not digit 1) option in fixparts.

Check the [FixParts Web page](http://www.rodsbooks.com/fixparts/) for more detail on its operation. I've also got a [Web page on the problem generally,](http://www.rodsbooks.com/missing-parts/index.html) but it's in bad need of editing -- it's too long and confusing at the moment, I'm afraid.

---

### Post by panand178 on 2011-03-15
@coffeecat , @srs5694: Here's the output of *sudo sfdisk -d /dev/sda*

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=102398247, Id= 7, bootable
/dev/sda2 : start=102398310, size=103362210, Id=83
/dev/sda3 : start=205760520, size=282615480, Id= f
/dev/sda4 : start=409593303, size= 78782697, Id= 7
/dev/sda5 : start=205776648, size=101418282, Id= 7
/dev/sda6 : start=307194993, size= 98301672, Id= 7
/dev/sda7 : start=405496728, size=  4096512, Id=82

```

Would you recomment me backing up all my data from all the existing partitions to an external Hard drive before going ahead with this?

---

### Post by coffeecat on 2011-03-15
> **panand178 said:**
> @coffeecat , @srs5694: Here's the output of *sudo sfdisk -d /dev/sda*

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=102398247, Id= 7, bootable
/dev/sda2 : start=102398310, size=103362210, Id=83
/dev/sda3 : start=205760520, size=282615480, Id= f
/dev/sda4 : start=409593303, size= 78782697, Id= 7
/dev/sda5 : start=205776648, size=101418282, Id= 7
/dev/sda6 : start=307194993, size= 98301672, Id= 7
/dev/sda7 : start=405496728, size=  4096512, Id=82

```Would you recomment me backing up all my data from all the existing partitions to an external Hard drive before going ahead with this?

Don't forget to archive your parts.txt file as srs5694 explained, although so long as the Ubuntuforums server doesn't fail us you now have a backup in this thread! :)

Yes, backing up data is a very good idea. As srs5694 said, running fixparts or sfdisk is unlikely to affect data within partitions, but it's always a good idea to make backups whenever you do any partition editing or changes. And if you haven't archived your data yet, now's the time to do it!

---

### Post by panand178 on 2011-03-15
@coffeecat: Since most of my partitions are almost running at full capacity it's going to take me a while to back up everything. I shall keep you posted on this. I won't get a better opportunity to clean up and discard a lot of unwanted/redundant data! :)

I shall keep you guys posted on this.

---

### Post by coffeecat on 2011-03-16
> **panand178 said:**
> I shall keep you posted on this.

I'll look forward to an update. I hope everything goes well.

I'll post this now in case I forget. I've been involved in several threads with a similar partition table problem - a "primary" partition sitting inside an extended, and they interest me. In most cases it would seem to be the Windows XP installer which has done this, although this is not certain.  Only with one very special set of circumstances was I able, in a simulation, to get the XP installer to take an existing logical partition and rewrite its partition table entry so that it looked like a primary, except that it was still within the extended partition.

Do you remember whether you installed XP after Ubuntu? If so, do you remember whether you created an NTFS partition for it with the Ubuntu partitioner, or did you use the Windows installer to reformat an existing partition?

---

### Post by panand178 on 2011-03-16
@coffeecat, @srs5694: I just want to let you know that I am currently posting this from my new 10.04 installation. :D

Everything went really smooth. I love fixparts! Worked like a charm. All my NTFS partitions were intact and I did not lose any data (even though I had backed it up)

Thanks a lot for all the help guys!

@coffeecat: to answer your question I had re-installed windows a few days back before I upgraded my Ubuntu. I had used the windows installer to format the existing NTFS partition. These partitions were created way back in 2008 and I think I had installed windows first along with few other NTFS partitions and deleted one of those using the ubuntu 8.04 installer and installed Ubuntu. Again I am not 100% sure of this since it was a long time back.

---

### Post by coffeecat on 2011-03-16
Excellent. I'm glad to hear it went well. 

> **panand178 said:**
> @coffeecat: to answer your question I had re-installed windows a few days back before I upgraded my Ubuntu. I had used the windows installer to format the existing NTFS partition. These partitions were created way back in 2008 and I think I had installed windows first along with few other NTFS partitions and deleted one of those using the ubuntu 8.04 installer and installed Ubuntu. Again I am not 100% sure of this since it was a long time back.

Thanks for that. It fits a pattern. The XP installer reformats a pre-existing partition and at the same time seems to make a mess of one of the logical partitions. Now that I've got your corrupted partition table, it's easy to work out what it probably was before and I can use that in one of my simulations - when I get a chance.

Good luck!

---

### Post by srs5694 on 2011-03-16
> **panand178 said:**
> Everything went really smooth. I love fixparts! Worked like a charm. All my NTFS partitions were intact and I did not lose any data (even though I had backed it up)

I'm glad to hear it!

---

