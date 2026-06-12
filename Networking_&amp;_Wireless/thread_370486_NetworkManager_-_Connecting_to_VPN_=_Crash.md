---
title: "NetworkManager - Connecting to VPN = Crash"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by penvzila on 2007-02-25
I am trying to use NetworkManager to connect to a VPN.  When I input my username and password, it crashes and gives me this in the Bug Reporting Tool:

```
Memory status: size: 113991680 vsize: 113991680 resident: 13094912 share: 8593408 rss: 13094912 rss_rlim: -1
CPU usage: start_time: 1172450597 rtime: 29 utime: 26 stime: 3 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100

Backtrace was generated from '/usr/libexec/nm-ppp-auth-dialog'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47468851409568 (LWP 11669)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00002b2c31f19eb5 in waitpid () from /lib/libpthread.so.0
#0  0x00002b2c31f19eb5 in waitpid () from /lib/libpthread.so.0
#1  0x00002b2c2ecc8a07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
#2  <signal handler called>
#3  0x00002b2c3209186b in free () from /lib/libc.so.6
#4  0x0000000000404c9b in ?? ()
#5  0x00002b2c31532358 in g_object_unref ()
   from /usr/lib64/libgobject-2.0.so.0
#6  0x0000000000402f99 in ?? ()
#7  0x00002b2c320400c4 in __libc_start_main () from /lib/libc.so.6
#8  0x0000000000402a39 in ?? ()
#9  0x00007fff7bf55a18 in ?? ()
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 47468851409568 (LWP 11669)):
#0  0x00002b2c31f19eb5 in waitpid () from /lib/libpthread.so.0
No symbol table info available.
#1  0x00002b2c2ecc8a07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0x00002b2c3209186b in free () from /lib/libc.so.6
No symbol table info available.
#4  0x0000000000404c9b in ?? ()
No symbol table info available.
#5  0x00002b2c31532358 in g_object_unref ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#6  0x0000000000402f99 in ?? ()
No symbol table info available.
#7  0x00002b2c320400c4 in __libc_start_main () from /lib/libc.so.6
No symbol table info available.
#8  0x0000000000402a39 in ?? ()
No symbol table info available.
#9  0x00007fff7bf55a18 in ?? ()
No symbol table info available.
#10 0x0000000000000000 in ?? ()
No symbol table info available.
#0  0x00002b2c31f19eb5 in waitpid () from /lib/libpthread.so.0

```Anyone else have this problem?

---

### Post by stefano67 on 2007-03-01
The same here.
I'm on Edgy AMD64 connecting to a Microsoft VPN.

---

### Post by haelters on 2007-03-15
the bugreport en a workaround can be found here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/67881](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/67881)

---

