---
title: "rtl8192eu on Ubuntu 15.10 doesn't work but it does on Ubuntu 14.04 and 15.04"
date: 2015-11-01
forum: Networking &amp; Wireless
---

### Post by Unaxx on 2015-11-01
Hi, I have a issue with rtl8192eu drivers, but on Ubuntu 15.10 (amd64). The network wifi usb [adpater]("http://www.acteck.com.mx/producto.php?id=LKAD-403&fam=LINK%20IT") works on Ubuntu 14.04 and 15.04 but not on 15.10 (amd64). 
I have tried to install the deb file drive dkms_rtl8192eu_4.3.1.1.11320.20140505_all.deb and add "EXTRA_CFLAGS += -Wno-date-time" to the make file. But it throw an error that you can see on "make.log" file. **I do the same on Ubuntu 14.04 and 15.04 and it works fine. **
Can anybody help me? Anyone have any suggestions?

Make.log file
> DKMS make.log for rtl8192eu-4.3.1.1.11320.20140505 for kernel 4.2.0-16-generic (x86_64)
dom nov  1 01:28:18 CST 2015
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.2.0-16-generic/build M=/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-16-generic'
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_beamforming.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/rtw_odm.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/os_intfs.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/usb_intf.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/usb_ops_linux.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/ioctl_linux.o
/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/ioctl_linux.c: In function &#8216;translate_scan&#8217;:
/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/ioctl_linux.c:771:1: warning: the frame size of 1200 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/xmit_linux.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/mlme_linux.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/recv_linux.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/wifi_regd.o
  CC [M]  /var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/rtw_android.o
/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/rtw_android.c: In function &#8216;rtw_android_cmdstr_to_num&#8217;:
/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/rtw_android.c:340:11: error: implicit declaration of function &#8216;strnicmp&#8217; [-Werror=implicit-function-declaration]
   if(0 == strnicmp(cmdstr , android_wifi_cmd_str[cmd_num], strlen(android_wifi_cmd_str[cmd_num])) )
           ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/rtw_android.o' failed
make[2]: *** [/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build/os_dep/linux/rtw_android.o] Error 1
Makefile:1398: recipe for target '_module_/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build' failed
make[1]: *** [_module_/var/lib/dkms/rtl8192eu/4.3.1.1.11320.20140505/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic'
Makefile:1324: recipe for target 'modules' failed
make: *** [modules] Error 2

---

### Post by subbia2 on 2015-11-03
I've got this working on my system. A bit of patches needed:
- Makefile, add these bits: 
  - EXTRA_CFLAGS += -I/usr/include
  - EXTRA_CFLAGS += -I/usr/include/x86_64-linux-gnu

- rtw_android.c add:
  - #include <string.h> and substitute strnicmp with strcasecmp as per [https://en.wikipedia.org/wiki/C_string_handling](https://en.wikipedia.org/wiki/C_string_handling)
- hal_com_phycfg.c comment the declaration of file_path. It's wrong and it is used in the standard way in this file.

run dkms autoinstall and modprobe 8192eu to get your wifi working again.

I'm running my hostapd again :)

---

### Post by praseodym on 2015-11-03
What about attaching the driver with the patches included?

---

### Post by subbia2 on 2015-11-05
[ATTACH]265375[/ATTACH][ATTACH]265376[/ATTACH]

These two files are renamed. Take away the .zip. Use 7zip to open (split archive for size limit on the forum). It's the same name of the old module. I just run dkms mkdeb from the patched sources I used to build my version. First time I do so, so please apologize if I got it wrong.

Hope this helps. :)

---

### Post by Unaxx on 2015-11-08
I tried to install the deb file you provided, and this gives the following error in a clean ubuntu 15.10 installation.


> Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 177794 files and directories currently installed.)
Preparing to unpack .../rtl8192eu-dkms_4.3.1.1.11320.20140505_allFInal.deb ...
Error! There are no instances of module: rtl8192eu
4.3.1.1.11320.20140505 located in the DKMS tree.
dpkg: warning: subprocess old pre-removal script returned error exit status 3
dpkg: trying script from the new package instead ...
dpkg: ... it looks like that went OK
Unpacking rtl8192eu-dkms (4.3.1.1.11320.20140505) over (4.3.1.1.11320.20140505) ...
Setting up rtl8192eu-dkms (4.3.1.1.11320.20140505) ...
Error! rtl8192eu-4.3.1.1.11320.20151105 is already added!
Aborting.


Unable to load DKMS tarball /usr/share/rtl8192eu-dkms/rtl8192eu-4.3.1.1.11320.20140505.dkms.tar.gz.
Common causes include: 
 - You must be using DKMS 2.1.0.0 or later to support binaries only
   distribution specific archives.
 - Corrupt distribution specific archive


