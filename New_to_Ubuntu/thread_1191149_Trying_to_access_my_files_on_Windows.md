---
title: "Trying to access my files on Windows?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by SamR09 on 2009-06-18
Well hey everyone, i'm new to Ubuntu, and i've switched mainly for the looks and the stability of the OS, (I came from Windows Vista.)

Anyhow, I've ran into a problem, i'm currently using a Dual Boot to get on here ( I get the choice wether i want to run Vista or Ubuntu on startup ) And i want to be able to access the files on my C:/ that are on my vista boot, on my ubuntu boot. 

How can i do it? I dont know if that mounting a partition or whatever works, i've tried it but i don't think i've done it right, so i thought i'd post on here for some one to one help. 


Please help me ;) 

:KSSam:KS

---

### Post by bodhi.zazen on 2009-06-18
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Mauler5858 on 2009-06-18
You should be able to go to Places>Computer.  Find the partition you are looking for(it should be listed here)...doublej click it and Gnome/Nautilus should take care of mounting it and getting you browsing it.  It may ask you for sudo password which is fine.  From there you can just browse it.

However this will not persist through reboot.

In order to do that you will have to append a line to your /etc/fstab file.

/dev/sda1	/media/WINXPPRO	ntfs-3g	defaults	0 0

Something like this would suffice, of course substituting in the correct device node(first column) and the correct mount point(second column)

Enjoy!

---

### Post by SamR09 on 2009-06-18
I've tried this guide, when i open up the NTFS-Config tool, i get this

[IMG]http://www.psychocats.net/ubuntu/images/mountwindows14.png[/IMG]


But the 'Enable write support for internal device' Isn't there, i click ok, and nothing happens.




EDIT:


Opening up Computer and looking for it doesen't work either, I just have Filesystem and CD-ROM/DVD-ROM Drive.

---

### Post by BinaryFeast on 2009-06-18
Also, if you have installed Ubuntu with wubi (from inside windows), your Windows files can be found under "/host".

---

### Post by SamR09 on 2009-06-18
When i go to /host all i see is folders and no .exe's or anything else.

Actually no, that's just my World of Warcraft folder.. Nevermind. i think it's all working.

---

