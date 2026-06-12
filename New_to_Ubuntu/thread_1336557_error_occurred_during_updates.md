---
title: "error occurred during updates"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by mommachoo on 2009-11-24
parse error, in file `/var/lib/dpkg/updates/0000' near line 34 package `sun-java6-plugin':EOF during value of field `Depends' (missing final newline)
Please can anyone help with this problem? Unable to update or install from synaptic.

I've been researching on all archive forums for the past 3 hours and tried all suggestions. sudo dpkg --configure -a does NOT work, I get the above message. 

Does anyone have any suggestions!!?

---

### Post by mgranet on 2009-11-24
Delete everything in /var/cache/apt then retry sudo dpkg --configure -a.

---

### Post by mommachoo on 2009-11-27
Hi, sorry I've only just seen your reply. Thank you for this,  I know I sound stupid, but I'm a absolute beginner and I don't know how to delete /var/cache/apt. Please can you tell me?  Thanks:confused:


I've just tried apt-get autoclean but no good

Also tried sudo rmdir directory_/var/cache/apt 
it say's no such file or directory!! 

sudo apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
mommachoo@LEBURG99:~$ sudo dpkg --configure -a
dpkg: unable to create `/var/lib/dpkg/updates/tmp.i': No such file or directory
mommachoo@LEBURG99:~$

---

### Post by mommachoo on 2009-11-27
I have found a solution   `sudo mkdir -p /var/cache/apt/archives/partial`

Everything OK now

---

