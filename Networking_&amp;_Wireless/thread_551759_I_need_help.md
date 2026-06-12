---
title: "I need help"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by krazy1912 on 2007-09-15
Try to remove the module ath_pci to let ndiswrapper to use the wifi.
"sudo rmmod ath_pci" or "sudo modprobe -r ath_pci"

also try put that module in the blacklist of modprobe to avoid his
loading on the startup:

sudo nano /etc/modprobe.d/blacklist-common

Insert this line:
blacklist ath_pci

Then restart.
When u will boot again.
Load the windows driver it from the uncompress folder:
#ndiswrapper -i net5211.inf
then install to modprobe
#ndiswrapper -m

----------------------------------------------------------------------------------------------

root@eric-laptop:~# ndiswrapper -i net5211.inf
Installing net5211
couldn't copy net5211.inf at /usr/sbin/ndiswrapper-1.8 line 144.

What's the deal?

---

### Post by kevdog on 2007-09-15
Id check your version of ndiswrapper to start with.  You should have installed from source code rather than repository.  Anything less than version 1.47 might give you problems.

Also completely clearout the /etc/ndiswrapper directory -- ie delete everything inside this directory

---

### Post by krazy1912 on 2007-09-15
I have 1.8 I think. 1.9 is the most current I think, But I'm running edgy.

How do i do that? 

Do I open the file and just delete everything?
If so How do I open the directory?

---

### Post by krazy1912 on 2007-09-15
K i downloaded the 1.47 tar file.

I'm going to attempt the install.

---

### Post by krazy1912 on 2007-09-17
Help

---

