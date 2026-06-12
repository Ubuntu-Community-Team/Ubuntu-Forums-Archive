---
title: "Problems with Nvidia mx440 driver compiling from source (nvidia-kernel-legacy-source)"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by bodzasfanta on 2008-12-12
So I have a special problem.

I have an old computer running with Nvidia mx440 video card.
I decided to install Xubuntu 8.10 on this computer.
Everything went fine, but the system doesn't support this video card.

After some searching I've found this page:
[http://www.nvidia.com/object/IO_32667.html]("http://www.nvidia.com/object/IO_32667.html")
Says:
*"The following GPUs are no longer supported in the regular NVIDIA Unified UNIX Graphics Driver. Instead, these GPUs will continue to be supported through special "Legacy GPU" drivers"*

My mx440 is on the list... No money for new card so I have to find some solution (:

On the page of Debian packages I've found my driver:
nvidia-glx-legacy-96xx_96.43.07-2_i386.deb
[http://packages.debian.org/sid/nvidia-glx-legacy-96xx]("http://packages.debian.org/sid/nvidia-glx-legacy-96xx")

But it depends on this:
nvidia-kernel-legacy-96xx-2.6.26-1-686_96.43.07+2_i386.deb
[http://packages.debian.org/sid/nvidia-kernel-legacy-96xx-2.6.26-1-686a-kernel-legacy-96xx-2.6.26-1-686]("http://packages.debian.org/sid/nvidia-kernel-legacy-96xx-2.6.26-1-686a-kernel-legacy-96xx-2.6.26-1-686")

You can see this is for an older linux kernel so I "have to" complie the
driver from source.

The source is here:
nvidia-kernel-legacy-96xx-source
[http://packages.debian.org/sid/nvidia-kernel-legacy-96xx-source]("http://packages.debian.org/sid/nvidia-kernel-legacy-96xx-source")

I read through the readme file and I started the compiling

Here are the instructions from the readme file:

[I]As root (or using fakeroot)
1. cd /usr/src 
   tar xzvf nvidia-kernel-legacy-96xx-source.tar.gz -C <YOUR BUILD LOCATION>         
   (It will install in <YOU BUILD LOCATION>/modules) 
   - or -
   tar xzvf nvidia-kernel-legacy-96xx-source.tar.gz  (if building in /usr/src) 
   
   The standard build location is /usr/src
   
2. Find out your kernel version:
	             
   uname -r   For example: 2.6.14-2-k7
				          
3. Download and install package: linux-headers-2.6.14-2-k7
   It will install in /usr/src/
   Note that packages prior to 2.6.12 used the kernel- prefix rather than
   linux-
   
   Make sure your kernel image and headers have matching release numbers to
   avoid possible problems in packages built from different sources. 
   
4. Set some environment variables (if bash is your shell):
	           
    export KSRC=/usr/src/linux-headers-2.6.14-2-k7
    export KVERS=2.6.14-2-k7
			 		            
5. Then build nvidia-kernel package:
	      	           
   cd <YOUR BUILD LOCATION>/modules/nvidia-kernel-legacy-96xx
   debian/rules binary_modules
   
(You can also combine step 4 and 5 into one line:
KSRC=/usr/src/linux-headers-2.6.14-k7 KVERS=2.6.14-4-k7 debian/rules binary_modules)
				 	      		    	   
6. Install nvidia-kernel-common on the machine where the module will be
deployed:
   
   If not installed already
   apt-get install nvidia-kernel-common
   
7. Install the nvidia-kernel package:
	    		     
   dpkg -i ../nvidia-kernel-legacy-96xx-2.6.14-2-k7_96.43.07-1+_.Custom_i386.deb
   ( or similar filename )[/I]

Everything went fine, but in step 5 I got this log:

```

bodzasfanta@ubuntu:/usr/src/modules/nvidia-kernel-legacy-96xx$ sudo KSRC=/usr/src/linux-headers-2.6.27-9-generic KVERS=2.6.27-9-generic debian/rules binary_modules
# select which makefile to use.
rm -f /usr/src/modules/nvidia-kernel-legacy-96xx/nv/Makefile || true
if [ 6 = 6  ]; then \
	     cd /usr/src/modules/nvidia-kernel-legacy-96xx/nv ; \
	     ln -s Makefile.kbuild Makefile ; \
	     cd .. ; \
	     if [ 0  = 1 ] ; then \
	        dpatch apply 04_minion ; \
	     fi ; \
	     if [ 0 = 1 ]; then \
	     	dpatch apply 01_sysfs ; \
		dpatch status 01_sysfs >patch-stamp ; \
		dpatch apply 02_pcialias ; \
               	dpatch status 02_pcialias >>patch-stamp ; \
	     fi ; \
	fi
if [  6 = 4  ]; then \
	     cd /usr/src/modules/nvidia-kernel-legacy-96xx/nv ; \
	     ln -s Makefile.nvidia Makefile ; \
	     cd .. ; \
	fi
if ! gcc -v 2> /dev/null  ; then \
	   echo "Compiler gcc does not exist on the system" ; \
	   exit 1; \
	fi   
touch configure-stamp
if [ -f /usr/src/modules/nvidia-kernel-legacy-96xx/debian/control.template ]; then \
		cp  /usr/src/modules/nvidia-kernel-legacy-96xx/debian/control.template /usr/src/modules/nvidia-kernel-legacy-96xx/debian/control; \
	fi
dh_testdir
dh_testroot
PATCHLEVEL = 6 
Kernel compiler version : 4.3.2
Detected compiler version : 4.3.2
Using compiler gcc version 4.3.2
touch /usr/src/modules/nvidia-kernel-legacy-96xx/nv/gcc-check
touch /usr/src/modules/nvidia-kernel-legacy-96xx/nv/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc"  /usr/bin/make -C /usr/src/modules/nvidia-kernel-legacy-96xx/nv -f Makefile SYSSRC=/usr/src/linux-headers-2.6.27-9-generic   KBUILD_PARAMS="-C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/modules/nvidia-kernel-legacy-96xx/nv" module;
make[1]: Entering directory `/usr/src/modules/nvidia-kernel-legacy-96xx/nv'
NVIDIA: calling KBUILD...
make CC=gcc -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/modules/nvidia-kernel-legacy-96xx/nv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
make[3]: Warning: File `/usr/src/modules/nvidia-kernel-legacy-96xx/nv/conftest.h' has modification time 3.2e+03 s in the future
  CC [M]  /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.o
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:19,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/asm/bitops.h: In function ‘set_bit’:
include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arithmetic
include/asm/bitops.h: In function ‘clear_bit’:
include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/list.h:6,
                 from include/linux/preempt.h:11,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:57,
                 from include/linux/sched.h:54,
                 from include/linux/utsname.h:35,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:19,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/prefetch.h: In function ‘prefetch_range’:
include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:19,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/sched.h: In function ‘object_is_on_stack’:
include/linux/sched.h:1971: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/asm/dma-mapping.h:9,
                 from include/linux/dma-mapping.h:52,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from include/asm/pci.h:94,
                 from include/linux/pci.h:983,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:85,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/scatterlist.h: In function ‘sg_virt’:
include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:106:27: error: asm/semaphore.h: No such file or directory
In file included from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:108,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/highmem.h: In function ‘zero_user_segments’:
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h: In function ‘nv_execute_on_all_cpus’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:627: error: too many arguments to function ‘on_each_cpu’
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c: In function ‘__nv_setup_pat_entries’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:836: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c: In function ‘__nv_restore_pat_entries’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:862: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c: In function ‘nv_kern_cpu_callback’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1188: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1191: error: too many arguments to function ‘smp_call_function’
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1195: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1198: error: too many arguments to function ‘smp_call_function’
make[3]: *** [/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.o] Error 1
make[2]: *** [_module_/usr/src/modules/nvidia-kernel-legacy-96xx/nv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make[1]: Leaving directory `/usr/src/modules/nvidia-kernel-legacy-96xx/nv'
make: *** [build-stamp] Error 2

```

Any solution?
OK. Maybe that's the most hard way to install the driver but
it has to work!

---

### Post by unutbu on 2008-12-12
Do you have the build-essential package installed?

---

### Post by bodzasfanta on 2008-12-12
yes

---

### Post by unutbu on 2008-12-12
The first error is this:```

/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:106:27: error: asm/semaphore.h: No such file or directory

```
Searching [http://www.debian.org/distrib/packages#search_contents](http://www.debian.org/distrib/packages#search_contents) for "asm/semaphore.h"
yielded this hit:

[http://packages.debian.org/search?searchon=contents&keywords=asm%2Fsemaphore.h&mode=path&suite=stable&arch=any](http://packages.debian.org/search?searchon=contents&keywords=asm%2Fsemaphore.h&mode=path&suite=stable&arch=any)

So it appears you need to download the debian linux-kernel-headers package.
(linux-kernel-headers_2.6.18-7_i386.deb?)

This package installs its files in /usr. If you want to put them elsewhere, you can 
do this:
```

sudo dpkg --extract linux-kernel-headers_2.6.18-7_i386.deb /destination/path
```

You would then have to edit the Makefile to include /destination/path.

---

### Post by bodzasfanta on 2008-12-13
Okay... I give up. I got an error again...

```
bodzasfanta@ubuntu:/usr/src/modules/nvidia-kernel-legacy-96xx$ sudo KSRC=/usr/src/linux-headers-2.6.27-9-generic KVERS=2.6.27-9-generic debian/rules binary_modules
# select which makefile to use.
rm -f /usr/src/modules/nvidia-kernel-legacy-96xx/nv/Makefile || true
if [ 6 = 6  ]; then \
	     cd /usr/src/modules/nvidia-kernel-legacy-96xx/nv ; \
	     ln -s Makefile.kbuild Makefile ; \
	     cd .. ; \
	     if [ 0  = 1 ] ; then \
	        dpatch apply 04_minion ; \
	     fi ; \
	     if [ 0 = 1 ]; then \
	     	dpatch apply 01_sysfs ; \
		dpatch status 01_sysfs >patch-stamp ; \
		dpatch apply 02_pcialias ; \
               	dpatch status 02_pcialias >>patch-stamp ; \
	     fi ; \
	fi
if [  6 = 4  ]; then \
	     cd /usr/src/modules/nvidia-kernel-legacy-96xx/nv ; \
	     ln -s Makefile.nvidia Makefile ; \
	     cd .. ; \
	fi
if ! gcc -v 2> /dev/null  ; then \
	   echo "Compiler gcc does not exist on the system" ; \
	   exit 1; \
	fi   
touch configure-stamp
if [ -f /usr/src/modules/nvidia-kernel-legacy-96xx/debian/control.template ]; then \
		cp  /usr/src/modules/nvidia-kernel-legacy-96xx/debian/control.template /usr/src/modules/nvidia-kernel-legacy-96xx/debian/control; \
	fi
dh_testdir
dh_testroot
PATCHLEVEL = 6 
Kernel compiler version : 4.3.2
Detected compiler version : 4.3.2
Using compiler gcc version 4.3.2
touch /usr/src/modules/nvidia-kernel-legacy-96xx/nv/gcc-check
touch /usr/src/modules/nvidia-kernel-legacy-96xx/nv/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc"  /usr/bin/make -C /usr/src/modules/nvidia-kernel-legacy-96xx/nv -f Makefile SYSSRC=/usr/src/linux-headers-2.6.27-9-generic   KBUILD_PARAMS="-C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/modules/nvidia-kernel-legacy-96xx/nv" module;
make[1]: Entering directory `/usr/src/modules/nvidia-kernel-legacy-96xx/nv'
NVIDIA: calling KBUILD...
make CC=gcc -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/modules/nvidia-kernel-legacy-96xx/nv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.o
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:19,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/asm/bitops.h: In function ‘set_bit’:
include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arithmetic
include/asm/bitops.h: In function ‘clear_bit’:
include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/list.h:6,
                 from include/linux/preempt.h:11,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:57,
                 from include/linux/sched.h:54,
                 from include/linux/utsname.h:35,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:19,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/prefetch.h: In function ‘prefetch_range’:
include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:19,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/sched.h: In function ‘object_is_on_stack’:
include/linux/sched.h:1971: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/asm/dma-mapping.h:9,
                 from include/linux/dma-mapping.h:52,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from include/asm/pci.h:94,
                 from include/linux/pci.h:983,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:85,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/scatterlist.h: In function ‘sg_virt’:
include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:106,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/asm/semaphore.h:8:33: error: asm-i486/semaphore.h: No such file or directory
In file included from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:108,
                 from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
include/linux/highmem.h: In function ‘zero_user_segments’:
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:14:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h: In function ‘nv_execute_on_all_cpus’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv-linux.h:627: error: too many arguments to function ‘on_each_cpu’
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c: In function ‘__nv_setup_pat_entries’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:836: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c: In function ‘__nv_restore_pat_entries’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:862: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c: In function ‘nv_kern_cpu_callback’:
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1188: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1191: error: too many arguments to function ‘smp_call_function’
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1195: warning: comparison between signed and unsigned
/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.c:1198: error: too many arguments to function ‘smp_call_function’
make[3]: *** [/usr/src/modules/nvidia-kernel-legacy-96xx/nv/nv.o] Error 1
make[2]: *** [_module_/usr/src/modules/nvidia-kernel-legacy-96xx/nv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make[1]: Leaving directory `/usr/src/modules/nvidia-kernel-legacy-96xx/nv'
make: *** [build-stamp] Error 2

```

---

### Post by Elfy on 2008-12-13
I had this card until recently - I installed the driver ok through the hardware drivers. At the time I had to enable the proposed repos and allow jockey updates (I think) to allow the card to be recognised.

But it did work, not sure about compiz as I never bother with that.

I didn't need to use the nvidia supplied driver.

---

