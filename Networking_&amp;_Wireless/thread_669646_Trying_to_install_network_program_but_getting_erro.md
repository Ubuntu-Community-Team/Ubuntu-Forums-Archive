---
title: "Trying to install network program but getting error on &quot;Make&quot;"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by osonegro on 2008-01-16
I am trying to install a program that came as a tar file. I got it to configure but when I run "make" I get the following error messages:

-------------------------------------------------------------------------------------
make all-recursive
make[1]: Entering directory `/usr/local/src/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/usr/local/src/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c:9:18: error: pcap.h: No such file or directory
In file included from PacketSource.h:31,
from callbacks.c:24:
/usr/include/linux/wireless.h:650: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:663: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:677: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:688: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:704: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:717: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:744: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:806: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:820: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:834: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:842: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:851: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:863: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:886: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:901: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:945: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1046: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1064: error: expected specifier-qualifier-list before ‘__u16’
In file included from callbacks.c:24:
PacketSource.h:153: error: expected specifier-qualifier-list before ‘pcap_t’
PacketSource.h:178: warning: ‘struct pcap_pkthdr’ declared inside parameter list
PacketSource.h:178: warning: its scope is only this definition or declaration, which is probably not what you want
PacketSource.h:179: warning: ‘struct pcap_pkthdr’ declared inside parameter list
callbacks.c:79: error: ‘PCAP_ERRBUF_SIZE’ undeclared here (not in a function)
callbacks.c: In function ‘fillDeviceList’:
callbacks.c:121: error: storage size of ‘ir’ isn’t known
callbacks.c:129: error: ‘IFF_LOOPBACK’ undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/usr/local/src/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/airsnort-0.2.7e'
make: *** [all] Error 2
--------------------------------------------------------------------------------
Lots of errors but I don't know where to go from here... HELP!

---

### Post by sqrt2 on 2008-01-16
sudo apt-get install libpcap-dev

---

### Post by osonegro on 2008-01-16
I did what you suggest but this is still what I get:

--------------------------------------------
root@oso-desktop:/usr/local/src/airsnort-0.2.7e# make
make  all-recursive
make[1]: Entering directory `/usr/local/src/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/usr/local/src/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
        then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
In file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:650: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:663: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:677: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:688: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:704: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:717: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:744: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:806: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:820: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:834: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:842: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:851: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:863: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:886: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:901: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:945: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1046: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1064: error: expected specifier-qualifier-list before ‘__u16’
callbacks.c: In function ‘fillDeviceList’:
callbacks.c:121: error: storage size of ‘ir’ isn’t known
callbacks.c:129: error: ‘IFF_LOOPBACK’ undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/usr/local/src/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/airsnort-0.2.7e'
make: *** [all] Error 2
root@oso-desktop:/usr/local/src/airsnort-0.2.7e# 
----------------------------------------------------------

I think it got me a little further but no cigar!!

---

### Post by odiseo77 on 2008-01-16
airsnort is already on Gutsy's repositories, so all you have to do is install it with apt-get/aptitude/synaptic.

---

### Post by osonegro on 2008-01-18
Your right I also found the file in the Snaptic package manager.  I tried this program but had the wrong card for use with it so unintalled it.

However, I would still like to pursue this thread as sometime in the future I might need to install a program that is not in one of the packages... or maybe I should just tackle that when the bridge has to be crossed.

---

### Post by sqrt2 on 2008-01-18
I also just tried compiling airsnort on my system and experienced the same errors. What worked for me was adding the includes <linux/if.h> and <linux/types.h> to the files that failed compiling.
 
 Anyway, the problem you experienced here is limited to a small percentage of all software you could possibly want to compile. If you're not interested in airsnort anyway, you don't have to bother fixing the problem. Furthermore, the exact solution will vary for each piece of software that won't compile because of this problem.

---

