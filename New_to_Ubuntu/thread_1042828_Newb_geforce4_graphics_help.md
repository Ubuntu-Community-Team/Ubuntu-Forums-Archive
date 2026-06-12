---
title: "Newb geforce4 graphics help"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by seedlings on 2009-01-17
As cool as 640x480 used to be back in '82, it's a real pain now.

I just blew away xp and installed ubuntu.  My emachine has an inbread (onboard) nvidia geforce4 mx and the auto-update nvidia version 96 has installed.

I downloaded another linux driver from nvidia's site.  I don't know how to install the driver.  It says to type a command - I assume into the Terminal prompt, but that errors.  The driver file is sitting on the desktop.

You all are not mortals, I've read the linux-speak posts, and do not understand.  I am not unintelligent, just an infant... and mortal.

Thanks for your time.

---

### Post by taurus on 2009-01-17
What is the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by seedlings on 2009-01-18
I'm on the laptop so I have to type it in this post manually...

total 13100
drwxr-xr-x  2 computer computer     4096 2009-01-17 22:02
drwxr-xr-x 30 computer computer     4096 2009-01-17 22:55
-rs-r--r--  1 computer computer 13384929 2009-01-17 22:02 NVIDIA-Linux-x86-96.43.01-pkg1.run

---

### Post by taurus on 2009-01-18
First, make sure that is the driver for your graphic card because if you install a wrong one, you could crash your X server.

Now, boot your machine and at the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  At the prompt, stop the X server.

```
sudo /etc/init.d/gdm stop
```
Then, change to ~/Desktop directory and install that nvidia driver.

```
cd ~/Desktop
chmod +x NVIDIA-Linux-x86-96.43.01-pkg1.run
sudo ./NVIDIA-Linux-x86-96.43.01-pkg1.run
```
Once the installation is done, restart the X server with

```
sudo /etc/init.d/gdm start
```

---

### Post by seedlings on 2009-01-18
There is no GUI login screen? <newb reminder>

On reboot, the ubuntu screen shows up with the orange bar.  Next the desktop shows up.

I hit ctrl-alt-F2 at the orange bar screen before the desktop shows up.  The screen went black and some commands started scrolling down.  I did the ctro-alt-F2 again and got the prompt at the bottom.  I typed in that first command and it said invalid.  I retyped it several times.

---

### Post by taurus on 2009-01-18
What's the output of this command?

```
ps -A
```

---

### Post by seedlings on 2009-01-18
The output of that command is very long and would take me forever to type over here on the laptop.

I tried your previous instructions several times and got the nvidia loader to come up.

I accepted the terms, then it did a scan for a minute, then it told me there was an error and I'd have to go to nvidia.com for help.

---

### Post by taurus on 2009-01-18
Do you know the exact error message?  If it's too long to write, perhaps take a picture of the screen and post it here if you have access to a camera (or phone camera).

---

### Post by seedlings on 2009-01-18
To be more specific regarding the NVIDIA accelerated Graphics Driver for Linux-x86 (96.43.01) errors:

No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site?

>YES

No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compoile a kernel interface for your kernel.

>OK

Building kernel module... ... ...

ERROR: Unable to build the NVIDIAkernel module.

>OK

ERROR:  Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

>OK


End of messages.

---

### Post by taurus on 2009-01-18
What does /var/log/nvidia-installer.log say?

```
cat /var/log/nvidia-installer.log
```

---

### Post by seedlings on 2009-01-18
pic

[IMG]http://i206.photobucket.com/albums/bb54/seedlings/screen13.jpg[/IMG]

---

### Post by Leo Dragonheart on 2009-01-18
I don't know if this will help but it fixed my nVidia problem. I installed the recomended 173 driver then did this that someone else told me to do...


First you need to open your xorg.conf file in Gedit, like this:

Go to Main Menu>Accessories>Terminal...then cut and paste, or type in the (Bold Type)code below...

Code:

**sudo gedit /etc/X11/xorg.conf**

You'll have to enter your password to gain editing privileges.

