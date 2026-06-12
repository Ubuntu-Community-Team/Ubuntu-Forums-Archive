---
title: "Cleaning up the boot screen?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Razmear on 2009-04-07
I've been using Ubuntu 8.10 for a few months now and I've gotten a fair number of kernel updates stacked up in my boot loader, about a page and a half or so including the 'recovery' options for each version. 

Is there a way to tell the system to only save the last 3 kernel updates and automatically keep the boot screen cleaner, or is this going to be a manual edit of a config file somewhere to clean up? 

How much disk space is being taken up by having all these old versions on the system? I don't want to just clean up the boot screen, but would like to purge these old versions as well. 

When I update to 9.04 when it's released, will all these 8.10 versions go away or will I still be able to go back in case there are some problems? 

I can see a good reason to keep the last 2 or 3 versions in case there is a problem, but going beyond that just seems like a waste of disk space and screen space on the boot screen. 

Thanks for any pointers,
eb

---

### Post by Razmear on 2009-04-07
I think I just googled up the answer to my question. 
It's in the first comment here: 

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

hth,
eb

---

### Post by Walter Melon on 2009-04-07
ummm...you don't actually have to delete the lines in menu.lst.  Just find the line that tells you how many kernel versions to display.

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2
```

change the ```
#howmany=
``` to however many versions you want to display.

---

