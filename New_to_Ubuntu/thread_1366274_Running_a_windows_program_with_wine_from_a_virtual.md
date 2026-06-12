---
title: "Running a windows program with wine from a virtual drive"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Cooter2543 on 2009-12-28
I am trying to run a windows program from an .img file in Ubuntu 9.10
I don't have a cd burner to burn the .img, so I have to run it through a virtual drive.

What is a good program to do this in Linux, and is this possible with Wine?

---

### Post by Ben Wright on 2009-12-28
By using the mount command you will be able to mount the image file which will allow you to read it and if it contains an exe wine has a reasonable change of being able to play it.  Try something like: (See [http://ubuntuforums.org/showthread.php?t=149197](http://ubuntuforums.org/showthread.php?t=149197)). Thanks

```

sudo mkdir /media/temp (your new temp mount point)
mount -t udf your_file.img /media/temp -o loop (the meat of the operation)

```

---

### Post by Cooter2543 on 2009-12-29
The terminal command didn't work for me.

I finally did get it to work by using AcetoneISO2. It's a great program, and I would recommend it to anyone.

I am now running a program (that was designed for Windows), from a disc image, through a virtual disk drive, under a Windows compatibility layer (Wine), and it runs flawlessly, in fact even better than it did in Windows XP. Take THAT Microsoft! :lolflag:

---

