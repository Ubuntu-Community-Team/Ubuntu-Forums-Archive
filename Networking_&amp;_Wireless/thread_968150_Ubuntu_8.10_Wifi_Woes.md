---
title: "Ubuntu 8.10 Wifi Woes"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Haluci on 2008-11-02
Per the output of lspci, I have a 0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01) wireless card.  After installing Ubuntu, the hardware drivers tool offered me a wireless driver (fwcutter) for this wireless card.  After enabling this driver, my wi-fi card did not work.  So, following many tutorials on this forum, I tried ndiswrapper.  It appears that I have installed the driver ok, the output of ndiswrapper -l gives me this:

```
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: wl)
```

and the green light on my wifi card is on, but I still have no wireless.  I've tried nidswrapper -m and modprobe ndiswrapper with no success.

So, I suppose my question is if anybody has some troubleshooting ideas as to why my wireless card doesn't work, or if anybody knows of a good tutorial for configuring fwcutter.

Thanks!

EDIT: I'm trudging through the massive ndiswrapper post stickied here as you're reading this.  I'll update this as needed.

EDIT: here's my output from lshw -C Network

```
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

```

If I do rmmod ssb, I have to do rmmod b44, which breaks my wired connection.

EDIT: I've blacklisted ssb and b44 and added ndiswrapper to the list of modules to be loaded on startup, but for some reason they still load on boot.

EDIT: This is all that dmesg | grep -e ndis -e wlan gives me:

```
[   17.862895] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   18.050202] usbcore: registered new interface driver ndiswrapper
```

EDIT: Even installing from source doesn't work.  Here's the errors I get:

```
root@roycenh-laptop:~/Desktop/ndiswrapper-1.53# make
make -C driver
make[1]: Entering directory `/home/roycenh/Desktop/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/roycenh/Desktop/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/roycenh/Desktop/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/roycenh/Desktop/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/roycenh/Desktop/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/roycenh/Desktop/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/roycenh/Desktop/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/roycenh/Desktop/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/roycenh/Desktop/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/roycenh/Desktop/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/roycenh/Desktop/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/roycenh/Desktop/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.o
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c: In function &#8216;ndis_translate_scan&#8217;:
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
make[3]: *** [/home/roycenh/Desktop/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/roycenh/Desktop/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/roycenh/Desktop/ndiswrapper-1.53/driver'
make: *** [all] Error 2
```

EDIT: After stumbling around for a while doing random things I finally got this to work.  Never mind this post.

EDIT: To those of you who wondered what I ended up doing:

```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy 
sudo rmmod wl 
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

And then to preserve this through reboots:

```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

---

