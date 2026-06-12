---
title: "sda9 full"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Mylorharbour on 2009-05-27
Hi guys,

I'm still trying to get to grips with the file system but I have a related problem. I'm running a multiboot system using Hardy on sda9 as my first choice. My problem is that I can't update it as the sda9 partition appears to be full. It's a 10Gb partition.

What do I need to do to see what's on that partition. My other distros, also on 10Gb partitions each seem to have about 6Gb free.

I try to store music & photos etc on other NTFS partitons so they're accessible from Windows too but I get the feeling some stuff is being stored on sda9 that shouldn't be.

Any ideas?

---

### Post by taurus on 2009-05-27
You should consider emptying the trash bin since when you click something to delete, it just moved it over to the trash bin, taking up the same space.  Also, clean out the cache too.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by Mark Phelps on 2009-05-28
> **Mylorharbour said:**
> What do I need to do to see what's on that partition. My other distros, also on 10Gb partitions each seem to have about 6Gb free.

Any ideas?

If it's not already installed, grab GParted from Synaptic and install it.

If it's an NTFS partition, make sure that ntfs-3g and ntfsprogs are also installed.

Then run the Partition Editor, open the drive, and you will see the space utilization of each partition.

---

### Post by Mylorharbour on 2009-05-28
Taurus,
Too late I'm afraid. Now when I select Hardy (sda9) from Grub I get the Ubuntu banner then a DOS type screen with the message:

GDM could not write new authorisation entry to disk. Possibly out of disk space. Error: No space left on device.



Mark,
I ran Gparted before and could see that sda9 was full. It's an ext3 partition with Hardy on it. I just booted into Intrepid which is on sda8 and ran Gparted again which showed just 48Kb free on sda9.

---

### Post by Paqman on 2009-05-28
You said you have other distros? Boot up into one of those, mount sda9 and go clean out everything in /var/cache/apt. That might give you enough space to boot Ubuntu and do a bit of housekeeping from there.

Other places you could look for stuff to throw out would be /home/username/.thumbnails and /home/username/.local/share/Trash.

---

### Post by Mylorharbour on 2009-06-04
Thanks Paqman. I did that and was able to boot into Hardy. I then cleared the folders you suggested but there wasn't much in there.

Taurus, result of df -h

```
[FONT="Courier New"]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             9.8G  9.7G     0 100% /
varrun               1006M  104K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
udev                 1006M   92K 1006M   1% /dev
devshm               1006M   12K 1006M   1% /dev/shm
lrm                  1006M   39M  967M   4% /lib/modules/2.6.24-23-generic/volatile
/dev/sda6             110G   13G   92G  13% /home
/dev/sdb5             193G  292M  183G   1% /media/video_workspace
/dev/sdb6             271G   22G  249G   9% /media/Shared
overflow              1.0M  248K  776K  25% /tmp
gvfs-fuse-daemon      9.8G  9.7G     0 100% /home/roy/.gvfs
/dev/sdc1             233G  188G   46G  81% /media/Maxtor_External_____
[/FONT]
```
As you can see sda9 is still almost full. How do I clean out the cache? Is that what i did when I cleared /var/cache/apt? There's also very little in the /tmp folder even when I view hidden files. I also tried sudo rm -rf ~/.Trash/*


I'd still like to list all that's in sda9. Can it be done?

Cheers guys.

---

### Post by Volt9000 on 2009-06-04
One thing you can do is run Disk Usage Analyzer, which, when you scan a device, will give you a nice graphical representation of what's taking up space.

It's similar to the Windows program WinDirStat.

To start Disk Usage Analyzer just run from terminal:

```

gksu baobab

```

I think the gksu is necessary to access some root-owned stuff.

---

### Post by drs305 on 2009-06-04
Take a look at the linked guide in my signature line for Recovering 'Lost' Disk Space. 

It has a series of steps you can take to search for the causes and provides remedies for many of the most common things which eat up disk space.

---

### Post by Mylorharbour on 2009-09-27
Thanks guys. I still couldn't get to the bottom of it but as I've now had the same problem on my laptop, running Intrepid, I delved a little deeper using drs305's disk space link.

On the laptop the sda7 mount point is /
sda7 is a 20Gb partition, 
/home is sda8 but is largely unused as file storage is on an NTFS partition /media/Shared which shares files with WinXP in a dual boot configuration.

Now I'm still playing with linux apps so I've been downloading quite a few which I would have expected to be the root cause but here's what I've done to date to free up space.

I've deleted files in /var/cache/apt as Paqman says (for anyone else reading this do not delete the archives/partial folders nor the archives/lock file..... thanks Paqman) and deleted the trash which leaves me with 3.9Gb free on sda7. There is no root trash to delete. The Disk Usage Analyser, run as root with just sda7 (/) scanned shows / usage to be 3.5Gb so the question is what's using the rest of sda7? By the rest I mean 20Gb-(3.5Gb-3.9Gb)=12.6Gb

System Monitor/File Systems shows sda7 as ext3, Total 18.3Gb, Free 3.9Gb, Available 2.9Gb, Used 14.5Gb, 83% used. Why would the free and available figures be different?

I appear to be developing a blind spot for the linux filestem but I'll keep plugging away till one day when I believe I'll experience that eureka moment.

Thanks again guys

---

### Post by Mylorharbour on 2009-09-29
Solved

Whatever I did to delete root's trash didn't work. The cause of my problem was that Simple Backup's default destination is /var/backups. Set to do daily backups it didn't take long to fill the 20Gb. I reckon I must have been logged in as root when I deleted these which put them into root's trash.

The most effective way to clear root's trash is:

```
gksu nautilus /root/.local/share

```

The command will open and display the Trash folder. Delete it using SHIFT-DEL. If you use DEL only it will only move it back to the same place. You can look at the contents of Trash if you want - you will find two folders - info & files. "files" will contain the actual deleted files.

Note: When you shift-delete the Trash folder, it and the subfolders will be removed. However, the next time root deletes something they will be recreated.

Thanks to drs305 for helping me with this.

---

