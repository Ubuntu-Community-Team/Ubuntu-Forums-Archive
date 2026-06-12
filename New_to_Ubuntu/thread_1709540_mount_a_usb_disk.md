---
title: "mount a usb disk"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by Willye on 2011-03-18
Hi, i have a  new usb hard drive, i have copied files from windows, i want to use it disk as backup of my windows(personal files) and use it to save linux files, i mounted it on my ubuntu 10.04, but i have a little issue, 'cause the permissions appears as follow:
```

```
/media> mount
...
...
/dev/sdb1 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,allow_other,blksize=4096)

/media> l
total 12
**drwxrwxrwx 1 root root 4096 2011-03-18 17:29 DATA**
lrwxrwxrwx 1 root root    7 2011-01-25 18:05 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2011-01-25 18:05 floppy0
drwxr-xr-x 2 root root 4096 2011-02-13 20:53 kingston


the permisions of DATA are 777, inside data i have all my files, but if i try to change permissions or owner or group it has not effect, always appears:

/media/DATA> l
total 8
drwxrwxrwx 1 root root 4096 2011-03-18 12:18 FILES
drwxrwxrwx 1 root root    0 2011-03-18 11:34 Movies
drwxrwxrwx 1 root root 4096 2011-03-18 11:26 My Music
drwxrwxrwx 1 root root    0 2011-03-18 09:30 RECYCLER
drwxrwxrwx 1 root root    0 2011-03-18 15:09 Software
drwxrwxrwx 1 root root    0 2011-03-18 09:30 System Volume Information

what must i do ????

```

```

---

### Post by Willye on 2011-03-18
Any Ideas ????

---

### Post by andrewthomas on 2011-03-18
What is the filesystem type?

---

### Post by seawolf167 on 2011-03-18
NTFS formatted drives cannot store linux permission properties, they will all gain 777 upon moving, this is one of the reasons why you should never backup your system to an NTFS drive.

---

### Post by Willye on 2011-03-18
ntfs

---

### Post by Willye on 2011-03-18
so, what can i do, i need to have permisions for my files in linux, and i need to copy data from windows systems, i need it for both functions, do i need to format again? ... how ????

---

### Post by seawolf167 on 2011-03-18
I think the easiest solution would be to format the hard drive as ext3 or ext4 so you have no issues with *nix permissions/attributes. Then to copy Windows files over, simply mount your Windows partition in Ubuntu and copy over from there.

You can automatically mount your Windows partition by adding an entry in /etc/fstab, do it via the command *mount*, or the easiest GUI way is to click Places -> XYZ GB Filesystem (where XYZ will be the partition size for your Windows installation)

---

### Post by Willye on 2011-03-18
the thing is that the windows files are in several computers, home,  office, friends, ..., so it's a bit difficult, what other thing could i do ??????

---

### Post by seawolf167 on 2011-03-18
There are a [couple programs ]("http://www.howtoforge.com/access-linux-partitions-from-windows")that let you view ext2/3 (not sure about the newer ext4) from Windows computers.

You could always split your external hard drive into two partitions, one NTFS and the other ext3/4, then Windows would only see the NTFS partition and Ubuntu would see both.

---

### Post by Willye on 2011-03-19
that's could be a possible solution, i did not want to do that, but apparently there are not much more options

---

