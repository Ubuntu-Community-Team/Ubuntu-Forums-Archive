---
title: "partitioning: mount point to choose for data partition"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by wyatt roberts on 2010-01-03
I am partitioning a large drive.  I have made some data partitions for storage. While I am setting up the partition from the alternative install disk, I have /boot, /, /home on separate partitions.  The rest of the disk is carved up into Data partitions.  I am at the point of writing the partitions and get the following message:  &quot;No mount point assigned for the ext3 filesystem in partition #1 of LVM VG Volumegroup1 Bigdata1.  If you do not go back to the partitioning menu and assign a mount poinnt from there, this partition will not be used at all.  Do you want to return to the partitioning menu?    I'm sure I do want to return to the partitioning menu but don't know what selection to make: Leaving aside /root, /, /home the rest of the choices are: /tmp, usr, var, svr, opt, /usr/local - local hiearchy, enter manually, do not mount it.  My intention is to keep documents, web page saves, much the kind of things that might be kept in home but allow less often used info to go keep out of the way... I think I could mount the data partitions only when needed but it would be convenient to have at least one mount automatically, which I think this choice will allow.   Recommendations?  Thanks, wyatt

---

### Post by LinuxRules1 on 2010-01-03
i think that you should install with all the partitions except for the storage one and then when the install finishes you can create/format the last partition with gparted. you won't need to specify a mount point when you create it. but in order to make it automatically mount you have to include the drive in /etc/fstab.

---

### Post by wyatt roberts on 2010-01-03
> **LinuxRules1 said:**
> i think that you should install with all the partitions except for the storage one and then when the install finishes you can create/format the last partition with gparted. you won't need to specify a mount point when you create it. but in order to make it automatically mount you have to include the drive in /etc/fstab.

 Then, I can choose &quot;do not mount it&quot; and then edit /etc/fstab after the drive is partitioned and mount it automatically from fstab?  Haven't done that, but most of this I haven't done.   Thanks,  wyatt

---

### Post by jnew93 on 2010-01-03
A data partition without a specific system mount point (/home, /boot, etc) will just act like an external HD or flash drive, in that you do not need it mounted for the system to run, but can mount or unmount when needed. This sounds like what you need it to do.

---

### Post by LinuxRules1 on 2010-01-03
this is how you would automount the drive.

you should format the storage partition as NTFS

in terminal type this

```
sudo blkid
```

once you do that look for the line that has TYPE="ntfs"

look at the far left of that line to where it says /dev/(something)

you will have to create the directory for the mount point. to do that type this.

```
sudo mkdir /media/storage
```

you will also have to give full write permissions to that directory. do that with this command.

```
sudo chmod 777 /media/storage
```

now we have to edit /etc/fstab.
add this line to /etc/fstab.

```
/dev/(something) /media/storage ntfs-3g ro,user,auto,fmask=0177,dmask=0077,uid=1000 0   0
```

that's pretty much it.

hope this helps you.

---

### Post by wyatt roberts on 2010-01-03
> **jnew93 said:**
> A data partition without a specific system mount point (/home, /boot, etc) will just act like an external HD or flash drive, in that you do not need it mounted for the system to run, but can mount or unmount when needed. This sounds like what you need it to do.

 Great.  That's exactly what I'd like.  My last install I used some of the unformatted hard drive to make a partition with Gparted and it can be mounted but to umount it I had to "sudo umount /media/sda3"; enter my password and then it would unmount.  My external drive however does not require the "sudo umount" routine, just unmount from the GUI.  Any thoughts on That difference and how to avoid it?   Anyway, I intend to just not make a mount point in the partition-er...  I appreciate you help, wyatt

---

### Post by wyatt roberts on 2010-01-03
> **LinuxRules1 said:**
> this is how you would automount the drive.

you should format the storage partition as NTFS

in terminal type this

```
sudo blkid
```once you do that look for the line that has TYPE="ntfs"

look at the far left of that line to where it says /dev/(something)

you will have to create the directory for the mount point. to do that type this.

```
sudo mkdir /media/storage
```you will also have to give full write permissions to that directory. do that with this command.

```
sudo chmod 777 /media/storage
```now we have to edit /etc/fstab.
add this line to /etc/fstab.

```
/dev/(something) /media/storage ntfs-3g ro,user,auto,fmask=0177,dmask=0077,uid=1000 0   0
```that's pretty much it.

hope this helps you.

I haven't looked but I think the partitoner didn't offer NTFS I think.  Maybe Gparted does... I'm on another computer now.  I can see how that might work better to access from a windows computer.  I am planning to dual boot for a while since there are some programs I need or think I do, by using a separate hard drive and switching drive order in the bios screen.  But where I am now in the partitioner section of the alternative install disk, I may have to choose something that is a choice they offer and I don't recall NTFS being offered...

Question 1: My ultimate plan is to move to Ubuntu and I don't know what I'm talking about here but things like permissions, do they work with NTFS and ntfs-3g, can you write the permissions there?

Question 2: If I stay with ext3 will similar instructions to those above work for ext3 mounting or be required to mount it ?
Thanks,
wyatt

---

### Post by wyatt roberts on 2010-01-03
OK... it's later...about 4 hours later
I described a behaviour in one of the replys above to jnew9 where I had to go to sudo to unmount a mounted drive: "

Quote:
Originally Posted by jnew9:
A data partition without a specific system mount point (/home, /boot, etc) will just act like 

