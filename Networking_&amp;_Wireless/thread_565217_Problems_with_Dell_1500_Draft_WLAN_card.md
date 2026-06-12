---
title: "Problems with Dell 1500 Draft WLAN card"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by Rana1974 on 2007-10-02
Hi,
I was trying to get my Dell 1500 Draft WLAN minicard 802.11n to work using the method described in [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-1df44a09e46a94f274aeed9eb3ba3bbd3bf1215c](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-1df44a09e46a94f274aeed9eb3ba3bbd3bf1215c)

I was able to get to the stage of downloading the driver and un ziping it (I am suspecting that this shold not have been done however as the sample file and the driver both had.exe extensions so I did it anyway...). The following is the terminal data that I copied and saved for future reference...in case I land in trouble ..which I did..:-( I hope I can put the details here or is there a place I can upload the files too? 


rn@ubuntu:~$ tar xvzf ndiswrapper-1.28.tar.gz
tar: ndiswrapper-1.28.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rn@ubuntu:~$ tar xvzf ndiswrapper-1.48.tar.gz
ndiswrapper-1.48/
ndiswrapper-1.48/AUTHORS
ndiswrapper-1.48/ChangeLog
ndiswrapper-1.48/INSTALL
ndiswrapper-1.48/Makefile
ndiswrapper-1.48/README
ndiswrapper-1.48/ndiswrapper.spec
ndiswrapper-1.48/ndiswrapper.8
ndiswrapper-1.48/loadndisdriver.8
ndiswrapper-1.48/utils/
ndiswrapper-1.48/utils/Makefile
ndiswrapper-1.48/utils/ndiswrapper
ndiswrapper-1.48/utils/loadndisdriver.c
ndiswrapper-1.48/utils/ndiswrapper-buginfo
ndiswrapper-1.48/driver/
ndiswrapper-1.48/driver/divdi3.c
ndiswrapper-1.48/driver/hal.c
ndiswrapper-1.48/driver/iw_ndis.c
ndiswrapper-1.48/driver/iw_ndis.h
ndiswrapper-1.48/driver/loader.c
ndiswrapper-1.48/driver/loader.h
ndiswrapper-1.48/driver/longlong.h
ndiswrapper-1.48/driver/Makefile
ndiswrapper-1.48/driver/crt.c
ndiswrapper-1.48/driver/ndis.c
ndiswrapper-1.48/driver/ndis.h
ndiswrapper-1.48/driver/ndiswrapper.h
ndiswrapper-1.48/driver/ntoskernel.c
ndiswrapper-1.48/driver/ntoskernel.h
ndiswrapper-1.48/driver/ntoskernel_io.c
ndiswrapper-1.48/driver/pe_linker.c
ndiswrapper-1.48/driver/pe_linker.h
ndiswrapper-1.48/driver/pnp.c
ndiswrapper-1.48/driver/pnp.h
ndiswrapper-1.48/driver/proc.c
ndiswrapper-1.48/driver/rtl.c
ndiswrapper-1.48/driver/usb.c
ndiswrapper-1.48/driver/usb.h
ndiswrapper-1.48/driver/winnt_types.h
ndiswrapper-1.48/driver/workqueue.c
ndiswrapper-1.48/driver/wrapmem.h
ndiswrapper-1.48/driver/wrapmem.c
ndiswrapper-1.48/driver/wrapper.c
ndiswrapper-1.48/driver/wrapndis.h
ndiswrapper-1.48/driver/wrapndis.c
ndiswrapper-1.48/driver/lin2win.h
ndiswrapper-1.48/driver/win2lin_stubs.S
rn@ubuntu:~$ cd ndiswrapper-1.48
rn@ubuntu:~/ndiswrapper-1.48$ 
rn@ubuntu:~/ndiswrapper-1.48$ make distclean
make -C driver clean
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/driver'
make -C utils clean
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/utils'
rm -f *~
rm -fr ndiswrapper-1.48 ndiswrapper-1.48.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/driver'
make -C utils distclean
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/utils'
rm -f .\#*
rn@ubuntu:~/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/rn/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /home/rn/ndiswrapper-1.48/driver/built-in.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/crt.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/hal.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/iw_ndis.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/loader.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/ndis.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/ntoskernel.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/ntoskernel_io.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/pe_linker.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/pnp.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/proc.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/rtl.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/wrapmem.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/wrapndis.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/wrapper.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/usb.o
  CC [M]  /home/rn/ndiswrapper-1.48/driver/divdi3.o
  LD [M]  /home/rn/ndiswrapper-1.48/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rn/ndiswrapper-1.48/driver/ndiswrapper.mod.o
  LD [M]  /home/rn/ndiswrapper-1.48/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/driver'
make -C utils
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/utils'
rn@ubuntu:~/ndiswrapper-1.48$ sudo make install
make -C driver install
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/rn/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/driver'
make -C utils install
make[1]: Entering directory `/home/rn/ndiswrapper-1.48/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/rn/ndiswrapper-1.48/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
rn@ubuntu:~/ndiswrapper-1.48$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48
vermagic:       2.6.20-16-generic SMP mod_unload 586 
rn@ubuntu:~/ndiswrapper-1.48$ gksudo gedit /etc/apt/sources.list
rn@ubuntu:~/ndiswrapper-1.48$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 5B in 0s (6B/s)  
Reading package lists... Done
rn@ubuntu:~/ndiswrapper-1.48$ sudo apt-get install cabextract unzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unzip is already the newest version.
The following NEW packages will be installed:
  cabextract
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 53.9kB of archives.
After unpacking 188kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe cabextract 1.2-2 [53.9kB]
Fetched 53.9kB in 0s (84.8kB/s)
Selecting previously deselected package cabextract.
(Reading database ... 106596 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.2-2_i386.deb) ...
Setting up cabextract (1.2-2) ...
rn@ubuntu:~/ndiswrapper-1.48$ cd ~
rn@ubuntu:~$ mkdir bcm4311
rn@ubuntu:~$ mv R140747.exe bcm4311
mv: cannot stat `R140747.exe': No such file or directory
rn@ubuntu:~$ cd bcm4311
rn@ubuntu:~/bcm4311$ ls
R140747.EXE
rn@ubuntu:~/bcm4311$ cabextract R140747.EXE
R140747.EXE: no valid cabinets found

All done, errors in processing 1 file(s)
rn@ubuntu:~/bcm4311$ unzip R140747.EXE
Archive:  R140747.EXE
  inflating: msvcr71.DLL             
  inflating: preflib.dll             
  inflating: README.rtf              
  inflating: setup.exe               
  inflating: setup.inx               
  inflating: Setup.ini               
  inflating: setup.iss               
  inflating: WLBCGCBPRO731.DLL       
  inflating: wltray.exe              
  inflating: wltrynt.dll             
  inflating: wltrysvc.exe            
  inflating: AMD64/atl71.dll         
  inflating: AMD64/BCMLogon64.dll    
  inflating: AMD64/bcmwlcpl64.cpl    
  inflating: AMD64/MFC71.DLL         
  inflating: AMD64/msvcp71.DLL       
  inflating: AMD64/msvcr71.DLL       
  inflating: DRIVER/bcm43xx.cat      
  inflating: DRIVER/bcm43xx64.cat    
  inflating: DRIVER/bcmwl5.inf       
  inflating: DRIVER/bcmwl5.sys       
  inflating: DRIVER/bcmwl564.sys     
  inflating: ATL71.DLL               
  inflating: bcm1xsup.dll            
  inflating: BCMLogon.dll            
  inflating: Bcmnpf64.sys            
  inflating: bcmwlcpl.cpl            
  inflating: bcmwlhlp.cab            
  inflating: bcmwlhlp.chm            
  inflating: bcmwliss.dll            
  inflating: bcmwlnpf.sys            
  inflating: bcmwlpkt.dll            
  inflating: bcmwls.ini              
  inflating: bcmwls32.exe            
  inflating: bcmwls64.exe            
  inflating: bcmwltry.exe            
  inflating: bcmwlu00.exe            
  inflating: data1.cab               
  inflating: data1.hdr               
  inflating: data2.cab               
  inflating: DellInfo.exe            
  inflating: DellInfo64.exe          
  inflating: dellinst.exe            
  inflating: ikernel.ex_             
  inflating: is.exe                  
 extracting: launcher.ini            
  inflating: layout.bin              
  inflating: MFC71.DLL               
  inflating: msvcp71.DLL             
  inflating: Version.txt             
rn@ubuntu:~/bcm4311$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
c[COLOR="Red"]ouldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
rn@ubuntu:~/bcm4311$ cd DRIVER[/COLOR]
rn@ubuntu:~/bcm4311/DRIVER$  sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
rn@ubuntu:~/bcm4311/DRIVER$ ndiswrapper -l
bcmwl5 : invalid driver!
rn@ubuntu:~/bcm4311/DRIVER$ cd bcm4311
bash: cd: bcm4311: No such file or directory
rn@ubuntu:~/bcm4311/DRIVER$ bcm4311
bash: bcm4311: command not found
rn@ubuntu:~/bcm4311/DRIVER$ 
rn@ubuntu:~$ cd bcm4311
rn@ubuntu:~/bcm4311$ ls
AMD64          bcmwlcpl.cpl  bcmwlu00.exe    launcher.ini  setup.inx
ATL71.DLL      bcmwlhlp.cab  data1.cab       layout.bin    setup.iss
bcm1xsup.dll   bcmwlhlp.chm  data1.hdr       MFC71.DLL     Version.txt
bcm43xx64.cat  bcmwliss.dll  data2.cab       msvcp71.DLL   WLBCGCBPRO731.DLL
bcm43xx.cat    bcmwlnpf.sys  DellInfo64.exe  msvcr71.DLL   wltray.exe
BCMLogon.dll   bcmwlpkt.dll  DellInfo.exe    preflib.dll   wltrynt.dll
Bcmnpf64.sys   bcmwls32.exe  dellinst.exe    R140747.EXE   wltrysvc.exe
bcmwl564.sys   bcmwls64.exe  DRIVER          README.rtf
bcmwl5.inf     bcmwls.ini    ikernel.ex_     setup.exe
bcmwl5.sys     bcmwltry.exe  is.exe          Setup.ini
rn@ubuntu:~/bcm4311$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
rn@ubuntu:~/bcm4311$ ndiswrapper -l
bcmwl5 : invalid driver!
rn@ubuntu:~/bcm4311$ ls /etc/ndiswrapper
bcmwl5
rn@ubuntu:~/bcm4311$ ls /etc/ndiswrapper/bcmwl5
rn@ubuntu:~/bcm4311$ ls /etc/ndiswrapper/bcmwl5
rn@ubuntu:~/bcm4311$ ls /etc/ndiswrapper/bcmwl5
rn@ubuntu:~/bcm4311$ ndiswrapper -l
bcmwl5 : invalid driver!
rn@ubuntu:~/bcm4311$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rn@ubuntu:~/bcm4311$ lspci -n
00:00.0 0600: 80[COLOR="Lime"].........a lot of them showed up...[/COLOR]
0c:00.0 0280: 14e4:4328 (rev 01).[COLOR="Lime"].this being my wlan card I think...[/COLOR]
rn@ubuntu:~/bcm4311$ cd
rn@ubuntu:~$ lspci -n
00:00.0 0600: 80.....
0c:00.0 0280: 14e4:4328 (rev 01)
rn@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
rn@ubuntu:~$ cd bcm4311
rn@ubuntu:~/bcm4311$ sudo ndiswrapper -a 14e4:4328 bcmwl5
driver 'bcmwl5' is not installed (properly)!
rn@ubuntu:~/bcm4311$ ls /etc/ndiswrapper
bcmwl5
rn@ubuntu:~/bcm4311$ ls /etc/ndiswrapper/bcmwl5
rn@ubuntu:~/bcm4311$ 
rn@ubuntu:~/bcm4311$ 

After extracting the  driver, the folder showed a sub folder called driver in it [Please see the line marked in red above], so I cut and paste all the files from there into the bcm4311 folder (i think i screwed up here)...to get the driver to install.
When I ckedked for the driver it says installed (not properly!).
Can anyone please help me rectify this problem?
I am using Ubuntu Fiesty 7.04 installed using wubi-7.04.04.
As I am new to this system I have tried to give as much information as possible. 
Thanks,
Rana.

---

### Post by noob12 on 2007-10-02
I recommend that you try this thread: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
The online installer should reinstall your ndiswrapper and the bcmwl5 driver properly.

---

