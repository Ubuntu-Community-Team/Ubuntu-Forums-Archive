---
title: "Transmission"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by stroyeror on 2010-11-05
Ubuntu 10.04

Every time i add a torrent file to transmission it crashes.  the first torrent i added was this 
[http://live.linux-gamers.net/?s=download](http://live.linux-gamers.net/?s=download) , i thought it was the torrent file so i added a torrent download from opensuse. still it crashes.  The window turns a drak color and never recovers.  Any idea what is going on?

---

### Post by Paul820 on 2010-11-05
I had loads of problems with Transmission, very slow downloads of 5Kb/s, crashing, not connecting etc. I switched to qBitorrent and my speeds went up to 380Kb/s. Lovely interface as well.

---

### Post by stroyeror on 2010-11-05
so is this a bug everyone is experiencing?

---

### Post by ibizatunes on 2010-11-05
works fine for me, 
I would do this
```
sudo rm -rf /home/YOUR USERNAME/.config/transmission/
```
then reload transmission

that will delete transmission from your home directory, and it will recreate it when you next load transmission

---

### Post by JohnHeikkila on 2010-11-05
I am not experiencing any trouble at all. First try ibizatunes' way, but if it doesn't work, then..

Check if Transmission has any updates from the Software Center, or then there is this second way to find out *why* your Transmission crashes.

Open your Terminal (console) and write the following:
```
gdb transmission
```

Then when you see the (gdb) in your terminal, type **run** and press Enter.

This should start your Transmission. Do whatever you do that crashes the program, then after the program crashes, go back to your terminal and type **bt** .

If there's just blank and no (gdb), then first press CTRL+Z.

The "bt" command in gdb will show you the backtrace of the crash. Copy this and the output of the gdb entirely here so we can take a look at the backtrace ;)

---

### Post by sadaruwan12 on 2010-11-05
Try Deluge it's very stable and it's the uTorrent of the linux world and also very fast.

---

### Post by JohnHeikkila on 2010-11-05
Geez, guys...
He's asking for help with Transmission, not to list all possible alternatives for Transmission :/

---

### Post by sadaruwan12 on 2010-11-05
> **JohnHeikkila said:**
> Geez, guys...
He's asking for help with Transmission, not to list all possible alternatives for Transmission :/

Some of us have mentioned how to rectify the problem he has and if all fails alternatives are there also so he could try them out as well if he wishes.

---

### Post by tajiknomi on 2010-11-05
[SIZE=2]*If you all has a problem with Transmission, Use ***K-get**[/SIZE]...[SIZE=2]It works well...[/SIZE]

---

### Post by dpepin on 2010-11-22
I have the same probelems, so I thought I would post my output.

GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/transmission...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/transmission 
[Thread debugging using libthread_db enabled]
[New Thread 0xb7e77b70 (LWP 1763)]
[New Thread 0xb7676b70 (LWP 1764)]
[New Thread 0xb6cffb70 (LWP 1765)]
[New Thread 0xb54d5b70 (LWP 1766)]

Program received signal SIGPIPE, Broken pipe.
[Switching to Thread 0xb7e77b70 (LWP 1763)]
0x0012d422 in __kernel_vsyscall ()
(gdb) bt
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x00733edb in write () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080b9234 in ?? ()
#3  0x080b93dd in ?? ()
#4  0x080ba98c in tr_peerIoFlush ()
#5  0x080b09e7 in ?? ()
#6  0x080b14c8 in tr_bandwidthAllocate ()
#7  0x080bbcf0 in ?? ()
#8  0x006f7274 in event_base_loop () from /usr/lib/libevent-1.4.so.2
#9  0x006f73c9 in event_loop () from /usr/lib/libevent-1.4.so.2
#10 0x006f73ee in event_dispatch () from /usr/lib/libevent-1.4.so.2
#11 0x080a7b6d in ?? ()
#12 0x080937f2 in ?? ()
#13 0x0072c96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0x00ac3a4e in clone () from /lib/tls/i686/cmov/libc.so.6

---

