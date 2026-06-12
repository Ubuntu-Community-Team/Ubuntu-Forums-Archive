---
title: "Installing Google Earth on 64 Bit Intrepid"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by cfree220 on 2009-02-04
Hi, I'm trying to install Google Earth on 64 bit Intrepid Ibex. I down;oaded the GoogleEarthLinux.bin file from google. This is what my attempt to install it looks like:

```
cfreeman@CFreeman-PC:~$ cd ~/Desktop
cfreeman@CFreeman-PC:~/Desktop$ chmod +x GoogleEarthLinux.bin
cfreeman@CFreeman-PC:~/Desktop$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
cfreeman@CFreeman-PC:~/Desktop$ 
```


I'm pretty new to Linux, so I'm not entirely sure what to make of it. There's no reason why 32 bit software shouldn't work on a 64 bit OS... Can anyone help me get this up and running?

---

### Post by RomeReactor on 2009-02-04
Hi. You need to have the [ia32-libs]("apt:ia32-libs") package installed in order to run 32 bit programs in Ubuntu 64 bit.

---

### Post by cfree220 on 2009-02-04
OK, I installed the ia32-lib packages and tried again. I got farther this time, but when I tried to launch the program, it began to start up and then crashed (Window opened up, I got a brief glimpse of the blue planet, and then the Windows burst into flames (desktop effect) as it closed itself). The terminal looked like this:

```
cfreeman@CFreeman-PC:~$ cd ~/Desktop
cfreeman@CFreeman-PC:~/Desktop$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
cfreeman@CFreeman-PC:~/Desktop$
```

---

### Post by taurus on 2009-02-04
Why don't you install the x86_64 version then?

[http://packages.medibuntu.org/pool/non-free/g/googleearth/googleearth-4.3_4.3.7284.3916-0medibuntu3_amd64.deb](http://packages.medibuntu.org/pool/non-free/g/googleearth/googleearth-4.3_4.3.7284.3916-0medibuntu3_amd64.deb)

---

### Post by cfree220 on 2009-02-04
I just tried installing from that link and got the following error in the installer:

Status: Error: Dependency is not satisfiable: googleearth-4.3-data

---

### Post by RomeReactor on 2009-02-04
Add the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu") and install GoogleEarth from Synaptic.

---

### Post by cfree220 on 2009-02-04
Ah, nevermind. Got it to work. Had to get rid of libcrypto.so.0.9.8 in ~/google-earth

---

