---
title: "wlu11a compex usb wireless card adapter"
date: 2005-07-04
forum: Networking &amp; Wireless
---

### Post by borys on 2005-07-04
Pleasssseee pals! im a newbie in linux... im just starting.. but i just cant get out with the install of this usb wirless lan adapter, i've downloaded the driver called atmelwlandriver_RFMD.tar.gz, i've already extracted it and followed all the instructions, when i run ./install gives me a few errors... this is what happens when i run ./install

Build all=N -start
Build all -end
Beginning to input pre-defined variables... ...
End of input... ...
X Windows include files missing
Kernel Version Running 2.6.10-5-386
Found Kernel Source Directory ()
End of Make Config process... ...
Finished. Now run make clean, all, install
find . -name '*.o' -o -name '*.map' |xargs rm -f
Building src/usb
make[1]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
for i in  rfmd; do make $i || exit 1; done
make[2]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
make final CFLAGS:='-D__KERNEL__ -O3 -fno-strict-aliasing -fomit-frame-pointer -pipe         -I/include -I/home/borys/temp/atmelwlandriver/src/includes -I/home/borys/temp/atmelwlandriver/src/includes/usb -Wall  -DRFMD' MODULE:='usbvnetr.o'
make[3]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
gcc -D__KERNEL__ -O3 -fno-strict-aliasing -fomit-frame-pointer -pipe         -I/include -I/home/borys/temp/atmelwlandriver/src/includes -I/home/borys/temp/atmelwlandriver/src/includes/usb -Wall  -DRFMD   -c -o callbacks.o callbacks.c
make[3]: gcc: Command not found
make[3]: *** [callbacks.o] Error 127
make[3]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make[2]: *** [rfmd] Error 2
make[2]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make: *** [all] Error 1


the same thing happens when i run ./install2 , this is what happens:

