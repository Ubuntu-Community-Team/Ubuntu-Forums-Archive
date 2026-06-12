---
title: "Brand New Install (And User) Cloning A Drive To Another Drive"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Glkanter on 2011-04-16
Hi, I am a newbie and I have a brand new PC with only Ubuntu 10.10 installed. I have a 2.0 TB drive, with 1.4 TB 'unallocated'. Which is kind of my first problem.

I also have my 'old' Windows drives in the system, just as they were. They are a 1.0 TB SATA split evenly into 2 500GB logical drives and a 250GB SATA drive. The content on these and the formatting can be erased.

My system sees everything great, but I'm sure things could be better.

Since I have an abundance of space and physical drives, I figure my backup strategy should be simple and complete: Copy the entire Linux system onto one of the other drives in a way that the backup drive is bootable, and complete. I could make this backup every night. It's just no problem.

So, I know what I want to do, but I'm spinning my wheels trying to find the right tools.

Here's what Red Hat Disk Utility 2.30.1 reports for the 2.0 SATA drive:
Bios Boot Partition 1.0 mb
Linux Basic Data Partition 52 GB [Linux system only]
Linux Basic Data Partition 500 GB [all data files]
Unallocated space 1.4 TB [I'd like to make logical drives out of this]
Linux Swap Partition 28 GB

So, how can I copy all the Linux stuff and data verbatim to one of the other drives in my system, so that it will be ready and able as an immediately available replacement drive?

Thank you!

Please let me know if I was too verbose, or whatever. I want to be a good forum member.

---

### Post by coolbrook on 2011-04-16
Consider the Clonezilla Live CD.

---

### Post by Glkanter on 2011-04-16
OK, that's a fast and great start. I've read a few page about Clonezilla, until it got too dense for me.

Would this be a solution where a cd boots and does the copying?

I was hoping for a solution where the system would trigger the whole cloning to happen in the middle of the night. Is that possible?

Any thoughts on how best to partition all of those drives?

Thanks!

---

### Post by lmarmisa on 2011-04-16
I do not recommend at all a full copy of your Ubuntu system on the fly.

Clonezilla is a good solution for a complete backup of your system (or a complete cloning of your hard drive) because the copy is made while the Ubuntu system is stopped. This backup/cloning is 100% reliable.

Other alternative is to make periodical backups of the files of the home directory. This is not difficult using commands like **at**, **cron** and **rsync**.

I really recommend both alternatives. For example a complete backup every month and a daily backup on the fly of your home directory.

---

### Post by Glkanter on 2011-04-16
Thanks. Yes, I can understand that an image can't be done on the fly. Too bad, though.

This is just a home PC, with nothing mission critical on it. For the reasons I explained in the original post, I'm focused on the hard drive cloning.

Does Clonezilla have a GUI? Will I need to download and/or install anything else? Any tips or advice that might make this easier for me, or keep me out of trouble?

Thanks!

---

### Post by lmarmisa on 2011-04-16
> **Glkanter said:**
> Thanks. Yes, I can understand that an image can't be done on the fly. Too bad, though.

This is just a home PC, with nothing mission critical on it. For the reasons I explained in the original post, I'm focused on the hard drive cloning.

Does Clonezilla have a GUI? Will I need to download and/or install anything else? Any tips or advice that might make this easier for me, or keep me out of trouble?

Thanks!

Yes. Clonezilla Live has a GUI. You only have to follow the different menus. Quite simple.

You do not need any other program. [Clonezilla]("http://clonezilla.org/clonezilla-live.php") is able to run from a Live CD, from a USB flash drive or even from a partition of a USB hard drive.

---

### Post by Glkanter on 2011-04-16
OK. I've downloaded the Clonezilla ISO. And I've downloaded k3b-2.02 to copy Clonezilla to the CD.

But this is where I get lost. I have very little experience with the command line, and I can't always understand what the instructions are telling me. I go back to DOS, so I understand about changing/making directories and copying files. But I still have trouble with Linux terminology.

So, while this is easy for you to follow, I'm having some trouble. This is what I get when I double click on the "INSTALL" file  for K3B2.02:

"Installing K3b 2.0
------------------


What you need to run K3b:
 mandatory:
  - since K3b is a CD writing program a cd writer would be a good thing to have ;-)
  - the QT4 library (at least version 4.3)
  - the KDE4 libraries (at least version 4.0)
  - the cdparanoia library for cd ripping from Monty
  - the cdrtools (cdrecord, mkisofs) from Joerg Schilling
  - the dvd+rw-tools by Andy Polyakov for DVD writing

 optional:
  - cdrdao, the other linux cd writing program from Andreas Mueller
  - the transcode tools for DVD ripping and DivX/XviD encoding from Thomas Oestreich
  - vcdimager >= 0.7 for creating video cds
  - libmad for mp3 decoding
  - ogg-vorbis libraries for encoding and decoding
  - the FLAC++ libraries for flac-decoding
  - the eMovix package
  - TagLib by Scott Wheeler for reading Meta data tags
  - the musepack (or now mpcdec) library for decoding Musepack audio files
  - the ffmpeg library to decode other audio file formats such as wma
  - the sndfile library to decode audio file formats such as AIFF or VOC
  - the lame library to encode audio files in the mp3 format
  - sox to encode audio files in formats such as AIFF or VOC
  - a dynamically compiled libffmpeg for wma decoding
  - the musicbrainz library for metadata queries for single audio titles
  - polkit-qt for K3bSetup (tool for changing permissions of programs and devices)

