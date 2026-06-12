---
title: "Newbie...Need modem help"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by tlappy on 2005-08-13
Hi folks. First of all, I am a newbie as far as ubuntu is concerned ! I have installed 5.04 on an amd k6-2 machine (dual booting with windoz) and the install seems to have gone well enough. This particular machine also has a cm8738 type modem installed on it. It does work with windoz. I found that I needed to install a driver for it in order to use it with any *nix distro. Ok, googled about a bit and found that pctel-0.9.7-9-rht-4 should work, and work under the 2.6 kernel. I downloaded this file, extracted it, and proceeded to follow directions.

Running the configure -a option, I got:

xxx@xxx:~/pctel-0.9.7-9-rht-4/src$ ./configure -auto
checking for running kernel version...2.6.10
checking for ptserial...ptserial-2.6.c
checking for gcc...3.3.5
searching for kernel includes...found at /lib/modules/2.6.10-5-386/build/includechecking for autoconf.h.../lib/modules/2.6.10-5-386/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in version.h...UTS_RELEASE is 2.6.10-5-386
checking type of tty_struct.count...int
detecting your modem...found. Your modem is a cm8738 type modem.

Cool so far, modem found and recognized,
However, when I tried to "make" (even tried a "make clean" first) i get the following:

xxx@xxx:~/pctel-0.9.7-9-rht-4/src$ make
  CC    vuart.o
  LD    binary.a
lib/cm8738/pctel-cm8738.o(.text+0x118): In function `get_uart_mcr':
: multiple definition of `get_uart_mcr'
vuart.o(.text+0xf8): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x1): multiple definition of `COM_Viir'
vuart.o(.data+0x1): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x208): In function `put_uart_ier':
: multiple definition of `put_uart_ier'
vuart.o(.text+0x1e8): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x5): multiple definition of `COM_Vmsr'
vuart.o(.data+0x5): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x0): multiple definition of `COM_Vier'
vuart.o(.data+0x0): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x170): In function `get_uart_msr':
: multiple definition of `get_uart_msr'
vuart.o(.text+0x150): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x254): In function `put_uart_dll':
: multiple definition of `put_uart_dll'
vuart.o(.text+0x234): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x230): In function `put_uart_lsr':
: multiple definition of `put_uart_lsr'
vuart.o(.text+0x210): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x26c): In function `put_uart_dlm':
: multiple definition of `put_uart_dlm'
vuart.o(.text+0x24c): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x218): In function `put_uart_lcr':
: multiple definition of `put_uart_lcr'
vuart.o(.text+0x1f8): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x224): In function `put_uart_mcr':
: multiple definition of `put_uart_mcr'
vuart.o(.text+0x204): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x2): multiple definition of `COM_Vlcr'
vuart.o(.data+0x2): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x20): In function `get_uart_rx':
: multiple definition of `get_uart_rx'
vuart.o(.text+0x0): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x4): multiple definition of `COM_Vlsr'
vuart.o(.data+0x4): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x28c): In function `PctelInitVUartVars':
: multiple definition of `PctelInitVUartVars'
vuart.o(.text+0x26c): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x6): multiple definition of `COM_Vscr'
vuart.o(.data+0x6): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x8): multiple definition of `COM_Vdll'
vuart.o(.data+0x8): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x1ac): In function `get_uart_scr':
: multiple definition of `get_uart_scr'
vuart.o(.text+0x18c): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x214): In function `put_uart_iir':
: multiple definition of `put_uart_iir'
vuart.o(.text+0x1f4): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x60): In function `get_uart_ier':
: multiple definition of `get_uart_ier'
vuart.o(.text+0x40): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x1b4): In function `get_uart_dll':
: multiple definition of `get_uart_dll'
vuart.o(.text+0x194): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x23c): In function `put_uart_msr':
: multiple definition of `put_uart_msr'
vuart.o(.text+0x21c): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x248): In function `put_uart_scr':
: multiple definition of `put_uart_scr'
vuart.o(.text+0x228): first defined here
lib/cm8738/pctel-cm8738.o(.data+0x3): multiple definition of `COM_Vmcr'
vuart.o(.data+0x3): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x1c4): In function `put_uart_tx':
: multiple definition of `put_uart_tx'
vuart.o(.text+0x1a4): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x110): In function `get_uart_lcr':
: multiple definition of `get_uart_lcr'
vuart.o(.text+0xf0): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x120): In function `get_uart_lsr':
: multiple definition of `get_uart_lsr'
vuart.o(.text+0x100): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x68): In function `get_uart_iir':
: multiple definition of `get_uart_iir'
vuart.o(.text+0x48): first defined here
lib/cm8738/pctel-cm8738.o(.text+0x1bc): In function `get_uart_dlm':
: multiple definition of `get_uart_dlm'
vuart.o(.text+0x19c): first defined here
make: *** [binary.a] Error 1

