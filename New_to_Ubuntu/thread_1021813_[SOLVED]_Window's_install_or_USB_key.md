---
title: "[SOLVED] Window's install or USB key"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by WASHAD on 2008-12-25
For some reason, something seems to be wrong with my hard drive and I am not able to resize. 

My next options are to install into Windows or install onto a 2gb USB key. Any opinions? 

Thanks, 

SteveJ

---

### Post by eagle416 on 2008-12-26
What were you doing? what error messages does it give?
do you mean that you cannot resize the *partition* in the installer?

---

### Post by WASHAD on 2008-12-26
You can see the details here:

[http://ubuntuforums.org/showthread.php?t=1020878](http://ubuntuforums.org/showthread.php?t=1020878)


For this thread, though, lets just assume that my IS dpt. has placed some kind of restriction on my ability to size partitions. 

Thanks, 

SteveJ

---

### Post by DGortze380 on 2008-12-26
> **WASHAD said:**
> You can see the details here:

[http://ubuntuforums.org/showthread.php?t=1020878](http://ubuntuforums.org/showthread.php?t=1020878)


For this thread, though, lets just assume that my IS dpt. has placed some kind of restriction on my ability to size partitions. 

Thanks, 

SteveJ

Check with the security policies, then look into a windows virtual machine.

---

### Post by pansz on 2008-12-26
2GB usb key isn't enough, even 4G isn't enough if you want anything more than a bare base system. 8G is recommended.

Please note that the ubuntu install cd is not able to resize NTFS partition which is very popular among windows. Use gparted livecd to resize it instead.

---

### Post by ELF_O8 on 2008-12-26
> **pansz said:**
> 
Please note that the ubuntu install cd is not able to resize NTFS partition which is very popular among windows. Use gparted livecd to resize it instead.

Really? I have never had any problem resizing a Windows partition or fiddling with it in the Live Desktop. I didn't know this restriction was set.

---

### Post by bumanie on 2008-12-26
I too have found the live ubuntu cd lacking in some functionality with regard to gparted - the live gparted cd is a dedicated tool, whereas the ubuntu installation cd is aimed at getting the OS installed. Try the live gparted live cd.

---

