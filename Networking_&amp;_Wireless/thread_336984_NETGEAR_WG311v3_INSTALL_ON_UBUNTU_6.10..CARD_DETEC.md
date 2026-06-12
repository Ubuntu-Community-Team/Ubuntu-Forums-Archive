---
title: "NETGEAR WG311v3 INSTALL ON UBUNTU 6.10..CARD DETECTED BUT NO CONNECTION...HELP"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by aggie333 on 2007-01-12
hi guys,
   im tryin to install the above mentioned card and im facing problems doing it....i used ndiswrapper-1.8 to install the drivers...the card is being detected but i am not able to configure the card...i tried installing network manager but there was an error saying "networking->tools 28pre29 not installed or not active"...i then installed madwifi...it is able to scan for the available networks but is not able to connect to them...i cannot overwrite parameters with iwconfig..(when i try to do so they remain the same..)...i live in a apartment block with about 10 open routers in it so i cannot give a specific ESSID or WEP key... will try installin the drivers with ndiswrapper-1.34 now but in the mean while im hopin some one will be able to figure out what the problem is...
 

#lspci
root@linmach:~/Desktop/NetworkManager-0.6.4# lspci
00:00.0 Host bridge: Intel Corporation 82815 815 

Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
root@linmach:~/Desktop/NetworkManager-0.6.4# #iwconfig o/p  
lo        no wireless extensions
eth0      no wireless extensions
wlan0     IEEE 802.11b  ESSID:"HotSite8B"  Nickname:"HotSite8B"

          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:E0:63:81:F3:3F   
          Bit Rate=11 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off          Power Management:off 
          Link Quality:100/100  Signal level:-67 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0       
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions



# ifconfig
eth0     Link encap:Ethernet  HWaddr 00:04:76:36:12:A7  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0     
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000        RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
         Interrupt:9 Base address:0xc00 
lo       Link encap:Local Loopback     
         inet addr:127.0.0.1  Mask:255.0.0.0          inet6 addr: ::1/128 Scope:Host     
         UP LOOPBACK RUNNING  MTU:16436  Metric:1       
         RX packets:2028 errors:0 dropped:0 overruns:0 frame:0       
         TX packets:2028 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:0     
         RX bytes:153800 (150.1 KiB)  TX bytes:153800 (150.1 KiB)
root@linmach:~/Desktop/NetworkManager-0.6.4



# iwconfig o/p
lo        no wireless extensions
eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:"HotSite8B"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B     
          Encryption key:off          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions
root@linmach:~/Desktop/NetworkManager-0.6.4



#ifdown o/p
root@linmach:~/Desktop/NetworkManager-0.6.4# ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:c4:cb:5d
Sending on   LPF/wlan0/00:14:6c:c4:cb:5d
Sending on   Socket/fallback
wlanctl-ng: Operation not supported
root@linmach:~/Desktop/NetworkManager-0.6.4



# ifup wlano
Ignoring unknown interface wlano=wlano.
root@linmach:~/Desktop/NetworkManager-0.6.4# ifup wlan0
wlanctl-ng: Operation not supported
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/wlan0/00:14:6c:c4:cb:5d
Sending on   LPF/wlan0/00:14:6c:c4:cb:5d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
root@linmach:~/Desktop/NetworkManager-0.6.4



#interfaces file
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
wireless-essid Hotsite8B
wireless-key s:



#network manager install output
root@linmach:~/Desktop/NetworkManager-0.6.4# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type...i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directoryGNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for mode_t... yes
checking for pid_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for select... yes
checking for socket... yes
checking for uname... yes
checking for intltool >= 0.27.2... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv.../usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  bg bs ca cs da de el en_CA en_GB es fi fr gu hr hu it ja ko lt pl mk nb ne nl pa 
pt_BR rw sk sq sr@Latn sr sv uk vi wa zh_CN zh_TW
checking for /etc/redhat-release... no
checking for /etc/SuSE-release... no
checking for /etc/fedora-release... no
checking for /etc/gentoo-release... no
checking for /etc/debian_version... yes
checking for /etc/arch-release... no
checking for /etc/slackware-version... no
checking for wireless-tools >= 28pre9... no
configure: error: wireless-tools >= 28pre9 not installed or not functional
root@linmach:~/Desktop/NetworkManager-0.6.4#

---

### Post by phossal on 2007-01-12
What is the output to:
```
ndiswrapper -l
```

---

### Post by aggie333 on 2007-01-12
hey,
the output to tat is-
wg311v3 : driver installed
device(11AB:1FAA) present

i uninstalled ndiswrapper1.8 and installed ndiswrapper1.34 and reinstalled the drivers....still no luck...](*,)

---

### Post by phossal on 2007-01-12
I recommend turning off any wep/wpa on the router, even if there are other routers in your area without wep/wpa. I recommend using iwconfig exclusively, without any of the gui tools. I recommend issuing the command using *sudo*, so your command looks like this (where wlan0 is your wireless interface):
```
sudo iwconfig wlan0 essid <routerESSID> channel <channel> 
```

Finally, I recommend immediately trying (where wlan0 is your wireless interface):
```
sudo dhclient wlan0
```

---

