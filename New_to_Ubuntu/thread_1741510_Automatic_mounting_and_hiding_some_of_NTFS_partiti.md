---
title: "Automatic mounting and hiding some of NTFS partitions"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by johncoss on 2011-04-28
Hello everyone,

I started using Ubuntu at home after using it a year on work. I installed ubuntu along side with Win XP and 7 on separate partition and used GRUB to select OS on startup. No problem there.
When I start ubuntu, in Nautilus (left panel) it lists all ntfs partitions that I have and I need to click on every partition so they can be mounted in filesystem (/media/{partition_name}). Most of my linux programs uses (reads) files from ntfs partitions (music, etc...) so they are unavailable when I start those programs. Example: qmmp in his playlist has mp3s located on ntfs partitions and they are not readable until I mount them from Nautilus. This is a bit irritating to do every time I log in. Is there a way to make automatic mounting of filesystems when I start Ubuntu?
Also, can I somehow hide Windows System partitions (where WinXP and Win7 resides) since I don't want to Ubuntu 'accidentally' mess with them. Simply, I want them totally invisible and unmountable from Nautilus (or anywhere else from Gnome).

Thanks!

---

### Post by jtarin on 2011-04-28
Time to study [FSTAB c]("https://help.ubuntu.com/community/Fstab")onfiguration.

---

### Post by Morbius1 on 2011-04-28
Might I suggest a simpler approach - use templates instead for your fstab entries.

I'll show you my own set up as an example:
[B]
[COLOR=Blue]EDIT[/COLOR]:[/B] If you currently have any of these partition mounted then unmount them first.

[1] Run the following command to see how your system sees your partitions:
```
sudo blkid -c /dev/null
```You'll get an output that looks something like this:
> /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" 
/dev/sdb1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" 
[2] Create permanent mount points:
```
sudo mkdir /mnt/WinXP
sudo mkdir /media/Backup
```[COLOR=Blue]*I created a mountpoint for WinXP in /mnt so that a mount icon will not show up on the desktop.*[/COLOR] [COLOR=Blue]*Mountpoints in /home/username and /media produce mount icons on the desktop.*[/COLOR]
[3] Add the following lines to fstab:
```
UUID=DA9056C19056A3B3 /mnt/WinXP ntfs defaults,nls=utf8,umask=227,gid=46 0 0
UUID=66E4DC83E4DC56C1 /media/Backup ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```[COLOR=Blue]*The Backup line is exactly the way the Ubuntu installer would have created the line in fstab had you asked it to do so during the initial install. *[/COLOR]

Note: the WinXP line will allow all local login users to read but not write to the partition. If you want to prevent all access then change the umask value to: umask=777. That will prevent all access - except for root.

[4] Save fstab and run the following command to test for errors and mount the new partitions:
```
sudo mount -a
```

---

### Post by jtarin on 2011-04-28
@Morbius1....a concise digest of my link.....which has a little more detailed documentation, but let's not get too detailed.:P

---

### Post by johncoss on 2011-04-29
Thanks for your info. I used information that I read from fstab and now I mounted my ntfs drives correctly. Thanks for your help guys :)

---

### Post by Paddy Landau on 2011-04-30
It's good that you solved the problem.

I learned some things here, too.

Please mark your thread as solved.

---