Begin make install process ... ...
set -x
grep: /etc/pcmcia/wireless.opts: No such file or directory
install: cannot create regular file `/etc/pcmcia/': Is a directory
depmod -aq
OK
End of make install process... ...

please help me!! im crazy with this!!! and i deeply hate the dark side of the force (refering to Wastedows!) all i want is having my OS!!!!!!!

---

### Post by darrell on 2005-07-05
looks like you've not got a compiler...

try

```
sudo apt-get install build-essential
```

this should install most of what you need. Try the install/make again - it may still complain if there are other necessary packages not installed on your system, but you should be able to work out from the error messages what you're missing.

Welcome to open source - it can be a bit painful to start with, but stick with it, you'll be flying in no time.

---

### Post by borys on 2005-07-05
[QUOTE=darrell]looks like you've not got a compiler...

try

```
sudo apt-get install build-essential
```

this should install most of what you need. Try the install/make again - it may still complain if there are other necessary packages not installed on your system, but you should be able to work out from the error messages what you're missing.

Welcome to open source - it can be a bit painful to start with, but stick with it, you'll be flying in no time.[/QUOTE]


first i wanna thank you cause you're trying to help.. but after i did what you said it still giving me those errors...  I DONT KNOW What TO DO!!! I WANT MY wierless usb adapter working!!!! Please help...

---

### Post by darrell on 2005-07-06
the same errors? you still get "gcc: command not found"? Or are the errors slightly different? post your output.

---

### Post by borys on 2005-07-06
ok.. first of all i want to thank you again for answering me.. i copyied all the errors.. please i need your help..


when i run:
sudo apt-get install build-essential

root@borys:/home/borys/temp/atmelwlandriver # sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

until there is all Ok...

then i run...make config

root@borys:/home/borys/temp/atmelwlandriver # make config
Build all=N -start
Build all -end
Beginning to input pre-defined variables... ...
End of input... ...
X Windows include files missing
Kernel Version Running 2.6.10-5-386
Found Kernel Source Directory ()
End of Make Config process... ...
Finished. Now run make clean, all, install

then i run make clean..

root@borys:/home/borys/temp/atmelwlandriver # make clean
find . -name '*.o' -o -name '*.map' |xargs rm -f

then i run make all...

root@borys:/home/borys/temp/atmelwlandriver # make all
Building src/usb
make[1]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
for i in  rfmd; do make $i || exit 1; done
make[2]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
make final CFLAGS:='-D__KERNEL__ -O3 -fno-strict-aliasing -fomit-frame-pointer -pipe         -I/include -I/home/borys/temp/atmelwlandriver/src/includes -I/home/borys/temp/atmelwlandriver/src/includes/usb -Wall  -DRFMD' MODULE:='usbvnetr.o'
make[3]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
gcc -D__KERNEL__ -O3 -fno-strict-aliasing -fomit-frame-pointer -pipe         -I/include -I/home/borys/temp/atmelwlandriver/src/includes -I/home/borys/temp/atmelwlandriver/src/includes/usb -Wall  -DRFMD   -c -o callbacks.o callbacks.c
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/netdevice.h:489,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:28,
                 from callbacks.c:22:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/netdevice.h:489,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:28,
                 from callbacks.c:22:
/usr/include/linux/irq.h:70: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/include/linux/irq.h:72,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/netdevice.h:489,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:28,
                 from callbacks.c:22:
/usr/include/asm/hw_irq.h:28: error: `NR_IRQS' undeclared here (not in a function)
/usr/include/asm/hw_irq.h:31: error: `NR_IRQS' undeclared here (not in a function)
In file included from callbacks.c:22:
/home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:91:1: warning: "ALIGN" redefined
In file included from /usr/include/asm/system.h:5,
                 from /usr/include/asm/processor.h:18,
                 from /usr/include/asm/thread_info.h:13,
                 from /usr/include/linux/thread_info.h:21,
                 from /usr/include/linux/spinlock.h:19,
                 from /usr/include/linux/capability.h:45,
                 from /usr/include/linux/sched.h:7,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/linux/kernel.h:28:1: warning: this is the location of the previous definition
callbacks.c: In function `GetCmd_callback':
callbacks.c:71: error: `USB_ST_NOERROR' undeclared (first use in this function)
callbacks.c:71: error: (Each undeclared identifier is reported only once
callbacks.c:71: error: for each function it appears in.)
callbacks.c:73: error: `USB_ST_STALL' undeclared (first use in this function)
callbacks.c:74: error: `USB_ST_TIMEOUT' undeclared (first use in this function)
callbacks.c: In function `ctrl_callback':
callbacks.c:348: error: `USB_ST_NOERROR' undeclared (first use in this function)
callbacks.c:350: error: `USB_ST_STALL' undeclared (first use in this function)
callbacks.c:355: error: `USB_ST_TIMEOUT' undeclared (first use in this function)
callbacks.c: In function `RxCallback':
callbacks.c:808: warning: implicit declaration of function `FILL_BULK_URB'
callbacks.c:814: error: too few arguments to function `usb_submit_urb'
make[3]: *** [callbacks.o] Error 1
make[3]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make[2]: *** [rfmd] Error 2
make[2]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make: *** [all] Error 1


then i run make install..

root@borys:/home/borys/temp/atmelwlandriver # make install
set -x
grep: /etc/pcmcia/wireless.opts: No such file or directory
install: cannot create regular file `/etc/pcmcia/': Is a directory
depmod -aq
OK

then i run make realclean...

root@borys:/home/borys/temp/atmelwlandriver # make realclean
find . -name '*.o' -o -name '*.map' |xargs rm -f
rm -f .config
Now run make config

then i run make config..

root@borys:/home/borys/temp/atmelwlandriver # make config
Build all=N -start
Build all -end
Beginning to input pre-defined variables... ...
End of input... ...
X Windows include files missing
Kernel Version Running 2.6.10-5-386
Found Kernel Source Directory ()
End of Make Config process... ...
Finished. Now run make clean, all, install

then i run make clean...

root@borys:/home/borys/temp/atmelwlandriver # make clean
find . -name '*.o' -o -name '*.map' |xargs rm -f

then i run make all...

root@borys:/home/borys/temp/atmelwlandriver # make all
Building src/usb
make[1]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
for i in  rfmd; do make $i || exit 1; done
make[2]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
make final CFLAGS:='-D__KERNEL__ -O3 -fno-strict-aliasing -fomit-frame-pointer -pipe         -I/include -I/home/borys/temp/atmelwlandriver/src/includes -I/home/borys/temp/atmelwlandriver/src/includes/usb -Wall  -DRFMD' MODULE:='usbvnetr.o'
make[3]: Entering directory `/home/borys/temp/atmelwlandriver/src/usb'
gcc -D__KERNEL__ -O3 -fno-strict-aliasing -fomit-frame-pointer -pipe         -I/include -I/home/borys/temp/atmelwlandriver/src/includes -I/home/borys/temp/atmelwlandriver/src/includes/usb -Wall  -DRFMD   -c -o callbacks.o callbacks.c
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/netdevice.h:489,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:28,
                 from callbacks.c:22:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/netdevice.h:489,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:28,
                 from callbacks.c:22:
