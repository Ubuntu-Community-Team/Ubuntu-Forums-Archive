---
title: "&quot;Motorolla modem - can't install driver&quot;"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by rose_flower23kish on 2008-02-25
Dear members , please hellllp me
I installed ubuntu 7.10 long time ago bout I could not installed modem driver . my system is i686 and the modem is motorola 
I used scanmodem and found that I sould use conexant driver for my modem . the result of scanmodem :```
Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,


 as HTML can contain viruses. Use as the email Subject Line:

           YourName, YourCountry  kernel 2.6.22-14-generic 

 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.

 YourCountry will enable Country specific guidance. Your contry's local Linux experts

 can be found through: http://www.linux.org/groups/index.html. 

They will know your Country's modem code, which may be essential for dialup service.

Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.

 So in a day, also check the Archived responses at http://www.linmodems.org 

--------------------------  System information ----------------------------

CPU=i686,  

Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007

 scanModem update of:  2008_01_22





 There are no blacklisted modem drivers in /etc/modprobe*  files 

 PCI slot 00:1b.0 has a High Definition Audio Card



The Advanced Linux Sound Architecture (ALSA) packages providing audio support, 

also includes drivers for some modems. The ALSA diagnostics are written during 

bootup to /proc/asound/ folders.



 The /proc/asound/ audio+modem diagostics are being copied.

 Finished copy to Modem/ALSAroot.tgz



The ALSA verion is 1.0.14

The modem cards detected by "aplay -l"  are:

card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]



The /proc/asound/pcm file reports:

-----------------------

00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1

00-01: AD198x Digital : AD198x Digital : playback 1

00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1



about /proc/asound/cards:

------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel

                      HDA Intel at 0xb0000000 irq 22





The driver snd-hda-intel with its dependent drivers:

snd_hda_intel         263712  1 

snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss

snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

----------

provide audio + modem support for many soft modem chips residing on the High Definition Audio (HDA) card subsystem. However modem support for some is not yet fully implemented.





The driver snd-hda-intel with its dependent drivers:

snd_hda_intel         263712  1 

snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss

snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

----------

provide modem + audio support.





 The modem codec file for the the HDA card is: /proc/asound/card0/codec#1

--------------------------------------------------------

Codec: Motorola Si3054

Address: 1

Vendor Id: 0x10573055

Subsystem Id: 0x10573055

Revision Id: 0x100700



 The audio card hosts a softmodem chip:  0x10573055



 The modem codec file for the the HDA card is: /proc/asound/card0/codec#1

--------------------------------------------------------

Codec: Motorola Si3054

Address: 1

Vendor Id: 0x10573055

Subsystem Id: 0x10573055

Revision Id: 0x100700



 The audio card hosts a softmodem chip:  0x10573055

USB modem not detected by lsusb



For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:

 PCI slot   PCI ID      SubsystemID   Name

 ----------   ---------   ---------   --------------

 00:1b.0   8086:2668   17c0:2017   Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 



 Modem interrupt assignment and sharing: 

 22:      20957   IO-APIC-fasteoi   HDA Intel, i915@pci:0000:00:02.0

 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----

[   16.516000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 22

[   16.516000] PCI: Setting latency timer of device 0000:00:1b.0 to 64





 === Finished modem firmware and bootup diagnostics section. ===

 === Next deducing cogent software ===







 For candidate modem in PCI bus:  00:1b.0

   Class 0403: 8086:2668 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW

      Primary PCI_id  8086:2668

    Subsystem PCI_id  17c0:2017 

    Softmodem codec or chipset from diagnostics: 

                               from    Archives: 

                        



 Lacking a dsp (digital signal processing) chip, the modem is a software 

 intensive or "softmodem" type. Its primary controller manages the traffic 

 with the CPU. But the software needed is specified in the Subsystem.

 -----------------------------------------

Support type needed or chipset:   



Support can likely be achieved through two mutually exclusive alternatives:

1) The hsfmodem software for Conexant chipset modems: Read Conexant.txt

The following ALSA alternative CANNOT work with Conexant modems.



2) An ALSA modem driver plus slmodemd.  Read Smartlink.txt for details, and

to test get the package SLMODEMD.gcc4.1.tar.gz from:  

   http://linmodems.technion.ac.il/packages/smartlink/



----------------end Softmodem section --------------



Writing Intel.txt



For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt



 Read Conexant.txt



Writing Conexant.txt



Writing Smartlink.txt

============ end Smartlink section =====================





 The base of the UDEV device file system is: /dev/.udev



 Versions adequately match for the compiler installed: 4.1.3

             and the compiler used in kernel assembly: 4.1.3





 

 Minimal compiling resources appear complete:

   make utility - /usr/bin/make

   Compiler version 4.1

   linuc_headers base folder /lib/modules/2.6.22-14-generic/build



 However some compilations and executable functions may need additional files,

 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .

 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 







If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then

Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev

and any of its dependents, under Ubuntu linux-libc-dev



If an alternate ethernet connection is available,

$  apt-get update

$  apt-get -s install linux-kernel-devel

will install needed package

For Debian/Ubuntu related distributions, run the following command to display the needed package list:



Otherwise packages have to be found through http://packages.ubuntu.com

Once downloaded and transferred into a Linux partition,

they can be installed alltogether with:

$ sudo dpkg -i *.deb





Checking pppd properties:

   -rwsr-xr-- 1 root dip 269256 2007-10-04 23:27 /usr/sbin/pppd



In case of an "error 17" "serial loopback" problem, see:

    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html



To enable dialout without Root permission do:

   $ su - root  (not for Ubuntu)

        sudo chmod a+x /usr/sbin/pppd

or under Ubuntu related Linuxes

   sudo chmod a+x /usr/sbin/pppd



Checking settings of:   /etc/ppp/options

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

see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html



Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1

Which can interfere with Browser naviagation.



 Don't worry about the following, it is for the experts

 should trouble shooting be necessary.

==========================================================



 Checking for modem support lines:

 --------------------------------------

     /device/modem symbolic link:   

slmodemd created symbolic link /dev/ttySL0:  

     Within /etc/udev/ files:



     Within /etc/modprobe.conf files:

/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers

/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem

/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem

/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2

/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2

     Within any ancient /etc/devfs files:



     Within ancient kernel 2.4.n /etc/module.conf files:



--------- end modem support lines --------
```
the result of wvdialconfig :
```
mahdieh@mahdieh-laptop:~$ wvdialconf

Editing `/etc/wvdial.conf'.



