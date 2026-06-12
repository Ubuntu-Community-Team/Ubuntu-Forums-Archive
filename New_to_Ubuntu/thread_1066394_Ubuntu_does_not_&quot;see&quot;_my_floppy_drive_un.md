---
title: "Ubuntu does not &quot;see&quot; my floppy drive unit"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-02-10
How do you make Linux see a floppy drive?
It works fine under Win XP on dual boot computer.

Ed

P.S.

Until I figure out why wired ethernet, (under Ubuntu, works with Win XP) is not working I will have to transfer data to this pc for posting to forum. Have to get floppy working to do that.

---

### Post by karlmp on 2009-02-10
use a flash drive ?

floppies are outdated

---

### Post by jasonmh on 2009-02-10
First open a terminal and type "ls /dev/fd*" and make sure that you even have the fd0 module loaded.  If not than skip these instructions and go to the following command.
[Instructions on mounting a floppy]("http://www.alwanza.com/howto/linux/floppy.html")

If you don't have /dev/fd0 then open a terminal and do the following command.
```
sudo modprobe floppy
```
Note that this only corrects the issue for that instance.  When you reboot your computer, you'll have to do this again.

---

### Post by ozark_hillbilly on 2009-02-10
since i just spent 7 to 8 hundred bucks on this new system i don't need further expenditures right now. a flash drive would be nice but not an option at present. 
is there a way to extract file from linux partition under win xp. i could then copy to floppy.

Ed

---

### Post by ozark_hillbilly on 2009-02-10
how do i make it permanently see floppy?

ed

---

### Post by HotShotDJ on 2009-02-10
> **jasonmh said:**
> If you don't have /dev/fd0 then open a terminal and do the following command.
```
sudo modprobe floppy
```
Note that this only corrects the issue for that instance.  When you reboot your computer, you'll have to do this again.Actually, I don't think this is correct.  You need to check a few things... open Applications --> Accessories --> Terminal and then type the following:```
ls /media
```If there is a directory listing for "floppy0" then you should be all set, otherwise, execute the following command:```
sudo mkdir /media/floppy0
```Next, you need to execute the following command:```
gksudo gedit /etc/fstab
```See if there is an entry for your floppy drive.  I'm pretty sure that there is not.  If there IS, edit it to look like the following line.  If it is not there at all, add the following line to the end of the file:
```
# Floppy Drive
/dev/fd0     /media/floppy0     auto     rw,user,noauto,exec,utf8    0  0
```You shouldn't have to do anything else.  You should now be able to use your floppy

---

### Post by karlmp on 2009-02-10
[http://www.google.co.ve/search?q=extract+file+from+linux+partition+under+win+xp&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.ve/search?q=extract+file+from+linux+partition+under+win+xp&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)

---

