---
title: "cannot mount volume"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by ironrod05 on 2009-03-11
when trying to open drive i received the error cannot mount volume. the extended details read as follows:


 $LogFile indicates unclean shutdown (0,0) Failed to mount '/ dev/sdal': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action:Choice !:if you have Windows then disconnect the external devices by clicking on the 'safely remove hardware' icon in the windows taskbar then shutdown windows cleanly. 
choice 2: if you don't have windows then you can use the 'force' option for your responsibility. for example type on the command line: mount -t ntfs-3g/dev/sda1/media/disk -o force or add the option to the relevant row in the /ect/fstab: /dev/sda1/medai/disk ntfs-3g force 0 0

i have tried the second option and still can not get the volume to open. any help would be great.

---

### Post by kansasnoob on 2009-03-11
Look at Taurus' post #2 here:

[http://ubuntuforums.org/showthread.php?t=1090486&highlight=ntfsfix](http://ubuntuforums.org/showthread.php?t=1090486&highlight=ntfsfix)

Of course you're working with a different partition number!

Clear as mud?

---

### Post by presence1960 on 2009-03-11
Do you have Windows? If you do you should boot Windows, connect the drive, then remove the device by clicking the "safely remove hardware" icon in the task bar. When you restart you should be able to access the drive from linux. This happened to me and thank God for this forum, because I had all my files backed up to that drive.

---

### Post by ironrod05 on 2009-03-12
> **kansasnoob said:**
> Look at Taurus' post #2 here:

[http://ubuntuforums.org/showthread.php?t=1090486&highlight=ntfsfix](http://ubuntuforums.org/showthread.php?t=1090486&highlight=ntfsfix)

Of course you're working with a different partition number!

Clear as mud?


thanks for pointing me to taurus' post, i think that i should work. ill give it a try after work today

---

### Post by inos22 on 2009-04-22
I apologize for the redundancy on this subject. I am experiencing a similar issue where i cannot open my 194.4 gb media.  i would like to know if running the option suggested will delete any of my data?
 I currently have windows:redface: on my pc but i'm having a reboot loop issue with it, this is why i am using ubuntu to extract my business files from the hard drive in order to restore it.

 A reply on this will be greatly appreciated. 
Thank you!

---

### Post by lukjad on 2009-04-22
The usual reason that Ubuntu cannot read a filesystem is that it was not closed properly. What is needed is for someone to boot to the partition (if it is a partition that has an operation system in it) or mount it, and the nproperly shut it down. If you are able to access the drive, mount it, then unmount it in Windows, that **should** fix the problem.

---