an external HD or flash drive, in that you do not need it mounted for the system to run, but 

can mount or unmount when needed. This sounds like what you need it to do."

Wyatt:
Great. That's exactly what I'd like. My last install I used some of the unformatted hard drive 

to make a partition with Gparted and it can be mounted but to umount it I had to "sudo umount 

/media/sda3"; enter my password and then it would unmount. My external drive however does not 

require the "sudo umount" routine, just unmount from the GUI. Any thoughts on That difference 

and how to avoid it? Anyway, I intend to just not make a mount point in the partition-er... I 

appreciate you help, wyatt  End of reply

Wyatt:

Now that I think about it, I think I had to sudo to mount it as well as to unmount it. But I didn't know about fstab then...

That is what is happening now... I tried to follow the instructions above by LinuxRules1 but the partitioner in the alternative install disk did not list NTFS, I formatted them as ext3 but did not choose a mount point. When the install is done, there there are to choose and open but they have permissions for root and cannot be written to as user. 

So I dropped back and tried to follow the recommendations of LinuxRules1:

" Re: partitioning: mount point to choose for data partition
LinuxRules1:
"this is how you would automount the drive.

you should format the storage partition as NTFS

in terminal type this

Code:

sudo blkid

once you do that look for the line that has TYPE="ntfs"

look at the far left of that line to where it says /dev/(something)

you will have to create the directory for the mount point. to do that type this.

Code:

sudo mkdir /media/storage

you will also have to give full write permissions to that directory. do that with this command.

Code:

sudo chmod 777 /media/storage

now we have to edit /etc/fstab.
add this line to /etc/fstab.

Code:

/dev/(something) /media/storage ntfs-3g ro,user,auto,fmask=0177,dmask=0077,uid=1000 0   0

that's pretty much it.

hope this helps you."  End of LinuxRules1's reply


Wyatt: 
AND IT DID... 
I would never have gotten this far without the above...using the fstab quoted below the chosen data disk auto mounts, I can write to the drive and delete from the drive.  But I cannot umount the drive unless I sudo umount the full drive name...
/dev/mapper/VolumeGroup1-data4... That is a lot to rememeber.  This is a drive mapped to a volume group under LVM.  

So, in the boot up process the drive is mounted from fstab with root privileges and I, as user, have the ability to write to and delete from the drive...

I've been playing with the fstab file and there may be something better but what works for the above is:

***********************
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/VolumeGroup1-root /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=90615dd1-c985-46d6-a441-de6d6a058e90 /boot           ext3    defaults        0       2
/dev/mapper/VolumeGroup1-home /home           ext3    defaults        0       2
/dev/mapper/VolumeGroup1-swap none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/VolumeGroup1-data4 /media/storage ext3    defaults        0        0

**********************

I tried "user,auto,fmask=0177,dmask=0077,uid=1000" with and with out the rw but couldn't get it to work... these options yielded an error message, failed to mount the drive and what is listed above works.

SO....

This is CLOSE...

How can I unmount the drive like I do an external USB drive?  I suppose a script would do it, but there must be a more elegant way...


Thanks for the help,
wyatt

---

### Post by LinuxRules1 on 2010-01-03
you can unmount it with less to remember like this.

```
sudo umount /media/storage
```

if you would like, i can write you a quick script that will unmount the drive for you.

---

### Post by Cheesemill on 2010-01-03
You could always have just selected 'enter manually' at the choices during install and typed /media/storage (or whatever you wanted). This would have taken care of everything for you :)

Sorry I didn't post earlier, only just seen this thread.

---

### Post by wyatt roberts on 2010-01-03
> **Cheesemill said:**
> You could always have just selected 'enter manually' at the choices during install and typed /media/storage (or whatever you wanted). This would have taken care of everything for you :)

Sorry I didn't post earlier, only just seen this thread.

I feel pretty stupid but am greatful for all the help everyone has offered.  I appreciate the offer of the script from LinuxRules1... I didn't chose enter manually at the choices, I didn't choose any of them.  I said continue without choice.  I am quoting from another answer in another fourm:

" Originally Posted by wyatt roberts:
I just clicked on my usbkey icon on the desktop and chose "Safely Remove "; and it umounted the drive and never asked me for a password... It's a drive, like usb drives, that is partitioned and the partition is mounted when I plug it in,,,

I suppose there is a way it does that but it is listed on the desktop pulldown list in the same list of "removable media" that lists the partition I want to mount as a user: Places > Removable Media > data4...

So, if you have to be root to mount a drive how does my USBkey get mounted as a user accessible drive and get unmounted by the GUI ... Could I lie to the system and "emulate" the usbkey, however it does it?

Thanks,
wyatt

Well... I am reporting back to say that the problem is solved. I don't know what step I missed so I cannot accurately say what led me down this blind alley. I restarted and my external eSata drive was not automounted. I scratched my head and found it listed in Places > Removable Media > MyBook. It mounted with a click. So I unmounted and it did. I tried one more thing and commented out the line in fstab that mounted my partition that somehow required mounting as root earlier. I restarted. I was able to mount it with a click from Places > Removable Media > data4... I umounted it with a click. I am removing the line from fstab. [COLOR=Red]Postmortem.[/COLOR] I suspect I made one of the changes painfully documented in these poss and DIDN'T reboot so it never changed behavior. Anyway, Problem solved. 

Thanks all. 
Wyatt 

I will marked this solved by editing the original post title

---

