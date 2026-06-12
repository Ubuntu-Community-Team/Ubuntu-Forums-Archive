---
title: "accessing drives using terminal??"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by koyakishore on 2009-09-01
hi..

wen i was trying to access my drive thru command prompt..
it is gettin displayed that No such file existing..

with the other user..it is working fine..
I dono wat exactly the prob is..??

I'm following the below procedure in terminal..

cd /media(after dis if i type DIR..it is showing all the drives whch are present).. but if I type
cd /drivename
it is displaying NO USCH FILE OR DIRECTORY existing..

am i wrong anywhere??

---

### Post by tuxxy on 2009-09-01
Did you mount the drive you would like to CD to?

---

### Post by st33med on 2009-09-01
Yes, the /media or /mnt folder is where all mounted storage goes. It is not in the root ('/') folder

---

### Post by MrWES on 2009-09-01
from the terminal type

df

lets see what you have mounted and where it's at.

Bill

---

### Post by earthpigg on 2009-09-01
hi,

the folders in /media are waiting for a filesystem (cd, thumb drive, etc) to need it.

they will sit there waiting even if no cd-rom is inserted.
this will show you what you have mounted at present, and where it's at:
> df
this will show you what you have mounted in an easier to read format:
> df -Th -x tmpfs

edit:

also, it wont be cd /drivename anyways. observe, and note the *wrong command* and the _correct command_:
```
ep@chris-laptop:~$ cd /media
ep@chris-laptop:/media$ ls
cdrom  cdrom0
ep@chris-laptop:/media$ [I]cd /cdrom0
bash: cd: /cdrom0: No such file or directory[/I]
ep@chris-laptop:/media$ _cd cdrom0_
ep@chris-laptop:/media/cdrom0$ echo woot
woot
ep@chris-laptop:/media/cdrom0$ 
```


edit2: also, ls works a bit better in ubuntu than dir :D

---

### Post by koyakishore on 2009-09-02
thanks alott:)

actually, i used wrong command cd /DRIVENAME

i solved itt by using cd DRIVENAME..

its working now..

thanks everyone:)

---

