---
title: "Adrian"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by AdrianV on 2011-03-04
i had just installed Ubuntu because my laptop with Windows 7 had some problems and constantly booted to a blue screen... i was tired of it so i elected to try UBUNTU.  i downloaded ubuntu 10.10 netbook and used a USB drive and installed it from there.  I am new to Ubuntu so i have no idea what to do so i just kinda winged it.  (it didn't even ask me to install ubuntu alongside another OS).

My laptop hard drive has 3 partitions, C, D, and E.  D is just full of data and E i think is recovery stuff for windows.  so when i installed ubuntu, i partitioned C into 2 and fully deleted E.  Everything went well until it asked me to restart to complete installation.  I did.. and when it restarted, it went straight to Windows Recovery.. i didnt even have an option what to load.

any suggestions?

---

### Post by turtle153 on 2011-03-04
If you don't want Windows at all, just opt to install Ubuntu on the whole drive.

---

### Post by deconstrained on 2011-03-04
Did you install Ubuntu inside of Windows (WUBI) or did you boot to the USB disk and repartition/install using Ubiquity?

---

### Post by AdrianV on 2011-03-04
I actually have a new problem... i did the install using the whole hard drive... i have a 250 hard drive so i partitioned it into 4 groups..

5g designated /
100 gigs /home
140 gigs /user
5g swap

(im not sure if this is good or bad, but i had no idea so i just did that)

anyways, after installing (asked me for time zone, name, password, and took time til everything was done), it asked me to restart to finalize installation.

when i restarted my laptop... the usual HP screen with the escape F2, F9, F10 etc came up then went blank with a blinking cursor on the top upper left corner.. and nothing else happened... so now my laptop is windows free.. but apparently Ubuntu isn't loading either... 

so i took the USB pendrive again, and looked at it said that dev1 has Ubuntu 10.10 installed in it.. but i dont know why it wouldn't load.

thanks for the help!

---

### Post by deconstrained on 2011-03-05
Since boot-up issues are the most aggravating problem that so often causes users to run straight to the forums, someone wrote a boot/block device info script that gets posted in 99% of all "ubuntu won't boot" threads.
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
That should give you the necessary diagnostic information.

---

