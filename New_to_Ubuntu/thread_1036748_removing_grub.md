---
title: "removing grub"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by richard101 on 2009-01-11
Oops, I had Windows and Ubuntu dual booting on an old machine and decided to remove Ubuntu. In Windows I formatted the Ubuntu drive. Now it wont boot ...

Grub Loading, Please Wait ...
Error 17

help

---

### Post by HunterThomson on 2009-01-11
> **richard101 said:**
> Oops, I had Windows and Ubuntu dual booting on an old machine and decided to remove Ubuntu. In Windows I formatted the Ubuntu drive. Now it wont boot ...

Grub Loading, Please Wait ...
Error 17

help

Boy there is a better one but the Super Grub CD will work for you 'too'.

[www.supergrubdisk.org](www.supergrubdisk.org)

---

### Post by richard101 on 2009-01-11
Thanks for the quick reply. I found I can boot from an Ubuntu disk. 

Will the "Super Grub CD" help me remove grub? or just boot?

---

### Post by HunterThomson on 2009-01-11
> **richard101 said:**
> Thanks for the quick reply. I found I can boot from an Ubuntu disk. 

Will the "Super Grub CD" help me remove grub? or just boot?

Well it will be your boot loader. It will over write the Grub you have now and you set it up to just boot strait into windows with no stop off at the boot loader screen. You will need to read up on how to set it up but I know that will solve your problem. There is a way to have windows fix the MBR but your probably best just using the SuperGrub boot loader from now on.

---

### Post by richard101 on 2009-01-11
thanks/sorted. booted from windows cd / recover / (admin pw) / fixmbr / y.

---

### Post by ajgreeny on 2009-01-11
Are you going to reinstall ubuntu at some time or keep the windows only situation.  If it will be windows only it is probably best to restore your windows mbr using the windows CD.  Exactly how you do it depends on which windows you are running, but it is basically a case of starting up and booting to the windows CD and then using the recovery module.  A google search will give you more info.

You can also restore it if you have no windows CD by other means using the ubuntu live CD as follows.
Boot into the ubuntu live CD and in terminal run
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr

```This assumes that your windows is on sda, of course.
Then you should be able to boot directly into Windows again. Let me know how it goes or if you run into problems.

---

