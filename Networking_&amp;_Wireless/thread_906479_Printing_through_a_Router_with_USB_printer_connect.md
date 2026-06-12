---
title: "Printing through a Router with USB printer connected to router"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by nicenick on 2008-08-31
Sorry for long message, but wanted to be complete as possible

System Information:

Ubuntu
Release 8.04 (hardy)
Kernel Linux 2.6.24-19-generic

Hardware
Memory 725.2 MiB
Processor Mobil AMD Athlon XP-M Processor 2800T

Systems Connected
Windows XP Desktop (wired) to US Robotics Router / USB print server
Windows Vista Laptop (wireless) to US Robotics Router / USB print server
Ubuntu Desktop (wired) to US Robotics Router / USB print server

Printer
HP PSC 1310 connected to US Robotics USB print server port

US Robotics Router / USB print server information

Name: USRobotics Wireless MAXg Router (USR5465)
 Current time: Sun, 31 Aug 2008 09:16:18 
Firmware: 4.139.6.1.2 (May 16 2007) Boot loader: CFE 4.139.6.1.0 
Printer status: Ready 
Printer location: [http://192.168.2.1:1631/printers/My_Printer](http://192.168.2.1:1631/printers/My_Printer)

Process I followed

Step 1
connected printer directly to Vista laptop, found new hardware, installed printer test page OK
connected printer directly to XP Desktop, found new hardware, installed printer test page OK
connected printer directly to Ubuntu Desktop, found printer, test page OK.

Step 2
Connected printer to US Robotics USB print server port
Connected XP desktop to Router port (wired)  found printer prints OK
Connected Vista Laptop to Router Wireless (found network etc) found printer prints OK
Connected Ubuntu Desktop to Router (wired) 

System > Administration> Printing

Please see attached picture .PNG format

Select Print Test Page
Print State: changes from Idle to Processing

I have waited 2 to 3 minutes but the printer does nothing, I Canel job and Printer State returns to Idle.

I have tried at least 5 different tutorials, nothing helps.

Again, plug in printer directly to Desktop. Printer works, back to USB print server, never prints.


From one of the tutorials, here is the result of hp-check -r

nick@nick-desktop:~$ sudo hp-check -r 
[sudo] password for nick: 

HP Linux Imaging and Printing System (ver. 2.8.2) 
Dependency/Version Check Utility ver. 13.0 

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP 
This software comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to distribute it 
under certain conditions. See COPYING file for more details. 

Note: hp-check can be run in three modes: 
1. Compile-time check mode (-c or --compile): Use this mode before compiling the 
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies 
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log 

Initializing. Please wait... 
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/ 

--------------- 
| SYSTEM INFO | 
--------------- 

Basic system information: 
Linux nick-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux 

Distribution: 
ubuntu 8.04 

HPOJ running? 
No, HPOJ is not running (OK). 

Checking Python version... 
OK, version 2.5.2 installed 

Checking PyQt version... 
OK, version 3.17 installed. 

Checking SIP version... 
error: SIP not installed or version not found. 

Checking for CUPS... 
Status: scheduler is running 
error: Version: (Not available. CUPS may not be installed or not running.) 


------------------------ 
| RUNTIME DEPENDENCIES | 
------------------------ 


Checking for dependency: cups - Common Unix Printing System... 
OK, found. 

Checking for dependency: cups-ddk - CUPS driver development kit... 
OK, found. 

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer... 
OK, found. 

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)... 
OK, found. 

Checking for dependency: ppdev - Parallel port support kernel module.... 
OK, found. 

Checking for dependency: PyQt - Qt interface for Python... 
OK, found. 

Checking for dependency: Python 2.3 or greater - Required for fax functionality... 
OK, found. 

Checking for dependency: Reportlab - PDF library for Python... 
OK, found. 

Checking for dependency: SANE - Scanning library... 
OK, found. 

Checking for dependency: scanimage - Shell scanning program... 
OK, found. 

Checking for dependency: xsane - Graphical scanner frontend for SANE... 
OK, found. 


---------------------- 
| HPLIP INSTALLATION | 
---------------------- 


Currently installed HPLIP version... 
HPLIP 2.8.2 currently installed in '/usr/share/hplip'. 

Current contents of '/etc/hp/hplip.conf' file: 
# hplip.conf.  Generated from hplip.conf.in by configure. 

[hpssd] 
# Note: hpssd does not support dynamic ports 
# Port 2207 is the IANA assigned port for hpssd 
port=2207 

[hplip] 
version=2.8.2 

[dirs] 
home=/usr/share/hplip 
run=/var/run 
ppd=/usr/share/ppd/hpijs/HP 
ppdbase=/usr/share/ppd/hpijs 
doc=/usr/share/doc/hplip-doc/HTML 
icon=no 
cupsbackend=/usr/lib/cups/backend 
cupsfilter=/usr/lib/cups/filter 
drv=/usr/share/cups/drv 