I don't know what to make of this ('scuse the pun).  Also tried configure -manual,
but didn't change anything as far as the make errors go. 
Any help would be greatly appreciated.   
(I know, winmodems are a pain, get an external modem...etc, but if the thing CAN work, I would like to MAKE it work, sorta like, I hate machines kickin my butt!)

Thanx.

---

### Post by autocrosser on 2005-08-13
Well- did you sudo configure--sudo make or just configure---make?  I believe that you would need root priv to make--install a tty dev driver......Any one else chime in that would have more info---

---

### Post by tlappy on 2005-08-13
Tried sudo make, also tried logged in as root, same results.

---

### Post by az on 2005-08-13
The pctel driver for 2.6 kernel is bleeding-edge and not really ready for prime-time.  You may have luck using the sl-modem driver since they can make an ac97 codec modem work.  I think the pctel modems can fall under that category.

---

### Post by tlappy on 2005-08-13
Thanx azz, I give that a shot, and post back with results.   :)

---

### Post by tlappy on 2005-08-14
Hello again.

I downloaded slmodem-2.9.10.tar, followed instructions, seemed to "make" allright,
finished "make install" but when I tried "modprobe slamr" this failed. I did download and run scanModem which generated several files for my info. Heh, thats really cool, but I don't know how to use them. Here they are, maybe someone with some linux savvy knows what all this means (yes, I am becoming more humble and confused by the hour!) :



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_July_21
------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i586
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 and later kernels. 
Concerning Intel-536ep and 537
   [http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/) 
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)
   
 The kernel was assembled with compiler:  3.3.5
 with current System compiler GCC=3.3.5
    /usr/bin/gcc -> gcc-3.3

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
The kernel-headers have base folder: 
/lib/modules/2.6.10-5-386/build -> /usr/src/linux-headers-2.6.10-5-386
/usr/src/linux-headers-2.6.10-5-386
Please install the package WVDIAL for modem testing and dialout.

 A /dev/modem symbolic link is not set.
 USB modem not detected.

0000:00:0d.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

Modem candidates are at PCI_buses:   0000:00:0d.1
    
Providing detail for device at  0000:00:0d.1
  with vendor-ID:device-ID
	    ----:----
Class 0780: 13f6:0211   Communication controller: C-Media Electronics Inc CM8738 (rev 20)
  SubSystem 13f6:0211   C-Media Electronics Inc CM8738
0000:00:0d.1 0780: 13f6:0211 (rev 20)
	Flags: medium devsel, IRQ 9
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 13f6:0211 13f6:0211 debian 2.6.10-5-386  3.3.5 3.3.5    i586

 == Checking PCI IDs through modem chip suppliers ==

 Vendor 13f6 is C-Media Electronics, which produced modem:
     13f6:0211  C-Media Electronics Inc CM8738,
     13f6:0211  subsystem HSP56 Audiomodem Riser
 supported under 2.4.n kernels by PCTEL software.
 BUT there is no support under 2.6.n kernels.

 Under 2.6.n kernels, there is NO support for this Pctel modem.
 Read ModemData.txt  and Pctel.txt in the new sub-folder Modem/

  ======= PCI_ID checking completed ====== 
 Update=2005_July_21