/usr/include/linux/irq.h:70: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/include/linux/irq.h:72,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from /usr/include/linux/netdevice.h:489,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:28,
                 from callbacks.c:22:
/usr/include/asm/hw_irq.h:28: error: `NR_IRQS' undeclared here (not in a function)
/usr/include/asm/hw_irq.h:31: error: `NR_IRQS' undeclared here (not in a function)
In file included from callbacks.c:22:
/home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:91:1: warning: "ALIGN" redefined
In file included from /usr/include/asm/system.h:5,
                 from /usr/include/asm/processor.h:18,
                 from /usr/include/asm/thread_info.h:13,
                 from /usr/include/linux/thread_info.h:21,
                 from /usr/include/linux/spinlock.h:19,
                 from /usr/include/linux/capability.h:45,
                 from /usr/include/linux/sched.h:7,
                 from /home/borys/temp/atmelwlandriver/src/includes/usb/vnetusba.h:24,
                 from callbacks.c:22:
/usr/include/linux/kernel.h:28:1: warning: this is the location of the previous definition
callbacks.c: In function `GetCmd_callback':
callbacks.c:71: error: `USB_ST_NOERROR' undeclared (first use in this function)
callbacks.c:71: error: (Each undeclared identifier is reported only once
callbacks.c:71: error: for each function it appears in.)
callbacks.c:73: error: `USB_ST_STALL' undeclared (first use in this function)
callbacks.c:74: error: `USB_ST_TIMEOUT' undeclared (first use in this function)
callbacks.c: In function `ctrl_callback':
callbacks.c:348: error: `USB_ST_NOERROR' undeclared (first use in this function)
callbacks.c:350: error: `USB_ST_STALL' undeclared (first use in this function)
callbacks.c:355: error: `USB_ST_TIMEOUT' undeclared (first use in this function)
callbacks.c: In function `RxCallback':
callbacks.c:808: warning: implicit declaration of function `FILL_BULK_URB'
callbacks.c:814: error: too few arguments to function `usb_submit_urb'
make[3]: *** [callbacks.o] Error 1
make[3]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make[2]: *** [rfmd] Error 2
make[2]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/borys/temp/atmelwlandriver/src/usb'
make: *** [all] Error 1

then i run make install...

root@borys:/home/borys/temp/atmelwlandriver # make install
set -x
grep: /etc/pcmcia/wireless.opts: No such file or directory
install: cannot create regular file `/etc/pcmcia/': Is a directory
depmod -aq
OK

And thats all, i did a lot of thing without any sense, cause i had errors before.. i know.. but i only want to show you this errors to have your help! PLEASE help ME!

---

### Post by az on 2005-07-06
I think your driver source is looking for pcmcia headers.  Also, do you have the linux-headers package installed?


Anyway, I have had success with this type of device with the alternate drivers from berlios:
[http://at76c503a.berlios.de/](http://at76c503a.berlios.de/)

Look here and try the package I made.  It *may* work for you...

[http://ubuntuforums.org/showthread.php?t=44324&highlight=usb](http://ubuntuforums.org/showthread.php?t=44324&highlight=usb)

---

