---
title: "Picking ubuntu 10.04 over 9.10"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by gordon33 on 2010-06-24
Hello All

I have  a duel boot Ubuntu 9.10 and Ubuntu 10.4.  I want to get rid of the Ubuntu 9.10.  
Can I use?
Code;
 sudo apt-get install lilo

 Code:
sudo apt-get install lilo

I added 9.10  to see if I could connect to my wireless router.

---

### Post by Paqman on 2010-06-24
[LIST=1]
[*]Open up Software Centre or Synaptic and install "Gparted"
[*]Go to System > Admin > Gparted
[*]Pick the partitions used by 9.10 and delete them
[*]Go to Applications > Accessories Terminal and enter the following command:
[/LIST]
```
sudo update-grub
```
Put in your password (it looks like it's not going in,but it really is) and let it do it's thing.

If you want you can use Gparted to expand your Ubuntu 10.04 partitions to take up the space your created delete 9.10, but it can take a while and I wouldn't bother until you need the space.

---

### Post by gordon33 on 2010-06-24
Hello 

I am not sure how to tell the partitions used by 9.10.  

Gordon

---

### Post by CharlesA on 2010-06-24
If you are booting into 10.04 now, what is the device listed as "/" with this command:

```
mount
```

it should look like this:

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)

```

Delete the other partition then update grub. :)

---

### Post by oldfred on 2010-06-24
You use lilo to boot windows, not Ubuntu. Which install are you using to boot with. If the 9.10 was second did it install into the MBR and now you boot thru it? If so you should install the boot loader from 10.04 before deleting 9.10.

Boot into 10.04
reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

If you do not do this then you have to reinstall grub from a liveCD.
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by Paqman on 2010-06-24
> **gordon33 said:**
> Hello 

I am not sure how to tell the partitions used by 9.10.  

Gordon

Anything that isn't marked as being in use when you're running 10.04. Partitions that are in use have a little lock symbol on them, and can't be modified, so it's impossible to get it wrong.

---

### Post by anewguy on 2010-06-24
> **oldfred said:**
> You use lilo to boot windows, not Ubuntu.....

Not true - lilo is a boot loader used by some Linux distributions - see Slackware for example.  It's been a LONG time since I knew, but if I remember correctly lilo actually stands for linux loader. 

However, you are correct that this is not what the OP wants to do.


Dave ;)

---

### Post by gordon33 on 2010-06-24
Hello

I deleted the particions that did not have a key.  i did not read the above directions well.  I missed the part from oldfred who asked "Which install are you using to boot with. If the 9.10 was second did it install into the MBR and now you boot thru it? If so you should install the boot loader from 10.04 before deleting 9.10."

Now i have a mostly black screen.  in the upper left corner is: 
GRUB loading
error: no such partition
grub rescue>

What can i do now to get Ubuntu 10.04 to boot up.

Gordon33

---

### Post by oldfred on 2010-06-24
I also gave you the backup install from liveCD instructions in case you missed it.

If you do not do this then you have to reinstall grub from a liveCD.
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda     

Dave is of course correct lilo is a linux boot loader. It works like windows in the sense the second part is in the partition boot record, so its MBR also just looks for a boot flag and jumps to the partition boot sector to keep booting. We have been using just the MBR part as an easy to install from Ubuntu replacement for the windows boot loader.

---

### Post by -kg- on 2010-06-24
Good job, Oldfred.  Yes, you'll need to install GRUB from the installation, using the Live CD.

I always hate coming across a thread like this where someone says "go into GParted and just delete the partition with (the other) OS on it."  It is almost ***never*** that simple.  Take it from me...I've made that little mistake!  Another problem you might run across...

Whenever you delete a partition, whether you'll be able to boot into the (other) OS or not depends on your partitioning scheme.  As Oldfred points out, there is a little code segment in the MBR which points to the rest of GRUB in the partition which has control of GRUB.  In this case, it was the installation you deleted...thus the necessity of installing GRUB from the other installation so ***it*** has control.  ***_However_...***

A lot depends on what the partition number of the controlling OS (I assume it was 9.10) was.  When you delete a partition, the partition numbering scheme of the following partitions (i.e., sda7 "follows" sda5).  If you, say, delete partition sda5 and have a partition sda6, sda6 will become the new sda5.  This convention does not follow actual position on the disk...it follows the chronology of their creation.

I recently had a problem with this.  I fresh installed 10.04, and in the process I deleted a couple of partitions and created a new one.  I have several installations on my laptop, including one that was installed on a partition following the deleted partitions, as described.

When I tried to boot in to that installation, it froze part way through the boot-up process, complaining about not being able to "find partition sdb11."  I ended up having to reinstall that OS, because the later stages of its GRUB (not in control of the segment in the MBR) was set to "look for itself" in the old partition number.  "sudo update-grub" from the controlling OS found the installation perfectly...it just couldn't "find itself."  (Think I should have sent it on a European vacation? :p )

Hopefully, you don't run across that problem, but thought I'd give you a heads up and explanation, in case you do.  There might be a way other than re-installation, but I wasn't aware of it, and the other installation (OpenSUSE) was new and unused enough that I just went ahead and re-installed.

---

### Post by gordon33 on 2010-06-25
Hello all 

Thank you for the help so far.*

Should I run: sudo grub-install /dev/sda ?  

I reinstalled the 9.10 version of Ubuntu.* Now I am back to where I was at the start of this thread, wanting Just 10.04.* 

When I turn the computer on it offers 2 options at the top that bring up 9.10 there are about 20 options that start with Ubuntu 10.04. their are also several Memory Test options. I pick the first one with Ubuntu 10.04. I have been assuming this is booting in to 10.04. 

Once 10.04 is booted up I go to terminal and type in the commands oldfred post. Here are the results.

gordon@gordon-laptop:~$ sudo fdisk -l

[sudo] password for gordon: 



Disk /dev/sda: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x58bf6ae5



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        9826    78927313+  83  Linux

/dev/sda2            9827       19457    77361007+   5  Extended

/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

/dev/sda6            9827       18296    68035212   83  Linux

/dev/sda7           18297       18662     2939863+  82  Linux swap / Solaris



Partition table entries are not in disk order


Should I run: sudo grub-install /dev/sda ?  

Oldfred said to if it's "/dev/sda" then just run: udo grub-install /dev/sda    
I am wondering if the 1,5,6,7 is an unacceptable difference.  

Gordon

---

### Post by oldfred on 2010-06-25
You only have sda so you install grub to sda. You do not install grub to partitions. If you have booted you have booted into either sda1 or sda6 as those are your linux partitions. Swap is for RAM overflow and not the install.

When you reinstalled did you not overwrite your current install in sda1 but create sda6 second root & sda7 second swap as an additional install, so actually you have two installs?

---

### Post by gordon33 on 2010-06-25
Hello oldfred

When I reinstalled 9.10 I thought it went to its original partitions. How would I tell if the reinstall of 9.10 went to sda1, sda6, or second root & sda7.  

Should I run: sudo grub-install /sda ?  Once I am logged in to 10.04.

This is all new to me.  

Gordon33

---

### Post by oldfred on 2010-06-25
If you want to know what you have booted

```
grub-install -v
lsb_release -a
```

If you want that to be the default to boot to:
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub


If you really want all the details of what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by anewguy on 2010-06-25
Nice work, oldfred!  Just a small side note to the OP - grub is for booting, and as such modified the Master Boot Record, which is a Disk area, not a partition area.  So when oldfred is asking you to install to sda, sda is a device (disk) not a partition.  Don't know if that helps you understand that little part or not.

Dave ;)

---

### Post by gordon33 on 2010-06-26
Hello Oldfred.

Thank you again for your help.

I think I made a little progress.  After: sudo grub-install /dev/sda 
My computer is booting up in 10.04.

I have a screen shot of the GParted from when I booted up in 10.04.  Once I mark 6 and 7 will I go to the "Partition" pull down menu and click Delete.  and finish the removal of 9.10 by using the EDIT pull down menu and chousing Apply?

Gordon33

---

### Post by gordon33 on 2010-06-27
Hello Oldfred and every one else.

Solved

I decided to take the risk and decided to just do the Delete and Apply as I wrote about in my last message.

The updated screen shot of Gparted is attached. 

Last question what is the "Unallocated" 67.69 GiB.  If lots of movies and or photos are saved will they use this space?

Gordon Webb

---

### Post by oldfred on 2010-06-27
Unavailable is just that. You can shrink the extended and expand root, but I prefer to have data separate from the system partition. Many recommend a separate /home which also makes it easily to save your settings if you want to reinstall. I also like a separate /data partition for most of the data that usually is in /home so /home only has user settings. It totally depends on how you want to set up your system and as you use it more and more your requirements will change. In my case it was about 3 years and a new hard drive so I had lots of space to reorganize.

Extra info incase you are interested:

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio, (I used cp -a old new)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Without -a and copying as sudo root takes ownership

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by gordon33 on 2010-06-27
Thank you Oldfred 

I will spend some time reviewing the additional commands you shared. 

I like the idea of making your home folder on a seprate partition.

Gordon

---