# Following values are determined at configure time and cannot be changed. 
[configure] 
network-build=yes 
pp-build=yes 
gui-build=yes 
scanner-build=yes 
fax-build=yes 
cups11-build=no 
doc-build=yes 
shadow-build=no 
foomatic-drv-install=yes 
foomatic-ppd-install=no 
foomatic-rip-hplip-install=no 
internal-tag=2.8.2.10 


------------------------------- 
| DISCOVERED PARALLEL DEVICES | 
------------------------------- 

No devices found. 

-------------------------- 
| DISCOVERED USB DEVICES | 
-------------------------- 

No devices found. 

--------------------------------- 
| INSTALLED CUPS PRINTER QUEUES | 
--------------------------------- 

 
PDF 
--- 
Type: Unknown 
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend. 
Device URI: cups-pdf:/ 
PPD: /etc/cups/ppd/PDF.ppd 
PPD Description: Generic PDF file generator 
Printer status: printer PDF is idle.  enabled since Sat 20 Oct 2007 08:30:19 AM EDT 
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP. 
usbprinter 
---------- 
Type: Unknown 
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend. 
Device URI: [http://192.168.2.1:1631/printers/My_Printer](http://192.168.2.1:1631/printers/My_Printer) 
PPD: /etc/cups/ppd/usbprinter.ppd 
PPD Description: HP PSC 1310 Foomatic/hpijs, hpijs 2.8.2 
Printer status: printer usbprinter is idle.  enabled since Sun 31 Aug 2008 12:53:44 PM ENo %%BoundingBox: comment in header! 
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP. 

---------------------- 
| SANE CONFIGURATION | 
---------------------- 

'hpaio' in '/etc/sane.d/dll.conf'... 
error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf). 

Checking output of 'scanimage -L'... 
 
No scanners were identified. If you were expecting something different, 
check that the scanner is plugged in, turned on and detected by the 
sane-find-scanner tool (if appropriate). Please read the documentation 
which came with this software (README, FAQ, manpages). 


--------------------- 
| PYTHON EXTENSIONS | 
--------------------- 

Checking 'cupsext' CUPS extension... 
OK, found. 

Checking 'pcardext' Photocard extension... 
OK, found. 

Checking 'hpmudext' I/O extension... 
OK, found. 

Checking 'scanext' SANE scanning extension... 
OK, found. 


----------------- 
| USB I/O SETUP | 
----------------- 


Checking for permissions of USB attached printers... 
 
----------- 
| SUMMARY | 
----------- 

error: 5 errors and/or warnings. 

Please refer to the installation instructions at: 
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html) 


Can anyone help me get my Ubuntu Desktop to print?

Thanks Very Much

---

### Post by pfdevil on 2008-08-31
Could you just make sure that there is no ip clash with your linux pc and the printer. Just check if there ip's are different and that they are in the same range.

---

### Post by nicenick on 2008-08-31
Glad to, but I don't know how.

---

### Post by nicenick on 2008-08-31
Maybe this will help.
System > Administration > Network Settings
Local Hosts
127.0.0.1 local host
127.0.1.1 Nick-desktop

---

### Post by pfdevil on 2008-08-31
Open up a terminal and type ifconfig, paste the output here.

Cheers

---

### Post by nicenick on 2008-08-31
nick@nick-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:ec:5d:55:2a  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ecff:fe5d:552a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20059851 (19.1 MB)  TX bytes:2314621 (2.2 MB)
          Interrupt:22 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1288281 (1.2 MB)  TX bytes:1288281 (1.2 MB)

---

### Post by pfdevil on 2008-08-31
the ip of your pc is 192.168.2.2 . So that is o.k, could you just maybe check if the other windows computers has the same ip as that. Also try to browse the printer from linux, by opening a firefox and typing [http://192.168.2.1](http://192.168.2.1)

---

### Post by nicenick on 2008-09-01
Browse the Router at 192.168.2.1 works.  I can find many pages of setup info.
Windows XP desktop TC/pip won't show me an address it is set up to get an IP automatically., However the printer on XP machine is shown as 192.168.2.1:1631 with the http port showing My_Printer.

Regards,
Nice Nick

---

### Post by collegeKid28 on 2009-02-15
Also a problem for me.  I have a WRT54GL v1.1 router and I'm trying to print from my laptop through the router.  I setup/printed via USB no problems, however, I'm not able to print through router.  Any suggestions?

Thanks


Edit: This has been solved for me.

---

### Post by douham on 2009-02-28
> **collegeKid28 said:**
> Also a problem for me.  I have a WRT54GL v1.1 router and I'm trying to print from my laptop through the router.  I setup/printed via USB no problems, however, I'm not able to print through router.  Any suggestions?

Thanks


Edit: This has been solved for me.

Hi collegeKid28, would you be able to post how you managed to solve this problem, I'm sure the OP and myself would like to know how you solved printing via USB on router.
Doug

---

### Post by sgosnell on 2009-03-01
What has always worked for me is to just install a new printer, specify that it's a network printer, and Ubuntu finds it.  I've done it on both Brother and HP printers, and never had a glitch.  The HP software wouldn't even load on my XP box, but booting Ubuntu on it enabled all the HP functionality OOTB.

---

