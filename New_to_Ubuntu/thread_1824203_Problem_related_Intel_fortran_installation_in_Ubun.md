---
title: "Problem related Intel fortran installation in Ubuntu 11.04 64bit"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by sukantamech on 2011-08-13
i have just installed intel composer xe 2011.5.220 in Ubuntu-64 bit-11.04
after installation i have given the following command...but it is showing some error...please help me...!!!


s[COLOR=Blue]ukanta@Energy:~$ sudo /opt/intel/composerxe-2011.5.220/bin/compilervars.sh intel64
[sudo] password for sukanta: 
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator

ERROR: Unknown option 'intel64'

Syntax:
  /opt/intel/composerxe-2011.5.220/bin/compilervars.sh <arch> [MKL_interface] [mod]

   <arch> must be one of the following
       ia32         : Set up for IA-32 target
       intel64      : Set up for Intel(R) 64 target
       mic          : Set up for Intel(R) MIC target

   mod (optional) - set path to MKL F95 modules

   MKL_interface (optional) - MKL programming interface for intel64
                              Not applicable without mod
       lp64         : 4 bytes integer (default)
       ilp64        : 8 bytes integer

sukanta@Energy:~$ 
[/COLOR]

---

### Post by sukantamech on 2011-08-13
[COLOR=Purple]
[/COLOR]   [COLOR=Red]I am using 64bit ubuntu 11.04 destop, 500gb hdd, 4gb ram, i3 processor.[/COLOR]

---

### Post by Mark Phelps on 2011-08-14
You could try using "sudo bash ...".  Should not be necessary to include "bash" -- but I've seen this work at times.

---

### Post by lrsantos11 on 2011-08-22
You have to use the following:
```
source /opt/intel/composerxe/bin/compilervars.sh intel64 
```

You'll always use ```
source
``` to link either the MKL or even to invoke icc, icpc or ifort.

You can add the line above to the end of your .bashrc file (wich is located on your home directory).

---

### Post by ptaylor1951 on 2011-08-29
Hi

I am a new UBUNTU user attempting to use INTEL FORTRAN because Compaq Fortran 6.6 no longer works under Windows 7.
I followed the installation without seemingly any problems.
However, I cannot get executables to run.

I have followed the Intel Fortran Compiler User and Reference Guides and compiled the sample programs on P111. However, when I type in 'calc' as instructed under "Running the Sample program", I get a message "program 'calc' is currently not installed. You can install it by typing: sudo apt-get install apcalc"
The link at step 4 has created something called 'calc' because I can see it in the current folder, so why does UBUNTU not recognise this as an executable as the User Guide states?

---

