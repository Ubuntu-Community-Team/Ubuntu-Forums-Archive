---
title: "Trying to get NVIDIA drivers installed"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by killbydemons on 2008-12-23
Hi all, I'm taking my first steps in Ubuntu, and it seems I've fallen.  I'm trying to install the 177.82 release nforce drivers for Ubuntu 64 bit, and I get a warning message telling me "You do not appear to have an NVIDIA GPU supported by the 177.82 NVIDIA Linux graphics driver installed in this system. For further..." blah blah.  I have a geforce 9800gx2, and I read the readme for the 177.82 release driver, where it states that my video card *is* supported.


Some help please?

---

### Post by taurus on 2008-12-23
Did you try to install that driver for your nvidia card from System -> Administration -> Hardware Drivers?

---

### Post by killbydemons on 2008-12-23
It doesn't find any...

"No proprietary drivers are in use on this system."

I have the nvidia driver package downloaded to my desktop.

---

### Post by LastWho on 2008-12-23
hey give me 10 mn and i ll show u how to install it step by step :popcorn:

---

### Post by bodhi.zazen on 2008-12-23
You have two options :

```
sudo apt-get install nvidia-glx-new
```

use synaptic to search for "nvidia" without quotes for other options.

Option 2 is envy :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

either way, reboot after installing the nvidia driver

---

### Post by killbydemons on 2008-12-23
> **bodhi.zazen said:**
> You have two options :

```
sudo apt-get install nvidia-glx-new
```

use synaptic to search for "nvidia" without quotes for other options.

Option 2 is envy :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

either way, reboot after installing the nvidia driver

i do not understand what synaptic and envy are....completely new to Ubuntu here, I'm a windows baby :)

---

### Post by LastWho on 2008-12-23
Edit: sorry didn't read ur thread carefully :D
Make sure u re choosing the right driver dude :D

Eidt: sorry for my bad english, i m french

ok, 
This is how i installed my nvidia driver:

