---
title: "ndiswrapper with Linksys WPC54G TI ACX111"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by cracker on 2005-12-03
Hello everyone. I am having trouble getting my wireless card working. I know the card is being detected properly because lspci displays the proper chipset, and I know I have the right drivers because I have used them on a knoppix livecd, and the card worked. I think it has to do with the version of ndiswrapper being only 1.1, because I know the latest is 1.6. I tried to compile the latest version using the information found [here](https://wiki.ubuntu.com//SetupNdiswrapperHowto), but make deb failed with a 'command not found' error in gcc-version.sh. I also cannot get ndisgtk to install, because I cannot figure out what to do wtih this .diff file. [The tutorial](https://wiki.ubuntu.com/forum/hardware/ndiswrapper) states to install a deb package, but on the [download page](http://packages.ubuntu.com/breezy/net/ndisgtk) there is no deb package.

I know this card works with ndiswrapper 1.5 and newer. Can someone help me get it working?

---

### Post by cracker on 2005-12-03
Here is a full log of my attempt to compile ndiswrapper 1.6:

```
root@delli6000:/usr/src/ndiswrapper-1.6# make deb
make[1]: Entering directory `/usr/src/ndiswrapper-1.6'
make -f debian/rules binary-utils
make[2]: Entering directory `/usr/src/ndiswrapper-1.6'
sed -e 's/-#KVERS#//g' \
-e 's/#DRIVER_VERSION#/1.6/g' \
-e 's/#UTILS_VERSION#/1.6/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.utils > debian/changelog
sed -e 's/#DRIVER_VERSION#/1.6/' \
-e 's/#UTILS_VERSION#/1.6/' \
-e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
debian/control.utils > debian/control
echo "utils/loadndisdriver /sbin" > debian/ndiswrapper-utils.install
echo "utils/ndiswrapper /usr/sbin" >> debian/ndiswrapper-utils.install
echo "utils/ndiswrapper-buginfo /usr/sbin" >> \
        debian/ndiswrapper-utils.install
cp debian/dirs.utils debian/dirs
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installchangelogs: Compatibility levels before 3 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 3 are deprecated.
dh_installexamples
dh_installexamples: Compatibility levels before 3 are deprecated.
dh_installdebconf
dh_installdebconf: Compatibility levels before 3 are deprecated.
export DH_OPTIONS='-i'
dh_installman ndiswrapper.8
dh_installman: Compatibility levels before 3 are deprecated.
make -C utils
make[3]: Entering directory `/usr/src/ndiswrapper-1.6/utils'
gcc -g -Wall -DUTILS_VERSION=\"1.6\"  -o loadndisdriver loadndisdriver.c
make[3]: libusb-config: Command not found
** USB programming library "libusb" is not installed. It is needed for compiling load_fw_ar5523, which is required for loading firmware for Atheros USB driver. "libusb" can be downloaded from http://libusb.sourceforge.net.
make[3]: Leaving directory `/usr/src/ndiswrapper-1.6/utils'
dh_install
dh_install: Compatibility levels before 3 are deprecated.
dh_link
dh_link: Compatibility levels before 3 are deprecated.
dh_strip
dh_strip: Compatibility levels before 3 are deprecated.
dh_compress
dh_compress: Compatibility levels before 3 are deprecated.
dh_fixperms
dh_fixperms: Compatibility levels before 3 are deprecated.
dh_perl
dh_perl: Compatibility levels before 3 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 3 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 3 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 3 are deprecated.
dh_gencontrol
dh_gencontrol: Compatibility levels before 3 are deprecated.
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dh_md5sums
dh_md5sums: Compatibility levels before 3 are deprecated.
dh_builddeb --destdir=..
dh_builddeb: Compatibility levels before 3 are deprecated.
dpkg-deb: building package `ndiswrapper-utils' in `../ndiswrapper-utils_1.6-1_i386.deb'.
dh_clean
dh_clean: Compatibility levels before 3 are deprecated.
make[2]: Leaving directory `/usr/src/ndiswrapper-1.6'
make -f debian/rules binary-modules
make[2]: Entering directory `/usr/src/ndiswrapper-1.6'
sed -e 's/#KVERS#/2.6.12-9-386/g' \
-e 's/#DRIVER_VERSION#/1.6/g' \
-e 's/#UTILS_VERSION#/1.6/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.modules > debian/changelog
sed -e 's/#KVERS#/2.6.12-9-386/' \
-e 's/#DRIVER_VERSION#/1.6/' \
-e 's/#UTILS_VERSION#/1.6/' \
debian/control.modules > debian/control
sed -e 's/#KVERS#/2.6.12-9-386/' debian/postinst.modules > debian/postinst
if [ 6 == 4 ];then \
        module=ndiswrapper.o; \
else \
        module=ndiswrapper.ko; \
fi; \
echo "driver/$module /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper" \        > debian/ndiswrapper-modules-2.6.12-9-386.install
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installchangelogs: Compatibility levels before 3 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 3 are deprecated.
dh_installexamples
dh_installexamples: Compatibility levels before 3 are deprecated.
dh_installdebconf
dh_installdebconf: Compatibility levels before 3 are deprecated.
dh_installdirs lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
dh_installdirs: Compatibility levels before 3 are deprecated.
make -C /usr/src/ndiswrapper-1.6/driver
make[3]: Entering directory `/usr/src/ndiswrapper-1.6/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/usr/src/ndiswrapper-1.6/driver \
        DRIVER_VERSION=1.6
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[4]: gcc-3.4: Command not found
make[4]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  LD      /usr/src/ndiswrapper-1.6/driver/built-in.o
  CC [M]  /usr/src/ndiswrapper-1.6/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[5]: *** [/usr/src/ndiswrapper-1.6/driver/hal.o] Error 127
make[4]: *** [_module_/usr/src/ndiswrapper-1.6/driver] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/usr/src/ndiswrapper-1.6/driver'
make[2]: *** [build-modules] Error 2
make[2]: Leaving directory `/usr/src/ndiswrapper-1.6'
make[1]: *** [binary] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.6'
make: *** [deb] Error 2

```

---

### Post by Lambert on 2005-12-03
the TI chipset has a native driver in breezy. If you tried ndiswrapper 1.1 maybe you had a driver conflict with the acx111 driver. You may want to run this command to see if the acx111 driver is taking the primary spot with the device.

sudo lshw

find the device you're working with and a line configuration: in that section and you should see driver=xxxx if not then there is no driver.

As far as compiling I know little but did you install build-essentails and gcc3.4

---

### Post by cracker on 2005-12-03
The card is in that listing, and it does have a configuration line:

configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+

I noticed it uses driver 'acx_pci' but it is a pcmcia card. The main problem is, the card will not power up. All the drivers seem to be recognizing it, but the power light will not come on.

---

### Post by eJamesPC on 2005-12-03
Hi, I am also having a bear of a time getting the WPC54G v2 Linksys card working in Breezy.  I had no problemw with ndiswrapper on another distro.  For awhile I at least I got the power indicator to turn on, now nothing...

ndiswrapper -i LSTINDS.INF

Installed ndis drivers:
lstinds driver present, hardware present

wlan0     Link encap:Ethernet  HWaddr 00:12:17:B1:3D:06
          inet6 addr: fe80::212:17ff:feb1:3d06/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10

sudo lshw -C network
*-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@01:00.0
       logical name: wlan0
       version: 00
       serial: 00:12:17:b1:3d:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:c820000-c821fff iomemory:c800000-c81ffff irq:10

---

### Post by Lambert on 2005-12-03
1. So the acx_pci driver which is part of the breezy kernel build is loading and taking the driver spot for the device. Try to connect using this driver. system>admin>networking. You can click on the wirelesstroubleshootingguide in my signature and try to get connected using this driver. Make sure ndiswrapper is not loaded as you'll have a driver conflict 

modprobe -r ndiswrapper
(you may need to use sudo at begininning of command)

If you can get it working make sure you remove ndiswrapper from /etc/modules so it doesn't load.

2. If you can't get it working then you can try using windows drivers with ndiswrapper. make sure you remove the acx driver

modprobe -r acx_pci

If you get your device working with ndiswrapper then add this to a file /etc/hotplug/blacklist

blacklist acx_pci

This prevents the acx driver from loading on boot.

You may want to just use ndiswrapper 1.1 which is on the install cd or in the repositories. If that doesn't work and you want to continue trying to compile latest ndiswrapper somebody else will have to jump in. 

acx driver resource.
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#acx100]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#acx100")

---

### Post by eJamesPC on 2005-12-03
Hi Lambert, 
1. Don't have system>admin>networking (From KDE menu)
2. System Settings >> Networking - menu is off the bottom of the screen, only way I can log in as admin is to hit tab and then enter. 
3. sudo modprobe -r acx_pci and added blacklist to etc/modprobe.d with blacklist acx_pci

Rebooted: lshw -C network
 *-network DISABLED
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@01:00.0
       logical name: wlan0
       version: 00
       serial: 00:12:17:b1:3d:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:c820000-c821fff iomemory:c800000-c81ffff irq:10

Driver is still acx_pci (*Don't have ndiswrapper loading any drivers)

Thanks for the help.

---

### Post by cracker on 2005-12-03
Thanks a bunch Lambert, disabling acx_pci lit my card up instantly, and it was a breeze from there.

EDIT: Ok, Im having problems after rebooting. The blacklist isn't working. I had to create the file /etc/modprobe.d/blacklist and all it contains is blacklist acx_pci .

---

