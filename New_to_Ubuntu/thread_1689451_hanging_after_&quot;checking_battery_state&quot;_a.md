---
title: "hanging after &quot;checking battery state&quot; after installing several libraries"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by mario123 on 2011-02-16
Hi, my computer is hanging after "checking battery state" after installing several libraries

I am using ubuntu server 10.10

I can log on to the machine via ssh and web interface

I can not login to gde desktop via console anymore..

I think the problem is:
libpixman-1.so.0 => /usr/local/lib/libpixman-1.so.0 (0xb76da000)

It should be pointing towards /usr/lib ---- if i am not wrong ???

this problem also occurred after I installed this library.


mario@host:/usr/lib$ ldd /usr/bin/Xorg
        linux-gate.so.1 =>  (0xb77bc000)
        libudev.so.0 => /lib/libudev.so.0 (0xb779f000)
        libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb772b000)
        libdl.so.2 => /lib/libdl.so.2 (0xb7726000)
        libpciaccess.so.0 => /usr/lib/libpciaccess.so.0 (0xb771d000)
        libpthread.so.0 => /lib/libpthread.so.0 (0xb7703000)
        libpixman-1.so.0 => /usr/local/lib/libpixman-1.so.0 (0xb76da000)
        libXfont.so.1 => /usr/lib/libXfont.so.1 (0xb76a1000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb769d000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7696000)
        libm.so.6 => /lib/libm.so.6 (0xb7670000)
        librt.so.1 => /lib/librt.so.1 (0xb7667000)
        libc.so.6 => /lib/libc.so.6 (0xb750a000)
        libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb7505000)
        /lib/ld-linux.so.2 (0xb77bd000)
        libz.so.1 => /lib/libz.so.1 (0xb74ef000)
        libfreetype.so.6 => /usr/local/lib/libfreetype.so.6 (0xb747f000)
        libbz2.so.1.0 => /lib/libbz2.so.1.0 (0xb746d000)
        libfontenc.so.1 => /usr/lib/libfontenc.so.1 (0xb7466000)
mario@host:/usr/lib$ 


I also get an error when I try to run startx
--------------------------------------------------

mario@host:~/pixman-0.10.0$ sudo startx
xauth:  error in locking authority file /home/mario/.Xauthority
xauth:  error in locking authority file /home/mario/.Xauthority

/usr/bin/X: symbol lookup error: /usr/bin/X: undefined symbol: pixman_disable_out_of_bounds_workaround

giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /home/mario/.Xauthority
mario@host:~/pixman-0.10.0$ 

Please help asap :)
Cheers, Mario

---

### Post by mario123 on 2011-02-16
**hanging after "checking battery state" after installing several libraries** 			
 			 			 		   		 		 		Hi, my computer is hanging after "checking battery state" after installing several libraries

I am using ubuntu server 10.10

I can log on to the machine via ssh and web interface

I can not login to gde desktop via console anymore..

I think the problem is:
libpixman-1.so.0 => /usr/local/lib/libpixman-1.so.0 (0xb76da000)

It should be pointing towards /usr/lib ---- if i am not wrong ???

this problem also occurred after I installed this library.


mario@host:/usr/lib$ ldd /usr/bin/Xorg
        linux-gate.so.1 =>  (0xb77bc000)
        libudev.so.0 => /lib/libudev.so.0 (0xb779f000)
        libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb772b000)
        libdl.so.2 => /lib/libdl.so.2 (0xb7726000)
        libpciaccess.so.0 => /usr/lib/libpciaccess.so.0 (0xb771d000)
        libpthread.so.0 => /lib/libpthread.so.0 (0xb7703000)
        libpixman-1.so.0 => /usr/local/lib/libpixman-1.so.0 (0xb76da000)
        libXfont.so.1 => /usr/lib/libXfont.so.1 (0xb76a1000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb769d000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7696000)
        libm.so.6 => /lib/libm.so.6 (0xb7670000)
        librt.so.1 => /lib/librt.so.1 (0xb7667000)
        libc.so.6 => /lib/libc.so.6 (0xb750a000)
        libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb7505000)
        /lib/ld-linux.so.2 (0xb77bd000)
        libz.so.1 => /lib/libz.so.1 (0xb74ef000)
        libfreetype.so.6 => /usr/local/lib/libfreetype.so.6 (0xb747f000)
        libbz2.so.1.0 => /lib/libbz2.so.1.0 (0xb746d000)
        libfontenc.so.1 => /usr/lib/libfontenc.so.1 (0xb7466000)
mario@host:/usr/lib$ 


I also get an error when I try to run startx
--------------------------------------------------

mario@host:~/pixman-0.10.0$ sudo startx
xauth:  error in locking authority file /home/mario/.Xauthority
xauth:  error in locking authority file /home/mario/.Xauthority

/usr/bin/X: symbol lookup error: /usr/bin/X: undefined symbol: pixman_disable_out_of_bounds_workaround

giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /home/mario/.Xauthority
mario@host:~/pixman-0.10.0$ 

Please help asap :smile:
Cheers, Mario

---

### Post by overdrank on 2011-02-16
Hi and welcome, Please do not create multiple threads on the same issue. Threads merged. :)

---

