---
title: "Help! Buffer overflow detected"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by dredtech on 2009-05-29
Ubunto 9.04 desktop 
Installed squid (working fine) and just installed sarg 2.2.3.1
was working fine for a few minutes and then got this message.

Can someone help me fix this?


root@ubuntu:~# sarg restart
*** buffer overflow detected ***: sarg terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7eceda8]
/lib/tls/i686/cmov/libc.so.6[0xb7ecceb0]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7ecc184]
sarg[0x8061587]
sarg[0x8063631]
sarg[0x8050d65]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7de7775]
sarg[0x80495f1]
======= Memory map: ========
08048000-08079000 r-xp 00000000 08:06 137066     /usr/bin/sarg
08079000-0807a000 r--p 00030000 08:06 137066     /usr/bin/sarg
0807a000-08084000 rw-p 00031000 08:06 137066     /usr/bin/sarg
08084000-0822a000 rw-p 08084000 00:00 0 
09250000-09271000 rw-p 09250000 00:00 0          [heap]
b7db4000-b7dc1000 r-xp 00000000 08:06 112737     /lib/libgcc_s.so.1
b7dc1000-b7dc2000 r--p 0000c000 08:06 112737     /lib/libgcc_s.so.1
b7dc2000-b7dc3000 rw-p 0000d000 08:06 112737     /lib/libgcc_s.so.1
b7dd0000-b7dd1000 rw-p b7dd0000 00:00 0 
b7dd1000-b7f2d000 r-xp 00000000 08:06 129792     /lib/tls/i686/cmov/libc-2.9.so
b7f2d000-b7f2e000 ---p 0015c000 08:06 129792     /lib/tls/i686/cmov/libc-2.9.so
b7f2e000-b7f30000 r--p 0015c000 08:06 129792     /lib/tls/i686/cmov/libc-2.9.so
b7f30000-b7f31000 rw-p 0015e000 08:06 129792     /lib/tls/i686/cmov/libc-2.9.so
b7f31000-b7f34000 rw-p b7f31000 00:00 0 
b7f40000-b7f43000 rw-p b7f40000 00:00 0 
b7f43000-b7f44000 r-xp b7f43000 00:00 0          [vdso]
b7f44000-b7f60000 r-xp 00000000 08:06 112695     /lib/ld-2.9.so
b7f60000-b7f61000 r--p 0001b000 08:06 112695     /lib/ld-2.9.so
b7f61000-b7f62000 rw-p 0001c000 08:06 112695     /lib/ld-2.9.so
bfe0d000-bfe61000 rw-p bffac000 00:00 0          [stack]
Aborted
root@ubuntu:~#

---

### Post by nandemonai on 2009-05-29
1. You should be using sudo not root.
2. How did you install sarge? Looks like a bug to me. You might want to file a report with the developers.

---

