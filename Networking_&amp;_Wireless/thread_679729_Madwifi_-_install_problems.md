---
title: "Madwifi - install problems"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by smooveg on 2008-01-27
Help!! When running the "make" command for madwifi (downloaded v. 0.9.3.3 from madwifi.org), I get a mess of output. Can anyone help me interpret this and see how to fix it??

scott@scott-laptop:~/madwifi-0.9.3.3$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/scott/madwifi-0.9.3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /home/scott/madwifi-0.9.3.3/ath_hal/uudecode
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c: At top level:
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c: In function 'main':
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/scott/madwifi-0.9.3.3/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/scott/madwifi-0.9.3.3/ath_hal/uudecode] Error 1
make[2]: *** [/home/scott/madwifi-0.9.3.3/ath_hal] Error 2
make[1]: *** [_module_/home/scott/madwifi-0.9.3.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

---

### Post by kevdog on 2008-01-27
Do the following at the command line to install prerequisite packages to enable compiling capabilities

sudo aptitude install build-essential linux-headers-$(uname -r)

---

### Post by smooveg on 2008-01-27
Ok -- install went fine. Now, to the debugging!

The results of sudo ifconfig ath0 up are:
ath0: ERROR while getting interface flags: No such device

I am seeing this for my network scans:

scott@scott-laptop:~/madwifi-0.9.3.3$ **iwconfig**
[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.[/INDENT]

scott@scott-laptop:~/madwifi-0.9.3.3$ **lshw -C network**
[INDENT]*-network
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0[/INDENT]


       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:24:d7:fa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.100 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
scott@scott-laptop:~/madwifi-0.9.3.3$

---

### Post by kevdog on 2008-01-27
Ok, the driver is not associated with your wirless card.

Do the following:

sudo modprobe ath_pci

and then check dmesg (please do not post the entire file), for any error messages.  If there are any errors, they would be at the end of the file.

---

### Post by smooveg on 2008-01-27
> **kevdog said:**
> Ok, the driver is not associated with your wirless card.

Do the following:

sudo modprobe ath_pci

and then check dmesg (please do not post the entire file), for any error messages.  If there are any errors, they would be at the end of the file.

Here are the last couple of lines that seem to be addressing the ethernet and wireless devices:

[INDENT][ 2669.848000] wlan: 0.8.4.2 (0.9.3.3)
[ 2669.856000] ath_pci: 0.9.4.5 (0.9.3.3)
[ 2669.856000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 2669.856000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[ 2669.904000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[ 2669.904000] ACPI: PCI interrupt for device 0000:06:00.0 disabled[/INDENT]

---

### Post by smooveg on 2008-01-27
> **kevdog said:**
> Ok, the driver is not associated with your wirless card.

Do the following:

sudo modprobe ath_pci

and then check dmesg (please do not post the entire file), for any error messages.  If there are any errors, they would be at the end of the file.
More confusion!! I did the fix provided in this thread _[http://ubuntuforums.org/showthread.php?t=672800](http://ubuntuforums.org/showthread.php?t=672800)_ regarding an install of subversion and madwifi-ng. The install went fine, did another sudo modprobe ath_pci, and still dmesg shows

[ 2669.848000] wlan: 0.8.4.2 (0.9.3.3)
[ 2669.856000] ath_pci: 0.9.4.5 (0.9.3.3)
[ 2669.856000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 2669.856000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[ 2669.904000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[ 2669.904000] ACPI: PCI interrupt for device 0000:06:00.0 disabled

What am I missing here????????

---

### Post by kevdog on 2008-01-27
Did you look on the madwifi website and see specifically if you atheros based card was supported .. Check compatibility.

---

### Post by smooveg on 2008-01-27
> **kevdog said:**
> Did you look on the madwifi website and see specifically if you atheros based card was supported .. Check compatibility.

Good point -- yes, my AR5006EG chip is specifically mentioned as being supported, which is weird as to why I'm getting the Hal Status 13 error.

As you can see, I was able to load the ath_pci and wlan_scan_sta modules, but ifconfig still gives no results:

scott@scott-laptop:/$ lsmod
Module                  Size  Used by
ath_pci               114856  0
ath_hal               233952  1 ath_pci
wlan_scan_sta          14976  0
wlan                  211248  2 ath_pci,wlan_scan_sta
...

scott@scott-laptop:/$ lshw -C network
  *-network
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:24:d7:fa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.100 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

scott@scott-laptop:/$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device

NOW -- after toggling the wireless LAN switch, rebooting, I find this at the end of dmesg output:

[ 1491.984000] ath_pci: driver unloaded
[ 1491.984000] wlan: driver unloaded
[ 1491.988000] ath_hal: driver unloaded
[ 2316.052000] wlan: 0.8.4.2 (svn r2834)
[ 2703.904000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[ 2703.912000] ath_pci: 0.9.4.5 (svn r2834)
[ 2703.912000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[ 2703.912000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 2703.912000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[ 2703.916000] MadWifi: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
[ 2703.916000] ACPI: PCI interrupt for device 0000:06:00.0 disabled

---

### Post by smooveg on 2008-01-27
> **kevdog said:**
> Did you look on the madwifi website and see specifically if you atheros based card was supported .. Check compatibility.

I see this line in the driver compatibility note for my chip:

works with madwifi-r2153-20070224

It redirects to: [http://madwifi.org/changeset/2153](http://madwifi.org/changeset/2153)

...this may be going a little beyond my capabilities here, as I don't really understand what's happening with this link....:confused:

---

### Post by smooveg on 2008-01-27
> **kevdog said:**
> Did you look on the madwifi website and see specifically if you atheros based card was supported .. Check compatibility.

OK -- ONE more thing I see happening here is this:

scott@scott-laptop:/$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

This is even with ndiswrapper blacklisted. Do I need to also blacklist net5211, as well??

Hopefully  solution will arise....

---

### Post by kevdog on 2008-01-27
unload the driver

sudo modprobe -r ndiswrapper

and then retry loading the madwifi driver

sudo modprobe ath_pci

---

### Post by smooveg on 2008-01-27
> **kevdog said:**
> unload the driver

sudo modprobe -r ndiswrapper

and then retry loading the madwifi driver

sudo modprobe ath_pci

Well, beyond frustration, :mad:, I did a fresh install. I was going off a fresh install anyway, so nothing lost. Here are my default settings. Is a situation where you would recommend installing Madwifi, especially since there are no issues with ndiswrapper conflicting??

scott@scott-laptop:~$ lshw -C Network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:24:d7:fa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.100 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

scott@scott-laptop:~$ lsmod
ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci

Thanks again for helping out -- this thread is ending up all over the place.

---

### Post by kevdog on 2008-01-27
Ok, do the following b/c I found this on the madwifi site:

	Had to change order of module insertion. Works when order is:modprobe wlan_scan_sta,modprobe wlan_wep,modprobe ath_pci

Ok so unload any modules first.  This would include wlan_scan wlan_wep and any module beginning with ath found when you do a lsmod | grep ath statement.

After unloading the modules, load them up in the order specified above.  

I would definitely try a fresh compile of madwifi from svn if you can, if not a tar.gz would be ok.

Here is where I found the reference:
[http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG)

---

### Post by ugm6hr on 2008-02-03
Sorry, haven't read the whole thread, just trying to put AR5006/7 users in touch with potential solutions.

This may be of relevance:

[http://ubuntuforums.org/showpost.php?p=4259805&postcount=14](http://ubuntuforums.org/showpost.php?p=4259805&postcount=14)

---

### Post by kevdog on 2008-02-03
Good links ugm6hr!!!

---

