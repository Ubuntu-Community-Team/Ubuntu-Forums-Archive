---
title: "Ndiswrapper from Src - Version magic?"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by incunabulum on 2005-08-09
Hi there,

on my laptop the ndiswrapper package shipped with ndiswrapper does works unstable from time to time I tried to install the new ndiswrapper 1.2 from source.

What I did was as follows (the quick rundown):
- remove old package and configuration
- install kernel headers
- compile ndiswrapper, make debs, install packages
- install the wireless driver with ndiswrapper -i

Ndiswrapper by default creates the kernel module in the wrong place, so I copied  ndiswrapper.ko to lib/modules/2.6.10-5-386/kernel/net/drivers/ndiswrapper

What does **not** work is:
[INDENT]modprobe ndiswrapper[/INDENT]

This gives 
[INDENT]*FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted *[/INDENT]

Dmesg reports:[INDENT]
[I]ndiswrapper: no version for "struct_module" found: kernel tainted.
ndiswrapper: version magic '2.6.10-5 SMP preempt PENTIUM4 4KSTACKS gcc-3.3' should be '2.6.10-5-386 preempt 386 gcc-3.3'
ndiswrapper: no version magic, tainting kernel.
ndiswrapper: Unknown symbol __per_cpu_offset
ndiswrapper: Unknown symbol del_timer_sync [/I][/INDENT]

I do use the default Ubuntu kernel. 

Does anyone know what is the reason for my problem? I do not want to recompile the kernel and disable the 4kStacks limit there.

So, what is the best way to proceed?

Thanks!

Michael

---

### Post by ilbahr on 2005-08-09
just wondering if you got the right kernel headers
try this apt-get linux-headers-$(uname -r)

to get the proper kernel headers then look at this page for installation
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)

did you make an alias for the ndiswrapper
sudo ndiswrapper -m

then sudo modprobe ndiswrapper

hope this help

to check your linux kernel ver type
$uname -r

---

### Post by az on 2005-08-09
You must also remove any other INF file installation that you previously did.  That can also cause the module to refuse to load.

sudo ndiswrapper -e (driver)

---

