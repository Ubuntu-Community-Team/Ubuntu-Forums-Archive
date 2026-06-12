---
title: "Anybody able to compile and use the latest wireless tools package??"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-09-08
Recently installed vanilla kernel 2.6.22.6.  
With the wireless tools utilities like iwlist scan, I keep getting the following message:

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

The tools do work.  Im assuming by this message they mean the wireless tools package supports up to 2.6.20.x kernels rather than 2.6.22 version kernels.

Anyway I downloaded and tried to compile/install/execute the latest alpha and beta wireless tools package:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html#latest](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html#latest)
I was able to compile and install them, however both sets dont really work.  

With regular iwlist:
iwlist --version
iwlist    Wireless-Tools version 28
          Compatible with Wireless Extension v11 to v20.

Kernel    Currently compiled with Wireless Extension v22.

wlan0     Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v22.

kevin@Homer:/usr/local/sbin$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:17:D9:68
                    ESSID:"Dorchester"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

With newly compiled version
kevin@Homer:/usr/local/sbin$ ./iwlist --version
iwlist    Wireless-Tools version 28
          Compatible with Wireless Extension v11 to v20.

Kernel    Currently compiled with Wireless Extension v22.

*** glibc detected *** ./iwlist: free(): invalid next size (fast): 0x080531c8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e727cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e75e30]
./iwlist[0x804e13f]
./iwlist[0x804c444]
./iwlist[0x804d8b9]
./iwlist[0x804da7e]
./iwlist[0x804a610]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7e20ebc]
./iwlist[0x8049041]
======= Memory map: ========
08048000-08052000 r-xp 00000000 03:02 1161317    /usr/local/sbin/iwlist
08052000-08053000 rw-p 00009000 03:02 1161317    /usr/local/sbin/iwlist
08053000-08074000 rw-p 08053000 00:00 0          [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7e0a000-b7e0b000 rw-p b7e0a000 00:00 0 
b7e0b000-b7f46000 r-xp 00000000 03:02 1844637    /lib/tls/i686/cmov/libc-2.5.so
b7f46000-b7f47000 r--p 0013b000 03:02 1844637    /lib/tls/i686/cmov/libc-2.5.so
b7f47000-b7f49000 rw-p 0013c000 03:02 1844637    /lib/tls/i686/cmov/libc-2.5.so
b7f49000-b7f4c000 rw-p b7f49000 00:00 0 
b7f4c000-b7f71000 r-xp 00000000 03:02 1844641    /lib/tls/i686/cmov/libm-2.5.so
b7f71000-b7f73000 rw-p 00024000 03:02 1844641    /lib/tls/i686/cmov/libm-2.5.so
b7f73000-b7f74000 rw-p b7f73000 00:00 0 
b7f87000-b7f92000 r-xp 00000000 03:02 1844666    /lib/libgcc_s.so.1
b7f92000-b7f93000 rw-p 0000a000 03:02 1844666    /lib/libgcc_s.so.1
b7f93000-b7f96000 rw-p b7f93000 00:00 0 
b7f96000-b7faf000 r-xp 00000000 03:02 1844610    /lib/ld-2.5.so
b7faf000-b7fb1000 rw-p 00019000 03:02 1844610    /lib/ld-2.5.so
bff79000-bff8f000 rw-p bff79000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted

kevin@Homer:/usr/local/sbin$ ./iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Interface doesn't support scanning.


Anyone been able to compile and execute the alpha or beta version??

---

### Post by kevdog on 2007-09-12
Bump

---

