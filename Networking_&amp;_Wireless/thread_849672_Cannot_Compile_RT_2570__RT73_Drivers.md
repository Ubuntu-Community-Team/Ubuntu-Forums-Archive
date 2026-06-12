---
title: "Cannot Compile RT 2570 / RT73 Drivers"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by blumnday99 on 2008-07-04
I'm trying to install some drivers for my HWUG1 (Ralink) wireless adapter.  I've tried downloading different RT2570 and RT73 tarballs and can't get the drivers to compile.  I got these drivers to work on Gutsy, but now it's not working on Hardy.  Here's the output from running 'make' on an RT 2570 tarball I downloaded.

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/mark/Desktop/rt2570/Module/rtusb_main.o
/home/mark/Desktop/rt2570/Module/rtusb_main.c: In function ‘usb_rtusb_probe’:
/home/mark/Desktop/rt2570/Module/rtusb_main.c:1964: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/mark/Desktop/rt2570/Module/rtusb_main.c:1984: error: ‘struct net_device’ has no member named ‘weight’
/home/mark/Desktop/rt2570/Module/rtusb_main.c:2015: error: too few arguments to function ‘first_net_device’
make[2]: *** [/home/mark/Desktop/rt2570/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/home/mark/Desktop/rt2570/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
rt2570.ko failed to build!
make: *** [module] Error 1


Anyone know what this is?  Is it a bug with the current linux kernel?

---

### Post by chili555 on 2008-07-04
Please check posts #2 and #4 here: [http://ubuntuforums.org/showthread.php?t=797823&highlight=2570](http://ubuntuforums.org/showthread.php?t=797823&highlight=2570)

---

### Post by blumnday99 on 2008-07-05
I tried 
wget [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
tar zxvf rt2570-cvs-daily.tar.gz
cd rt2570-cvs-2008051809/Module
sudo make
sudo make install


Output from sudo make install is 

2.6 module install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/mark/rt2570-cvs-2008070418/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  INSTALL /home/mark/rt2570-cvs-2008070418/Module/rt2570.ko
  DEPMOD  2.6.24.3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for rausb0

It looks like it installed correctly, but running sudo modprobe rt2570 gives me a "module not found" error.

---

### Post by lswb on 2008-07-05
can you verify that the rt2570.ko file was actually copied into the correct directory?

should be here, where the 2.6.24etc string is substitute your running kernel.
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2500.ko

Also you might be interested in the module-assistant package. 

I was playing with compiling the rt2500 driver for a pcmcia card before I installed a mini-pci card in my laptop. Just FYI if you didnt know, hardy uses the newer rt2xxxpci modules for ralink chips and you will need to blacklist or remove them to use the older rt2xxx modules. Also, NetworkManager does not work with the older modules, though wicd does as I recall.

---

### Post by chili555 on 2008-07-05
It should have installed here:```
/lib/modules/2.6.24-16-generic/extra/rt2570.ko
```Check with:```
sudo updatedb
locate 2570 | grep .ko
```

---

### Post by blumnday99 on 2008-07-05
there is no extras directory located in /lib/modules/2.6.24-16-generic/.  

I have the Hawking HWUG1 (Ralink chipset) and was using the RT73 drivers when I got it running in Gutsy.  I think I've installed some version of the RT73 driver and I can now detect the HWUG1 as device RAUSB0 but cannot put it into monitor mode.  I was looking through other threads and I believe I blacklisted the other drivers (RT73USB and some others) by adding them to a 'blacklist' file (can't remember which one it was) and then rebooting.  

Should I even be using the RT73 drivers or are the RT2570 drivers the correct one?  The aircrack-ng website lists RT73 as the correct drivers for the HWUG1.  Where can I get the correct updated drivers to place it in monitor mode? 

Sorry for all the questions...I had all this figured out in Gutsy, but I'm completely lost now.

---

### Post by chili555 on 2008-07-06
If you have it running now, let's find out which driver it's actually using. Please do:```
sudo lshw -C network
```It should show your wireless device and any ethernet devices you have. If the device has an associated driver, it will show. You might also do:```
lsmod | grep rt
```That will show any modules that are inserted and running with 'rt' in the name, such as rt73usb or rt2570 or rt-whatever.

You blacklist file can be read with:```
cat /etc/modprobe.d/blacklist
```To get my wireless card into monitor mode, I have to 'down' it first. Here is my sequence; substitute your interface name here:```
sudo ifdown eth1
sudo iwconfig eth1 mode monitor
```

---

### Post by blumnday99 on 2008-07-07
**sudo lshw -C network shows**

  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:70:a3:df
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.239 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:c3:26:9d
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:0e:3b:09:c3:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT73STA driverversion=1.1.0.0 firmware=514(769) link=no multicast=yes wireless=RT73 WLAN
**lsmod | grep rt shows**

rt73                  239756  1 
parport_pc             36260  0 
parport                37832  3 ppdev,parport_pc,lp
agpgart                34760  3 drm,intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
usbcore               146028  11 rt73,usblp,usb_storage,usbmouse,libusual,uvcvideo,usbkbd,usbhid,ehci_hcd,uhci_hcd

**Blacklist file contains the following**
#ADDED BY DWL SCRIPT:
blacklist rt2570
blacklist rt73usb
blacklist rt2500usb
blacklist rt2x00lib
#END.
[B]
sudo ifdown rausb0[/B] returns a "interface rausb0 not configured".

I used to run 
sudo ifconfig rausb0 up
sudo iwpriv rausb0 forceprism 1
sudo iwpriv rausb0 rfmontx 1
sudo iwconfig rausb0 mode monitor

to place the card in monitor mode when using Gutsy.  Will these commands no longer work?

Thanks for the help!

---

### Post by blumnday99 on 2008-07-13
*bump*

---

