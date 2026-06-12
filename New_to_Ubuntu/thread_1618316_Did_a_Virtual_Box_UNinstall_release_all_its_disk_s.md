---
title: "Did a Virtual Box UNinstall release all its disk space back to Ubuntu 10.10?"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by daibak2010 on 2010-11-10
As newbie who recently installed (sudo apt-get vbox) and uninstalled (Synaptic complete removal) VirtualBox 3.2.10 r66523 with VBOXADDITIONS_3.2.10_66523 for Linux Guest Additions running Maverick Meerkat I'm suspicious some of about 30GB hard drive space I had assigned to the VirtualBox installation (installed in part of existing Ubuntu /home partition) has not been fully released back to Ubuntu 10.10 now MaverickM is once again the one and only OS on this PC.

Of three partitions I originally set up in Ubuntu 10.10 MaverickM
sda1 root (/) with <30GB
sda5 /home    with 120GB Home Properties' Contents 36.2GB Free space 76GB
linux-swap    with 2GB
it would seem I'm missing free disk space of around 10GB or am I stupidly misreading this?

Current Ubuntu terminal output shows disk usage:

> daibak@HP-Pavilion-xz148:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              26G  3.2G   22G  13% /
none                  478M  228K  477M   1% /dev
none                  486M  316K  485M   1% /dev/shm
none                  486M   88K  485M   1% /var/run
none                  486M     0  486M   0% /var/lock
/dev/sda5             120G   38G   76G  34% /home
/home/daibak/.Private
                      120G   38G   76G  34% /home/daibak
daibak@HP-Pavilion-xz148:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda5 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/daibak/.Private on /home/daibak type ecryptfs (ecryptfs_sig=7826f7fca1c4a4a1,ecryptfs_fnek_sig=c0d70dd0ced43a70,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/daibak/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daibak)

If anybody can also link to howto's how to shrink the / partition by 10GB and resize the /home partition to pick up all the slack I'll be very grateful. 

TIA to all, daibak
==================
Ubuntu 10.10 only OS on ex-WinXP 2002 HP Pavilion xz148 Notebook PC
upgraded to 1GB RAM, 160GB 5400rpm Samsung HD, Belkin 54G WiFi card.

---

### Post by anewguy on 2010-11-10
Did you ever create a virtual machine using VBox?  If so, the package manager only removes the package, NOT the virtual disks, settings, etc., set up for you.  These are stored in your home folder.  I don't remember the exact folder name, and perhaps the folder is hidden so when using "Places" be sure to tell it to show hidden files.  I believe the folder is something like "vbox" or ".vbox".  You'll need to delete all of that also to return space still used even though you uninstalled the package.

Dave ;)

---

### Post by mrnelson1986 on 2010-11-10
> **anewguy said:**
> Did you ever create a virtual machine using VBox?  If so, the package manager only removes the package, NOT the virtual disks, settings, etc., set up for you.  These are stored in your home folder.  I don't remember the exact folder name, and perhaps the folder is hidden so when using "Places" be sure to tell it to show hidden files.  I believe the folder is something like "vbox" or ".vbox".  You'll need to delete all of that also to return space still used even though you uninstalled the package.

Dave ;)

I think by default they are saved in your /home folder, but yes you have to delete them manually (unless you delete them in the virtualbox application before you uninstall) so that is what is eating up your drive space.  When in doubt and not able to find the file, install a program called kdirstat and run it, it will show all files on your drive in "boxes" as well as a list by directory, and it will be pretty easy to identify a big 10GB chunk.

---

### Post by cpmman on 2010-11-10
Virtualbox keeps its Machines and HardDisks in your /home/<username>/.Virtualbox directory. (note the . before Virtualbox)

Check those to see if there is any residual items left - if so delete them and you will have all your disc space back.

To reallocate your partition sizes you need to boot into your live cd and use the Gparted program to re-size.

You MUST take a backup before using Gparted - partitioning is a delicate exercise at best depending on where the files have been placed within the partition.

---

### Post by daibak2010 on 2010-11-10
Many thanks for all your prompt replies with suggestions.
I'd already deleted the guest OS Fedora 14 *.vdi hard disk image from VBox Media Manager prior to deleting VBox app, as well as manually deleted all remnants of Vbox installation in hidden (leading dot or .) VirtualBox folder that Synaptic left behind in /home/username/.
Great suggestion to use GParted, thanks too for that and I'll observe the back-up caveats before proceeding with that. All much appreciated.
Perhaps I should mention for other newbies keen to try try out virtualization that Virtual Box 3.2.10 once you add the Guest Additions works just fine even on vintage hardware but I found Fedora 14 far too clunky and absolutely no match for Ubuntu 10.10 MaverickM's ease of use.

---

### Post by drs305 on 2010-11-10
And since these vdi's can be very large files, don't forget that the space is not released until you empty your trash. Until then they will continue to occupy hard drive space.

The same applies to anything you deleted as 'root', but these files reside in /root/.local/share/Trash. If you delete them from a 'root' browser use SHIFT-DEL so they don't just immediately return to the trash bin.

---

### Post by anewguy on 2010-11-12
Extremely good point - some of us assume the user knows things like that and forget to mention them, and the next thing you know you find out they didn't empty the trash!

Wish I had thought of it! ;) (but in reality I'm pretty stupid anyway ;) )

Thanks!
Dave ;)

---

