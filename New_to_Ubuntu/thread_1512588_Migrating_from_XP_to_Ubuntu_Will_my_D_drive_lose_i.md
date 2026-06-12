---
title: "Migrating from XP to Ubuntu: Will my D drive lose its data?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by jfjoubert on 2010-06-18
Hello,

I want to do a "clean install" of Ubuntu on my C drive. I am curruntly using WinXp. I understand this will erase everything on my C drive. But...can I use my D drive to backup all my data? 

Will Ubuntu be able to access the data written by XP on the D drive, like it can read a usb key?

Thank you for the help,


jfjoubert

---

### Post by Irony on 2010-06-18
Yes you can move your stuff to D drive and install Ubuntu to C drive - just make sure you actually install to C drive.

Ubuntu will be able to read the D drive once it is installed, just go to System > Admin > Disk Utility.

You can test this all out from the live CD before you install.

---

### Post by ronnielsen1 on 2010-06-18
Are you erasing winxp or dual booting. Ubuntu 10.04 will pull in all settings (music, documents, bookmarks, etc) from windows if it detects an installation. Unless you've been playing with linux for a while, you might want to consider dual boot for a while.

---

### Post by jfjoubert on 2010-06-18
I am completely erasing windows XP by installing Ubuntu on the C drive. I just wanted to be sure my D drive would be left intact and still be readable.

---

### Post by lukeiamyourfather on 2010-06-18
> **jfjoubert said:**
> I am completely erasing windows XP by installing Ubuntu on the C drive. I just wanted to be sure my D drive would be left intact and still be readable.

As long as you don't wipe the drive or format the partition/drive the files on the D: drive will be unaffected by install Ubuntu. If its a separate physical disk from he C: drive I suggest unplugging the D: drive while you install Ubuntu so it would be impossible to accidentally format the disk during the install process. Cheers!

---

### Post by mikewhatever on 2010-06-18
> **jfjoubert said:**
> I am completely erasing windows XP by installing Ubuntu on the C drive. I just wanted to be sure my D drive would be left intact and still be readable.

The installer will not let you choose a specific paartition to install to, unless you use the manual/advanced partitioning option. By default, the installer will try to shrink one of the existing partitions.
To accomplish what you want easily, delete the Windows partition first, then launch (or re-launch) the installer, and look for the 'Use the free space available' option.

---

### Post by jfjoubert on 2010-06-18
Well this is getting hair raising fast :)

I prompted by the installer to "erase and use entire disk"...my two drives are seen as one 120G drive.

(Not good)  :)

When specifying partitions manually, I see sda1 (5G), sda2(57G) and sda3 (57G).

sda2 (ntfs)and sda3 (fat32) look like the size of c and d drives.

What should I do now?

By the way, the drives are inside a laptop and hard to unplug...

If I delete a partition, does that mean I'm deleting the creation of a partition...so by deleting the sda3 partition...it would leave the d drive unaffected...

I think I'm going to buy some blank dvds ans start backing up...

---

### Post by mikewhatever on 2010-06-18
> **jfjoubert said:**
> Well this is getting hair raising fast :)

I prompted by the installer to "erase and use entire disk"...my two drives are seen as one 120G drive.

(Not good)  :)

That's not a prompt, but rather an option, it's there, but you are not required to use it. What two drives are you talking about?
> 
When specifying partitions manually, I see sda1 (5G), sda2(57G) and sda3 (57G).

sda2 (ntfs)and sda3 (fat32) look like the size of c and d drives.

What should I do now?

Which partition do you want Ubuntu on? The 5GB sda1?


> If I delete a partition, does that mean I'm deleting the creation of a partition...so by deleting the sda3 partition...it would leave the d drive unaffected...

I think I'm going to buy some blank dvds ans start backing up...

Deleting the creation of a partition ...:confused: You lost me there. If D: is the sda3 partition and you delete it, it will be deleted, which is very much affected. ;)
By the way, it looks like sda2 and sda3 are just a logical partition inside an extended.
Why don't you post the output of **sudo fdisk -l** from Applications->Accessories->Terminal.

---

### Post by cetacean on 2010-06-18
This is a tangential comment.

The partitioning part of the install is extremely user un-friendly to newbies because of the threatening language of the instructions. 

As I remember, that "erase and use entire disk" really meant "erase and use entire partition" and it took a real leap of faith to press that enter key. Partitioning itself is alien and problematic to most Windows users, although apparently very common in Linux.

People who understand all this like 2nd nature don't see it, but if they could put themselves in the shoes of a newbie, and really look at the specific language of those instructions, they might realize that it is very confusing and scary.

Just a thought.

---

### Post by mikewhatever on 2010-06-18
cetacean, "erase and use entire disk" actually means exactly what it says. This option will delete all partitions and their contents, which is useful if you have nothing valuable on the disk and want to start from scratch. As mentioned above, it's one of the options, and you don't have to click it.;)

---

### Post by cetacean on 2010-06-20
Mike - 

Thank you. I must be remembering wrong. But I do remember that there was one dialog box that seemed extremely intimidating, and only after you clicked through it did you get to see some less frightening choices. Maybe something like "Manually Configure" that was under a scary heading like "Use Entire Disk".

And there was still yet one more layer of "are you sure you want to do this?" but I remember doing it a couple of times and feeling very nervous.

On my desktop tower, with multiple drives, it was easy, I just gave one whole clean drive to Linux and did not have to worry.

---

### Post by JKyleOKC on 2010-06-20
> **jfjoubert said:**
> Well this is getting hair raising fast :)

I prompted by the installer to "erase and use entire disk"...my two drives are seen as one 120G drive.

(Not good)  :)

When specifying partitions manually, I see sda1 (5G), sda2(57G) and sda3 (57G).

sda2 (ntfs)and sda3 (fat32) look like the size of c and d drives.

What should I do now?

By the way, the drives are inside a laptop and hard to unplug...

If I delete a partition, does that mean I'm deleting the creation of a partition...so by deleting the sda3 partition...it would leave the d drive unaffected...

I think I'm going to buy some blank dvds ans start backing up...What these cryptic numbers are telling you is that you don't have two separate drives! Instead, you have just one 120-GB drive that's partitioned into three separate areas. The 5-GB sda1 partition is probably the factory recovery area, that has code to erase everything from the others and put them back to the state they were in when the box left the factory. Your "C drive" is probably sda2, and D is then sda3.

Thus the answer to your initial question is no, D would not survive an "entire disk" installation of Ubuntu.

However there are several solutions. Rather than buying a few hundred DVDs and attempting to backup to them, get an external hard drive that connects via USB, and backup to it. It's not only less costly in the long run and takes less time, but is much more reliable and can be used for future backups.

Then you can boot from the Live CD, and before attempting the installation, select the sda1 partition from "Places" and verify that it is in fact your Windows C drive. This is to make certain of my guess; if you see the normal C drive folders when you view the sda1 partition, it's there. If not, check sda2. When you know which is which, then (still running from the CD) use gparted to delete the C drive's partition but leave the others alone. You can delete the 5-GB partition also if you want; I always leave it in place so that I can restore the original Windows installation if I want to get rid of the box someday.

With the C partition returned to "unallocated space" you can now do the installation, but at the partitioning prompt tell it to use available space rather than the whole disk. You should wind up with a 57-GB Ubuntu installation, and your original D drive still intact.

Incidentally it's not uncommon for a system to have multiple logical drives but only one physical drive. Setting it up in this way makes it easier to distinguish data and system areas -- but can be quite confusing at times, such as you're now experiencing!

---

