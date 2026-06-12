---
title: "Fixing write permission problem - possible with Ubuntu?"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by edanto on 2011-07-15
I have an external drive full of files that my better half can't write to with her Mac.  She can't create folders/files at any level on the drive.

I can create files/folders when it is connected to my ubuntu laptop.

The problem arose from a dodgy iomega NAS, which messed up the file permissions on our data and eventually died.  The external drive in question is our backup of that NAS.

Is it possible for me to do something with Ubuntu, since I can write to the drive, to change the permissions so that she can also write to the drive when it is connected to her Mac?

I don't really speak command line, but would be happy to try anything recommended.  thanks!

---

### Post by aktiwers on 2011-07-15
```
sudo chmod 777 -R /media/thenameofyourdrive
```If you dont know the name of the drive, look in your /media folder and find it there.

---

### Post by Blasphemist on 2011-07-15
I'll add this link for more detail.
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

---

### Post by edanto on 2011-07-15
Thanks guys.

My command would be : sudo chmod 777 -R /media/Seagate 1TB

One more small hurdle to get over. The name of the drive is two words (Seagate 1TB) and the command won't work because of it.  

When I go into disk utility and unmount and try to edit label, I get the error that

"Error changing fslabel: helper exited with exit code 1: helper failed with:
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' option.
NOTE: If you had not scheduled check and last time accessed this volume
using ntfsmount and shutdown system properly, then init scripts in your
distribution are broken. Please report to your distribution developers
(NOT to us!) that init scripts kill ntfsmount or mount.ntfs-fuse during
shutdown instead of proper umount."

Is there something I can do about that, please?

---

### Post by aktiwers on 2011-07-15
Just type the command and when you are at sudo chmod 777 -R /media/S 
Hit your tab key - it will autocomplete the word.  (I guess you know its the one above capslock, but now I say it anyways).

---

### Post by edanto on 2011-07-15
Ah ha!  Very handy, thanks.

Seems to be running now, I guess I'll check it in the morning and see if it's all fixed.

Much appreciated.

---

### Post by Blasphemist on 2011-07-15
I believe that the reason for 2 boots in windows is that the first one will run a chkdsk and you want to boot it again to make sure it still doesn't see an issue.

---

### Post by edanto on 2011-07-16
Thanks guys, I ran that last night, but it doesn't seem to have worked.

When I connect the drive to the Mac, it's read-only but on the Ubuntu its fine.

Any other ideas please?

---

### Post by Morbius1 on 2011-07-16
It's very likely based on your description that the external usb device is formatted in NTFS. There's 2 problems with NTFS:

* You can't chmod an ntfs partition because there there are no Linux permission bits on an NTFS filesystem.

* By default OSX can't write to an NTFS partition - only read. If you are running Snow Leopard I think ( I repeat - I think .. ) that ntfs-3g is installed by default but write is not enabled. 

I would either go to the apple forums or change the title of your post to indicate that you want to write to NTFS on OSX so someone with OSX experience can see your question.

In the event that I'm wrong and this is an ext3 or ext4 partition then you have another problem. I don't think that OSX recognizes a Linux filesystem at all. Another question for the apple forum.

There is another possibility - but it depends on how lucky your are. You could insert the drive into your Ubuntu box and use Samba to share it and access it from the Mac across the network. Just open up Nautilus, right click on wherever the drive mounted, select "Sharing Options", mark all three boxes and see if she can access the share. Despite what you may have read Samba works out of the box for the majority of people but when it doesn't it's a living hell.

BTW, never ever do a "chmod -R 777 /path". It will make every file executable and throw out the window 40 years of UNIX tradition. Use this instead:
```
sudo chmod -R a+rwX /path
```

---

### Post by JC Cheloven on 2011-07-16
We could start by the begining finding out what filesystem it is. Please run ```
sudo fdisk -l
``` and see (post back the output if you don't understand it). 

Also, my mate can r/w to ntfs from his mac. I think he had to install something additional (like ntfs-3g), but it's user transparent and works fine once installed. Just as in linux.

---

### Post by idoitprone on 2011-07-17
if you do have a ntfs file system 

[http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html](http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html)   

[http://code.google.com/p/macfuse/downloads/list](http://code.google.com/p/macfuse/downloads/list) 
  mac fuse itself 

[http://sourceforge.net/projects/ntfs-3g/](http://sourceforge.net/projects/ntfs-3g/)
 mac fuse 3g driver

---

