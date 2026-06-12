---
title: "Partition after installing"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Malacoda103 on 2009-04-13
So I've installed Ubuntu Intrepid x64, and i quite like it. 
Now i guess i made the big mistake of using the whole disk to install guided mode or something rather then partitioning it. is it too late now or is it still possible to do so?

thanks!

---

### Post by cariboo on 2009-04-13
Have a look at this [howto]("http:///www.howtoforge.com/linux_resizing_ext3_partitions"). The only thing that you might have a problem with is the:

```
sudo su
```

command, use

```
sudo -i
```

Jim

---

### Post by Malacoda103 on 2009-04-14
thanks,

I think all of that is waaaaaaaaay above my head though.....

---

### Post by hyper_ch on 2009-04-14
if you just have installed it and if you have backups of your documents, give it a try and check out how it works out. if it works out you learnt something... if you screw up you can reinstall and do the partitioning there :)

---

### Post by raedbenz on 2009-04-14
also is useful to try install "Gnome Partition Editor" using synaptics. 
search in synaptics about "GParted"

---

### Post by Malacoda103 on 2009-04-15
I've made my partition but i'm a bit lost on a couple things...
What type of partition should i make it if i just want to store data on it such as music photos word docs ETC? i currently have it set as FAT32, but a problem i am encountering is i have 4.4Gb file that when i try to copy to this partition it says in a popup window at 4.0Gb
```
There was an error copying the file into /media/disk.
Error writing to file: File too large 
```
It shouldn't say this as i have over 200Gb of free space on this drive.

I originally had it as ext3 and then ext2 both of which would not let me write to it.

Oh and another question, how do i get the partition to mount upon booting?

thanks for all the advice!

Matt

---

### Post by kansasnoob on 2009-04-15
What exactly do you want to change?

Do you want to dual boot?

An example:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

The multi-boot bible:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Malacoda103 on 2009-04-15
No my partition is just for storing music, photos and data so that if i have to reload my OS (ubuntu).i wont lose all of the above.

---

### Post by MegaJim on 2009-04-15
If you are using linux-only OS, choose ext3, if you need to share data between linux and windows you can choose either NTFS or ext3 (or FAT32, but don't).

Ext3 has the advantage of being fast under linux and windows, but windows tools for reading Ext3 tend to mess it up sometimes

NTFS will work great under both, but takes quite a few CPU cycles under linux, so would not be ideal for running games or high activity apps like bit torrent.

---

### Post by Malacoda103 on 2009-04-15
ok, so it's ext3 now, i found a thread that helped me take ownership so i could write to the partition ([http://ubuntuforums.org/showthread.php?t=677244](http://ubuntuforums.org/showthread.php?t=677244)).

So i'm wondering how do i get linux to mount this drive as i boot up so i dont have to manually do it?

Also there is a lost and found folder on this partition. Is it necessary to have or can i delete it?

thanks for everyone's help on this matter.

---

### Post by ranch hand on 2009-04-15
I hope you are doing the partioning from your Live CD.  You should not be partitioning from the same drive that you are partitioning.

---

### Post by nandemonai on 2009-04-15
> **Malacoda103 said:**
> ok, so it's ext3 now, i found a thread that helped me take ownership so i could write to the partition ([http://ubuntuforums.org/showthread.php?t=677244](http://ubuntuforums.org/showthread.php?t=677244)).

So i'm wondering how do i get linux to mount this drive as i boot up so i dont have to manually do it?

Also there is a lost and found folder on this partition. Is it necessary to have or can i delete it?

thanks for everyone's help on this matter.

In order for the system to mount a partition at boot you need to add it to the /etc/fstab file.

Best way to do this is mount the disc then open up a gnome terminal.

This first command will output your mounts in a way that can be used with fstab:

```
cat /etc/mtab
```

You'll get a bunch of lines for all the mounts in the system that look something like this...

```
/dev/sda4 /home ext3 rw,relatime 0 0
```

That's an example of my home partition mount.

Find the line that corresponds to the partition you want to mount at boot and copy that line to the bottom of your /etc/fstab file.

```
gksudo gedit /etc/fstab
```

Save the file, reboot and hopefully your drive will be mounted on boot ;)

As far as the lost+found dir, it's the place where corrupted files are placed when they are found during a filesystem check so best leave it be.

---

### Post by bodhi.zazen on 2009-04-15
> **ranch hand said:**
> I hope you are doing the partioning from your Live CD.  You should not be partitioning from the same drive that you are partitioning.

You can change your partitions with a live CD.

See :

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

and you will want to edit /etc/fstab as well:

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

If you are having difficulty understanding what to do you need to be more specific, what questions do you have ?

---

### Post by Malacoda103 on 2009-04-15
Hi guys,

All is well, the only question i had left was how to mount the drive while it was being booted. Nandemonai has answered this question for me.

So when i figure out how to mark this thread as solved i will!

thanks!
Matt

---

