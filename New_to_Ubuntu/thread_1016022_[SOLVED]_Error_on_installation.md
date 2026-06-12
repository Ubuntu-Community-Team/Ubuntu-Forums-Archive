---
title: "[SOLVED] Error on installation"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by bob brazie on 2008-12-19
I had trouble installing an application and now wen I open the package manager I get an error message saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

When I close this warning the package manager closes too.

I do not understand how to run this command in the terminal to correct this situation.

Any help would be greatly appreciated. 

Thanks in advance, Bob.

---

### Post by Titan8990 on 2008-12-19
Go to Application -> Accessories -> Terminal


copy and paste the following:


sudo dpkg-reconfigure -a

---

### Post by Michael.Godawski on 2008-12-19
Had the command worked?
```
sudo dpkg-reconfigure -a 	
```

You can also try
```
sudo apt-get install -f
```

---

### Post by bob brazie on 2008-12-19
Thanks, I tried both and the problem is still there when I try to open the package manager.

Here is the end of the output from the first code and the output form the second code if this will help.

he system user `messagebus' already exists. Exiting.
* Reloading system message bus config...                                [ OK ] 
Updating OpenOffice.org's dictionary list... done.
* Running DKMS auto installation service for kernel 2.6.27-9-generic            *  fglrx (8.543)...                                                     [ OK ] 
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
/usr/sbin/dpkg-reconfigure: doc-base is broken or not fully installed
bob@ubuntu:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
bob@ubuntu:~$

---

### Post by Michael.Godawski on 2008-12-19
Try this.
```
sudo apt-get purge doc-base
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install doc-base
```

---

### Post by bob brazie on 2008-12-19
I don't know why but i re- booted and it is working fine without trying any of the last codes.

Thanks so much.

---

