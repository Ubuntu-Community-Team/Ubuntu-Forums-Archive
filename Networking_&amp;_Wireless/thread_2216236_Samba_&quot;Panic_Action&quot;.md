---
title: "Samba &quot;Panic Action&quot;"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2014-04-10
Getting one or two of these a day. Ubuntu 12.04, sharing out a couple directories for Windows users here. The system keeps running and no one is complaining that they are having file access problems, but still . . . 

```

To: root@CCD-6-Linux
Subject: Panic or segfault in Samba
User-Agent: Heirloom mailx 12.5 6/20/10
MIME-Version: 1.0
Content-Type: text/plain; charset=us-ascii
Content-Transfer-Encoding: 7bit

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 6156 (/usr/sbin/smbd).

This means there was a problem with the program, such as a segfault.
Below is a backtrace for this process generated with gdb, which shows
the state of the program at the time the error occurred.  The Samba log
files may contain additional information about the problem.

If the problem persists, you are encouraged to first install the
samba-dbg package, which contains the debugging symbols for the Samba
binaries.  Then submit the provided information as a bug report to
Ubuntu by visiting this link:
https://launchpad.net/ubuntu/+source/samba/+filebug

[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1".
0xb6df2424 in __kernel_vsyscall ()
#0  0xb6df2424 in __kernel_vsyscall ()
#1  0xb6a447c3 in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0xb69caff3 in ?? () from /lib/i386-linux-gnu/libc.so.6
#3  0xb725808b in smb_panic ()
#4  0xb7247202 in ?? ()
#5  <signal handler called>
#6  0xb6a10f66 in ?? () from /lib/i386-linux-gnu/libc.so.6
#7  0xb72280ee in rep_strlcpy ()
#8  0xb72667cf in connections_fetch_entry ()
#9  0xb6ecf238 in yield_connection ()
#10 0xb6f5275c in close_cnum ()
#11 0xb6ed70f7 in conn_close_all ()
#12 0xb751db8e in ?? ()
#13 0xb751dffe in exit_server_cleanly ()
#14 0xb6f488ed in ?? ()
#15 0xb726cda7 in tevent_common_check_signal ()
#16 0xb726a0aa in run_events_poll ()
#17 0xb6f4ef33 in smbd_process ()
#18 0xb751d950 in ?? ()
#19 0xb726a3e6 in run_events_poll ()
#20 0xb726a59b in ?? ()
#21 0xb726b368 in _tevent_loop_once ()
#22 0xb6ebc7f4 in main ()
A debugging session is active.

    Inferior 1 [process 6156] will be detached.


```

Any ideas?

---

### Post by Rocket J Squirrel on 2014-04-19
Anyone?

---

