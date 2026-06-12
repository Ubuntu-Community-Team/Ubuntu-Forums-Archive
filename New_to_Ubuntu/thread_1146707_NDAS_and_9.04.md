---
title: "NDAS and 9.04"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by kerryandjane on 2009-05-02
Hey Guys love the auto compatibility of most of the Ubuntu 9.04 features but one thing i can't find is a howto on NDAS does one exist? i've been searching and googling and found some for older versions of Ubuntu but nothing for the latest. how do you find out what kernel your useing? and how the freak do you use it? 

Please help Cheers:confused:

---

### Post by 123456789123456789123456 on 2009-05-02
use the following command in terminal
uname -r
that should output the kernal version

---

### Post by prasanna1975 on 2009-05-10
Hi

I am facing the same issue we would require patch for the new kernel 2.6.28-11-generic, has any one got patch for 2.6.28-11-generic 

Prasanna

---

### Post by kevinbeard on 2009-05-10
> **prasanna1975 said:**
> Hi

I am facing the same issue we would require patch for the new kernel 2.6.28-11-generic, has any one got patch for 2.6.28-11-generic 

Prasanna

Please see my post on 

[http://ubuntuforums.org/showthread.php?t=979370&highlight=ndas&page=2](http://ubuntuforums.org/showthread.php?t=979370&highlight=ndas&page=2)

---

### Post by ntginson on 2009-05-10
> **kevinbeard said:**
> Please see my post on 

[http://ubuntuforums.org/showthread.php?t=979370&highlight=ndas&page=2](http://ubuntuforums.org/showthread.php?t=979370&highlight=ndas&page=2)



Hi Kevinbeard,

I have read and reread the thread you've linked here, but as it is, I am very, very new to Linux in General and Ubuntu 9.04 in particular and most if not all of the posts there are confusing to me. I hope you can provide a step by step procedure on how to go about installing/mounting a mediagate mg 350hd (NDAS) to Ubuntu 9.04 so that I can have read/write access to the mediagate mg 350hd

Thanks in advance

Bong

---

### Post by deankelly_68 on 2009-05-11
Hi - slightly different take on this one: I've just upgraded from 8.10 where I had NDAS working fine (thanks to the old "code.ximeta.com" site which is now seemingly dead.
 
9.04 promptly killed my NDAS functionailty and since the ximeta website seems to be defunct I can't get it up and working.
 
I've downloaded the kernal patches mentioned on the 8.10 thread, but when I issue the patch command (sudo patch -p1 < [the unzipped 2.6.28 patch]) I get nothing back - the patch command just seems to hang. I eventually killed it after 10 mins of inactivity.
 
Does anyone have a record of the full set of instructions that used to be up on the ximeta page? I had no trouble at all getting this running on 8.10 but 9.04 seems determined to scupper all attempts :(
 
Cheers,
Dean

---

### Post by ntginson on 2009-05-11
> **deankelly_68 said:**
> Hi - slightly different take on this one: I've just upgraded from 8.10 where I had NDAS working fine (thanks to the old "code.ximeta.com" site which is now seemingly dead.
 
9.04 promptly killed my NDAS functionailty and since the ximeta website seems to be defunct I can't get it up and working.
 
I've downloaded the kernal patches mentioned on the 8.10 thread, but when I issue the patch command (sudo patch -p1 < [the unzipped 2.6.28 patch]) I get nothing back - the patch command just seems to hang. I eventually killed it after 10 mins of inactivity.
 
Does anyone have a record of the full set of instructions that used to be up on the ximeta page? I had no trouble at all getting this running on 8.10 but 9.04 seems determined to scupper all attempts :(
 
Cheers,
Dean


Dean,

Would you mind helping me out. Can you provide a guide on how to install NDAS to Ubuntu?

---

### Post by deankelly_68 on 2009-05-11
The guide is actually what I was asking for in my post!
 
A few minutes ago, however, I noticed that the code.ximeta.com webiste seems to be back up again.
 
When I set this up on 8.10 a few weeks ago, I did it by following (to the letter) the instructions on that site. This was the instruction set I used:
 
[http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)
 
Good luck. I'll be trying it out on 9.04 tonight, with any luck.

---

### Post by kevinbeard on 2009-05-12
> **deankelly_68 said:**
> The guide is actually what I was asking for in my post!
 
A few minutes ago, however, I noticed that the code.ximeta.com webiste seems to be back up again.
 
When I set this up on 8.10 a few weeks ago, I did it by following (to the letter) the instructions on that site. This was the instruction set I used:
 
[http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)
 
Good luck. I'll be trying it out on 9.04 tonight, with any luck.

Great news that the site is up at last.

However, I haven't had much luck getting things working on 9.04 yet.  I can get the drivers built and installed and I can enable the ndas device but then the driver crashes with a NULL pointer issue.

I've been debugging for a few evening but no luck so far.

I'll post my findings once I've been back through the site

---

### Post by prasanna1975 on 2009-05-12
Hi 

I have been trying to install NDAS for 9.04, tried to build the driver manually but got the following errors

Invoking make againt the kernel at /lib/modules/2.6.28-11-generic/build
make -C /lib/modules/2.6.28-11-generic/build \
		SUBDIRS=/home/prasanna/Desktop/ndas-1.1-24 \
		KBUILD_VERBOSE=1 \
		ndas_root=/home/prasanna/Desktop/ndas-1.1-24 \
		modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/prasanna/Desktop/ndas-1.1-24/.tmp_versions ; rm -f /home/prasanna/Desktop/ndas-1.1-24/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/prasanna/Desktop/ndas-1.1-24
  gcc -Wp,-MD,/home/prasanna/Desktop/ndas-1.1-24/block/.block26.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DMODULE -DLINUX -I/home/prasanna/Desktop/ndas-1.1-24/inc -D_X86 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(block26)"  -D"KBUILD_MODNAME=KBUILD_STR(ndas_block)"  -c -o /home/prasanna/Desktop/ndas-1.1-24/block/.tmp_block26.o /home/prasanna/Desktop/ndas-1.1-24/block/block26.c
In file included from /home/prasanna/Desktop/ndas-1.1-24/block/block26.c:44:
include/linux/ide.h:121:1: warning: "PARTN_BITS" redefined
In file included from /home/prasanna/Desktop/ndas-1.1-24/block/block26.c:40:
/home/prasanna/Desktop/ndas-1.1-24/block/block.h:67:1: warning: this is the location of the previous definition
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:53: warning: initialisation from incompatible pointer type
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:54: warning: initialisation from incompatible pointer type
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:55: warning: initialisation from incompatible pointer type
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c: In function ‘nbio_alloc’:
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:155: error: ‘struct request’ has no member named ‘nr_hw_segments’
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c: In function ‘nblk_request_proc’:
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:437: error: ‘REQ_FAILFAST’ undeclared (first use in this function)
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:437: error: (Each undeclared identifier is reported only once
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:437: error: for each function it appears in.)
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c: At top level:
/home/prasanna/Desktop/ndas-1.1-24/block/block26.c:483: error: expected ‘)’ before ‘*’ token
make[2]: *** [/home/prasanna/Desktop/ndas-1.1-24/block/block26.o] Error 1
make[1]: *** [_module_/home/prasanna/Desktop/ndas-1.1-24] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [/home/prasanna/Desktop/ndas-1.1-24/ndas_sal.ko] Error 2

---

### Post by prasanna1975 on 2009-05-12
Hi

I followed [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)
it installed NDAS, had login error, but think it would get fixed after reboot

Prasanna

---

### Post by kevinbeard on 2009-05-12
> **prasanna1975 said:**
> Hi 

I have been trying to install NDAS for 9.04, tried to build the driver manually but got the following errors

...


I wouldn't spend too much effort if you can't build the drivers.  Those of us who have been able to still can't get the thing working.

There is a lot more info over at:
[http://code.ximeta.com/trac-ndas/ticket/839](http://code.ximeta.com/trac-ndas/ticket/839)

but the upshot is that since 2.6.28 noone has been able to get this to work yet :(

---

### Post by sergimunoz on 2009-05-12
Hi Prasanna
Apply the patches in order (both patches) to avoid this error.
The worst notice is after that you will find the commented crash ...
Sergi
Still waiting for a solution ...

---

### Post by deankelly_68 on 2009-05-20
Has anyone heard of any progress being made on this issue? It all seems to have gone very quiet...

---

### Post by prasanna1975 on 2009-05-24
Hi 

I tried everything , now I can see my Mediaget Online, but the command 
sudo /usr/sbin/ndasadmin enable -s 1 -o w gives the following output

Fail to get ndas information from /proc/ndas/slots/1/devname
enable: Unable to get the path of block device

Prasanna

---

### Post by Cuto on 2009-05-28
I am also there...

---

### Post by deankelly_68 on 2009-06-04
Still no news on code.ximeta.org. I'm wondering if we've been forgotten about?

---

### Post by Ispep on 2009-07-20
I'm new to Linux and have been using Windows 7 for a while know.  I have a wireless hdd that's connected to the TV and would like to be able to browse the drive and send file's to it.  Very simple with NDAS in windows.  I can't seam to get this to work in Ubuntu 9.04.
Can anyone help me ?

Thanks

---

### Post by Ispep on 2009-07-21
Terminal just hangs when trying to mount the drive.

The drive is NTFS.

---

### Post by Cuto on 2009-07-24
Taking time in finding a solution... anybody has succeded???
 
:confused:

---

### Post by gurbelunder on 2009-08-04
Hello anybody,
same problem as you all, any solutions?

---

### Post by Psykotik on 2009-08-04
Try debs from [http://code.ximeta.com/trac-ndas/ticket/1112](http://code.ximeta.com/trac-ndas/ticket/1112) (32bits) or [http://code.ximeta.com/trac-ndas/ticket/1113](http://code.ximeta.com/trac-ndas/ticket/1113) (64bits).

And please, report if it works or not; Arnaud is working hard to get the thing clean, but if many are complaining about the issues, no one tells exactly what's happening, if new release is better or not.

---

### Post by anicotra on 2009-09-20
I've been able to build the deb packages and install without error.  I noticed the tar with ticket #839 has all the patches already installed.  I've tried both that tar and the tar from xmetia (and patched myself).  

No problems with the install.  However, I can not mount the NDAS.  I can see the NDAS /dev/ndas-XXXXXXX-0. But that's it.

The drive is one NTFS partition, and was formatted from windows.  

Shouldn't I be able to mount -t ntfs /dev/ndas-XXXXXXX-0 /media/netdisk?  Or, does there have to be a partition id after the -0 above?  If so, does that mean I have to re-format the drive.  I don't see why?

I tried many clean installs with the same result.  The driver knows about the NDAS and size, but I can NOT mount it.

fdisk -l only shows /dev/ndas-XXXXXX-0.  It doesn't show and any cylinder or format information.  Why is that?

Anyone have an idea, or is this what everyone else is seeing.

Anthony

---

### Post by Grumpy242 on 2009-10-01
Psykotik
The ndasadmin .deb from ticket 1113 failed to start the service for me, the ndas-modules seemed to install fine.

My system:
grumpy@grumpy-desktop:~$ uname -a
Linux grumpy-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux


I followed the steps on /ticket/1110 and built from source and its working great.
I included all 4 patches (2 from ticket 839, openSuse from #1105, and Linux2.6.31.patch from #1110).  I did not apply the 2.6.31-1.patch.

/dev/ndas-00413651-0p1
                     156280288 124627000  31653288  80% /media/ndas

many thanks to Doug and Arnaud

---

### Post by anicotra on 2009-10-03
Well,  I got it mostly working as you can see in my original post.  However, I could not mount the drive, or see any partitions on it.  

My question is:  Should I be able to see partitions on the NDAS if the drive was formatted to NTFS within Windows?

an

---

