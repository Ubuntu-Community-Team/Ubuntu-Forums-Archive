---
title: "Network card doesn´t work (Marvell)"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by suicida on 2005-11-04
So, I try everything that i know (little) and everything that I found in Foruns, howsto, etc...

well, nothing solve my problem....

I buy a nb a few weeks ago, a Toshiba Satellite M55-S325

And when I first started and see that window, oh man, do i need to remember that??, so, when i saw that i thinked, UBUNTU!!!
So evertithing went fine, the instalattion, everything, so, I put my login name and passwd and was thinking, wow cool, now i just need connect to the hub and then no one can stop me, internet i´m coming....and nothing happens, the system doesn´t recognize the netcard....then i think, no problem i´ll load the module...

so, let´s go....

lspci and:
Marvell Technology Group Ltd.: Unknow device 4351 (rev 10)

hmm, this isn´t good...

lsmod and:
sk98lin 149216 0

hmm, strange...the module is loaded..

ifconfig and:
nothing

ifconfig -a:
just the wlan "already detected" and nothing more about the Marvell

so i try to put a line at the /etc/modules
so i try write ifconfig eth1 192.168.0.32 netmask 255.255.255.0 up
so i try to put a line athe the /etc/modules.conf alias eth1 sk98lin (this i do in another distro - Kurumin Linux)

ow, i tryed to put a line at the grub noacpi
kernel /boot/vmlinuz-2.6.10-5-386 root/dev/sda2 ro quiet splash noacpi

i tried acpi=off but that freezes the Ubuntu...

So, i don´t know what can i do...

ow i was forgeting...i downloaded the driver from the internet ( in another pc  :( )

and tar -jxfv install-8_28.tar.bz2
cd DriverInstall (something like this)
and sudo ./install.sh

and...and....FAILED (sorry the caps)
with the frase...
There is a version mismatch between the compiler that was used to build the current running kernel and the compiler wich you intend to compile the kernel module with. In most of the cases, this is no problem, but there are cases in which this compiler-mismatch leads to unexpected system crashes

If you know what you are doing and want to override this check, you can do so by setting IGNORE_CC_MISMATCH system variable:
Example: export IGNORE_CC_MISMATCH=1

well i come thru here and now almost all my hope is gone....
so, if someone know how to solve my problem, please, let me know....

[]´s

P.S. Sorry my terrible english...

---

