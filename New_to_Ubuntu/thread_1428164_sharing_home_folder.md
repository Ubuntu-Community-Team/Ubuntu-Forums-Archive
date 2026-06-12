---
title: "sharing /home folder"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by bobheaps on 2010-03-12
I am running 9.04. I would like to install 9.10 on another partition and select which one to use at boot. However I would like to use just one /home folder to be shared between the two systems. Can I do this? If so, how?

---

### Post by cairnzi on 2010-03-12
check this out.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=976298](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=976298)

---

### Post by mikewhatever on 2010-03-12
Do you have a separate home partition? If not, perhaps you can try and simlink the new home folder to the old one. I'd recommend testing it first in a virtual machine.

---

### Post by audiomick on 2010-03-12
> **cairnzi said:**
> check this out.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=976298](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=976298)
From post #10 onwards, this is pretty relevant.

---

### Post by cairnzi on 2010-03-12
@ audiomick, yeah sorry didnt read entire link just kind of thought it was what he was after.:D

---

### Post by ajgreeny on 2010-03-12
I suggest you use a / partition for each install which contains your home hidden folders, but also make a separate shared /data partition, mounted at boot time for both/all installs into which all your data files go, ie documents, photos, music, videos etc etc.  You could make a separate /home folder for each install if you wanted, but you will not have to do so.

You may need to link your hidden .mozilla/firefox folder from one to the other if you want to keep everything in sync, but that is easy to do; just drag from one partition to the other with the middle mouse button and you'll get an option menu, **Move here, Copy here, Link here** from which you can choose.

---

