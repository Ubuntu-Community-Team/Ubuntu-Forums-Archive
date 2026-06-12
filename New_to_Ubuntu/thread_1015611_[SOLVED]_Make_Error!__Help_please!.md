---
title: "[SOLVED] Make Error!  Help please!"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by mjheagle8 on 2008-12-19
I'm trying to compile gscpa to work my webcam.  I cant get gscpa to compile.  This is what i get in the terminal when i try to make it:
```
root@mike-laptop:/usr/src/gspcav1-20071224# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/usr/src/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2

```

thanks for any and all help!

---

### Post by meindian523 on 2008-12-19
Same problem here:
[http://ubuntuforums.org/showthread.php?t=1015043](http://ubuntuforums.org/showthread.php?t=1015043)
Same error too,only my webcam is a Z-star Microelectronics ZC0305

---

### Post by Kareeser on 2008-12-19
Sudo it.

If that doesn't work, you will need to make sure you fulfill the dependencies for compiling programs. I am not aware of what those are off the top of my head, but someone else will come along to help you out.

---

### Post by mrbiggbrain on 2008-12-19
```
sudo apt-get install  build-essential
```

ubuntu dosnt ship with all the headers gcc needs, try this

---

### Post by Kareeser on 2008-12-19
Nice and quick, thanks **mrbiggbrain**

---

### Post by mrbiggbrain on 2008-12-19
i just hope it fixes the problem, apparently not haveing it can cause ubuntu to not be able to recompile kernels and other programs

---

### Post by meindian523 on 2008-12-19
I don't know about OP,but I installed gspca-source from the repos and it brought build-essential with it as dependencies.And from the error reported by OP,it's obvious that build-essential is already installed.The problem looks to be in the code,but I'm not sure of that.

---

### Post by mjheagle8 on 2008-12-19
thanks for the help. i am running it with sudo.  and i have already installed build-essential.

---

### Post by meindian523 on 2008-12-19
I'm trying to install on a 64-bit system,can that be a problem?OP?

---

### Post by mjheagle8 on 2008-12-19
anyone able to help me?

---

### Post by Partyboi2 on 2008-12-19
> **mjheagle8 said:**
> anyone able to help me?
Are you getting the same error as originally  posted or is yours different?

---

### Post by meindian523 on 2008-12-19
This is my log file from /var/cache/modass/
```
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[1]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
    .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
    *.symvers *.err
make[1]: Leaving directory `/usr/src/modules/gspca'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/gspca'
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[2]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
    .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
    *.symvers *.err
make[2]: Leaving directory `/usr/src/modules/gspca'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-9-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-9-generic/g ;s/#KVERS#/2.6.27-9-generic/g ; s/_KVERS_/2.6.27-9-generic/g ; s/##KDREV##/2.6.27-9.19/g ; s/#KDREV#/2.6.27-9.19/g ; s/_KDREV_/2.6.27-9.19/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.27-9-generic KERNELDIR=/usr/src/linux
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2604: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2

```
mjheagle8:
Are you also trying to build on a 64-bit system?I don't intend to hijack your thread,but if you would co-operate and look at me as a user who has the same problem and willing to help by giving those who can help more information about our situation,then it will lead to a faster solution for both of us.

---

### Post by mjheagle8 on 2008-12-19
Partyboi, my error is the same.  This person just jumped on my thread.

---

### Post by Partyboi2 on 2008-12-19
> **mjheagle8 said:**
> Partyboi, my error is the same.  This person just jumped on my thread.
The joys of sharing :p
I had a play around with this and got the same error but I was able to get past it by following [[COLOR=Blue]this[/COLOR]]("http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/") and some of [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500"). as mentioned by Sweeper. Confused? This is the steps I took. 
Downloaded the source from
```
http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
```
then
downloaded the patch from [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500") and moved them both off the Desktop and into another directory (I used /usr/src) then extracted gspcav1-20071224.tar.gz
```
tar xvzf  gspcav1-20071224.tar.gz
```
then
```
gunzip gspca.patch.gz
```
then changed into gspcav1-20071224 directory
```
cd gspcav1-20071224
```
then apply the patch
```
patch < ../gspca.patch
```
then finally
```
sudo ./gspca_build
```

---

### Post by mjheagle8 on 2008-12-21
that worked! thank you for your help.

---

### Post by sangandongo on 2009-01-07
Unfortunately, this did not work for me. Here is the current error output I'm receiving. 

```


# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.27-9-generic KERNELDIR=/usr/src/linux
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2


```

---

