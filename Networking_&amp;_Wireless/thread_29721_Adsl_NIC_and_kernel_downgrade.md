---
title: "Adsl NIC and kernel downgrade"
date: 2005-04-25
forum: Networking &amp; Wireless
---

### Post by fantasyl on 2005-04-25
Hi to all!
My name is Roberto, I'm a linux newbie. I'm trying to downgrade the Hoary 
default kernel to 2.4.20....
this is a must for me as my adsl modem nic is an Itex PCI ....and Itex supplied 
the driver compiled for that kernel version (they're not gpl....), so I 
cannot insert the modules with insmod -f itexmodule

Is it possible to make the driver work with latest kernel (itex has gone bankrupt :( ) ?

Regarding the kernel downgrade, I hope this is possible......I untarred the 2.4.20 kernel under /usr/src , 
make the symbolic linux link, and then obtained strange result when doing 
make menuconfig.
After reading ton of doc I've been able to get to work "make xconfig" (which 
was not working.......), and "make dep" seems to go ok, too.
Actually the problem is when I do "make bzImage"....I get this output:

In file included from /usr/src/linux/include/asm/string.h:292,
from /usr/src/linux/include/linux/string.h:21,
from /usr/src/linux/include/linux/fs.h:23,
from /usr/src/linux/include/linux/capability.h:17,
from /usr/src/linux/include/linux/binfmts.h:5,
from /usr/src/linux/include/linux/sched.h:9,
from /usr/src/linux/include/linux/mm.h:4,
from /usr/src/linux/include/linux/slab.h:14,
from /usr/src/linux/include/linux/proc_fs.h:5,
from init/main.c:15:
/usr/src/linux/include/asm/system.h:148:9: missing terminating " character
In file included from /usr/src/linux/include/asm/string.h:292,
from /usr/src/linux/include/linux/string.h:21,
from /usr/src/linux/include/linux/fs.h:23,
from /usr/src/linux/include/linux/capability.h:17,
from /usr/src/linux/include/linux/binfmts.h:5,
from /usr/src/linux/include/linux/sched.h:9,
from /usr/src/linux/include/linux/mm.h:4,
from /usr/src/linux/include/linux/slab.h:14,
from /usr/src/linux/include/linux/proc_fs.h:5,
from init/main.c:15:
/usr/src/linux/include/asm/system.h: In function `__set_64bit':
/usr/src/linux/include/asm/system.h:149: error: syntax error before "movl"
/usr/src/linux/include/asm/system.h:150: warning: implicit declaration of 
function `cmpxchg8b'
/usr/src/linux/include/asm/system.h:150: error: syntax error before '%' 
token
/usr/src/linux/include/asm/system.h:151:21: invalid suffix "b" on integer 
constant
/usr/src/linux/include/asm/system.h:151: error: `jnz' undeclared (first use 
in this function)
/usr/src/linux/include/asm/system.h:151: error: (Each undeclared identifier 
is reported only once
/usr/src/linux/include/asm/system.h:151: error: for each function it appears 
in.)
/usr/src/linux/include/asm/system.h:151:23: missing terminating " character
In file included from /usr/src/linux/include/linux/string.h:21,
from /usr/src/linux/include/linux/fs.h:23,
from /usr/src/linux/include/linux/capability.h:17,
from /usr/src/linux/include/linux/binfmts.h:5,
from /usr/src/linux/include/linux/sched.h:9,
from /usr/src/linux/include/linux/mm.h:4,
from /usr/src/linux/include/linux/slab.h:14,
from /usr/src/linux/include/linux/proc_fs.h:5,
from init/main.c:15:
/usr/src/linux/include/asm/string.h:552:17: missing terminating " character
In file included from /usr/src/linux/include/linux/string.h:21,
from /usr/src/linux/include/linux/fs.h:23,
from /usr/src/linux/include/linux/capability.h:17,
from /usr/src/linux/include/linux/binfmts.h:5,
from /usr/src/linux/include/linux/sched.h:9,
from /usr/src/linux/include/linux/mm.h:4,
from /usr/src/linux/include/linux/slab.h:14,
from /usr/src/linux/include/linux/proc_fs.h:5,
from init/main.c:15:
/usr/src/linux/include/asm/string.h: In function `memscan':
/usr/src/linux/include/asm/string.h:553: error: syntax error before "jnz"
/usr/src/linux/include/asm/string.h:553:21: invalid suffix "f" on integer 
constant
/usr/src/linux/include/asm/string.h:555:17: missing terminating " character
In file included from /usr/src/linux/include/net/checksum.h:33,
from /usr/src/linux/include/linux/raid/md.h:34,
from init/main.c:24:
/usr/src/linux/include/asm/checksum.h:72:30: missing terminating " character
In file included from /usr/src/linux/include/net/checksum.h:33,
from /usr/src/linux/include/linux/raid/md.h:34,
from init/main.c:24:
/usr/src/linux/include/asm/checksum.h: In function `ip_fast_csum':
/usr/src/linux/include/asm/checksum.h:73: error: syntax error before "movl"
/usr/src/linux/include/asm/checksum.h:75:17: invalid suffix "f" on integer 
constant
/usr/src/linux/include/asm/checksum.h:82:17: invalid suffix "b" on integer 
constant
/usr/src/linux/include/asm/checksum.h:90:13: missing terminating " character
/usr/src/linux/include/asm/checksum.h:105:17: missing terminating " 
character
/usr/src/linux/include/asm/checksum.h: In function `csum_fold':
/usr/src/linux/include/asm/checksum.h:106: error: syntax error before "addl"
/usr/src/linux/include/asm/checksum.h:108:17: missing terminating " 
character
/usr/src/linux/include/asm/checksum.h:121:13: missing terminating " 
character
/usr/src/linux/include/asm/checksum.h: In function `csum_tcpudp_nofold':
/usr/src/linux/include/asm/checksum.h:122: error: syntax error before "addl"
/usr/src/linux/include/asm/checksum.h:126:9: missing terminating " character
/usr/src/linux/include/asm/checksum.h:128: error: `__x' undeclared (first 
use in this function)
/usr/src/linux/include/asm/checksum.h: At top level:
/usr/src/linux/include/asm/checksum.h:128: error: syntax error before ')' 
token
/usr/src/linux/include/asm/checksum.h:161:17: missing terminating " 
character
/usr/src/linux/include/asm/checksum.h: In function `csum_ipv6_magic':
/usr/src/linux/include/asm/checksum.h:162: error: syntax error before "addl"
/usr/src/linux/include/asm/checksum.h:173:17: missing terminating " 
character
/usr/src/linux/include/asm/checksum.h:176: error: `__x' undeclared (first 
use in this function)
/usr/src/linux/include/asm/checksum.h:176: warning: no return statement in 
function returning non-void
/usr/src/linux/include/asm/checksum.h: At top level:
/usr/src/linux/include/asm/checksum.h:176: error: syntax error before ')' 
token
/usr/src/linux/include/asm/checksum.h:176: error: syntax error before 
"__u32"
make: *** [init/main.o] Error 1

My sixth sense says this is related to gcc libraries version.....but I 
cannot go any further on my own :(
Hope someone could help.....I'd like to switch to linux/ubuntu, but 
connecting to internet is too important (and neither can afford a DSL router 
atm.....)
Thanks to all!

Roberto

---

