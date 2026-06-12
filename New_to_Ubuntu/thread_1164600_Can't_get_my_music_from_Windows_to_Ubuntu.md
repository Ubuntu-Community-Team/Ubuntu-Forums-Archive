---
title: "Can't get my music from Windows to Ubuntu"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by NoUrOtherLeft on 2009-05-19
Ok I know someone has probably asked this question, but, I had just installed Ubuntu 9.04 on to my laptop and I am trying to find all my music that was on Windows so I could put it on Ubuntu.  When I was searching in some of the topics in the forums I noticed that you have to go to "Places" and your windows partition is supposed to be there so you can mount it to get the folders for the music.  Well, when I go to "Places" the only thing that there is to mount is something called "TOSHIBA SYSTEM VOLUME" when I mount it and go into the drive it has the following folders:

"SOURCES" folder- Click on it and all it has in it is a "BOOT.WIM" file in it

"System Volume Information folder"- Click on it and it has a "tracking.log" file in it

A "BOOT.SDI" file

And a "WinREPartition.ini" file in it and that is it.


How do I get my music from Windows to Ubuntu?


Can someone PLEASE help me out I'm complete noob at Ubuntu.

---

### Post by taurus on 2009-05-19
Did you install Ubuntu on it own partition?  

Open a terminal and post the outputs of these commands, running one command at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by NoUrOtherLeft on 2009-05-20
well when i put ubuntu on my laptop i ran it from windows because for some reason my burner would not burn the iso on the disk....so i just mounted the iso on windows and ran it from there so.....in answer to your question....i guess not? im sorry i know i sound noobish but i did put in those commands you gave me and here is the output.....



germs@ubuntu:~$ sudo fdisk -l
[sudo] password for germs: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fff5971

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       14594   115683328    7  HPFS/NTFS
germs@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       11G  2.7G  7.2G  27% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  112K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  140K  497M   1% /dev
tmpfs                 497M   84K  497M   1% /dev/shm
/dev/sda2             111G  103G  7.5G  94% /host
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile

---

### Post by Laurence94 on 2009-05-20
i can only find dowloaded music itunes music which where from cds youll need to resync. mount the drive with music on and just like itunes find the file or foalder and click sync/add folder to music libray (excuse my spelling)

im sorry if i misunderstood the problem or my reply was not useful im also new to ubuntu!

---

### Post by NoUrOtherLeft on 2009-05-20
> **Laurence94 said:**
> i can only find dowloaded music itunes music which where from cds youll need to resync. mount the drive with music on and just like itunes find the file or foalder and click sync/add folder to music libray (excuse my spelling)

im sorry if i misunderstood the problem or my reply was not useful im also new to ubuntu!

yeah....that totally didn't help me....i need someone who knows what they are talking about but thanks for trying to help...

---

### Post by halitech on 2009-05-20
> **NoUrOtherLeft said:**
> Ok I know someone has probably asked this question, but, I had just installed Ubuntu 9.04 on to my laptop and I am trying to find all my music that was on Windows so I could put it on Ubuntu.  When I was searching in some of the topics in the forums I noticed that you have to go to "Places" and your windows partition is supposed to be there so you can mount it to get the folders for the music.  Well, when I go to "Places" the only thing that there is to mount is something called "TOSHIBA SYSTEM VOLUME" when I mount it and go into the drive it has the following folders:

"SOURCES" folder- Click on it and all it has in it is a "BOOT.WIM" file in it

"System Volume Information folder"- Click on it and it has a "tracking.log" file in it

A "BOOT.SDI" file

And a "WinREPartition.ini" file in it and that is it.


How do I get my music from Windows to Ubuntu?


Can someone PLEASE help me out I'm complete noob at Ubuntu.

the "TOSHIBA SYSTEM VOLUME" would be your windows restore partition. Can you still boot into windows? You may need to install the ntfs-3g programs as well.

---

### Post by NoUrOtherLeft on 2009-05-20
> **halitech said:**
> the "TOSHIBA SYSTEM VOLUME" would be your windows restore partition. Can you still boot into windows? You may need to install the ntfs-3g programs as well.

so why when i try to mount "TOSHIBA SYSTEM VOLUME" i still cant get my music? and yes....i can still boot windows.....and i installed the ntfs-3g programs(i think...well at least thats what it said) using the terminal and inputing the 'sudo apt-get install ntfs-3g' command and i got this message:

germs@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libtwolame0 libavutil49 gstreamer0.10-plugins-ugly libpostproc51
  libavformat52 gstreamer0.10-ffmpeg libswfdec-0.8-0 libdvdnav4 libdvdread4
  libsidplay1 libavcodec52 libmad0 libid3tag0 libmpeg2-4 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ntfs-config
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.0kB of archives.
After this operation, 442kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe ntfs-config 0.5.5-0ubuntu3 [41.0kB]
Fetched 41.0kB in 1s (33.2kB/s)     
Selecting previously deselected package ntfs-config.
(Reading database ... 111916 files and directories currently installed.)
Unpacking ntfs-config (from .../ntfs-config_0.5.5-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up ntfs-config (0.5.5-0ubuntu3) ...

so now what do i do?

---

### Post by halitech on 2009-05-20
because the "TOSHIBA SYSTEM VOLUME" is not your windows install, its the partition that holds the files to reinstall windows.

by the looks of what you posted, you installed the ntfs-config package, not ntfs-3g
```
sudo apt-get install ntfs-3g
```then see if you can see the windows partition

did you install ubuntu using WUBI?

---

### Post by nhasian on 2009-05-20
it sounds like you install ubuntu with wubi (inside of windows) so ubuntu does not get its own partition, it shares the ntfs partition with windows.  So to find your windows files in ubuntu:

on the menu go to Places->Computer and open Filesystem, then Host.  So basically your C: in windows is the same as /host/ and if you were using Windows Vista, your mymusic folder would be located in /host/Users/yourusername/Documents/My Music

---

### Post by 3rdalbum on 2009-05-20
> **halitech said:**
> 
did you install ubuntu using WUBI?

Yes he did.

If you had installed Ubuntu as a proper dual-boot system, then the advice given to you so far would be correct.

However, you installed Ubuntu as a "wubi" install - so Ubuntu is actually running from a file on your Windows partition. Therefore you will find your Windows partition in the filesystem, under /host.

---

### Post by halitech on 2009-05-21
I was thinking they had but wanted to confirm but it would certainly explain why the normal steps aren't working to see his data in windows.

---

