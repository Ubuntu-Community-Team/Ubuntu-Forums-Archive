---
title: "deleted partitions in a dual boot harddrive, would like to get them back"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by 440corbon on 2009-03-09
I was getting a little cocky and started playing around with things. I wound up deleting my partitions using gparted. I haven't formatted so everything is still there. But I need to get last years photos that weren't backed up before the wife kills me.

---

### Post by bumanie on 2009-03-09
Get testdisk from [here]("http://www.cgsecurity.org/wiki/TestDisk") and try to recover the partitions with it. If that doesn't work try photorec. I assume, ubuntu is not usable so download the .iso and burn it to a cd. If ubuntu is useable, > sudo apt-get install testdisk to use testdisk > sudo testdisk to use photorec > sudo photorecLook at the documentation on the link and also look [here]("http://www.users.bigpond.net.au/hermanzone/p21.html") for more tutorials. Good luck. Both these programs work very well. Testdisk can restore partitions, photorec will read data off the 'raw' hard drive, independent of the filesystem.

---

### Post by louieb on 2009-03-09
The  newest versions of testdisk and photorec are available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by 440corbon on 2009-03-09
Thanks guys. I had an older copy of testdisk and photorec. But was a little gun shy after my botch job. and for the life of me I couldn't get the new versions installed. I am dl'ing system rescue now. Hopefully it will work for me.

---

