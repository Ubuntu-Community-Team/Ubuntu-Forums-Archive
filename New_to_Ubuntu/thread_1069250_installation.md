---
title: "installation"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by rgroene on 2009-02-13
I've been having problems with my computer lately. Windows will not boot on my computer, so I decided to try to see if I could install Linux (I am currently running off of a CD-ROM). While I did create partitions (one being 2.5 GB and one being 1 GB) before, when I run the installation, it does not list anything at all, and the only options available are Quit, Back, and Forward.

If I just click Forward, it says, "No root file system is defined. Please correct this from the partitioning menu."

---

### Post by overdrank on 2009-02-13
> **rgroene said:**
> I've been having problems with my computer lately. Windows will not boot on my computer, so I decided to try to see if I could install Linux (I am currently running off of a CD-ROM). While I did create partitions (one being 2.5 GB and one being 1 GB) before, when I run the installation, it does not list anything at all, and the only options available are Quit, Back, and Forward.

If I just click Forward, it says, "No root file system is defined. Please correct this from the partitioning menu."

Hi and welcome, how did you set up the partitions, with the live cd?
2.5 gigs will not be enough for the installation of Ubuntu.
Are you able to see the partitions if you select manual partition?
You may also check the cd for errors.

---

### Post by rgroene on 2009-02-13
I didn't think it would be, but the other problem is that it won't let me partition any more (the other partition I made before with a different version of Linux using qtparted). When I unmount my hard drive, it has a warning/error sign next to it, and though there are 10 GB of free space, it won't let me reallocate any of it. But I'd think that it would still show something there.

How do you select manual partitions? Sorry, I'm new to Ubuntu and don't know too much about it. I could try making another copy of the CD (burning the ISO image again). It has been giving me error messages about some program called ubiquity crashing...

---

### Post by overdrank on 2009-02-13
> **rgroene said:**
> I didn't think it would be, but the other problem is that it won't let me partition any more (the other partition I made before with a different version of Linux using qtparted). When I unmount my hard drive, it has a warning/error sign next to it, and though there are 10 GB of free space, it won't let me reallocate any of it. But I'd think that it would still show something there.

How do you select manual partitions? Sorry, I'm new to Ubuntu and don't know too much about it. I could try making another copy of the CD (burning the ISO image again). It has been giving me error messages about some program called ubiquity crashing...

Hi and there could be errors on the windows partition and this can cause issues. You may check the cd for errors at the start and install page when first booting the cd. 
Manual partition is located in the install when you should be given the option of guided install. 
Could you give us some system specs?

---

### Post by kansasnoob on 2009-02-13
Could you post either the output of:

```
sudo fdisk -l
```

or a screenshot of the disc layout using either qtparted or gparted?

---

### Post by rgroene on 2009-02-14
Nevermind...

I checked the disk for errors, and it said that there were none. Then, for some reason, the next time that I clicked on installation it worked properly. I have no idea what I did to make it start working, but, in any case, I got Linux installed. I ultimately decided to forget about the partitions and just get rid of Windows altogether (as it didn't work anyway).

Thanks for you help. If I have any other problems with Linux I can't figure out, I'll be sure to come here for help.

---

