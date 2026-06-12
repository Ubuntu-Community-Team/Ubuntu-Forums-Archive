---
title: "Please help to educate me"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Acradon on 2009-01-04
Hi all, 

I am not a computer illiterate, however, there are some things I would like to understand better. 

I have just recently started to use Ubuntu again and am completly switching to it (at least at home, unfortunately I still have to use windows at work).

Yesterday I installed vuze and downloaded an .avi file. Here is a list of problems I encountered and mostly solved by shear luck not knowledge. I would like to know what I have done and what a couple of terms mean. 

1. Vuze keeps giving me an error about some installation problem and that it has to restart. On doing so, the error repeats and restarting is necessary agin and again and again...... As it was getting late I decided to postpone the problem solving to the next day, but vuze kept starting over and over again. WHY? I finally uninstalled it. 

2. Despite the problems encountered the programme worked when I just ignored the error and I was able to download a movie. In order to play the movie on my DVD player I consulted UBUNTU forums and found DeVeDe as a suitable conversion program (only after noticing that .avi files do not play in my DVD player...I am learning). I did manage to produce a DVD that played the movie in the DVD player but came across multiple steps where I had to guess what to do. a) What is a FAT32 exactly, I thought it was my hardrive, and why should I not place and image file there? I decided to place the image directly onto the DVD, which it didn't. I found the file in the default folder, although I am certain I changed this. b) When I wanted to burn the DVD it asked me whether I want to burn from file or from image. I chose image, which seemed to have been the right choice as it worked, but what is the difference? 

So in short: 

What is the problem with Vuze?
What is a FAT32 exactly? 
What is the difference between burning from image or file?

Thanks in advance for some answers. I would like to add that since I have Ubuntu I am a happy person. I want to be able to actually use the OS in an adequate way that it deserves. Therefore this post.

Acradon

---

### Post by kwacka on 2009-01-04
1. No idea what the problem with Vuze was - what was the error code given? I assume you have java installed running? There are alternatives - e.g. deluge-torrent or Transmission.

2. FAT32 is a method of formatting a harddrive that was developed by Microsoft. Not being a particulary effeicent system it means that you need to defrag the harddrive on a regular basis. Othe MS formats include FAT16 & NTFS (used by XP onwards. Linux usually uses ext2, ext3, or reiserfs formatting.

Most cameras (at least ther memory cards) use FAT.

3. An iso is a direct copy of a CD/DVD. If I burn it as usual I will find a single file (e.g. file.iso).

If I burn the image, the resultant CD/DVD will contain all the files, directories as the original CD/DVD

---

### Post by handydan918 on 2009-01-04
One of the specific shortcomings of fat32 was the filesize limitation. IIRC, it couldn't handle a file over 2 GB.

---

### Post by stderr on 2009-01-04
Hello Acradon

> **Acradon said:**
> I would like to add that since I have Ubuntu I am a happy person. 

You're not the only one :)

Unfortunately I'm unfamiliar with the applications you're using; however maybe I can give some answers.

FAT32 is a filesystem. In other words, it is a way of storing files on a hard drive and indexing those files such that they can be located by directory structures and names. Every hard drive (actually every "partition" of every hard drive) needs to have a filesystem before you can start doing things like loading an operating system or using it to store files.

There are many different filesystems... Linux's main filesystem is ext3, and Windows and Mac can also be made to read/write to ext3 with the correct software. It is a [journaling filesystem]("http://en.wikipedia.org/wiki/Journaling_file_system"). Windows' main filesystem, from XP onwards, is NTFS. Pre-XP (I think...) it was FAT32. Prior to that FAT16. Ubuntu can read/write NTFS and FAT32 by default.

There are many more; many people using linux choose ReiserFS, JFS, XFS and many more; although some are more suited to certain partitions and setups.

So, FAT32 is a simple filesystem that pretty much every OS can understand. It suffers from a limit of about 4GB, though.

As for the conversion, if you're converting an avi file to DVD .VOBs (i.e. you end up with a VIDEO_TS and maybe an AUDIO_TS folder containing VOBs and such), it won't do the conversion and burn it to disk at the same time. If the conversion was slower than the burning, that could cause problems, etc.

It builds the output first, on your hard drive, and when complete it will burn it to disk. You may have chosen to just create an image rather than create the folders VIDEO_TS etc... in which case it would have probably created an .[ISO image]("http://en.wikipedia.org/wiki/ISO_image"), which would be a direct copy of the VIDEO_TS etc. Then you'd have to burn the image to a disk. 

As for burning from image or file, when burning from an image you're saying you have a '[disk image]("http://en.wikipedia.org/wiki/Disk_image")' i.e. an actual block of data you want transferred directly to disk, rather than a file or set of files you want to be stored on it. If you had created a .iso, or .img or of that ilk, you should have selected to burn from image, as you did :)

As for the Vuze problem, I can't say I've tried Vuze myself, but perhaps just reinstalling would help?

```
sudo apt-get install vuze
```

or, if it's still installed, 

```
sudo apt-get install --reinstall vuze
```

or it may help to **purge** the installation, i.e. remove it and remove all it's configuration files too, and then re-install

```
sudo apt-get purge vuze
sudo apt-get install vuze
```

---

### Post by Acradon on 2009-01-04
Thank you all very much for your answers. No doubt I will come back with more soon, but this really helped a lot. I will try to reinstall Vuze and see whether I can get rid of the error somehow. Probably loosing the last bit of sanity that I have left, but it will be even more rewarding in the end. 

Acradon

---

