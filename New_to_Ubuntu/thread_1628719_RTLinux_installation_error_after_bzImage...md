---
title: "RTLinux installation error after bzImage.."
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Mahanthesh on 2010-11-23
Hi I am trying to install RTLinux in Linux Kernel 2.4.18 ... I am using rtlinux 3.2-pre3...
I have successfully followed steps till " **[B]make dep **[/B]"...
 After that i should give " **make bzImage** " ... But am getting following error after entering bzImage...
 Any guidance please..????
 
 
 
linux at ubuntu:/usr/src/linux-2.4.20$ sudo make bzImage
gcc -D__KERNEL__ -I/usr/src/linux-2.4.20/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i686 -DKBUILD_BASENAME=main -c -o init/main.o init/main.c
In file included from /usr/src/linux-2.4.20/include/linux/prefetch.h:13,
                 from /usr/src/linux-2.4.20/include/linux/list.h:6,
                 from /usr/src/linux-2.4.20/include/linux/wait.h:14,
                 from /usr/src/linux-2.4.20/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.20/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.20/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/asm/[[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]processor[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#").h:74: error: array type has incomplete element type
In file included from /usr/src/linux-2.4.20/include/asm/semaphore.h:39,
                 from /usr/src/linux-2.4.20/include/linux/fs.h:200,
                 from /usr/src/linux-2.4.20/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.20/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/asm/[[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]system[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#").h:8:25: error: asm/rtlinux.h: No such file or directory
/usr/src/linux-2.4.20/include/asm/system.h:333:29: error: asm/rtlinux_cli.h: No such file or directory
In file included from /usr/src/linux-2.4.20/include/linux/fs.h:318,
                 from /usr/src/linux-2.4.20/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.20/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/linux/ncp_fs_i.h:26: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp_fs_i.h:27: warning: ‘packed’ attribute ignored for field of type ‘__u8[6]’
In file included from /usr/src/linux-2.4.20/include/linux/ncp_mount.h:12,
                 from /usr/src/linux-2.4.20/include/linux/ncp_fs_sb.h:12,
                 from /usr/src/linux-2.4.20/include/linux/fs.h:703,
                 from /usr/src/linux-2.4.20/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.20/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/linux/ncp.h:24: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:25: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:26: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:27: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:28: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:29: warning: ‘packed’ attribute ignored for field of type ‘__u8[]’
/usr/src/linux-2.4.20/include/linux/ncp.h:37: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:38: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:39: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:40: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:41: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:42: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:43: warning: ‘packed’ attribute ignored for field of type ‘__u8[]’
/usr/src/linux-2.4.20/include/linux/ncp.h:137: warning: ‘packed’ attribute ignored for field of type ‘__u8’
/usr/src/linux-2.4.20/include/linux/ncp.h:138: warning: ‘packed’ attribute ignored for field of type ‘__u8[256]’
/usr/src/linux-2.4.20/include/linux/ncp.h:174: warning: ‘packed’ attribute ignored for field of type ‘__u8’
In file included from /usr/src/linux-2.4.20/include/linux/unistd.h:9,
                 from init/main.c:17:
/usr/src/linux-2.4.20/include/asm/unistd.h:375: warning: conflicting types for built-in function ‘_exit’
In file included from /usr/src/linux-2.4.20/include/asm/smp.h:18,
                 from init/main.c:69:
/usr/src/linux-2.4.20/include/asm/mpspec.h:86: warning: ‘packed’ attribute ignored for field of type ‘unsigned char[6]’
In file included from /usr/src/linux-2.4.20/include/asm/smp.h:22,
                 from init/main.c:69:
/usr/src/linux-2.4.20/include/asm/apic.h: In function ‘ack_APIC_irq’:
/usr/src/linux-2.4.20/include/asm/apic.h:56: warning: implicit declaration of function ‘label_ack_APIC’
init/main.c: In function ‘start_kernel’:
init/main.c:357: warning: format not a string literal and no format arguments
make: *** [init/main.o] Error 1

---