Some say you should back up the file first, but I found gedit does this automaticaliy, and right now your original file isn't doing you much good anyway.

Next, you have to add a few lines to specific sections of your xorg.conf file. BUT DO NOT CHANGE ANYTHING ELSE!

In the Monitor section add the lines that appear in bold:
Code:

Section "Monitor"
    Identifier     "Configured Monitor"
[B]    HorizSync       31.0 - 65.0
    VertRefresh     51.0 - 90.0	[/B]
EndSection

Note that these are the specs that fit my particular monitor. They'll probably work for yours also - but if you want to you can replace the VertRefresh and HorizSync values with your monitor's actual data if you know what they are.

Next, in the Screen section add the lines that appear in bold, right before the EndSection line.

Code:

[B]    SubSection     "Display"
       Depth       24
        Modes      "1280x1024_60"
    EndSubSection[/B]

This set my monitor to my desired resolution which is 1280X1024. You can substitute the resolution data to suit your needs. Reboot your computer and you should have a high resolution display. Next, you should run the NVIDIA settings program to fine tune your system.

If this doesn't work, then you can boot in recovery mode and select the fix x-server option. This will give you a high resolution display but no special effects, etc.

I hope this helps.

---

### Post by seedlings on 2009-01-18
Thx, LD.  Every bit helps...

---

### Post by Crafty Kisses on 2009-01-18
You need the "**build-essential**" package, run the following commands:
```
sudo apt-get update
sudo apt-get install build-essential
```
Once you've grabbed that package, you can try and recompile the NVIDIA drivers. If that doesn't work you may need to install certain kernel headers, it really all depends.

---

### Post by seedlings on 2009-01-18
Leo Dragonheart...

That first command pulled up the window:
xorg.conf (/ect/x11) - gedit

But there's nothing there but a blinking cursor???

---

### Post by seedlings on 2009-01-18
Codename, your suggestion is downloading right now...

setting up... unpacking... processing.....

OK.  Looks like it's finished, and we're back to the prompt.  Now what?

---

### Post by Leo Dragonheart on 2009-01-18
Can't help you with that sorry, this is only my 6th cup of Ubuntu...I'm a newb.

---

### Post by Crafty Kisses on 2009-01-18
Now try running the NVIDIA installer again:
```
cd ~/Desktop
chmod +x NVIDIA-Linux-x86-96.43.01-pkg1.run
sudo ./NVIDIA-Linux-x86-96.43.01-pkg1.run
```
Restart the X server with the following command:
```
sudo /etc/init.d/gdm start
```

---

### Post by 3rdalbum on 2009-01-18
The Nvidia installer seems to be complaining that it doesn't have "kernel headers".

The kernel headers are Linux's description of exactly where everything is inside the kernel. When you want to compile a new kernel module (e.g. a driver), the driver needs to know where everything is inside the kernel otherwise it can't talk to the kernel.

Go into Synaptic Package Manager and install the package "linux-headers-generic". The driver will be able to install now.

If you install the driver from Nvidia's website, then you will need to re-install it every time you install a kernel update. Each kernel update will automatically update the "linux-headers-generic" version so you will always have the current kernel headers for the Nvidia installer to use.

---

### Post by seedlings on 2009-01-18
> **3rdalbum said:**
> The Nvidia installer seems to be complaining that it doesn't have "kernel headers".

The kernel headers are Linux's description of exactly where everything is inside the kernel. When you want to compile a new kernel module (e.g. a driver), the driver needs to know where everything is inside the kernel otherwise it can't talk to the kernel.

Go into Synaptic Package Manager and install the package "linux-headers-generic". The driver will be able to install now.

If you install the driver from Nvidia's website, then you will need to re-install it every time you install a kernel update. Each kernel update will automatically update the "linux-headers-generic" version so you will always have the current kernel headers for the Nvidia installer to use.

Oh, how I would like to be able to do the things you say.  How do I "Go into Synaptic Package Manger"?

Also, Codename... I re-ran that NVIDIA program and it came up with the same errors as before.

---

