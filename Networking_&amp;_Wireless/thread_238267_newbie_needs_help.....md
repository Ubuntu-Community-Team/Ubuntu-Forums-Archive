---
title: "newbie needs help...."
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by maalvin15 on 2006-08-17
my problem is that I cant install my modem in ubuntu... i try scanning my modem using the scanmodem tool which i downloaded in linmodems.org and the datamodem.txt says:

0 snd_via82xx


 The kernel was assembled with compiler:  4.0.3

No compiler installed.
 a gcc-4.0.3  
package must be installed to support driver compiling


If compiling a modem driver proves to be necessary, 
one of the two procedures must be followed.

If not yet on the Internet, 
put the Dapper install CD in the drive

Open a terminal and therein:

$ sudo apt-get install  gcc-4.0  make

Additionally the package linux-headers-2.6.15-23-386 must be downloaded.  

Goto [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  
and search for linux-headers-2.6.15-23-386 

After downloading, it can be installed with:

$ sudo apt-get install linux-header*.deb


Or alternatively if online through Ethernet do:

$ sudo apt-get install build-essential

will do all the necessary installations mentioned above.



In either installation case, set a symbolic link which will be expected later:

$ sudo ln -s /usr/bin/gcc-4.0  /usr/bin/gcc

After check with:

$ ls -l /usr/bin/gcc*

which should display:

lrwxrwxrwx 1 root root    16 2006-07-09 21:53 /usr/bin/gcc -> /usr/bin/gcc-4.0

-rwxr-xr-x 1 root root 93584 2006-04-20 18:22 /usr/bin/gcc-4.0

-rwxr-xr-x 1 root root 16245 2006-04-20 18:13 /usr/bin/gccbug-4.0


-------------
 Compiling utility   make   Not found.
-------------

Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:0a.0
    
Providing detail for device at  0000:00:0a.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 14f1:2f00   Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
  SubSystem 14f1:2003  Conexant: Unknown device 2003
	Flags: bus master, medium devsel, latency 32, IRQ 10
 Checking for IRQ 10 sharing with modem.
      XT-PIC  uhci_hcd:usb3, VIA8233

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 14f1:2f00 14f1:2003 Ubuntu 2.6.15-23-386  4.0.3 none    i686
      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==
  14f1:2f00 is a Conexant HSF modem.

 Vendors 127a and 14f1 are Conexant, inheritor of  Rockwell modem  technology. There are also Conexant chipsets
 in some modems from vendors 158b - Allied Data Tech., 1024 - Zenith ,141a - Apache Micro and 148d Digicom Systems.
 With respect to software support there are two main types, hcfpcimodem* and hsfmodem* .
 Download driver code packages from [http://www.Linuxant.com/drivers](http://www.Linuxant.com/drivers)
  At   [http://linmodems.technion.ac.il/resources.html#conexant](http://linmodems.technion.ac.il/resources.html#conexant)  , there are scripts aiding installation:
      For HSF modems.
      For HCF modems.
 There is additional Conexant information written to Modem/Conexant.txt 
 

  ======= PCI_ID checking completed ====== 
 Update=2006_August_02
A PCMCIA CardBus is not detected on this System.
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted


      
 The Major.Minor versions differ in the designated compiler none and the 4.0.3 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.15-23-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.15-23-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.15-23-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.15-23-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.15-23-386 or kernel-smp-devel-2.6.15-23-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.15-23-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:11:5B:F5:C3:D1  
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294668.753000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[4294668.754000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[4294668.754000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[4294668.755000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[4294668.787000]   IO window: disabled.
[4294668.787000] audit: initializing netlink socket (disabled)
[4294770.372000] ibm_acpi: ec object not found
[4294770.404000] pcc_acpi: loading...
[4294791.706000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294791.706000] apm: overridden by ACPI.
  Ubuntu is not yet providing pre-compiled drivers for WinModems

WHAT AM I GOING TO DO NEXT? please help me!!!!
I tried installing the gcc-4.0.3 using the command
$ sudo apt-get install  gcc-4.0  make
but there's an error telling me that the system can't find the package but i am on its directory.... 

I also tried installing the linux header but same problem arises.
please help me....

---

### Post by Greycloak on 2006-08-17
> Compiling utility make not found

Try this:

```
sudo apt-get install make
```

---

