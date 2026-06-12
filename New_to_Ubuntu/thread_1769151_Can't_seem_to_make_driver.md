---
title: "Can't seem to make driver"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by erans on 2011-05-27
Hi there, 

I am trying to compile a Broadcom wireless driver for my Thinkpad E420. There is a thread on the Wireless forum with directions, but I am having problems correctly making the driver, which makes me think that I am doing something wrong. Here are the errors I get when I try to make: 

```
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CLEAN   /home/shayan/hybrid_wl/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/shayan/hybrid_wl/built-in.o
  CC [M]  /home/shayan/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /home/shayan/hybrid_wl/src/wl/sys/wl_linux.o
/home/shayan/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
/home/shayan/hybrid_wl/src/wl/sys/wl_linux.c:485:3: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/home/shayan/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/shayan/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 

```
I feel as though I might be missing something very basic, but I'm not sure. Any help would be greatly appreciated. 

The link to the original thread is here: [http://ubuntuforums.org/showthread.php?t=1749780](http://ubuntuforums.org/showthread.php?t=1749780)

Thank you.

---

### Post by wildmanne39 on 2011-05-27
> **erans said:**
> Hi there, 

I am trying to compile a Broadcom wireless driver for my Thinkpad E420. There is a thread on the Wireless forum with directions, but I am having problems correctly making the driver, which makes me think that I am doing something wrong. Here are the errors I get when I try to make: 

```
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CLEAN   /home/shayan/hybrid_wl/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/shayan/hybrid_wl/built-in.o
  CC [M]  /home/shayan/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /home/shayan/hybrid_wl/src/wl/sys/wl_linux.o
/home/shayan/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/shayan/hybrid_wl/src/wl/sys/wl_linux.c:485:3: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/shayan/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/shayan/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 

```
I feel as though I might be missing something very basic, but I'm not sure. Any help would be greatly appreciated. 

The link to the original thread is here: [http://ubuntuforums.org/showthread.php?t=1749780](http://ubuntuforums.org/showthread.php?t=1749780)

Thank you.
Hi, it has been a while since I compiled a package but I think your are missing something that the kernel needs to make the build, like kernel headers for dev or gcc, do you get a message that says that? Also you do have to be in the directory where the files were extracted too.

---

### Post by erans on 2011-05-27
> **wildmanne39 said:**
> Hi, it has been a while since I compiled a package but I think your are missing something that the kernel needs to make the build, like kernel headers for dev or gcc, do you get a message that says that? Also you do have to be in the directory where the files were extracted too.

Thanks for the help. I did install all of the necessary headers according to the original thread. I do get one message that makes me think that I am still missing something. It says ```
'error: implicit declaration of function;init_MUTEX'
```when I try to make the driver. 

Are there any other headers that I am missing? I installed build-essential and linux-headers-generic. 

Thanks again.

---

### Post by wildmanne39 on 2011-05-27
> **erans said:**
> Thanks for the help. I did install all of the necessary headers according to the original thread. I do get one message that makes me think that I am still missing something. It says ```
'error: implicit declaration of function;init_MUTEX'
```when I try to make the driver. 

Are there any other headers that I am missing? I installed build-essential and linux-headers-generic. 

Thanks again.
Hi, I do not remember all of them but you have to have gcc compiler installed.

---

### Post by jramshu on 2011-05-27
Did you try and install via b43-fwcutter?

I got an old Broadcom device working taht way.

---

### Post by erans on 2011-05-28
I fixed the make issue. There's a patch on the Broadcom website that you have to apply in order to compile the driver on certain kernel versions, so that's what I did. Now I'm having major problems installing the driver, for some reason. 

Here's what's happening when I try to remove the old wl drivers and install the new one: 

```
shayan@shayan-ThinkPad-E420:~$ lsmod | grep "b43\|ssb\|wl"
wl                   2568244  0 
lib80211               14991  1 wl
shayan@shayan-ThinkPad-E420:~$ rmmod wl
ERROR: Removing 'wl': Operation not permitted
shayan@shayan-ThinkPad-E420:~$ sudo rmmod wl
shayan@shayan-ThinkPad-E420:~$ lsmod | grep "b43\|ssb\|wl"
shayan@shayan-ThinkPad-E420:~$ sudo -i
root@shayan-ThinkPad-E420:~# rmmod wl
ERROR: Module wl does not exist in /proc/modules
root@shayan-ThinkPad-E420:~# lsmod | grep wl
root@shayan-ThinkPad-E420:~# lsmod | grep "wl"
root@shayan-ThinkPad-E420:~# ezit
No command 'ezit' found, did you mean:
 Command 'edit' from package 'mime-support' (main)
ezit: command not found
root@shayan-ThinkPad-E420:~# exit
logout
shayan@shayan-ThinkPad-E420:~$ sudo modprobe lib80211
[sudo] password for shayan: 
shayan@shayan-ThinkPad-E420:~$ insmod wl,ko
insmod: can't read 'wl,ko': No such file or directory
shayan@shayan-ThinkPad-E420:~$ cd hybrid_wl/
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ insmod wl.ko
insmod: error inserting 'wl.ko': -1 Operation not permitted
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 


```
Any input would be greatly appreciated. I'm very confused right now.

---

### Post by wildmanne39 on 2011-05-28
> **erans said:**
> I fixed the make issue. There's a patch on the Broadcom website that you have to apply in order to compile the driver on certain kernel versions, so that's what I did. Now I'm having major problems installing the driver, for some reason. 

Here's what's happening when I try to remove the old wl drivers and install the new one: 

```
shayan@shayan-ThinkPad-E420:~$ lsmod | grep "b43\|ssb\|wl"
wl                   2568244  0 
lib80211               14991  1 wl
shayan@shayan-ThinkPad-E420:~$ rmmod wl
ERROR: Removing 'wl': Operation not permitted
shayan@shayan-ThinkPad-E420:~$ sudo rmmod wl
shayan@shayan-ThinkPad-E420:~$ lsmod | grep "b43\|ssb\|wl"
shayan@shayan-ThinkPad-E420:~$ sudo -i
root@shayan-ThinkPad-E420:~# rmmod wl
ERROR: Module wl does not exist in /proc/modules
root@shayan-ThinkPad-E420:~# lsmod | grep wl
root@shayan-ThinkPad-E420:~# lsmod | grep "wl"
root@shayan-ThinkPad-E420:~# ezit
No command 'ezit' found, did you mean:
 Command 'edit' from package 'mime-support' (main)
ezit: command not found
root@shayan-ThinkPad-E420:~# exit
logout
shayan@shayan-ThinkPad-E420:~$ sudo modprobe lib80211
[sudo] password for shayan: 
shayan@shayan-ThinkPad-E420:~$ insmod wl,ko
insmod: can't read 'wl,ko': No such file or directory
shayan@shayan-ThinkPad-E420:~$ cd hybrid_wl/
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ insmod wl.ko
insmod: error inserting 'wl.ko': -1 Operation not permitted
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 


```
Any input would be greatly appreciated. I'm very confused right now.
Hi, are you using sudo? If you are sure they need to be removed and you know the exact name of the drivers you can use this command.
```
sudo apt-get --purge remove
```Aslo you might look in synaptic and you should be able to remove them that way, if you do check to remove completely not just remove.

---

### Post by erans on 2011-05-29
Solved. The problem was that there is a patch on the website for kernel 2.6.38 which I did not apply. The patch can be found with the driver download for the Broadcom chipset at the link below. Hope that helps someone.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by wildmanne39 on 2011-05-30
> **erans said:**
> Solved. The problem was that there is a patch on the website for kernel 2.6.38 which I did not apply. The patch can be found with the driver download for the Broadcom chipset at the link below. Hope that helps someone.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)Hi, thats great I am glad you got it working. Would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:D

---

