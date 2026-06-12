---
title: "How to move/delete files on a NTFS USB Drive"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Flywaver on 2009-05-16
Greetings,

I have an external USB drive that's NTFS and I can't move or delete files on this drive...is there a way other than formatting it?

Thanks in advance,

Cheers!

---

### Post by NHArticleTen on 2009-05-16
> **flywaver said:**
> greetings,

i have an external usb drive that's ntfs and i can't move or delete files on this drive...is there a way other than formatting it?

Thanks in advance,

cheers!

don't format it!

---

### Post by NHArticleTen on 2009-05-16
whew, that was close...

ok, more information is probably in order here...

such as, but not limited to, Operating Systems...

and, what you want to do with the stuff on the drive...

---

### Post by drs305 on 2009-05-16
> **Flywaver said:**
> Greetings,

I have an external USB drive that's NTFS and I can't move or delete files on this drive...is there a way other than formatting it?

You may be having permission problems. You should be able to read/write to NTFS partitions by default, but you can configure your system to make sure you are the owner. 

Open gconf-editor, go to the storage section and edit the NTFS mounting options. Right click on "Mount options", "Add" and enter  "uid=1000" assuming you are user 1000. You can check by typing "id" in a terminal.

```

gconf-editor /system/storage/default_options/ntfs/mount_options

```

That should mount any NTFS partition with you as the owner, which may solve your problem.

Although removable drives don't normally go in fstab, this is an excellent source of information by bodhi.zazen regarding booting different formats:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by Flywaver on 2009-05-16
well, it's my backup drive that I was using with windows.

Disregard, I went into storage device manager, selected the drive, went into the assistant and I saw that it was in read only mode! :)

All is cool!! Thanks anyways! :)

---