dpkg: error processing package rtl8192eu-dkms (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rtl8192eu-dkms

I tried to follow your steps and do it myself, but it is complex. Also, once your file deb is installed, I can not install another driver, and I can uninstall your deb file.

---

### Post by subbia2 on 2015-11-10
Try these 4 commands to make it working (assuming you run the dpkg -i of the deb file):
```

apt-get -f install (clean apt history. That will leave the sources files of the module behind)
dkms add -m rtl8192eu -v 4.3.1.1.11320.20140505
dkms build -m rtl8192eu -v 4.3.1.1.11320.20140505
dkms install -m rtl8192eu -v 4.3.1.1.11320.20140505

```
That is working on my Virtual Machine.

---

### Post by Unaxx on 2015-11-10
I did again a clean installation of Ubuntu 15.10. I executed the command "sudo dpkg -i" (and --install) and its throws me the following lines. I changed the filename thinking that it was the error. (I put [ ] to translate the lines). And I downloaded the file again thinking that it was corrupt or something. 

> benja @ benja-B85N-PHOENIX: / home $ sudo dpkg -i rtl8192eu-dkms_4.3.1.1.11320.20140505_all.deb 
[sudo] password for benja:
dpkg: [error processing file] rtl8192eu-dkms_4.3.1.1.11320.20140505_all.deb (--install): [You can not access the file: No such file or directory]
[Errors were encountered while processing] rtl8192eu-dkms_4.3.1.1.11320.20140505_all.deb
benja @ benja-B85N-PHOENIX: / home $ sudo dpkg --install rtl8192.deb
dpkg: [error processing file] rtl8192.deb (--install):
[You can not access the file: No such file or directory]
[Errors were encountered while processing] rtl8192.deb
benja @ benja-B85N-PHOENIX:

---

### Post by subbia2 on 2015-11-11
Attached new version. Same as before. take away the .zip from the names of both files. Open it with 7zip. Extract it. Then you'll get the deb file. Thanks!

---

### Post by Karan_Khanchandani on 2015-12-11
@subbia2: Thanks a lot man.!!! Worked like a charm.. :):)

---

### Post by subbia2 on 2016-01-06
> **Karan_Khanchandani said:**
> @subbia2: Thanks a lot man.!!! Worked like a charm.. :):)

Glad it worked well :)

Thanks!

---

### Post by brucele2 on 2016-02-02
hi guys, i have just try ubuntu mate and i have the same device rtl8192eu [ chipset (0bda:818b)]("https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-"), i would like to know if i can use the file.
if yes there's a problem with the donwload file.
i will be glad to use my wifi doungle !

---

### Post by Pilot6 on 2016-02-26
I added this driver to ppa. It is easier to download it from there

[https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192eu-dkms_4.3.1.1.11320.20140505~wily_all.deb](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192eu-dkms_4.3.1.1.11320.20140505~wily_all.deb)

---

### Post by Pilot6 on 2016-02-26
> **brucele2 said:**
> hi guys, i have just try ubuntu mate and i have the same device rtl8192eu [ chipset (0bda:818b)]("https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8192EU-chipset-0bda:818b-"), i would like to know if i can use the file.
if yes there's a problem with the donwload file.
i will be glad to use my wifi doungle !

You can use this file. Or you can download it from my ppa. It is the same driver. You can also install it this way:

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms

---

### Post by Unaxx on 2016-03-04
> **Pilot6 said:**
> You can use this file. Or you can download it from my ppa. It is the same driver. You can also install it this way:

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms

Hi,does it work with Ubuntu 16.04?

---

### Post by Pilot6 on 2016-03-05
It does not work with 16.04 yet with these commands, but you can directly download the deb.

[https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192eu-dkms_4.3.1.1.11320.20140505~wily_all.deb](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192eu-dkms_4.3.1.1.11320.20140505~wily_all.deb)

---

### Post by Pilot6 on 2016-03-21
I built a package for 16.04 and updated 14.04 package to support kernel 4.4.

---

### Post by Pilot6 on 2016-04-02
The PPA ppa:hanipouspilot/rtlwifi
now contains drivers for all supported Ubuntu releases and xenial.

For xenial I added version 4.3.8.

---

### Post by Unaxx on 2016-04-16
> **Pilot6 said:**
> The PPA ppa:hanipouspilot/rtlwifi
now contains drivers for all supported Ubuntu releases and xenial.

For xenial I added version 4.3.8.

Ohhh!! It finally works!!! Thanks alot! Im on Ubuntu 16.04!

---

### Post by Unaxx on 2016-04-19
Sometime the drive/module (I dont know) does not load... I add rtl8192eu 8192eu to /etc/modules-load.d/modules.conf
I think it solve the issue but Im not sure if it the solution because I dont know what the problem is
Thanks. 
Im using ubuntu 16.04

---

### Post by dirk-vanda on 2016-08-04
> **Pilot6 said:**
> You can use this file. Or you can download it from my ppa. It is the same driver. You can also install it this way:

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms

I have Ubuntu 16.04 and ran these commands and rebooted. When I plugged in the wifi dongle, it worked :).
But when I reboot with the dongle plugged in, it doesn't work until I remove it and plug it back in :(.
Who can this be fixed? How can the dongle work without plugging it out and in? 
Can anyone help? I am new in ubuntu.

---

