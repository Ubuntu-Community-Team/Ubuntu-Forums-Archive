---
title: "No wired connection with 8.04 64bit"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by Roque2 on 2008-10-19
Okay I have been searching around the forums for a fix on the Marvell Yukon 88E8056 network card, but every post I have looked at says to search the Marvell website. I have done so and downloaded the files install_v10.70.1.3.tar. When I extract and attempt to install the .sh file it errors. My card works on the 32bit Ubuntu both versions, why would it not work on 64bit.

---

### Post by Bucky Ball on 2008-10-19
Because:

 **install_v10.70.1.3.tar**

... *could* be 32bit driver?

---

### Post by Roque2 on 2008-10-19
okay got the install to work by creating a new link. but not its failing on the kernal header This is the error
 Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Could someone explain what I might need to do.

---

### Post by Bucky Ball on 2008-10-19
```
ln -s /usr/src/KERNEL_VERSION /usr/src/linux
```Try what it is tellling you in a terminal. Find your kernel version by typing in a terminal:

```
uname -r
```... use the command above, inserting the correct kernel version number where it says:

**/KERNEL_VERSION/**

For instance:

```
ln -s /usr/src/2.6.24-19-generic /usr/src/linux
```

---

