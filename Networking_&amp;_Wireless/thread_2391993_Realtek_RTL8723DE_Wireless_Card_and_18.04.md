---
title: "Realtek RTL8723DE Wireless Card and 18.04"
date: 2018-05-15
forum: Networking &amp; Wireless
---

### Post by shanasman450 on 2018-05-15
Is anyone who has a Realtek RTL8723DE wireless card currently having any issues with connectivity?

---

### Post by jeremy31 on 2018-05-15
What source code did you use?  What are results for ```
modinfo -p 8723de; modinfo -p rtl8723de
```

---

### Post by shanasman450 on 2018-05-15
I'm not currently on 18.04, my bad if I made it sound that way. I'm actually on 16.04 and had wireless issues that I fixed with a driver. I'm mainly trying to find out if this issue still persists with 18.04 and if it is still just a driver issue. If that's the case I'm going to go ahead and grab the iso and install it.

---

### Post by shanasman450 on 2018-05-15
Well, I decided to just go ahead and install 18.04. I'm wishing I hadn't now. I have the needed driver for the wireless card, but when I cd to the driver file location I can't use make/make install because make itself has to be installed. Problem is, I can't install make. I get this.

```

taylord@TaylorD:~$ sudo apt install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package make is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'make' has no installation candidate
taylord@TaylorD:~$ 

```

I'm connected via ethernet and using the laptop to post this, so I know it's not a network issue.

---

### Post by jeremy31 on 2018-05-16
Try ```
sudo apt update && sudo apt install build-essential
```

---

### Post by shanasman450 on 2018-05-16
Thanks, that did it.

---

### Post by phyzzy2008 on 2018-06-01
That didn't do it for me. Modprobe gives error:
ERROR: could not insert 'rtl8723de': Required key not available

---

### Post by jeremy31 on 2018-06-01
Go into BIOS settings and disable secure boot

---

### Post by vvmspace on 2018-10-30
Try this:
[https://github.com/vvmspace/rtl8723de](https://github.com/vvmspace/rtl8723de)

---

