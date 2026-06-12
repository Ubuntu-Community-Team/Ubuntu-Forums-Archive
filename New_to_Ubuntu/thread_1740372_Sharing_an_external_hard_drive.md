---
title: "Sharing an external hard drive"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by raincityrunner on 2011-04-26
I've been using an external hard drive to back up my stuff on a machine running osx10.6. The drive was formatted FAT32, I believe. I now want to leave it connected to my ubuntu machine (just started using), and access files on it from both machines ultimately. When I power up the drive when it's connected to the ubuntu machine, I can see many folders and subfolders, but they are all "empty" (size 0bytes), and I can't open any of them. 

I would be a very grateful noobie if someone can help with this.
Thanks for reading.

---

### Post by Buntumatic on 2011-04-27
Shouldn't happen with FAT32 ... are you sure this is what it is formatted to?

Anyway, open a terminal and do ```
tail -f /var/log/messages
``` then plug in your drive and try to access it. What messages you get?

---

### Post by josephmills on 2011-04-27
please plug the drive into the usb port then press ctrl+alt+t when the terminal pops up enter ```
lsusb
``` then paste here.  Also after you plug it in if you go to system-->admin-->disk utility do you see it there is it list as the wrong thing/size?

---

### Post by raincityrunner on 2011-04-27
josephmills: lsusb shows that it sees the device.
Buntumatic: not totally sure, that was the default format. When I go to disk utility it says Apple Partition map, idk if that's pertinent.

[IMG]http://raincityrunner.files.wordpress.com/2011/04/1740372shot.png[/IMG]

---

### Post by josephmills on 2011-04-27
unplug it then plug it back in then go to your terminal and type in ```
dmesg
``` and let us see like the last 40 lines

---

### Post by Buntumatic on 2011-04-27
Message from 21:25:33 indicates is formatted in HFS - Apple filesystem.

---

### Post by raincityrunner on 2011-04-27
So, if it's formatted in HFS, does that mean that I'm SOL?

---

### Post by K_45 on 2011-04-27
Back up all data off it, then format it with Gparted to NTFS.

---

### Post by Buntumatic on 2011-04-28
Why NTFS?!

If it is going to be connected to the Linux box and shared from there to other computers a native Linux filesystem is the best choice.

---

### Post by Buntumatic on 2011-04-28
> **raincityrunner said:**
> So, if it's formatted in HFS, does that mean that I'm SOL?Google ...
  [http://somethingkindawierd.com/blog/computers/linux-computers/08/2009/readwrite-to-hfs-on-ubuntu/](http://somethingkindawierd.com/blog/computers/linux-computers/08/2009/readwrite-to-hfs-on-ubuntu/)

---

### Post by K_45 on 2011-04-28
> **Buntumatic said:**
> Why NTFS?!

If it is going to be connected to the Linux box and shared from there to other computers a native Linux filesystem is the best choice.

  Because a Mac will be accessing it. So NTFS is a good choice.

---

### Post by Buntumatic on 2011-04-28
Mac will be accessing it over NFS (or CIFS or whatever). You seem not to understand there is a difference between NFS, CIFS, AFS and NTFS? The first three are network filesystems used to access remote volumes, the second one is proprietary local MS filesystem that has not much use in POSIX world.

---

### Post by K_45 on 2011-04-28
Its the OP's choice whether they want a local or network filesystem.

---

### Post by Buntumatic on 2011-04-28
> **raincityrunner said:**
> I've been using an external hard drive to back up my stuff on a machine running osx10.6. The drive was formatted FAT32, I believe. I **now want to leave it connected to my ubuntu machine** (just started using), and access files on it from both machines ultimately. When I power up the drive when it's connected to the ubuntu machine, I can see many folders and subfolders, but they are all "empty" (size 0bytes), and I can't open any of them. 

I would be a very grateful noobie if someone can help with this.
Thanks for reading.
The way I understand this raincityrunner wants to share it over network, thus local filesystem should be Linux native.

---

### Post by BertN45 on 2011-04-28
It is not clear from the question whether he thinks about network sharing. In all cases it is an USB disk, so the chance is big, that it will be needed again some day to connect directly to a MAC, Linux or Windows system.

The only safe choice for an USB disk is FAT32 or maybe NTFS in the near future. So I would advice to avoid HPS and EXT formats as proven by the current problem.

---

### Post by raincityrunner on 2011-05-02
Yes, my intention is ultimately to share files over a local network, accessing the external drive through the linux machine. The problem I have now is that the memory taken up on the external drive is bigger than either the linux or osx machine hard drives, therefore how to back up is a dilemma, unless there is a way to partition the disk without first wiping/formatting it (it is less than half full).

---

### Post by K_45 on 2011-05-02
What do you mean by memory? HDD space? How big is the external drive and how big are the other hard drives?

---

### Post by raincityrunner on 2011-05-06
HDD. External is 1TB, the internals are 150G and 40G.

---