A PCMCIA CardBus is not detected on this System.
GCCversion=3.3.5
   
For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
No local APIC present or hardware disabled
ACPI: Interpreter disabled.
pnp: PnP ACPI: disabled
audit: initializing netlink socket (disabled)
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
  debian is not yet providing pre-compiled drivers for WinModems



 If the Primary and Subsystem Vendor information was not adeqaute,
 it may be useful to search at  [http://www.pcidatabase.com/](http://www.pcidatabase.com/)


 ---------------------------------------------------------------------------------------------
 The proprietary Binary component of the some current winmodem drivers were compiled with
 version 2.9n gcc compiler.  Red Hat 8.0 and Mandrake 9.0 releases utilize
 version 3.nn gcc compilers.  This currently is causing difficulties either
 in compiling and/or insertion of updated winmodem drivers.

 The gcc compiler version of this System is:   3.3.5
 It will likely be necessary to force (-f) insertion of winmodem drivers, with credit to
 Jos Vos: [http://phep2.technion.ac.il/linmodems/archive/msg04510.html](http://phep2.technion.ac.il/linmodems/archive/msg04510.html)

 For the ltmodem drivers with proprietary binary provided by Agere Systems,
 compiling with versions gcc=3.nn is successful.
 A minor edit required to compile PCTEL drivers has also been reported:
     [http://phep2.technion.ac.il/linmodems/archive/msg04684.html](http://phep2.technion.ac.il/linmodems/archive/msg04684.html)

  Simple driver insertion fails in these cases with a message like:
----begin error----
% insmod lt_modem
Using /lib/modules/2.4.18-14/ltmodem/lt_modem.o
/lib/modules/2.4.18-14/ltmodem/lt_modem.o: The module you are trying to
load (/lib/modules/2.4.18-14/ltmodem/lt_modem.o) is compiled with a gcc
version 2 compiler, while the kernel you are running is compiled with
a gcc version 3 compiler. This is known to not work.
-----end error-----

 It is necessary as Root to force (-f) loading with commands like:
     insmod -f pctel

 respecting the dependency ordering of the drivers.
 Then check for insertion with:
    lsmod

 If driver insertion is successful, the forcing can be automated
 by putting the lines (credit to Bhaskaran Raman)  like the following,
    install pctel  /sbin/insmod --force pctel

 In order of preference depending on your particular Linux installation.
 Put these lines into ONLY ONE of the following files,
 within any modem loading subsection if present:
    /etc/modutils/ltmodem
    /etc/modutils/aliases
    /etc/modules.conf

 Then inform your System of the edit for Debian like Systems with
    update-modules
 which rewrites and reads /etc/modules.conf . For other System types
    depmod -a
 re-reads the edited      /etc/modules.conf .

 Thereafter module loading should behave as previously.
 For the ltmodem drivers loading,
 it should suffice to either start a ppp session or
    modprobe ptserial


  -----------------------------------------------------
  The System has Ethernet capability. If not expert, 
  shut down ethernet before initiated modem usage with:
  # ifconfig eth0 down



 Within /lib/modules/You_Kernel_Version/kernel/drivers/net/
 at least the following modules needed for communication should be found
   ppp_deflate.o
   zlib_inflate.o 
   zlib_deflate.o 
   bsd_comp.o
   ppp_async.o
   ppp_generic.o
   slhc.o
 BUT they may be present instead as ModuleName.o.gz
 If so unpack them with a commands like:
   # gzip /lib/modules/You_Kernel_Version/kernel/drivers/net/ModuleName.o.gz
 Alternatively, installing the dialer package KPPP may force their unpacking.
 
 Following a dialout attempt, display loaded modules with:
# /sbin/lsmod
 If there are not displayed lines like:

ppp_deflate             3512   1  (autoclean)
zlib_inflate           18980   0  (autoclean) [ppp_deflate]
zlib_deflate           18648   0  (autoclean) [ppp_deflate]
bsd_comp                4440   0  (autoclean)
ppp_async               7744   1  (autoclean)
ppp_generic            16380   3  (autoclean) [ppp_deflate bsd_comp ppp_async]
slhc                    5264   1  (autoclean) [ppp_generic

addition of the following lines to /etc/modprobe.* or /etc/modprobe.*.d/ folders may be needed:

### automate ppp modules loading ###
alias /dev/ppp          ppp_generic
alias char-major-108    ppp_generic
alias tty-ldisc-3       ppp_async
alias tty-ldisc-14      ppp_synctty
alias ppp-compress-21   bsd_comp
alias ppp-compress-24   ppp_deflate
alias ppp-compress-26   ppp_deflate
### end ppp block ####

 After any edit of /etc/modprobe.* or /etc/modprobe.*.d/ folders ,
 inform the System by logging into a console with
 # su - root
 and running the update command:
 #  depmod -a
 which re-reads /etc/modules.conf and parses all the modules dependencies.
 Debian like Distros should instead use:
   update-modules


  Attempted or effective networking links are displayed by command:
  #  /sbin/ifconfig
  A block with "lo" is an internal loopback test and harmless.
  However, ethernet "eth0" can be problematic for PPP connections,
  because of competition for DNS (domain name service).
  The default is to use the DNS specified for etherenet and
  without expert configuration, this will block browser naviagation through PPP.
  ========== ifconfig test =============
  lo        Link encap:Local Loopback  

  If is wisest to disable bootup establishment of ethernet in your Control Center.
  Depending on your Linux distribution,
      one of the following Root commands way alternatively be effective:
  # ifdown eth0
  # ifconfig eth0 down
  # /etc/init.d/network stop
  # /etc/init.d/networking stop


Yikes! Thanx again...

---

### Post by tlappy on 2005-08-14
Also...here is the log of the whole episode:

root@Nix-1:/home/ejw/slmodem-2.9.10 # make clean
make -C modem clean &&  make -C drivers clean &&  echo "done."
make[1]: Entering directory `/home/ejw/slmodem-2.9.10/modem'
rm -f slmodemd modem_test modem_main.o modem_cmdline.o modem_test.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o sysdep_common.o
rm -f *~
make[1]: Leaving directory `/home/ejw/slmodem-2.9.10/modem'
make[1]: Entering directory `/home/ejw/slmodem-2.9.10/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
make[1]: Leaving directory `/home/ejw/slmodem-2.9.10/drivers'
done.
root@Nix-1:/home/ejw/slmodem-2.9.10 # make
make -C modem all
make[1]: Entering directory `/home/ejw/slmodem-2.9.10/modem'
rebuild profile...
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_cmdline.o -c modem_cmdline.cgcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_datafile.o -c modem_datafile.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_at.o -c modem_at.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_timer.o -c modem_timer.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_pack.o -c modem_pack.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_ec.o -c modem_ec.c
modem_ec.c:689: warning: `t403_timeout' defined but not used
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_comp.o -c modem_comp.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_param.o -c modem_param.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_debug.o -c modem_debug.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o homolog_data.o -c homolog_data.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_sinus.o -c dp_sinus.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_dummy.o -c dp_dummy.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o sysdep_common.o -c sysdep_common.cgcc -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_test.o -c modem_test.c
gcc -o modem_test modem_test.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
make[1]: Leaving directory `/home/ejw/slmodem-2.9.10/modem'
root@Nix-1:/home/ejw/slmodem-2.9.10 # make
make -C modem all
make[1]: Entering directory `/home/ejw/slmodem-2.9.10/modem'
make[1]: Leaving directory `/home/ejw/slmodem-2.9.10/modem'
root@Nix-1:/home/ejw/slmodem-2.9.10 # make install
make -C modem all
make[1]: Entering directory `/home/ejw/slmodem-2.9.10/modem'
make[1]: Leaving directory `/home/ejw/slmodem-2.9.10/modem'
make -C drivers KERNEL_DIR=/lib/modules/2.6.10-5-386/build
make[1]: Entering directory `/home/ejw/slmodem-2.9.10/drivers'
cc -I/lib/modules/2.6.10-5-386/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.10-5-386
make[2]: Entering directory `/home/ejw/slmodem-2.9.10/drivers'
make modules -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/ejw/slmodem-2.9.10/drivers
make[3]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/ejw/slmodem-2.9.10/drivers/amrmo_init.o
  CC [M]  /home/ejw/slmodem-2.9.10/drivers/sysdep_amr.o
  CC [M]  /home/ejw/slmodem-2.9.10/drivers/st7554.o
/home/ejw/slmodem-2.9.10/drivers/st7554.c: In function `st7554_init':
/home/ejw/slmodem-2.9.10/drivers/st7554.c:1112: warning: implicit declaration of function `usb_endpoint_halted'
  LD [M]  /home/ejw/slmodem-2.9.10/drivers/slamr.o
  LD [M]  /home/ejw/slmodem-2.9.10/drivers/slusb.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/ejw/slmodem-2.9.10/drivers/.amrlibs.o.cmd for /home/ejw/slmodem-2.9.10/drivers/amrlibs.o
*** Warning: "usb_endpoint_halted" [/home/ejw/slmodem-2.9.10/drivers/slusb.ko] undefined!
  CC      /home/ejw/slmodem-2.9.10/drivers/slamr.mod.o
  LD [M]  /home/ejw/slmodem-2.9.10/drivers/slamr.ko
  CC      /home/ejw/slmodem-2.9.10/drivers/slusb.mod.o
  LD [M]  /home/ejw/slmodem-2.9.10/drivers/slusb.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[2]: Leaving directory `/home/ejw/slmodem-2.9.10/drivers'
make[1]: Leaving directory `/home/ejw/slmodem-2.9.10/drivers'
make install -C drivers KERNEL_DIR=/lib/modules/2.6.10-5-386/build
make[1]: Entering directory `/home/ejw/slmodem-2.9.10/drivers'
cc -I/lib/modules/2.6.10-5-386/build/include -o kernel-ver kernel-ver.c
mkdir -p /dev
mknod -m 600 /dev/slamr0 c 212 0 ;   mknod -m 600 /dev/slamr1 c 212 1 ;   mknod -m 600 /dev/slamr2 c 212 2 ;   mknod -m 600 /dev/slamr3 c 212 3 ;  echo -n
mknod -m 600 /dev/slusb0 c 213 0 ;   mknod -m 600 /dev/slusb1 c 213 1 ;   mknod -m 600 /dev/slusb2 c 213 2 ;   mknod -m 600 /dev/slusb3 c 213 3 ;  echo -n
make install KERNEL_VER=2.6.10-5-386
make[2]: Entering directory `/home/ejw/slmodem-2.9.10/drivers'
install -D -m 644 slamr.ko /lib/modules/2.6.10-5-386/extra/slamr.ko
install -D -m 644 slusb.ko /lib/modules/2.6.10-5-386/extra/slusb.ko
/sbin/depmod -a
make[2]: Leaving directory `/home/ejw/slmodem-2.9.10/drivers'
make[1]: Leaving directory `/home/ejw/slmodem-2.9.10/drivers'
install -D -m 755 modem/slmodemd /usr/sbin/slmodemd
rm -f -rf /var/lib/slmodem
install -d -D -m 755 /var/lib/slmodem
root@Nix-1:/home/ejw/slmodem-2.9.10 # modprobe slamr
FATAL: Error inserting slamr (/lib/modules/2.6.10-5-386/extra/slamr.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@Nix-1:/home/ejw/slmodem-2.9.10 # dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000f000000 (usable)
 BIOS-e820: 00000000ffef0000 - 00000000fff00000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
240MB LOWMEM available.
On node 0 totalpages: 61440
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 57344 pages, LIFO batch:14
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: Unable to locate RSDP
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro quiet splash
No local APIC present or hardware disabled
mapped APIC to ffffd000 (011e4000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 551.280 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 236188k/245760k available (1436k kernel code, 9036k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1089.53 BogoMIPS (lpj=544768)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000
CPU: AMD-K6(tm) 3D processor stepping 0c
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd9f8, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f7280
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6944, dseg 0xf0000
PnPBIOS: Missing SMALL_TAG_ENDDEP tag
PnPBIOS: Missing SMALL_TAG_ENDDEP tag
PnPBIOS: Missing SMALL_TAG_ENDDEP tag
PnPBIOS: Missing SMALL_TAG_ENDDEP tag
PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:00.1
Uncovering SIS18 that hid as a SIS503 (compatible=0)
Enabling SiS 96x SMBus.
PCI: Using IRQ router SIS [1039/0018] at 0000:00:01.0
audit: initializing netlink socket (disabled)
audit(1124036609.993:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kpnpbiosd not stopped
 Strange, kseriod not stopped
 done
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:00.1
SIS5513: chipset revision 208
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS540 ATA 66 controller
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 2B010H1, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 20012832 sectors (10246 MB) w/2048KiB Cache, CHS=19854/16/63, UDMA(66)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
Probing IDE interface ide1...
hdc: GCR-8523B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (457 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 273096k swap on /dev/hda3.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
hdc: ATAPI 52X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 540 chipset
agpgart: Maximum main memory to use for agp memory: 190M
agpgart: AGP aperture is 256M @ 0xe0000000
sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted.
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
PCI: Found IRQ 10 for device 0000:00:01.2
PCI: Sharing IRQ 10 with 0000:00:01.3
ohci_hcd 0000:00:01.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:01.2: irq 10, pci mem 0xffdfe000
ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
PCI: Found IRQ 10 for device 0000:00:01.3
PCI: Sharing IRQ 10 with 0000:00:01.2
ohci_hcd 0000:00:01.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:01.3: irq 10, pci mem 0xffdff000
ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-1: new low speed USB device using ohci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.00 Keyboard [Mitsumi Electric Mitsumi USB Keyboard] on usb-0000:00:01.2-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
sis900.c: v1.08.07 11/02/2003
PCI: Found IRQ 11 for device 0000:00:09.0
0000:00:09.0: SiS 900 Internal MII PHY transceiver found at address 1.
0000:00:09.0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xde00, IRQ 11, 00:e0:06:f4:c6:bf.
PCI: Found IRQ 5 for device 0000:00:0d.0
capifs: Rev 1.1.2.3
CAPI Subsystem Rev 1.1.2.8
capi20: Rev 1.1.2.7: started up with major 68 (middleware+capifs)
b1: revision 1.1.2.2
b1dma: revision 1.1.2.3
b1pci: revision 1.1.2.2
c4: revision 1.1.2.2
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[drm] Initialized drm 1.0.0 20040925
[drm] Initialized sis 1.1.0 20030826 on minor 0: Silicon Integrated Systems [SiS] SiS540 PCI Display Adapter
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
drivers/usb/input/hid-input.c: event field not found
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
usb 2-2: new full speed USB device using ohci_hcd and address 2
SCSI subsystem initialized
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: Memorex   Model: TD 2C             Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 1949696 512-byte hdwr sectors (998 MB)
sda: Write Protect is off
sda: Mode Sense: 23 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 1949696 512-byte hdwr sectors (998 MB)
sda: Write Protect is off
sda: Mode Sense: 23 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
usb 2-2: USB disconnect, address 2
Unable to handle kernel NULL pointer dereference at virtual address 00000194
 printing eip:
cfb2721f
*pde = 00000000
Oops: 0000 [#1]
PREEMPT
Modules linked in: nls_utf8 vfat fat sd_mod usb_storage scsi_mod ipv6 proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave sis drm apm c4 b1pci b1dma b1 capi kernelcapi capifs snd_cmipci snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib snd_timer snd_hwdep gameport snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore sis900 pci_hotplug usbhid ohci_hcd usbcore i2c_sis630 i2c_core sis_agp agpgart floppy pcspkr rtc nls_cp437 ntfs md dm_mod capability commoncap tsdev evdev psmouse mousedev parport_pc lp parport ide_cd cdrom ext3 jbd ide_generic sis5513 ide_disk ide_core unix processor fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
CPU:    0
EIP:    0060:[<cfb2721f>]    Not tainted VLI
EFLAGS: 00010246   (2.6.10-5-386)
EIP is at bus_reset+0x43/0xa4 [usb_storage]
eax: 00000000   ebx: c500ac00   ecx: c55ea000   edx: c2c4acb8
esi: c338a000   edi: fffffffb   ebp: c2c4aca0   esp: c338bf3c
ds: 007b   es: 007b   ss: 0068
Process scsi_eh_0 (pid: 7588, threadinfo=c338a000 task=c3a3ba00)
Stack: 00000282 c338a000 c2c4aca0 cfb915fc c2c4aca0 c2c4aca0 c338bfb8 00000000
       c2c4aca0 cfb91795 c2c4aca0 c55ea000 c338bfb0 c338bfb8 c55ea000 cfb91bf2
       c55ea000 c338bfb8 c338bfb0 c338bfb8 c338bfb0 c338bfb8 cfb91e7d c55ea000
Call Trace:
 [<cfb915fc>] scsi_try_bus_reset+0x60/0xc2 [scsi_mod]
 [<cfb91795>] scsi_eh_bus_reset+0x75/0x106 [scsi_mod]
 [<cfb91bf2>] scsi_eh_ready_devs+0x35/0x5d [scsi_mod]
 [<cfb91e7d>] scsi_unjam_host+0x18d/0x1a2 [scsi_mod]
 [<cfb91f6d>] scsi_error_handler+0xdb/0x11f [scsi_mod]
 [<cfb91e92>] scsi_error_handler+0x0/0x11f [scsi_mod]
 [<c01011f9>] kernel_thread_helper+0x5/0xb
Code: 21 e0 ff 48 14 8b 40 08 a8 08 74 05 e8 7a f4 73 f0 ff 0b 0f 88 cd 02 00 00 bf fb ff ff ff 8b 43 1c a9 00 00 20 00 75 43 8b 43 10 <8b> 80 94 01 00 00 80 78 04 01 74 07 bf f0 ff ff ff eb 2d ff 73
 <4>slamr: module license 'Smart Link Ltd.' taints kernel.
slamr: Unknown symbol get_device
slamr: Unknown symbol put_device
slamr: Unknown symbol device_release_driver
root@Nix-1:/home/ejw/slmodem-2.9.10 #

heh.....i dunno.....am I helpless? (scr**d?)  Yikes..........

---

### Post by mingus on 2005-08-15
If you are trying to use the Alsa option in the smartlink driver for your pctel modem, then you do not want to use the slamr driver, that is for the smartlink chipset.

You might have better luck just using the 2.9.9a modules already compiled rather than 2.10, see the Unofficial Starter Guide.  Actually, 2.9.9x is newer than 2.10.

Do:  $sudo dpkg-reconfigure sl-modem-daemon
to toggle between Alsa and slamr.

If still not being recognized, edit /etc/default/sl-modem-daemon line for device from "auto" to "hw:0" or "hw:1" (try both), reboot each time.

And finally, in the dialer (there are several to try) specify /dev/ttySL0 rather than /dev/modem until you get it working.

---