### Post by Crafty Kisses on 2009-01-18
You really don't have to go into Synaptic if you know the package name off the top of your head, but you can go into Synaptic by going to **System->Administration->Synaptic Package Manager**, but you can install those kernel headers, by running the following command:
```
sudo apt-get install linux-headers-generic
```

---

### Post by seedlings on 2009-01-18
OK.  I reinstalled the linux-headers-generic.

Now re-run the NVIDIA checker, I guess.

---

### Post by seedlings on 2009-01-18
And that still errors out.

---

### Post by Crafty Kisses on 2009-01-18
Yes, and if you're still getting errors, can you please post the results of this command?
```
cat /var/log/nvidia-installer.log
```

---

### Post by seedlings on 2009-01-18
> **Codename said:**
> Yes, and if you're still getting errors, can you please post the results of this command?
```
cat /var/log/nvidia-installer.log
```

***_I AM GOING TO BED  I'll try more tomorrow, thanks all!_***

computer@stupid-computer:~$ cat /var/log/nvidia-installer.log
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jan 18 00:27:45 2009

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
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
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
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL_
   _  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -in
   clude include/linux/autoconf.h -
   Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-stric
   t-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft
   -float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i
   586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-
   default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-c
   alls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz6856/N
   VIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wsw
   itch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar
   -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -
   D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"96.43.01\" -UDEBUG -U_DEBU
   G -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)" 
   -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6856/NVIDIA-Linux-x86
   -96.43.01-pkg1/usr/src/nv/.tmp_nv.
   o /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
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
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:1971: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv-linux.h:85,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv-linux.h:105:27:
   error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv-linux.h:107,
                    from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
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
   In file included from /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv-linux.h: In fun
   ction &#8216;nv_execute_on_all_cpus&#8217;:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv-linux.h:617: er
   ror: too many arguments to function &#8216;on_each_cpu&#8217;
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c: In function 
   &#8216;nvos_proc_create&#8217;:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:494: error: 
   &#65533;&#65533;proc_root_driver&#8217; undeclared (first use in this function)
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:494: error: (
   Each undeclared identifier is reported only once
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:494: error: f
   or each function it appears in.)
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c: In function 
   &#8216;__nv_setup_pat_entries&#8217;:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:822: warning:
   comparison between signed and unsigned
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c: In function 
   &#8216;__nv_restore_pat_entries&#8217;:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:848: warning:
   comparison between signed and unsigned
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c: In function 
   &#8216;nv_kern_cpu_callback&#8217;:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:1154: warning
   : comparison between signed and unsigned
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:1157: error: 
   too many arguments to function &#8216;smp_call_function&#8217;
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:1161: warning
   : comparison between signed and unsigned
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:1164: error: 
   too many arguments to function &#8216;smp_call_function&#8217;
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c: In function 
   &#8216;nv_kern_vma_nopage&#8217;:
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:1676: error: 
   &#8216;NOPAGE_SIGBUS&#8217; undeclared (first use in this function)
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c: At top level
   :
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:1683: error: 
   unknown field &#8216;nopage&#8217; specified in initializer
   /tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.c:1683: warning
   : initialization from incompatible pointer type
   make[3]: *** [/tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src/nv/nv.o
   ] Error 1
   make[2]: *** [_module_/tmp/selfgz6856/NVIDIA-Linux-x86-96.43.01-pkg1/usr/src
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
computer@stupid-computer:~$

---

### Post by minsf on 2009-01-18
i had the same problem. i also installed the nvidia driver via the .run file. 
first you need to be patient and be sure that it is going to work in the end. trust me, i was there, and i know how frustrating it is.
next i need you to understand that there are going to be two parts to the process: part A will be installing the driver. Part B will be configuring the setting (the xorg.conf file). so if someone gives you advice about xorg.conf , like LD, you say thank you very much, but you dont do it before you finish the installation of the driver. (and dont get me wrong, LD's advice is great, but it's not time for it yet).

now i am going to take you step by step.
STEP #1: i need you to give me the output of the command ```
uname -a
``` (everything i write as "code" you should type in the terminal and press enter. the best is if you can cut and paste it from the terminal window to the forum. (when cutting from the terminal, use ctrl+SHIFT+C rather than the standard ctrl+c)

---

### Post by minsf on 2009-01-18
It's getting late here, so before i fall aasleep let me give you the next step:
STEP #2: you need to download a newer version of the driver!! you are trying to use 96.43.01, but you need 96.43.09 (i tried with 96.43.07 but it didnt work for me, so i will help you with the newer 96.43.09). here's where you get this:
[ftp://download.nvidia.com/XFree86/Linux-x86/96.43.09/](ftp://download.nvidia.com/XFree86/Linux-x86/96.43.09/)
you are going to see two packages there. you need package 0. How do i know? because if you download package 1, and you run it with the parameter --history, it will tell you that it is intended for red hat/ fedora/suse etc. not debian/ubuntu! so you need package 0. 
right click that package and save it to your desktop. be sure not to confuse it with the other driver (it may be better to remove the previous driver 96.43.01 from your desktop).

---

### Post by seedlings on 2009-01-18
> **minsf said:**
> 
STEP #1: i need you to give me the output of the command ```
uname -a
``` (everything i write as "code" you should type in the terminal and press enter. the best is if you can cut and paste it from the terminal window to the forum. (when cutting from the terminal, use ctrl+SHIFT+C rather than the standard ctrl+c)

```

computer@stupid-computer:~$ uname -a
Linux stupid-computer 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
```

This is the output of the command, minsf.

Also, the NVIDIA softare installer is saying

```
Error: nvidia-installer must be run as root
```

When I try to install the new 09-pkg0.run file.

---

### Post by seedlings on 2009-01-18
I did some stuff on page1 here:

[http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub)

Now the screen works!  I'd love to be able to tell you what fixed it... but... I really have no idea.

Thanks!

---

### Post by minsf on 2009-01-18
no. 
i asked you to download it, no to run it. but fortunately it didnt run, so dont worry :) 
we need to prepare before we can run it. so dont left-click on the package. instead, right click on it, and save as blablabla.run on your desktop.

we will run it later, but first we need:
STEP #3: in the command line, enter
```
sudo dpkg -l | grep nvidia
```
it may ask for your password. then post the output here. this output is the nvidia-related packages already installed on your computer. i need to know them, to be sure that there will not be a conflict with the driver that we are going to install.

STEP #4 again in the terminal, enter:
```
sudo apt-get install linux-headers-generic gcc build-essential pkg-config xserver-xorg-dev 
```
this install some packages that the driver needs in order to run successfully. again it'll probably ask for your password, and it'll ask for your confirmation (enter Y). it'll probably say that some of them are already installed, that's ok (it will not double-install a package). we just need to be sure.

be patient out there, i know how frustrating it is, but in a month from now you'll be helping some newbie install this driver yourself :)

---

### Post by minsf on 2009-01-18
> **seedlings said:**
> I did some stuff on page1 here:

[http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub)

Now the screen works!  I'd love to be able to tell you what fixed it... but... I really have no idea.

Thanks!

well this means you installed a very old driver...
but if you are happy, that is what important. 
if you want to install the new one, then let me know and i will help you more.

one thing for the future: 
it is not so good to try out too many things together. if you decide to follow that howto- stick with it. if you decide to get my help-stick with it (and dont listen to someone else). if you decide to follow someone else- stick with it and dont listen to me :) 
the point is, only at the end of a process you can judge if something worked or not. and then if it didnt work in the end- change to a different resource. but you shouldnt change to a different resource if you are still in step 3 out of 7...

anyways, as long as you are happy with the screen, that is the important thing- ENJOY!

---

### Post by seedlings on 2009-01-18
I'd love to install the new driver.  Is your offer to help still available?

---

### Post by minsf on 2009-01-18
> **seedlings said:**
> I'd love to install the new driver.  Is your offer to help still available?
what is the output of the following command:
```
glxinfo | grep version
```
i also need the output from step #3 above.

---

### Post by seedlings on 2009-01-19
Step #3:
```
computer@stupid-computer:~$ sudo dpkg -l | grep nvidia
ii  nvidia-173-modaliases                     173.14.12-1-0ubuntu4                    Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-modaliases                     177.82-0ubuntu0.1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                      71.86.04-0ubuntu10                      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                      96.43.09-0ubuntu1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                             0.2.4                                   Find obsolete NVIDIA drivers
rc  nvidia-glx-96                             96.43.09-0ubuntu1                       NVIDIA binary Xorg driver
rc  nvidia-settings                           177.78-0ubuntu2.1                       Tool of configuring the NVIDIA graphics driv
computer@stupid-computer:~$ 

```

Per your latest request:
```
computer@stupid-computer:~$ glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 1.5.8 NVIDIA 96.43.09
computer@stupid-computer:~$ 
```


Step #4:
```
computer@stupid-computer:~$ sudo apt-get install linux-headers-generic gcc built-essential pkg-config xserver-xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
gcc is already the newest version.
E: Couldn't find package built-essential
computer@stupid-computer:~$
``` 

Thanks again, minsf.

---

### Post by minsf on 2009-01-19
the reason it did not install the third package is that you had a typo: it should be build-essential (rather than built-essential).
but this is irrelevant!

> **seedlings said:**
> I did some stuff on page1 here:
[http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub)


according to the last piece of info that you posted, it seems that you are running the latest version 96.43.09 
this means you actually did NOT follow the quoted guide (as it instruct you to install 97.55 from about a year and a half ago).
it seems like you were either (a) following some other guidance or (b) experienced enough to adjust that other guide or (c) lucky.
i say this because that guide tell you to prepare by installing only 3 of the 5 needed packages. so it seems you had the kernel headers and gcc correct before you ran the driver. also you built the correct driver and not the one suggested by that guide. 

Bottom line: you are running the latest nvidia driver and i hear no complains from you about the configuration file xorg.conf , so the only thing that is left for you to do is to buy a lottery ticket :)

cheers mate, and enjoy the driver
:)

---

### Post by seedlings on 2009-01-19
> **minsf said:**
> the reason it did not install the third package is that you had a typo: it should be build-essential (rather than built-essential).
but this is irrelevant!



according to the last piece of info that you posted, it seems that you are running the latest version 96.43.09 
this means you actually did NOT follow the quoted guide (as it instruct you to install 97.55 from about a year and a half ago).
it seems like you were either (a) following some other guidance or (b) experienced enough to adjust that other guide or (c) lucky.
i say this because that guide tell you to prepare by installing only 3 of the 5 needed packages. so it seems you had the kernel headers and gcc correct before you ran the driver. also you built the correct driver and not the one suggested by that guide. 

Bottom line: you are running the latest nvidia driver and i hear no complains from you about the configuration file xorg.conf , so the only thing that is left for you to do is to buy a lottery ticket :)

cheers mate, and enjoy the driver
:)

You're right.  I followed the other guide, substituting the driver you suggested.  I was just thinking... one other thing I did before following that other guide was to disable the driver that was already working in System>Admin>Hardware Drivers.

If you're game, I would like to know why, if, under Desktop>Right Click>Change Desktop Background>Visual Effects I select any option other than "None", I lose the top section of all windows with the minimize, maximize, X (close).  And, the Terminal window comes up 1/4 of the screen white, with no "File Edit.." words, no boarder, and I can't type in it.

Thanks again, minsf.

---

### Post by minsf on 2009-01-20
> **seedlings said:**
> You're right.  I followed the other guide, substituting the driver you suggested.  I was just thinking... one other thing I did before following that other guide was to disable the driver that was already working in System>Admin>Hardware Drivers.
good job!
> **seedlings said:**
> If you're game, I would like to know why, if, under Desktop>Right Click>Change Desktop Background>Visual Effects I select any option other than "None", I lose the top section of all windows with the minimize, maximize, X (close).  And, the Terminal window comes up 1/4 of the screen white, with no "File Edit.." words, no boarder, and I can't type in it.
I think adding the line ```
Option  "AddARGBGLXVisuals"  "True"
```
to the screen section in the /etc/X11/xorg.conf file will solve it. i had a similar problem, and our graphic cards are very similar (though not exactly the same).
enjoy,
minsf

---

### Post by seedlings on 2009-01-20
I can find that file, but it won't allow me to save any changes, tells me I don't have permission.

Here's the file's contents:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Mon Oct 27 14:37:20 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by minsf on 2009-01-20
> **seedlings said:**
> I can find that file, but it won't allow me to save any changes, tells me I don't have permission.
you need to edit the file as root, so in a terminal/console enter the following:
```
gksudo gedit /etc/X11/xorg.conf
```
this should open a graphical editor and you will now be able to save the file.
by the way, gksudo is the graphical equivalent of sudo, and will give you superuser permissions for one command in exchange for your password. 
here, we use it to get super-permissions while editing, since "gedit" is the command that starts the graphic editor in gnome (if you use kde you should use "kate" instead).
you can also use the nano editor to edit it in the command-line interface. again, you are going to need root permissions to edit it, so you'll need to enter "sudo nano /etc/X11/xorg.conf". but i think the graphical editor will be more intuitive for you.

anyways, you should probably add that line to the last section, so it becomes:
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    [COLOR="Red"]Option         "AddARGBGLXVisuals"  "True"[/COLOR]
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by minsf on 2009-01-20
a little advice: write a little note with what you did to install the driver. 
reason: when you update the kernel, you may need to reinstall the driver, or install a new nvidia driver that is compatible with it. you'll be able to do it quickly if you have a note with the steps you just did in the last couple of days :)

---

### Post by seedlings on 2009-01-20
> **minsf said:**
> a little advice: write a little note with what you did to install the driver. 
reason: when you update the kernel, you may need to reinstall the driver, or install a new nvidia driver that is compatible with it. you'll be able to do it quickly if you have a note with the steps you just did in the last couple of days :)

Do you think I'll need to reinstall a different driver?  I followed your instructions, and the file has been edited.  Still, the windows don't work right unless it's on the lowest Visual Effect setting.  It's really not that big of a deal, but if would be nice to have it work right.

As always, thanks for your generous help.

---

### Post by minsf on 2009-01-21
> **seedlings said:**
> Do you think I'll need to reinstall a different driver?  I followed your instructions, and the file has been edited.  Still, the windows don't work right unless it's on the lowest Visual Effect setting.  .
no it's not a problem of the driver. it's a problem with the configuration. you will only need to reinstall the driver when you upgrade your kernel- for instance when you upgrade to ubuntu 9.04
in 3 months...
trust me on that option line. edit the xorg.conf and add it in the right place! be very precise about the spelling. it's got to work!
post here the file after you edited it.
what monitor do you use?

---

### Post by minsf on 2009-01-21
also you have to realize that you and i have "old" graphic cards. so it's not a matter of the driver, but more of the hardware- if you want to enjoy 3D acceleration and eye candies, you need a newer graphic card... 
in the meantime, you should focus on configuring it right :)

---

### Post by igknighted on 2009-01-21
> **minsf said:**
> also you have to realize that you and i have "old" graphic cards. so it's not a matter of the driver, but more of the hardware- if you want to enjoy 3D acceleration and eye candies, you need a newer graphic card... 
in the meantime, you should focus on configuring it right :)

Actually, the driver in question (the 96 series) was from the early days of compiz (before beryl IIRC), so there were many bugs in the driver that are fixed with the latest ones (173/177/180 drivers).  However, since geforce4 cards are not supported after the 96 drivers, that's the best you can hope for.  At least until neauvou becomes a viable option.

You could try switching what use use for window decoration (emerald or metacity), perhaps one would work better.  Also, certain themes work better than others, so try a few.

---

### Post by seedlings on 2009-01-21
Maybe I'll just quit messing around with it.  Do you think the graphics card has something to do with this other problem:

[http://ubuntuforums.org/showthread.php?t=1045710](http://ubuntuforums.org/showthread.php?t=1045710)


Here's how the file looks after editing:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Mon Oct 27 14:37:20 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    Option         "AddARGBGLXVisuals"  "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

But still no cool effects.  Monitor is an eMachines eView 17c2.  Yes, CRT.

---

### Post by minsf on 2009-01-21
hey,
so the situation is basically that you have the newest driver for your graphic card and it seems to be stable with the "no visual effects". since your graphic card (and mine) is not supported by nvidia anymore, we have some troubles with compiz. you can try to change metacity to emerald or play with the themes. you can also try to adjust the options in the xorg.conf file. 

for instance, i found the following specifications for your monitor (you may want to search around a bit to check this out):
```

Max. Resolution: 	1280 x 1024
Synchronization Range - Horizontal : 	30 - 70 kHz
Synchronization Range - Vertical : 	50 - 160 Hz
Native (Recommended) Resolution: 	800 x 600

```
i imagine you dont want to work in the native resolution... but you should probably remove the 1600x1200 entry from that subsection, since your max resolution seems to be 1280x1024.
also you should try to change the resolutions in the monitor section in xorg.conf to these specifications.

i am sorry that the option i recommended before didnt solve the problem. i was following the compiz-nvidia wiki, which worked nicely with my geforce4. so i really thought it'll work with yours. you may be interested in the following link:
[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)
another good link for tinkering with xorg.conf is from the nvidia readme for our driver:
[ftp://download.nvidia.com/XFree86/Linux-x86/96.43.09/README/appendix-d.html](ftp://download.nvidia.com/XFree86/Linux-x86/96.43.09/README/appendix-d.html)

are you sure you have absolutely no visual effects? for instance when you grab a window (if you dont have the windows panels, then you can use alt+f7 to grab them), dont they bend nicely?
if you want to control the visual effects, you should probably install the compiz setting manager. in a terminal, enter:
```
sudo apt-get install compizconfig-settings-manager
```
after installation, you can go to System==>Preferences==>CompizConfig 
For instance, in the desktop section, you can choose "desktop cube" and "rotate cube". make sure they are enabled. now click alt+ctrl+RightArrow to change to the other side of the dektop. 
did it work?

---

### Post by minsf on 2009-01-21
by the way, if you changed some settings and it improved performance for you, then definitely let me know- we have similiar cards after all...

---

### Post by minsf on 2009-01-21
one more idea: your user is not a member of the video group, by default. this may cause a problem. to add users to the video group, enter the following command (in terminal or any other command line interface):
```
sudo gpasswd -a your_username video
```
then restart gnome with
```
sudo /etc/init.d/gdm restart
```
or ```
startx
```

by the way, are you sure that you restarted gnome after each change. like after adding that option to xorg.conf, did you restart gnome?

---

### Post by seedlings on 2009-01-21
minsf, I do not remember if I started or stopped gnome each time I tried to change something.

Honestly, I'm probably going to give up on that issue, since it seems to work ok now.  I just cannot mess with it any more.

The new issue with ubuntu, one which will require me to go back to XP has to do with printing coupons from [www.coupons.com](www.coupons.com) and other similar sites that are exclusive to windows.

I'm going to start another thread about that, though.  If you feel like trying to help, look it up.

You've done more than your share already.  Thanks once more.

---

### Post by minsf on 2009-01-21
> **seedlings said:**
> minsf, I do not remember if I started or stopped gnome each time I tried to change something.

Honestly, I'm probably going to give up on that issue, since it seems to work ok now.  I just cannot mess with it any more.

The new issue with ubuntu, one which will require me to go back to XP has to do with printing coupons from [www.coupons.com](www.coupons.com) and other similar sites that are exclusive to windows.

I'm going to start another thread about that, though.  If you feel like trying to help, look it up.

You've done more than your share already.  Thanks once more.

try wine 
it'll let you use windows applications in linux, as if you were running them on windows. 
i myself try to avoid it, but if it is important for you, then you try wine

as for the graphic card- the good bottom line is that it works. for fancy visual effects, one probably needs a new card, or to tinker with the options for hours...
anyways, glad i was able to help.
keep in touch :)

---

