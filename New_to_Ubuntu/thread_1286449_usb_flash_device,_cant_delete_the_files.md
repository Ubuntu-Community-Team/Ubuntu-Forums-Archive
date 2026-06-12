---
title: "usb flash device, cant delete the files"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by super kim on 2009-10-09
how do i get around this?
```

sudo rm 1st.avi
rm: cannot remove `1stl.avi': Read-only file system

```i don't want any of the files on the drive. i use the pen drive to watch avi's with my xbox so they are only copies

if i look at the disk properties it says this:

name   disk-1
type    folder(inode/directory)
contents   7 items, totaling 2.2gb

location   /media
volume   8.0gb media

free space 7.4gb

115.4mb used
7.4gb free

total capacity 7.5gb

filesystem type msdos


which does not add up, and i can't get rid of the files, they can be viewed and read (they don't play anymore tho) and two of them have thumbnails even.


i'm just going to play my guitar until someone helps make sense here:guitar:

---

### Post by itsbrad212 on 2009-10-09
4 things I could think of:

1) type:

```
sudo nautilus
```

then navigate to /media/   whatever your usb flash drive's ID is

then try to delete it from there

2) try a different USB port

3) delete the .1000Trash file from your flash drive if there is one (it is something like that)


4) make sure the trash on your computer is empty

try those and tell me what happeds :popcorn:

---

### Post by super kim on 2009-10-09
> **itsbrad212 said:**
> 4 things I could think of:

1) type:

```
sudo nautilus
```then navigate to /media/   whatever your usb flash drive's ID is

then try to delete it from there

2) try a different USB port

3) delete the .1000Trash file from your flash drive if there is one (it is something like that)


4) make sure the trash on your computer is empty

try those and tell me what happeds :popcorn:
1 tried the gksudo nautilus before i tried the sudo rm *.avi and it didn't work

2 didn't work

3 i can't delete them. thats where the files are, in the trashfile.

4 yes trash file on the computer is empty


when i mount the drive the files appear in the trash file, and cannot be deleted from there either.

---

### Post by PrePenguin on 2009-10-09
Format it ... Its worth a shot..

---

### Post by mcduck on 2009-10-09
> **super kim said:**
> how do i get around this?
```

sudo rm 1st.avi
rm: cannot remove `1stl.avi': Read-only file system

```

Since the error message says that the filesystem is mounted as read-only, even using superuser privileges is not going to help anything.

Anyway, that sounds like there's some problem with the data on the drive, so Ubuntu mounted it as read-only to protect it from further data loss. running fsck or chkdisk(in Windows) on the drive might solve the problem, but since you said the drive as no data that you'd have to keep you can also simply use gParted (or any other tool of your choice) to format the partition and create a new, filesystem on it.

---

### Post by super kim on 2009-10-09
> **PrePenguin said:**
> Format it ... Its worth a shot..

yea i probably will, i was going to earlier but couldn't work out if it was sdg1 of some thing else as three things came up when i mounted the drive.

i think the drive is mounted as read only since the error says "read only filesystem" and the files are not read only, how do i mount the drive a read and write?
it's a usb pen drive by the way


edit.

i was typing while your post came in mcduck.

i don't use windows.

do i need a live cd to partition the drive, or can i just type it into the terminal, oh yea and does anyone know an easy way to get the drives name like fdg1?

---

### Post by wdzieczny on 2009-10-09
Try this I know it sounds overall simplistic but trash the files then unmount the volume it will generally prompt you with an option to delete the trashed files.

---

### Post by renkinjutsu on 2009-10-09
try this as your mount parameters ```
sudo mount -o rw,user /mount/device /mount/point
```

---

### Post by PrePenguin on 2009-10-09
Another option replacing the obvious is 
sudo rm -rf /home/username/.local/share/Trash/

---

### Post by super kim on 2009-10-09
> **wdzieczny said:**
> Try this I know it sounds overall simplistic but trash the files then unmount the volume it will generally prompt you with an option to delete the trashed files.
yea it does the prompt, but does not delete the files, the issue is that the drive is mounted as read only, i should not need to format the drive, only mount it correctly.

i don't know if this is relevant but the problem happened when i was deleting the files and the drive lost power (my bad using a usb hub) then the computer froze, so i pulled the disk out, now i'm here, having fun.

---

### Post by mcduck on 2009-10-09
> **super kim said:**
> yea i probably will, i was going to earlier but couldn't work out if it was sdg1 of some thing else as three things came up when i mounted the drive.

i think the drive is mounted as read only since the error says "read only filesystem" and the files are not read only, how do i mount the drive a read and write?
it's a usb pen drive by the way


edit.

i was typing while your post came in mcduck.

i don't use windows.

do i need a live cd to partition the drive, or can i just type it into the terminal, oh yea and does anyone know an easy way to get the drives name like fdg1?

You don't need a live-CD to partition any other drive than your root partiton. But you need to unmount the drive before you can edit it's partitions and filesystems..

There are many ways to find out the device name for your USB drive, here are couple (pick the one that works best for you):

- run "mount" while the drive is mounted, and find the drive with correct size.

- run "sudo fdisk -l", and pick the drive with correct size.

- run "tail -f /var/log/dmesg" and then plug the drive in. You should see how the new device is detected and what name it's assigned.

---

### Post by super kim on 2009-10-09
> **renkinjutsu said:**
> try this as your mount parameters ```
sudo mount -o rw,user /mount/device /mount/point
```


this sound good this is wrong though
```
 sudo mount -o rw,user /mount/sdc1 /media/disk-1
```oh gosh i'm being blond right now i know sorry help me out please :KS

```
$ tail -f /var/log/dmesg
[   13.520037] type=1505 audit(1255027438.518:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1975
[   16.546823] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.546827] Bluetooth: BNEP filters: protocol multicast
[   16.616306] Bridge firewalling registered
[   18.637300] [drm] Initialized drm 1.1.0 20060810
[   18.674362] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.674369] pci 0000:00:02.0: setting latency timer to 64
[   18.674610] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   18.679714] [drm:i915_setparam] *ERROR* unknown parameter 4
[   18.679757] [drm:i915_getparam] *ERROR* Unknown parameter 6


```

---

### Post by super kim on 2009-10-09
ok i just unmounted and mounted it about a million times and then i could delete them all of a sudden :)

unexplainable but i'm happy

ha ha ubuntu did it all on it's own, it's clever like that.

---

### Post by PrePenguin on 2009-10-09
Ubuntu must be a male if ya mount and unmount us enough we will do anything for ya ;) lol anyways mark it as solved and glad your issue is resolved.

---

### Post by m4tic on 2009-10-09
I had this issue a lot of times, what i do is i copy the contents of thedrive to my home folder. then format the flash drive and restore what files i want back and the file that i wanted to remove i delete from the home folder

---

