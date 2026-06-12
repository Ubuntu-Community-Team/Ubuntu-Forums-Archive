---
title: "errors updating 8.10 to 9.04"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Matt26 on 2009-05-05
i decided to upgrade from ubuntu 8.10 to 9.04 last night, which didn't go so well.  i received a number of errors (attached) and by the end ubuntu indicates it is now 9.04, i'm not sure what state the update left my system in... what do these errors mean, and what should i do to resolve these issues?

i don't know if anyone else has run into these issues yet but any help would be appreciated.

i do have a backup of my hard drive in case i need to restore my 8.10 installation.

thanks.

---

### Post by collinp on 2009-05-05
I had these same errors, not sure what caused them. They mean that your package lists are corrupt, but I do not know how to remedy this. The only way I fixed it was to do a clean install, which was what I had been planning on doing. Anyone?

---

### Post by Michael.Godawski on 2009-05-05
hi, 

that's why I do not really like the Upgrade option and prefer a clean CD install. 

Is your system working in the first place? Do you encounter crashes?
Have you run
```
sudo dpkg --configure -a
```to check if some package are broken?
What does your menu.lst show?
```
cat /boot/grub/menu.lst
```How do your sources.list looks like?
```
cat /etc/apt/sources.list
```

---

### Post by Matt26 on 2009-05-05
i guess i may have spoke to soon- i checked the update manager and the linux kernel update was available so i downloaded it and it installed successfully, i restarted the computer and now so far most of what i was having issues with post-upgrade is now working again.

so my next question is now do i upgrade my file system from ext3 to ext4?  i thought the upgrade did the conversion but apparently not.

is this something i can do without reformatting?  how would i go about doing this update?

thanks.

---

### Post by Didius Falco on 2009-05-05
Here is a nice HowTo:  **Convert your ext2/ext3 file system to ext4 (in Jaunty)** 


[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)


Regards,

Didius

---

