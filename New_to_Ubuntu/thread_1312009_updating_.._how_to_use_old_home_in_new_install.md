---
title: "updating .. how to use old home in new install????"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by oldsoundguy on 2009-11-02
Starting the process of upgrading and picked a not for prime time computer to do it on first.

I have a separate partition on which I moved my /home folder and it booted fine (after following the directions on the psychocats site for doing so)
Then I did a clean install of 9.10 on the thing.
I KNOW that the partition is there as it was on 8.11 and gparted still shows it there.  Problem is there are NO hard drives shown in 9.10 (at least can't FIND them)
And then there is the issue of getting the contents of the home folder with all of it's installed programs and settings .. into 9.10.
Search as I might, can't find the info here (could be using  the wrong language in the search .. who knows?)
Would appreciate a few links on what to do and thanks!

---

### Post by NickJones on 2009-11-02
Does it show up under Places, Computer, chances are it won't have a name and when you open it it won't show your documents, you will have to go /home/username/ and you may have to do it under root.
Nick

---

### Post by pastalavista on 2009-11-02
If you have a seperate partition set as /home, it won't show as a seperate drive in Nautilus. It will show in gparted and in the output of fdisk -l. When you installed, did you use the manual mode and uncheck the format box for /home? If not, the data you had there is gone.

---

### Post by oldsoundguy on 2009-11-02
> **pastalavista said:**
> If you have a seperate partition set as /home, it won't show as a seperate drive in Nautilus. It will show in gparted and in the output of fdisk -l. When you installed, did you use the manual mode and uncheck the format box for /home? If not, the data you had there is gone.

OUCH!!  did NOT uncheck and go manually!  Oh well, as noted .. NOT a critical machine and this was the first time I tried to do it this way.  Almost always bit the bullet and installed fresh and then started adding goodies .. guess that's the story again! LOL 

BTW .. NO hard drives show in Nautilus .. NONE, and I have the primary partitioned and another untouched for data storage .. nothing shows!

Thanks for the reply!

At least it is not my LTS machine that I kludged!

---

### Post by pastalavista on 2009-11-02
If you gave your drives mountpoints when you created them, they will all be found in Filesystem. Does Filesystem show? All you should see is Filesystem and CD and removable drives. If you didn't assign mountpoints, they should show as seperate drives.

---

### Post by oldsoundguy on 2009-11-02
> **pastalavista said:**
> If you gave your drives mountpoints when you created them, they will all be found in Filesystem. Does Filesystem show? All you should see is Filesystem and CD and removable drives. If you didn't assign mountpoints, they should show as seperate drives.

YEP!!! Filesystem and floppy and the opticals and the card reader show .. so used to the old system where the hard drives showed also!

I am assuming what happened is that the home folder that is in it's own partition had the NEW home folder overwrite the old .. am I correct?

---

### Post by pastalavista on 2009-11-02
> **oldsoundguy said:**
> YEP!!! Filesystem and floppy and the opticals and the card reader show .. so used to the old system where the hard drives showed also!

I am assuming what happened is that the home folder that is in it's own partition had the NEW home folder overwrite the old .. am I correct?

That's right. If you format at install, everything is new. The only way to tell you're on a different partition/drive that you gave mountpoints (which adds them to the filesystem) in Nautilus is by the free space that shows in the status bar. If you remember the name you gave the mountpoints, you should have no problem finding them.

---

### Post by oldsoundguy on 2009-11-02
> **pastalavista said:**
> That's right. If you format at install, everything is new. The only way to tell you're on a different partition/drive that you gave mountpoints (which adds them to the filesystem) in Nautilus is by the free space that shows in the status bar. If you remember the name you gave the mountpoints, you should have no problem finding them.

Thanks for the info! .. Been using Linux (in a limited manner) since Mandrake 4!!  And Ubuntu FULL TIME (about 98% actually) since 7.40.  Just that I have really not delved into the "guts" of the program that much .. all I know is I like it and it WORKS for me!

---

