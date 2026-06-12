---
title: "help with gparted"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-10-05
im need help with gparted i cant tell  which thing i partion  without deleting  my main operating system  im trying to  put  windows xp and i catn figure out which partion to delete

[http://i801.photobucket.com/albums/yy295/pyrofreak99/Screenshot-1.png](http://i801.photobucket.com/albums/yy295/pyrofreak99/Screenshot-1.png)

---

### Post by foxmulder881 on 2010-10-05
An easier way would be to install WinXP first to the first half of the drive and then Ubuntu to the second half and it will automatically detect Windows install and configure grub for you so that you can dual boot.

---

### Post by KirbySmith on 2010-10-05
From your photo, partitions sda1, 2, and 5 are part of your linux build. You would want to add another partition in the space beyond sda5. However, as foxmulder881 noted, it is easier to do install windows before ubuntu because the ubuntu boot loader, grub2, will find the windows partition and include it in the boot options. 
 
As it stands now, if you construct the new partition and then install windows into it, grub won't know about it and you will need to do some added work to get grub to discover it. I suspect I can't help you adequately for that part of the process.
 
The windows boot loader provides options for booting multiple OSs, but these seem to be limited to Microsoft OSs. 
 
kirby

---

### Post by Aetixintro on 2010-10-05
I'd say you boot from the live CD of Ubuntu and use Gparted to set up the whole range of partitions anew.

You can easily set up 3 primary partitions as 4 are allowed. Use 2xRAM for Linux swap and split the rest between Ubuntu and Windows, accordingly. You should take into consideration that a gaming station or a kind of application station takes up more so you need to take into account your priorities before you split them into two halves.

I've also seen it mentioned that it's absolutely best to install the Windows system first, just so you are warned about it.

Be patient when you use Gparted because it takes considerable time to finish. I got a fine result and I'll think you'll be happy too! Good luck! :)

---

