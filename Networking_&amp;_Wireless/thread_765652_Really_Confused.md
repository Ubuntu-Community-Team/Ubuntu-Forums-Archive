---
title: "Really Confused"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Echoman on 2008-04-24
I recently installed ubuntu 7.10 on an old desktop of mine and i cant get a dial up connection to work. I have tried to find information on here but all the technical talk is confusing me. However i did install ScanModem and this is what i have
CPU=i686,
Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007
scanModem update of: 2008_04_16

There are no blacklisted modem drivers in /etc/modprobe* files
USB modem not detected by lsusb

For candidate card in slot 01:0b.0, firmware information and bootup diagnostics are:
PCI slot PCI ID SubsystemID Name
---------- --------- --------- --------------
01:0b.0 11c1:044e 1235:044e Communication controller: Agere Systems LT WinModem

Modem interrupt assignment and sharing:
===================================
The modem interrupt (IRQ) is 255 . IRQs of 0 or 255 are not functional!!
The CPU cannot control the modem until this situation is corrected!!
Possible corrections are:
1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
Instructions for accessing BIOS are at:
[http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within: Additional Resourcces.
2a) Add an option "pci=routeirq" to the kernel boot up line.
Here is an example paragraph from /boot/grub/menu.lst :
title Ubuntu, kernel 2.6.15-26-686
root (hd0,6)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
initrd /boot/initrd.img-2.6.15-26-686
savedefault
2b) Same as above, but use "pollirq" instead of "pci=routeirq".
3) Within some BIOS setups, IRQ assignments can be changed.
4) On non-laptop systems, moving the modem card to another slot has helped.
5) Sometimes upgrading the kernel changes IRQ assignment.
=====================================

--- Bootup diagnostics for card in PCI slot 01:0b.0 ----

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 01:0b.0:
Modem chipset detected on
CLASS="Class 0780: 11c1:044e"
NAME="Communication controller: Agere Systems LT WinModem "
PCIDEV=11c1:044e
SUBSYS=1235:044e
IRQ=255
IDENT=Agere.DSP

For candidate modem in: 01:0b.0
Class 0780: 11c1:044e Communication controller: Agere Systems LT WinModem
Primary PCI_id 11c1:044e
Support type needed or chipset: Agere.DSP


----------------end Softmodem section --------------

The modem has a Lucent/Agere/LSI Mars or Apollo DSP (digital signal processing) chipset.
Support packages for 2.6.n kernels are at:
[http://linmodems.technion.ac.il/pack...l-2.6/martian/](http://linmodems.technion.ac.il/pack...l-2.6/martian/) , with current update martian-full-20071011.tar.gz

See AgereDSP.txt for Details.


Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc.
Their Linux code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its
continued maintenance is only initiated at the request of a major chipset buyer,
or comparable sponsor. Several different modem chipset types are produced:
with varying support under Linux.
Device ID Support Name Comment
--------- ------------- ----------- -----------------------------
0480 serial drivers Venus controller chipset 1673JV7
0440-045d martian Mars/Apollo DSP (digital signal processing) chipsets
0462 none 56K.V90/ADSL Wildwire
048d none SV2P soft modem
048(c or f) AGRSM SV2P soft modem
0600 none soft modem, very few in the field.
0620 AGRSM Pinball soft modem, in some HP desktop PCs
062(1-3) none SV92PP,Pinball soft modem, in some HP desktop PCs

martian - At [http://linmodems.technion.ac.il/pack...l-2.6/martian/](http://linmodems.technion.ac.il/pack...l-2.6/martian/)

AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/)
The suse-10-2a.tar.gz has newer Agere/LSI code, but there are compiling problems with newer kernels/

0x044e -- Mars 3 Mercury data fax only
-------------- end Agere Systems section -------------------

Completed candidate modem analyses.

The base of the UDEV device file system is: /dev/.udev

Versions adequately match for the compiler installed: 4.1.3
and the compiler used in kernel assembly: 4.1.3



Minimal compiling resources appear complete:
make utility - /usr/bin/make
Compiler version 4.1
linuc_headers base folder /lib/modules/2.6.22-14-generic/build

However some compilations and executable functions may need additional files,
in the FileNames.h (so called kernel "h"eaders) collection installed in /usr/include/ .
For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu, linux-libc-dev). The also required headers of package libc6 are commonly installed by default.



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$ apt-get update
$ apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
-rwsr-xr-- 1 root dip 269256 2007-10-04 15:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
[http://linmodems.technion.ac.il/linm.../msg02637.html](http://linmodems.technion.ac.il/linm.../msg02637.html)

To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
sudo chmod a+x /usr/sbin/pppd

Checking settings of: /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/biga.../msg04656.html](http://linmodems.technion.ac.il/biga.../msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

Don't worry about the following, it is for the experts
should trouble shooting be necessary.

I dont understand any of this can someone give me a step by step of what to do next please?

---

### Post by Echoman on 2008-04-25
ok someone here must be smart enough to tell me what to do. I have looked through every "how to connect dial up" guide on here and have had no luck. Im starting to regret removing windows from this system because i had no idea you need a degree in computer programming just to get crappy dial up to work.

---

### Post by coolcat on 2008-04-25
Hi,
Sorry that no one has answered you yet but I will try giving you some links to help.

[http://www.faqs.org/docs/Linux-HOWTO/Winmodems-and-Linux-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Winmodems-and-Linux-HOWTO.html")

and

[http://www.sfu.ca/~cth/ltmodem/dists/debian/]("http://www.sfu.ca/~cth/ltmodem/dists/debian/")

And this one which should be of much help;

[http://phep2.technion.ac.il/linmodems/]("http://phep2.technion.ac.il/linmodems/")

I don't have or use a dial up modem so I can't test these for you.

The biggest problem with dial up modems is that most, like yours are made for use in Windows. That is why they are called winmodems.
The hardware is configured to use the Windows software instead of adding the needed components to the modem. This was the manufacturer's way of keeping prices down.

There are modems that contain the needed components so they can be used in Linux but they are far and few between and do cost quite a bit more then your standard winmodem.

Good luck and hopefully the above links will work for you.
And please post back here with your progress so that it may be used in the future for other users.

Thank you,

Cool Cat

---

### Post by Echoman on 2008-04-25
i still cant figure it out. can someone give me a suggestion of an external modem that i can plug in and it will work.

---