Scanning your serial ports for a modem.



Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.

Modem Port Scan<*1>: SHSF0 S0   S1   S2   S3   SHSF1 SHSF2 SHSF3 

Modem Port Scan<*1>: SHSF4 SHSF5 SHSF6 SHSF7 





Sorry, no modem was detected!  Is it in use by another program?

Did you configure it properly with setserial?



Please read the FAQ at http://open.nit.ca/wiki/?WvDial



If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

mahdieh@mahdieh-laptop:~$
```
after a while I heard that this driver does not work on ubuntu 7.10 and I should use hsfmodem_7.60.00.18oem_i386.deb so I download it from dell web site and installed :
```
mahdieh@mahdieh-laptop:~$ cd ~/Desktop 
mahdieh@mahdieh-laptop:~/Desktop$ sudo dpkg -i hsfmodem_*.deb 
[sudo] password for mahdieh: 
Selecting previously deselected package hsfmodem. 
(Reading database ... 89911 files and directories currently installed.) 
Unpacking hsfmodem (from hsfmodem_7.60.00.18oem_i386.deb) ... 
Setting up hsfmodem (7.60.00.18oem) ... 
Conexant HSF softmodem driver, version 7.60.00.18oem 
 
If you need assistance or more information, please go to: 
        http://www.linuxant.com/ 
 
When reporting a problem for the first time, please send 
us the file generated by "hsfconfig --dumpdiag". 
 
 
No pre-built modules for: Ubuntu-7.10 linux-2.6.22-14-generic i686-SMP 
 
Trying to automatically build the driver modules... 
(this requires a C compiler and proper kernel sources to be installed) 
 
Building modules for kernel 2.6.22-14-generic, using source directory 
/lib/modules/2.6.22-14-generic/build. Please wait... 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
done. 
 
Warning: no device detected by hsf driver - HDA modems may require reboot 
 
Note: kernel module snd-via82xx-modem overridden by hsfmc97via 
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis 
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati 
 
mahdieh@mahdieh-laptop:~/Desktop$ sudo hsfconfig 
Conexant HSF softmodem driver, version 7.60.00.18oem 
 
If you need assistance or more information, please go to: 
        http://www.linuxant.com/ 
 
When reporting a problem for the first time, please send 
us the file generated by "hsfconfig --dumpdiag". 
 
Warning: existing driver modules found under: 
        /lib/modules/2.6.22-14-generic/ 
Would you like to keep using them? [no]  
 
Would you like to use the replacement HDA modules? [yes]  
 
No pre-built modules for: Ubuntu-7.10 linux-2.6.22-14-generic i686-SMP 
 
Trying to automatically build the driver modules... 
(this requires a C compiler and proper kernel sources to be installed) 
 
Where is the linux source build directory that matches your running kernel? 
[/lib/modules/2.6.22-14-generic/build]  
 
Building modules for kernel 2.6.22-14-generic, using source directory 
/lib/modules/2.6.22-14-generic/build. Please wait... 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
Warning: Module snd_hda_intel is in use 
done. 
 
Warning: no device detected by hsf driver - HDA modems may require reboot 
 
Note: HDA support not compiled in the driver (requires a 2.6.16 or later kernel) 
 
Note: kernel module snd-via82xx-modem overridden by hsfmc97via 
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis 
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati 
mahdieh@mahdieh-laptop:~/Desktop$and it is the result of wvdial for hsfmodem_7.60.00.18oem_i386.deb :

```
and it is the result of wvdial for hsfmodem_7.60.00.18oem_i386.deb :
```
mahdieh@mahdieh-laptop:~$ wvdialconf 
Editing `/etc/wvdial.conf'. 
 
Scanning your serial ports for a modem. 
 
Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it. 
Modem Port Scan<*1>: SHSF0 S0   S1   S2   S3   SHSF1 SHSF2 SHSF3  
Modem Port Scan<*1>: SHSF4 SHSF5 SHSF6 SHSF7  
 
 
Sorry, no modem was detected!  Is it in use by another program? 
Did you configure it properly with setserial? 
 
Please read the FAQ at http://open.nit.ca/wiki/?WvDial 
 
If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
```
I really need your help
thank u so much

---

### Post by rose_flower23kish on 2008-02-25
The result of lshw -C modem :
```
mahdieh@mahdieh-laptop:~$ lshw -c modem 
Hardware Lister (lshw) - B.02.10 
usage: lshw [-format] [-options ...] 
       lshw -version 
 
        -version        print program version (B.02.10) 
 
format can be 
        -html           output hardware tree as HTML 
        -xml            output hardware tree as XML 
        -short          output hardware paths 
        -businfo        output bus information 
 
options can be 
        -class CLASS    only show a certain class of hardware 
        -C CLASS        same as '-class CLASS' 
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
        -quiet          don't display status 
 
mahdieh@mahdieh-laptop:~$  
 
 

```

---