[INDENT]**[COLOR="Teal"]A - Preparations:[/COLOR]** What u need before u install it:
[/INDENT] 
[INDENT][INDENT]1. download your driver from nvidia: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
(choose linux 32 or 64 it depends :D)
[/INDENT][/INDENT] [INDENT][INDENT]On a paper write the name of the driver, with capital letters and minuscules: (just in case u don't know how to play with the terminal :p tab or ls)
[/INDENT][/INDENT][INDENT][INDENT]NVIDIA-Linux-x86-...-pkg1.run
[/INDENT]
[INDENT]write down also the path to your driver, ex:
/home/killbydemons/downloads
[/INDENT][/INDENT] 


[INDENT][INDENT]     2- build-essential:
    
insert the Ubuntu-Cd, 
then in the terminal
application --> accessoire --> terminal (or Alt F2 --> gnome-terminal) 
copy and past this, (one by one and click enter after each one <-- i ve to, he is a newbee)
[/INDENT][/INDENT]    
[INDENT][INDENT]```
  
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```
[/INDENT][/INDENT]  


[INDENT][INDENT]     3- only to be sure (i needed that, that doesn't mean u will)
: System --> admin --> Synaptic package manajor
   
Search for theses:

        a - kernel-source --> choose from the list: nvidia-new-kernel-source
and install it

        b- kernel-headers --> install kernel-package the same way
[/INDENT][/INDENT]   
**Now you re ready to install it, u ve to log out so u must[COLOR=Red] write down all this:[/COLOR]**


[INDENT] **[COLOR="Teal"]B - Procedure:[/COLOR]**


[INDENT]     1. Log out, and at the login page click on this combination: Ctrl + Alt + F3 to access the tty3.. (to get out u need [COLOR="Red"]Ctrl + Alt + F7[/COLOR])

enter ur username and password
    
Then type:
```

    sudo su
```

    or 
```

    sudo -i
```
because You ve to install it as a root

    
2. Kill Mr X and install nvidia:
    type:
    ```

    /etc/init.d/gdm stop

```
    

    then go to the driver's location (by cd)
```

    cd /home/killbydemons/downloads
```

    

    then use sh to install ur driver:
    ```


    sh NVIDIA-Linux-x86-....-pkg1.run
```

    then click on yes, d'accord, ok, as u like, w/e ..every time it asks u :p



    3. Resuscitate Mr X to use ur nvidia card:
    type this:
```

    /etc/init.d/gdm start
```

    then type:
```

    exit
``` or CTRL + D


    Now use the combination:
[B] Ctrl + Alt + F7
[/B]
[/INDENT][/INDENT]and enjoy ur new nvidai card ;)

---

### Post by bodhi.zazen on 2008-12-23
LastWho gave you the manual way.

Envy is easier, follow the link I gave your for directions.

For synaptic see : [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by LastWho on 2008-12-23
@ Bodhi.zazen, didn't heard about envy before, thank u :)

---

### Post by killbydemons on 2008-12-24
okay, well I actually found some beta drivers that I want to install. they are [here]("http://www.nvnews.net/vbulletin/showthread.php?p=1882835")

the problem i'm having is that the drivers are presented as multiple package downloads.  Also I already got Envy, and the driver i want to get is not presented in the list of available drivers; maybe because they are betas.

so, how do I install the drivers when I have to download multiple packages? thanx

edit: I already figured out how to get the package, now I just need to get the dependencies installed.

---

### Post by Teabicky on 2008-12-24
Hi, try using envyng.  Go to synaptic and install envyng.  Then run it in Terminal 

> 
envyng -t

This will automatically set up your Nvidia drivers.

---

### Post by Teabicky on 2008-12-24
My card is a GeForce 9500 GT 256MB PCI-E Graphics Card and envyng did not recognise it so I manually installed it (option 5).  It gives you a warning saying that you do so at your own risk but it worked for me without any issues.

---

### Post by killbydemons on 2008-12-24
yeah, I could install drivers through Envy if I wanted to...but Envy doesn't supply the drivers I want to install.  I want to know how to manually install video drivers if I already have the .run file downloaded to the desktop.

---

### Post by bodhi.zazen on 2008-12-24
> **killbydemons said:**
> yeah, I could install drivers through Envy if I wanted to...but Envy doesn't supply the drivers I want to install.  I want to know how to manually install video drivers if I already have the .run file downloaded to the desktop.

LastWho gave detailed instructions in his (her ?) post. What part do you not understand ?

---

### Post by killbydemons on 2008-12-24
I do not like to follow long sets of instructions if I do not understand what they are doing. Also, I don't mean to sound snobbish, but there has to be an easier way to install video drivers.

---

### Post by bodhi.zazen on 2008-12-24
The easy way is to use the nvidia driver in the Ubuntu repositories.

Search in Synaptic for nvidia (may be nvidia-glx-new of by version number depending on the version of Ubuntu you use).

#2 is Envy (which is also in the repos).

But for the beta driver, nope, you need to manually install. If you want an "easier way" i suggest you give your feedback to the Nvidia Developers and ask them to open source their drivers or provide better / easier Linux support.

Basically what you are doing is installing a compiler , headers, dependencies, then compiling the nvidia driver by running the nvidia script.

---

### Post by killbydemons on 2008-12-24
okay, that's more informative than a set of instructions, so thank you.  since it seems like the betas are going to be a PITA no matter what I try, I'll just go ahead and install from Synaptic or Envy. thanks again.

---

### Post by killbydemons on 2008-12-24
drivers still not working ><

i think i should have mentioned that  I'm using Ubuntu through VWware Workstation. Maybe because of this, Ubuntu can't even detect that I have a video card available to use? How would I check what hardware Ubuntu is detecting?

---

### Post by bodhi.zazen on 2008-12-24
> **killbydemons said:**
> drivers still not working ><

i think i should have mentioned that  I'm using Ubuntu through VWware Workstation. Maybe because of this, Ubuntu can't even detect that I have a video card available to use? How would I check what hardware Ubuntu is detecting?

Yes, that is very different. VMWare does not use your videocard directly. Install the VMWare tools into the Ubuntu guest.

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by GrahamM on 2008-12-25
> **Teabicky said:**
> Hi, try using envyng.  Go to synaptic and install envyng.  Then run it in Terminal 



This will automatically set up your Nvidia drivers.

I tried using envyng on my machine that has an Nvidia TNT2. It went through the process apparently  OK, but on rebooting, it could not load the driver. I had to revert to the generic driver to restart.

I had previously downloaded the driver file NVIDIA-Linux-x86-71.86.06-pkg1.run but envy downloaded a different one with .86.04 in it. 

I was given the opportunity to edit a file of some sort, but passed on that because I just want to update the driver like I would in Windows.

I tried Synaptic PM but did not find nvidia-glx-new - unless by new you meant just a number - then tehre are some files, but which one would be for the TNT2? 

Do I need to try the manual method and install the file that I downloaded?


PS: Tried to find nvidia-glx-new but this is what I get:

graham@graham-desktop:~$ sudo apt-get install nvidia-glx-new
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  nvidia-glx-96 nvidia-glx-71 nvidia-glx-177 nvidia-glx-173
E: Package nvidia-glx-new has no installation candidate

---

### Post by bodhi.zazen on 2008-12-25
As of 8.04, they changed to naming of the nvidia drivers from "nvidia-glx-new" to "nvidia-glx-###" (thn numbers correspond to the actual nvidia driver, which is nice).

I am not sure which one is best for your card.

---

### Post by GrahamM on 2008-12-26
> **bodhi.zazen said:**
> As of 8.04, they changed to naming of the nvidia drivers from "nvidia-glx-new" to "nvidia-glx-###" (thn numbers correspond to the actual nvidia driver, which is nice).

I am not sure which one is best for your card.


It appears that the proper one is 71. The NVIDIA site says the file for the TNT/TNT2 is 71.86.06 or 71.08.07 beta. It appears from stuff that scrolls by during startup that current driver is 71.86.04. 

I went through the manual method and attempted to install NVIDIA-Linux-x86-71.86.06-pkg1.run

Everything seemed to be going OK but after is said it was compiling and showed 100% completion, it displayed a message saying the installation had failed. 

Can anyone see what problem is?

Here is log (I will probably delete this once I get this sorted!)
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Dec 26 15:08:57 2008
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 71.86.06.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-9-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-9-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-9-generi
   c/build SYSOUT=/lib/modules/2.6.27-9-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-9-generic/build SUBDIRS=
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL_
   _  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -in
   clude include/linux/autoconf.h -
   Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-stric
   t-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft
   -float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i
   586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-
   default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-c
   alls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz7703/N
   VIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wsw
   itch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar
   -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -
   D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__
   -DMODULE -DNV_VERSION_STRING=\"71.86.06\" -DNV_UNIX -DNV_LINUX -DNV_INT64_OK
   -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUIL
   D_BASENAME=KBUILD_STR(nv)"  -D"KB
   UILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz7703/NVIDIA-Linux-x86-71.8
   6.06-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg
   1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/bitops.h: In function &#8216;set_bit&#8217;:
   include/asm/bitops.h:60: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
   include/asm/bitops.h:97: warning: pointer of type &#8216;void *&#8217; used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1971: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:83,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:104:27:
   error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:106,
                    from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h: In fun
   ction &#8216;nv_execute_on_all_cpus&#8217;:
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:595: er
   ror: too many arguments to function &#8216;on_each_cpu&#8217;
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   &#8216;__nv_setup_pat_entries&#8217;:
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:887: warning:
   comparison between signed and unsigned
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   &#8216;__nv_restore_pat_entries&#8217;:
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:913: warning:
   comparison between signed and unsigned
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   &#8216;nv_kern_cpu_callback&#8217;:
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1239: warning
   : comparison between signed and unsigned
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1242: error: 
   too many arguments to function &#8216;smp_call_function&#8217;
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1246: warning
   : comparison between signed and unsigned
   /tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1249: error: 
   too many arguments to function &#8216;smp_call_function&#8217;
   make[3]: *** [/tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.o
   ] Error 1
   make[2]: *** [_module_/tmp/selfgz7703/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
```

---

### Post by GrahamM on 2008-12-29
Bumping - Can anyone help with this?

Still getting that DKMS FAIL message and system will only start in minimal vesa mode.

---

### Post by 67GTA on 2008-12-29
> **GrahamM said:**
> Bumping - Can anyone help with this?

Still getting that DKMS FAIL message and system will only start in minimal vesa mode.

What version of Ubuntu are you using 8.04/8.10? The legacy drivers 71 and 96 won't work with 8.10's version of xorg.

---

### Post by GrahamM on 2008-12-30
> **67GTA said:**
> What version of Ubuntu are you using 8.04/8.10? The legacy drivers 71 and 96 won't work with 8.10's version of xorg.


I am using 8.10. Nvidia site says to use 71 driver.  

If that won't work, then how do I get back to whatever driver Ubuntu installed? It at least allowed the full range of screen resolutions.

Or is there another one? Card is Riva TNT2.

---

### Post by loomsen on 2008-12-30
Only checked the last page, u made sure u chose the right driver in your xorg.conf?

Post the output of:
```

cat /etc/X11/xorg.conf
```

and:
```

cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

```

---

### Post by 67GTA on 2008-12-30
Ubuntu uses the open source nv driver by default, but don't support 3D. Just uninstall any nvidia drivers currently installed and delete your xorg.conf file and reboot. It will load by it's self. To delete the xorg.conf file, open a terminal and run ```
sudo rm /etc/X11/xorg.conf
``` The 8.10 release notes cover the nvidia legacy drivers: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810) The only other option is to install 8.04. The legacy drivers still work with it. There is a beta driver for the 96 series driver that is supposed to work with 8.10, but not sure about the 71 series.

---

### Post by GrahamM on 2008-12-30
> **loomsen said:**
> Only checked the last page, u made sure u chose the right driver in your xorg.conf?

Post the output of:
```

cat /etc/X11/xorg.conf
```

and:
```

cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

```

Sorry for delay in getting back but we lost our water pump, so that took a priority!

I have already deleted the file per 67GTA's instructions, but here is output of backup x.org.conf file anyway:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@palmer)  Thu Jun 26 06:22:40 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

and these may not be useful! :

graham@graham-desktop:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Unable to locate/open config file
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory

and 

graham@graham-desktop:~$ cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Warning, couldn't open module nv
(WW) Falling back to old probe method for fbdev
(WW) VESA(0): Unable to estimate virtual size

---

### Post by GrahamM on 2008-12-30
> **67GTA said:**
> Ubuntu uses the open source nv driver by default, but don't support 3D. Just uninstall any nvidia drivers currently installed and delete your xorg.conf file and reboot. It will load by it's self. To delete the xorg.conf file, open a terminal and run ```
sudo rm /etc/X11/xorg.conf
``` The 8.10 release notes cover the nvidia legacy drivers: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810) The only other option is to install 8.04. The legacy drivers still work with it. There is a beta driver for the 96 series driver that is supposed to work with 8.10, but not sure about the 71 series.

Thanks for input.  The release notes say:

nVidia "legacy" video support

*The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.*

Which is what you have said.

I deleted all nvidia references in Synaptic and now have nothing installed.

I also removed xorg.conf as suggested.

When I rebooted, the DKMS FAIL message did not appear. GOOD! A step in right direction!

But, the video driver installed is very basic. It offers just 640x480, 800x600 and 1024x768 and 0 Hz. After original installation, there were many more choices and I was running at 1280x1024 at 75 Hz.

Questions:

How do I get back to the original video driver?

Is there a way to go back to 8.04 without a total re-install? 
(*Might be an idea because my "Bible" is Beginning Ubuntu Linux and it is based on 8.04*)

---

### Post by 67GTA on 2008-12-30
There is no way to downgrade. Apt only goes up:D It should have defaulted to nv. Make sure the nvidia driver is not still activated in Hardware Drivers. We just need to get your system to use the nv driver. Post a copy of your /etc/X11/xorg.conf and /var/log/Xorg.0.log.

---

### Post by GrahamM on 2008-12-30
> **67GTA said:**
> There is no way to downgrade. Apt only goes up:D It should have defaulted to nv. Make sure the nvidia driver is not still activated in Hardware Drivers. We just need to get your system to use the nv driver. Post a copy of your /etc/X11/xorg.conf and /var/log/Xorg.0.log.

There is no longer an xorg.conf file - we removed it didn't we? There are a bunch of backup files at different dates and this (failsafe) one at today's date:

# xorg.conf.failsafe (X.Org X Window System server configuration file)


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

The log is long, so check it out here:

[http://home.cogeco.ca/~yachting/Xorg.0.log](http://home.cogeco.ca/~yachting/Xorg.0.log)

---

### Post by 67GTA on 2008-12-30
The new xorg automatically makes a new xorg file at each boot if one is not present. Your xorg log says the nv module is not present. Make sure ```
xserver-xorg-video-nv
``` is installed. Then check to see if it is loaded ```
lsmod | grep nv
``` If not ```
sudo modprobe nv
``` Then edit your xorg.conf file and change "vesa" to "nv" and try rebooting. ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by GrahamM on 2008-12-30
> **67GTA said:**
> The new xorg automatically makes a new xorg file at each boot if one is not present. Your xorg log says the nv module is not present. Make sure ```
xserver-xorg-video-nv
``` is installed. 

Looking at Synaptic, Yes it is

Then check to see if it is loaded ```
lsmod | grep nv
``` 

Nothing happens when I enter that

If not ```
sudo modprobe nv
``` 

graham@graham-desktop:~$ lsmod | grep nv
graham@graham-desktop:~$ sudo modprobe nv
[sudo] password for graham: 
FATAL: Module nv not found.

Then edit your xorg.conf file and change "vesa" to "nv" and try rebooting. ```
sudo gedit /etc/X11/xorg.conf
```

There was no xorg.conf file - just backups and failsafe from earlier dates.

I decided to reboot anyway and.. The screen came up with the original resolution! I checked and there still is no xorg.conf file in /etc/X11/.  I did a search and found one called xorg.conf.new in / (root). This is dated today, but time is 9:30am , so it could not have just been created.

Everything is working, but why? Only real change is that xserver-xorg-video-nv was not previously installed.

BTW - Thanks for your  efforts -  We have made great progress!

---

### Post by 67GTA on 2008-12-30
The new xorg will use hal and dbus at boot to set the graphical settings if your hardware is supported, so you can run without an xorg file. It will only create one if special directions are needed like loading modules, etc. The nv module must have gotten removed somehow when you were previously trying to install the nvidia driver. Glad you got it going. I would keep searching the Nvidia site for new drivers that support the new xorg. You might get lucky. I was helping another user with the 96 series driver, and he got a beta driver from Nvidia that supported 8.10's xorg. I'm not sure if they will do the same for the 71 series.

---

### Post by GrahamM on 2008-12-30
> **67GTA said:**
> The new xorg will use hal and dbus at boot to set the graphical settings if your hardware is supported, so you can run without an xorg file. It will only create one if special directions are needed like loading modules, etc. The nv module must have gotten removed somehow when you were previously trying to install the nvidia driver. Glad you got it going. I would keep searching the Nvidia site for new drivers that support the new xorg. You might get lucky. I was helping another user with the 96 series driver, and he got a beta driver from Nvidia that supported 8.10's xorg. I'm not sure if they will do the same for the 71 series.

One thing about this sort of problem, is that it makes you dig into things. I had not set up ftp yet, but had to to post the link to the one large file! So at least I have that working now too! I am also getting to know where things are in teh file system and how to around permissions!

Seems like some sort of driver front end is needed - Something that would prevent users from getting into the kind of mess I did, just by trying to install the driver that Nvidia recommended. I guess they (NV) too should state the limitations of their drivers. Or at least more clearly.

I don't think I will do much more messing with Ubuntu this year ;)

Thanks again!

---

### Post by 67GTA on 2008-12-30
Just for future reference:

nv=(Not from Nvidia)opensource nvidia driver with 2D support.
Nvidia from Ubuntu repos=From Nvidia, not the latest, but known to work with supported cards, 3D support.
Nvidia from Nvidia=Newest version of drivers, might/might not be buggy(not tested in Ubuntu yet), 3D support.
Nouveau=Experimental opensource 3D driver, Still buggy, not for everyday use yet.

A lot of people with Nvidia cards were pissed when they found about Nvidia not updating some of their legacy card drivers. They have gotten a lot of flac over it.

---

### Post by sharkster2007 on 2008-12-30
Easiest way is this this thread link to my solution [http://ubuntuforums.org/showthread.php?t=973038]("http://ubuntuforums.org/showthread.php?t=973038")

Ignore all the command line guff this works for me with an Nvidia 6600GT and I am a very new to Ubuntu 8.10 too, good luck.

Hope it works for you too ;-)

---

