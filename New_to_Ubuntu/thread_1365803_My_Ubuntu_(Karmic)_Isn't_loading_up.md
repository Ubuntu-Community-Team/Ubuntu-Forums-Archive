---
title: "My Ubuntu (Karmic) Isn't loading up"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by ylooF on 2009-12-27
Well, I've been using Ubuntu for about 6 months now. Upgraded to Karmic the day after launch & I've never had any major issues, but then... My computer froze (all except the mouse) & I couldn't do ANYTHING, I tried many different Key Combos, with no Results. So I hit the Reset button on my comp, but now when I try to boot It logs in fine, but while loading up, I see the Gnome taskbar at the top (with none of my launchers...) and that's as far as it gets, all I can do is move the mouse. I have tried Fail-safe mode and a few other things with no success. Anybody got any Ideas?

---

### Post by kansasnoob on 2009-12-27
Have you tried starting up in Recovery Mode:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Those instructions should be correct if you upgraded to 9.10 from 9.04. If you did a fresh install then you'll have grub2 so you need to press the space bar rather than the esc key.

Starting in Recovery mode may provide some clues, otherwise please boot the Live CD & post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by ylooF on 2009-12-27
Ok, so I booted into Recovery Mode and when I got to the [FONT=monospace][/FONT]"root@yourmachine:~#" I followed it up with; sudo fdisk -l & it brought these results: 

Device       Boot       Start      End
/dev/sda1   *             1            19086 

And then some more of my HDDs Specs, did I do this correctly?

---

### Post by kansasnoob on 2009-12-27
> **ylooF said:**
> Ok, so I booted into Recovery Mode and when I got to the [FONT=monospace][/FONT]"root@yourmachine:~#" I followed it up with; sudo fdisk -l & it brought these results: 

Device       Boot       Start      End
/dev/sda1   *             1            19086 

And then some more of my HDDs Specs, did I do this correctly?

I wished you had posted the full output like this:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            3764       19457   126062055    5  Extended
/dev/sda3            2678        3763     8723295   83  Linux
/dev/sda5            3764        4799     8321638+  83  Linux
/dev/sda6            4800        9284    36025731   83  Linux
/dev/sda7            9285       10301     8169021   83  Linux
/dev/sda8           10302       12215    15374173+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
/dev/sda10          15033       17103    16635276   83  Linux
/dev/sda11          17104       17870     6160896   83  Linux
/dev/sda12          17871       19457    12747546   83  Linux
/dev/sda13          12216       13046     6674976   83  Linux
/dev/sda14          13047       14879    14723541   83  Linux

Partition table entries are not in disk order

```

It's odd to see only one partition, normally there would be at least 3, 1 being / (aka: root), another extended and a third for SWAP.

Anyway I assume you have a Live CD? 9.04 or even older would be fine, then we could mount and chroot your installation and try to gather some more info.

Note: Read specifics about how my mount & chroot process works here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Assuming that /dev/sda1 is your root partition, from the terminal in the Live CD (please copy-n-paste):

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Then to be sure we're in the right place:

```
lsb_release -a
```

Then to gather some more disc info:

```
parted /dev/sda print
```

```
df -H
```

```
du -sh /*
```

Really need that info before deciding how else to proceed.

When we're done we'll:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

---

### Post by ylooF on 2009-12-27
root@ubuntu:/# parted /dev/sda print
Model: ATA Maxtor 6G160E0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  157GB  157GB   primary   ext3            boot
 2      157GB   160GB  3052MB  extended
 5      157GB   160GB  3052MB  logical   linux-swap(v1)

root@ubuntu:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              155G    33G   114G  23% /
none                   155G    33G   114G  23% /sys
df: `/sys/fs/fuse/connections': No such file or directory
df: `/sys/kernel/debug': No such file or directory
df: `/sys/kernel/security': No such file or directory
udev                   522M   144k   522M   1% /dev
none                   522M   144k   522M   1% /dev/shm
none                   155G    33G   114G  23% /var/run
none                   155G    33G   114G  23% /var/lock
none                   155G    33G   114G  23% /lib/init/rw
gvfs-fuse-daemon       155G    33G   114G  23% /home/fooly/.gvfs
/dev/sr0               155G    33G   114G  23% /media/cdrom0
root@ubuntu:/# du -sh /*
5.4M    /bin
41M    /boot
0    /cdrom
140K    /dev
18M    /etc
25G    /home
0    /initrd.img
0    /initrd.img.old
317M    /lib
16K    /lost+found
12K    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/5490/task/5490/fd/3': No such file or directory
du: cannot access `/proc/5490/task/5490/fdinfo/3': No such file or directory
du: cannot access `/proc/5490/fd/3': No such file or directory
du: cannot access `/proc/5490/fdinfo/3': No such file or directory
0    /proc
7.6M    /root
8.2M    /sbin
4.0K    /selinux
200K    /srv
4.0K    /sys
88K    /tmp
4.6G    /usr
548M    /var
0    /vmlinuz
0    /vmlinuz.old
root@ubuntu:/# 

Is this the correct information?

---

### Post by kansasnoob on 2009-12-27
Yes, that all looks fine. I wondered if there might be a disc space problem but there's not.

If you've already exited the chroot run those first three commands again and let's see what an update & upgrade renders.

Only if you've unmounted:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Then:

```
apt-get update && apt-get upgrade
```

That may provide some clues, but I'm also wondering if you had recently just begun using Compiz or made some other changes that might effect the Xserver?

I'm a dummy when it comes to Compiz but someone here would surely know how to disable 3D effects from terminal.

---

### Post by Mrandersonjr on 2009-12-27
If you are unable to mount the drive then run

sudo fsck -f -c -y /  (or wherever your drive that you are trying to mount is)

---

### Post by kansasnoob on 2009-12-27
Another command worth trying from within the chroot:

```
apt-get install --reinstall ubuntu-desktop
```

---

### Post by ylooF on 2009-12-27
Thank you very much for your help Kansas!
I'm about to try booting normally After running:
apt-get install --reinstall ubuntu-desktop 
Although Compiz would make sense because I use AWN (Avant Window Navigator) and it has always warned me about it...

After I get it back up and running, I'm switching to Gnome Do's Docky. ;)

Once again, Thanks for everything!

---

### Post by ylooF on 2009-12-27
It failed to boot. :(

Did you want this too?

root@ubuntu:/# apt-get update && apt-get upgrade
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  adobe-flashplugin
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@ubuntu:/# 



Should I post a new Thread asking for someone to help me disable 3D?

---

### Post by kansasnoob on 2009-12-28
> Should I post a new Thread asking for someone to help me disable 3D?

Possibly, yes!

I know how to mount & chroot a system to fix things, but, being legally blind, 3D is just wasted on me so I never use Compiz or any other type of 3D goodies.

---

