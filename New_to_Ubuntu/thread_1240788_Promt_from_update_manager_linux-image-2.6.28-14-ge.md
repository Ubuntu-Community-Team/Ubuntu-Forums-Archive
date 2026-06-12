---
title: "Promt from update manager linux-image-2.6.28-14-generic"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by colau on 2009-08-15
Hi,
Why does update-manager prompt for:
```

linux-image-2.6.28-14
linux-headers-2.6.28-14
linux-image-2.6.28-14-generic 
linux-headers-2.6.28-14-generic 
linux-headers-generic 
linux-image-generic 

```
uname -r
```

2.6.29-020629-generic

```

---

### Post by colau on 2009-08-15
ls -l /boot
```

-rw-r--r-- 1 root root  550328 2009-03-24 18:41 abi-2.6.29-020629-generic
-rw-r--r-- 1 root root   97251 2009-03-24 18:41 config-2.6.29-020629-generic
drwxr-xr-x 3 root root    4096 2009-08-15 15:45 grub
-rw-r--r-- 1 root root 7522777 2009-06-09 16:56 initrd.img-2.6.29-020629-generic
-rw-r--r-- 1 root root  128796 2009-03-27 23:15 memtest86+.bin
-rw-r--r-- 1 root root 1612304 2009-03-24 18:41 System.map-2.6.29-020629-generic
-rw-r--r-- 1 root root    1074 2009-04-17 09:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3541104 2009-03-24 18:41 vmlinuz-2.6.29-020629-generic

```

---

### Post by wojox on 2009-08-15
Did you install 2.6.29-020629-generic from the update manager?

I've still got 2.6.28-14-generic and I check every morning.

---

### Post by slakkie on 2009-08-15
I do not know, what does dpkg -l | grep linux-image give you and I assume you are running jaunty?

Jaunty is supposed to run on 2.6.28.x

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs)

Did you by any chance compile your own kernel?

---

### Post by colau on 2009-08-15
> **wojox said:**
> Did you install 2.6.29-020629-generic from the update manager?

I've still got 2.6.28-14-generic and I check every morning.
Installed downloading the .deb package.

---

### Post by colau on 2009-08-15
> **wojox said:**
> Did you install 2.6.29-020629-generic from the update manager?

I've still got 2.6.28-14-generic and I check every morning.
[2.6.29]("http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/")

---

### Post by colau on 2009-08-15
> **slakkie said:**
> I do not know, what does dpkg -l | grep linux-image give you and I assume you are running jaunty?

Jaunty is supposed to run on 2.6.28.x

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs)

Did you by any chance compile your own kernel?
dpkg -l | grep linux-image
```

ii  linux-image-2.6.28-11-generic              2.6.28-11.42                                 Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.29-020629-generic          2.6.29-020629                                Linux kernel image for version 2.6.29 on x86/x86_64
ii  linux-image-generic                        2.6.28.11.15                                 Generic Linux kernel image

```

---

### Post by colau on 2009-08-15
> **slakkie said:**
> I do not know, what does dpkg -l | grep linux-image give you and I assume you are running jaunty?

Jaunty is supposed to run on 2.6.28.x

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs)

Did you by any chance compile your own kernel?

[linux-kernel-2.6.29]("http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/")

---

### Post by wojox on 2009-08-15
That's one off the reasons I stay within the scope of Synaptic, is to avoid issues like such. Other than the update manager problem how is everything else working out for you? Any glitches or bugs? 

There is a thread I read about a few days ago, or you can google it, which you can open synaptic and configure it to stop asking you for those updates.

---

### Post by colau on 2009-08-15
> **wojox said:**
> That's one off the reasons I stay within the scope of Synaptic, is to avoid issues like such. Other than the update manager problem how is everything else working out for you? Any glitches or bugs? 

There is a thread I read about a few days ago, or you can google it, which you can open synaptic and configure it to stop asking you for those updates.
Working fine with 2.6.29.

---

### Post by slakkie on 2009-08-15
You need to pin your kernel package so that apt will not mention the upgrades to you. 

eg

