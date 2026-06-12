---
title: "Hi new to ubuntu HELP"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by jedidragon2001 on 2008-12-09
Hello, I'm new to ubuntu and I think I messed up good. I have had ubuntu on my laptop for about a week now dabiling on and off.  Well my wife was using the windows vista os and picked up a nasty trojan it stopped my system restore from working and dumps a bunch of explorer windows on my desktop.  Anyway  I tried to do a factory restore and ended up deleteing ubuntu from the harddrive but now it gives me 


grub 1.5 and 
grub please wait.... then
error22
_

if there is anything I can do please help
If I screwed please let me know also.

Thanks

---

### Post by Tatty on 2008-12-09
When you deleted Ubuntu, you also removed all the data which GRUB needs to work.

There are two ways to fix this.  If you intend to simply keep Vista on there then you will need to reinstall the vista mbr : [http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/](http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/)

Alternatively you can re-install Ubuntu, which will also re-install grub.

---

### Post by 73ckn797 on 2008-12-09
The restore disk probably wiped everything off the drive.

---

### Post by rev0lv3r on 2008-12-09
This is why I hate restore discs from OEM companies
They are so retarded and make many incorrect assumptions

One thing you might want to take a look at (if your situation permits: your wife doesn't need any kind of 3d heavy abilities) using nLite ( a windows app ) to trim and slim your windows installation cd, and then installing that into a virtual environment within your ubuntu OS

there are many free (and open source) hypervisors out there :)

---

### Post by cobra741 on 2008-12-09
Best bet for you would be do boot off your vista disk and jump into recovery mode and run the startup repair tool. This "should" get you back up and running. 

Failing that, jump into a console from vista's recovery mode and run the following: 

```
bootrec.exe /fixmbr
```
```
bootrec.exe /fixboot
```

This should get rid of GRUB and restore your boot.ini etc so vista boots straight off the bat. Then you can do your reinstall of Ubuntu

Hope it works out for you :)

---

### Post by jedidragon2001 on 2008-12-10
unfortunetly I can't get back in to vista because of the error 22

---

### Post by cardinals_fan on 2008-12-10
> **jedidragon2001 said:**
> unfortunetly I can't get back in to vista because of the error 22
Do you still want Ubuntu?  If so, just reinstall it and it'll handle the GRUB issue.

---

### Post by jedidragon2001 on 2008-12-10
I'm trying to install ubuntu, but when I'm partitioning the c drive for it, it say's "No root file system is defined"

---

### Post by 73ckn797 on 2008-12-11
> **jedidragon2001 said:**
> unfortunetly I can't get back in to vista because of the error 22


Check here: [U][http://www.bootdisk.com](http://www.bootdisk.com)

[/U]

---

