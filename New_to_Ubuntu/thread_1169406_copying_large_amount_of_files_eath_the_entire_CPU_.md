---
title: "copying large amount of files eath the entire CPU cycles..."
date: 2009-05-25
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-25
Hi
Thank you for reading my post
I tried to copy some 16.4GB of files from my hard disk to the external hard driver and the copy process eat 100% of the cpu power :O. is it normal?

I have Ubuntu 9.04, CPU 3.0GHz, Ram 2GB, internal hard drive: SATA, external hard drive: Western Digital, USB 2.

Thanks

---

### Post by Efros on 2009-05-25
If they are small files it can take a long time for the preparation for copying. I've also found that Nautilus can be a little flaky with copying and moving large numbers of files. When moving files to another drive on a remote computer I find that nautilus will copy the file and then usually crash when trying to delete the file source.

---

### Post by kpkeerthi on 2009-05-25
Copying lots of files should not occupy your CPU 100%. But your computer will start to crawl due to the IO (disc access) involved. 

You can use [ionice]("http://linux.die.net/man/1/ionice") if you want to tweak the IO priority of a program.

---

### Post by LiamWilson on 2009-05-25
try if you want to copy them, first make sure all the folders are in 1 file. open the terminal and run
```
cp /path/to/your/files /media/disk
```

for example, if i wanted to move a folder called stuff fom my Home folder to my external hard drive, i would run
```
cp /home/liam/stuff /media/disk1
```

Where the 'cp' command is the copy command, '/home/liam/stuff' is the folder i want to move, and '/media/disk1' is the drive I want to move it to.

Hope this helps.

---

### Post by 3rdalbum on 2009-05-25
If it's an NTFS hard disk, then it's normal to use high CPU cycles due to the driver involved. Otherwise, it's normal to use a high amount of your computer's IO ability (input/output) which will sometimes show up as CPU use, and likewise make your computer run slower.

---

### Post by blueridgedog on 2009-05-25
+1 to NTFS and processor load.

---