```

Package: linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic linux-server linux-image-server
Pin: version 2.6.29
Pin-Priority: 1001

```

Put this code in /etc/apt/preferences. This will make sure that your kernel stays at 2.6.29.

See also:
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

---

### Post by colau on 2009-08-15
> **slakkie said:**
> You need to pin your kernel package so that apt will not mention the upgrades to you. 

eg

```

Package: linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic linux-server linux-image-server
Pin: version 2.6.29
Pin-Priority: 1001

```

Put this code in /etc/apt/preferences. This will make sure that your kernel stays at 2.6.29.

See also:
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

Thanks.
How can I completely remove all version of 2.6.28 from system?

---

### Post by slakkie on 2009-08-15
I use this:

```

sudo aptitude purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-(generic|server)" | awk '{print $2}')

```

followed by removing old packages
```

sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
sudo aptitude clean                                           

```

Which are actually shell functions:

```

rmkernel() {
    sudo aptitude purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-(generic|server)" | awk '{print $2}')
    rmpkg                                                                                                                      
}                                                                                                                              

rmpkg() {
    sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
    sudo aptitude clean                                           
}                                                                 

```

Put these in your .bashrc and you never have to think about it again :)

What is does, it looks at your current kernel version and deletes all kernels which do not match that version.

---

### Post by colau on 2009-08-15
> **slakkie said:**
> I use this:

```

sudo aptitude purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-(generic|server)" | awk '{print $2}')

```

followed by removing old packages
```

sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
sudo aptitude clean                                           

```

Which are actually shell functions:

```

rmkernel() {
    sudo aptitude purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-(generic|server)" | awk '{print $2}')
    rmpkg                                                                                                                      
}                                                                                                                              

rmpkg() {
    sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
    sudo aptitude clean                                           
}                                                                 

```

Put these in your .bashrc and you never have to think about it again :)

What is does, it looks at your current kernel version and deletes all kernels which do not match that version.
```

rmkernel() {
    sudo aptitude purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-(generic|server)" | awk '{print $2}')
    rmpkg                                                                                                                      
}                                                                                                                              

rmpkg() {
    sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
    sudo aptitude clean                                           
}                                                                 

```
If I put these lines in .bashrc, when would these be executed?(after reboot?)

---

### Post by slakkie on 2009-08-15
no, you need to execute them manually. 

If you define the function and then execute them eg

```


foo() {
echo foo
}

foo

```

THen this gets called everything you start a new shell. 
To execute this at every boot, you need to create a script and put that in /etc/init.d and in /etc/rcX.d. But you don't want that!

---

### Post by diablo75 on 2009-08-15
> **colau said:**
> Hi,
Why does update-manager prompt for:
```

linux-image-2.6.28-14
linux-headers-2.6.28-14
linux-image-2.6.28-14-generic 
linux-headers-2.6.28-14-generic 
linux-headers-generic 
linux-image-generic 

```
uname -r
```

2.6.29-020629-generic

```

I upgraded to 2.6.29 manually a month ago and recieved the same notice for updates.  Go ahead and install the updates as they will not replace 2.6.29 and while new entries for 2.6.28-14 will be added, 2.6.29 will retain priority in GRUB.

---

### Post by colau on 2009-08-15
> **slakkie said:**
> no, you need to execute them manually. 

If you define the function and then execute them eg

```


foo() {
echo foo
}

foo

```

THen this gets called everything you start a new shell. 
To execute this at every boot, you need to create a script and put that in /etc/init.d and in /etc/rcX.d. But you don't want that!

Only these commands will do the job,won't these?(If I run in a terminal)
```

sudo aptitude purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-(generic|server)" | awk '{print $2}')
sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
sudo aptitude clean

```

---

### Post by slakkie on 2009-08-15
yes, but putting them in a function in your bashrc will make sure you can do this the next time you install a new kernel :)

---

### Post by colau on 2009-08-15
> **slakkie said:**
> yes, but putting them in a function in your bashrc will make sure you can do this the next time you install a new kernel :)
Thank you.

---

