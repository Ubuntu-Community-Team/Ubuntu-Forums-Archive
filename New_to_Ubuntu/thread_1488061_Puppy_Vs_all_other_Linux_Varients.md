---
title: "Puppy Vs all other Linux Varients"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by 13k on 2010-05-19
I never install linux, and only boot through usb, but you can add comments for cd also.

I heard Puppy Linux is launched into the ram(mostly) through the usb(or something) making it fast.

All Operating Systems(Linux) do launch using ram, but what i am asking how is it difference from Puppy, and please explain in detail if possible

and what the heck are with these beans for?

---

### Post by bodhi.zazen on 2010-05-19
Many systems boot using an [initrd]("http://en.wikipedia.org/wiki/Initrd")

You do not *need* an initrd so long as the kernel has all the drivers needed to boot.

Puppy and other live distros will load the entire system , / , /usr / etc to ram (usually a toram option).

Such a system is faster (with some functions) as it is a few orders of magnitude faster to read /bin/bash from ram vs hard drive or from your flash drive or CD drive.

You may do this with a large distro, such as Ubuntu, assuming you have enough RAM to store /usr

See [http://www.slax.org/documentation_boot_cheatcodes.php](http://www.slax.org/documentation_boot_cheatcodes.php) In particular the toram and copy2ram section (they are short).

HTH, I think this answers what you are asking , no ?

---

### Post by mike555 on 2010-05-19
all operating systems use some ram , but puppy is so small it can usually put all of itself into ram and you can take the cd out while running it (so you can use the cd for something else) and it's very fast ........

---

### Post by 13k on 2010-05-19
> **bodhi.zazen said:**
> Many systems boot using an [initrd]("http://en.wikipedia.org/wiki/Initrd")

You do not *need* an initrd so long as the kernel has all the drivers needed to boot.

Puppy and other live distros will load the entire system , / , /usr / etc to ram (usually a toram option).

Such a system is faster (with some functions) as it is a few orders of magnitude faster to read /bin/bash from ram vs hard drive or from your flash drive or CD drive.

You may do this with a large distro, such as Ubuntu, assuming you have enough RAM to store /usr

See [http://www.slax.org/documentation_boot_cheatcodes.php](http://www.slax.org/documentation_boot_cheatcodes.php) In particular the toram and copy2ram section (they are short).

HTH, I think this answers what you are asking , no ?

yes, somewhat, i think i understand what you are saying.

ISO size = RAM ??

---

### Post by bodhi.zazen on 2010-05-19
> **13k said:**
> yes, somewhat, i think i understand what you are saying.

ISO size = RAM ??

There is a correlation, the larger the iso the larger the ram you will need, but iso use casper or other methods to compress the image, so it will take more more RAM then the iso image.

You can look at this linky as well :

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

And this one is probably right up your alley

**[http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230)**

---

### Post by 13k on 2010-05-19
> **bodhi.zazen said:**
> There is a correlation, the larger the iso the larger the ram you will need, but iso use casper or other methods to compress the image, so it will take more more RAM then the iso image.

You can look at this linky as well :

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

And this one is probably right up your alley

**[http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230)**

ty.

---