After that it's all the same:

  mkdir build
  cd build
  cmake ..

If the cmake run was successful you are presented with a list of configure results that shows
which optional features are enabled. Now just compile K3b:

  make

Now you are ready to install:

  make install (as root)


See PERMISSIONS on hints how to properly setup the permissions to use K3b without problems.


Have fun
Sebastian Trueg (trueg@k3b.org)"

I understand that the instructions begin with "mkdir build". Is it really as simple as:
typing n those 3 commands?:
mkdir build
cd build
cmake ..
then the 4th:
make
and the 5th:
make install (as root)

Do I type in the '..' after 'cmake'?
Do I type in 'make'?
Do I type in the words "(as root)"?

Maybe you could tell me exactly what I have to do, and what I will see, step by step?

Thank you!

---

### Post by Dutch70 on 2011-04-16
Hi and welcome to UF

A link to those directions would be more helpful than copying & pasting them into your post.

Whenever you see (as root) it basically means to run it with admin privileges. To do that you put the word "sudo" in front of the command.
```
sudo make install 
```

Also, if you type the command in wrong, it will tell you that it's not recognized, no harm, no foul.

---

### Post by lmarmisa on 2011-04-16
Yo have to burn a CD with that ISO image file (use Applications -> Sound & Video -> Brasero Disc Burner -> Burn Image, for example).

Then boot your system from that CD and follow the menus. You do not need any command line.

I recommend you as the first test to make a complete backup of your first hard drive storing the backup files in your second hard drive.

---

### Post by Glkanter on 2011-04-16
> **lmarmisa said:**
> Yo have to burn a CD with that ISO image file (use Applications -> Sound & Video -> Brasero Disc Burner -> Burn Image, for example).

Then boot your system from that CD and follow the menus. You do not need any command line.

I recommend you as the first test to make a complete backup of your first hard drive storing the backup files in your second hard drive.

Clonezilla & Brasero were very reliable and easy to work with.

I, however, am neither of those things. I've spent most of the day getting myself into and out of trouble with disk drives. So, I am starting a new thread where I ask for help so that I can avoid another partitioning.

Otherwise, I just need to come up with an appropriate backup strategy, as the tools are doing their job, I think. Should I close this thread as "resolved"?

---

