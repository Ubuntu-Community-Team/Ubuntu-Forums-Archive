---
title: "Grub rescue/boot errors, removed linux"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by J Snazzy on 2010-04-04
Hi Guys,

I tried to use ubuntu but it was not for me. I was duel booting on a netbook and thought the solution would just be delete the partitions for Ubuntu and it would be gone.

I was wrong :(

If I load from my hard drive 1 or 0 (I believe these are the windows and the rescue drives)

GRUB loading.
error: no such partition
grub rescue> 

So then I acquired the windows 7 (This thread [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)) to do those steps.

Extracted the Iso to my flash drive, booted from my flashdrive, I get this

Syslinux 3.85 (date, ebios, peter Anvin)
No DEFAULT or UI configuration directive found!
boot:

if I try the bootrec.exe I get

Could not find kernel image: bootrec.exe


If you can help I would greatly appreciate it, this is a new netbook. 

Thanks!

---

### Post by talsemgeest on 2010-04-04
> **J Snazzy said:**
> Hi Guys,

I tried to use ubuntu but it was not for me. I was duel booting on a netbook and thought the solution would just be delete the partitions for Ubuntu and it would be gone.

I was wrong :(

If I load from my hard drive 1 or 0 (I believe these are the windows and the rescue drives)

GRUB loading.
error: no such partition
grub rescue> 

So then I acquired the windows 7 (This thread [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)) to do those steps.

Extracted the Iso to my flash drive, booted from my flashdrive, I get this

Syslinux 3.85 (date, ebios, peter Anvin)
No DEFAULT or UI configuration directive found!
boot:

if I try the bootrec.exe I get

Could not find kernel image: bootrec.exe


If you can help I would greatly appreciate it, this is a new netbook. 

Thanks!
Im afraid the windows disk does not work well with flash drives. It would probably be easier to burn the image to a cd and then work from there.

---

### Post by kansasnoob on 2010-04-04
How did you install Ubuntu? If you have an Ubuntu Live CD or Live USB you can use it to create a generic "windows readable" mbr by booting to the Live Desktop and then in Terminal running the following commands.

**[COLOR="Red"]Note[/COLOR]**: I'm assuming since this is a netbook you have only one hard drive and it's likely recognized by Ubuntu as /dev/sda. To check and be sure first run the command:

```
sudo fdisk -l
```

The ouput will be similar to this:

```
Disk **[COLOR="Red"]/dev/sda[/COLOR]**: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2589    20796111    7  HPFS/NTFS
/dev/sda2            2590        3683     8787555   83  Linux
/dev/sda3            3684        4757     8626905   83  Linux
/dev/sda4            4758       60801   450173430    5  Extended
/dev/sda5            4758        5341     4690917   83  Linux
/dev/sda6            5342        5919     4642753+  83  Linux
/dev/sda7           52539       53852    10554673+  83  Linux
/dev/sda8           53853       56511    21358386   83  Linux
/dev/sda9           56512       59192    21535101   83  Linux
/dev/sda10          59193       60566    11036623+  83  Linux
/dev/sda11          60567       60801     1887606   82  Linux swap / Solaris

```

You only care about the part I highlighted in red, if it is /dev/sda then continue:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Then hopefully you'll be able to boot Windows. I do hope you used only Windows own tools to resize your Windows partition.

---

### Post by J Snazzy on 2010-04-04
-- May have mispoken...checking it out.


kansasnoob you are my hero...Windows booted up :).

Is there anything else I should do to insure linux is off my HD, or am I good.


Thanks x10000000!

---

### Post by kansasnoob on 2010-04-05
> **J Snazzy said:**
> -- May have mispoken...checking it out.


kansasnoob you are my hero...Windows booted up :).

Is there anything else I should do to insure linux is off my HD, or am I good.


Thanks x10000000!

Did you (or do you want to) reclaim the space left from removing Ubuntu?

In Win Vista and 7 both that is best done using Win's own Disk Management tool:

[http://www.vista4beginners.com/How-to-manage-your-disks-using-only-Windows-Vista-Disk-Management-tool](http://www.vista4beginners.com/How-to-manage-your-disks-using-only-Windows-Vista-Disk-Management-tool)

---

