---
title: "Need some partitioning help"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by steve70 on 2009-02-22
Hello all, 

I have a 160GB HD that I split into two partitions, I was able to mount the partitions, now I want to use the second partition for virtualbox. How do I go about this?

---

### Post by x33a on 2009-02-23
create an save the virtual machine on the second partition.

---

### Post by Rolcol on 2009-02-23
VirtualBox creates a file for the "hard drive" of the operating system.  I suggest you use the option to create the entire file container because the dynamic expanding image may fragment therefore causing slowdowns.

---

### Post by sahabcse on 2009-02-23
Hi

Create one directory virtualbox and mount the secondary partition to that directory, then edit the fstab for permanent mount. After that save all the virtual os hard disk(.vdi) file to the mounted director. (Default it save on .Virtualbox in user home folder).
===============================================
#mkdir /virtualbox
#mount /dev/sda2 /virtualbox

/dev/sda2    /virtualbox   ext3 defaults 0 0 
                                 --->save the above entry in /etc/fstab
-----------------------------------------------

Regards,
Sahab

---

