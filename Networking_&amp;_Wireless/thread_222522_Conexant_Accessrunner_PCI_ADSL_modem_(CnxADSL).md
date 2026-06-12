---
title: "Conexant Accessrunner PCI ADSL modem (CnxADSL)"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by dontunderstand on 2006-07-25
Is there anyone who has this thing working?

Need to compile a kernel module for Ubuntu 6.06 Dapper Drake.

make errors: warning: "DBG" is not defined, invalid preprocessing directive #warn

Help me please to get it working, maybe i try to write a step-by-step how-to then. i'm pretty noobish you have to know.

look at:
[LIST]
[*][http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html]("http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html")
[*][http://ubuntuforums.org/showthread.php?t=1906]("http://ubuntuforums.org/showthread.php?t=1906")
[*][http://compsoc.tardis.ed.ac.uk/DebianConexant]("http://compsoc.tardis.ed.ac.uk/DebianConexant")
[/LIST]


Step1:
download driver source from: [http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html]("http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html")
(CnxADSL-6.1.2.007-PIM-2.6-1.4)

Step2:
install package from Synaptic:
linux-headers
(linux-headers-2.6.15-26-386)

Step3:
install package from Synaptic:
build-essential

Step4:
in terminal create a symlink to linux headers for the driver :
[FONT="Fixedsys"]```
ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/src/linux
```[/FONT]

Step5:
unpack the downloaded driver source and go to the unpacked folder in terminal.

[FONT="Fixedsys"]```
cd /somefolder/CnxADSL-6.1.2.007-PIM-2.6-1.4
```[/FONT]

Step6:
make
[FONT="Fixedsys"]```
sudo make
```[/FONT]

(or open terminal in terminal with [FONT="Fixedsys"]sudo gnome-terminal[/FONT] to be sudo all the time?)

-------------------------------------------------
MY PROBLEM:
-----------------------------
make gives out:

```
root@jan-desktop:/root/CnxADSL-6.1.2.007-PIM-2.6-1.4# make
for n in KernelModule/DpController; \
                do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make -C /usr/src/linux SUBDIRS=`pwd` modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o
In file included from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CardMgmt.h:50,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CnxADSL.h:41,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:42:
/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/UtilDbg.h:40:5: warning: "DBG" is not defined
In file included from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ChipALCdsl.h:37,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CardMgmt.h:369,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CnxADSL.h:41,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:42:
/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/Version.h:88:2: invalid preprocessing directive #warn
In file included from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ChipALCdsl.h:734,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CardMgmt.h:369,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/CnxADSL.h:41,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:42:
/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ChipALIoP46.h:620:5: warning: "DBG" is not defined
In file included from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ChipALCdslV.h:18,
                 from /root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.c:45:
/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ChipALSEmw.h:128:5: warning: "DBG" is not defined
make[4]: *** [/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule/ARMAbstract.o] Error 1
make[3]: *** [_module_/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[2]: *** [CnxADSL.ko] Error 2
make[2]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/CnxADSL-6.1.2.007-PIM-2.6-1.4/KernelModule'
make: *** [all] Error 2
```
------

so what is this "DBG not defined" thing is it something one needs to change in the driver source or in the kernel conf or something still not installed for building things or what???


oh and do i have to have the modem plugged in to my pc at the time im compiling the module?? problem is it serves internet in another computer at   the moment so i can read how-to's. 


---------------------------------------------------------------------
maybe i have to install gcc-3.3 and ln -sf /usr/bin/gcc-3.3 /usr/bin/gcc, nope seems not to help. oh and tell me please about difference ln -s and ln -sf.

---

### Post by mips on 2006-07-25
Do a search here for **Conexant Accessrunner** as there are other post with the same topic that might help you.

---

### Post by gnomeza on 2006-11-08
> **dontunderstand said:**
> Make errors: warning: "DBG" is not defined, invalid preprocessing directive #warn

I'll have a bash at compiling the driver with 6.06 this weekend.

> **dontunderstand said:**
> 
(or open terminal in terminal with [FONT="Fixedsys"]sudo gnome-terminal[/FONT] to be sudo all the time?)

Yes. If you feel confident enough not to accidentally kill your system. I never work as root except on test systems.
 
> **dontunderstand said:**
> 
so what is this "DBG not defined" thing is it something one needs to change in the driver source or in the kernel conf or something still not installed for building things or what???
Probably the linux-headers have changed a bit. I'll know when I take a look at the code.

> **dontunderstand said:**
> 
oh and do i have to have the modem plugged in to my pc at the time im compiling the module?? problem is it serves internet in another computer at   the moment so i can read how-to's. 

No. You only need the modem when you load the module. i.e. to test it.

> **dontunderstand said:**
> 
oh and tell me please about difference ln -s and ln -sf.
```
man ln
```

---

### Post by tin_truc22 on 2006-11-11
You must go to this Project
[http://sourceforge.net/projects/accessrunner/](http://sourceforge.net/projects/accessrunner/)

---

### Post by gnomeza on 2006-11-20
Nope, still haven't tried compiling on 6.06. Still need to find time to finish updating the test machine.

---

