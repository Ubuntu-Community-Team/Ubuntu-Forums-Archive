---
title: "Intermittent DWA-171 AC600 Dual Band USB NIC"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by Glen_Wilson on 2015-12-29
**EDIT: **I have marked this SOLVED because I have resolved my problem. The issue seems to have been in the router setup. I am pretty sure I did not change any particular wireless setting, but after trying a few things and resetting the router several times, the USB adapter seemed to connect reliably. At that point, I was connected to the router but had no internet access. I powered down the cable modem and the router and eventually got everything straightened out. Lesson here is that the driver and procedure outlined below does get the adapter working, but you may have to somehow get all of your components on the same page, and that may be a mysterious process.

How do I get this thing to work correctly every time? Any help would be appreciated.

I have a DWA-171  Hardware Version A1 AC600 USB 2.0 Dual Band Wireless Adapter plugged  into my Thinkpad SL410 (also has an internal wireless adapter), and I am running the most recent version of  Ubuntu-based Linux Lite 2.6 in 64-bit. I know that there is no native  support for this device in the kernel and have followed the advice given  in the thread below using the commands shown. I have a compatible 5.0  GHz D-link router and have established both 2.4 and 5.0 communication  several times. Unfortunately, the connection is usually made the first  time or two after running the modprobe command and then just times out  while trying subsequent connections at either 2.4 or 5.0 frequencies.  When it works in 5.0 mode, transfer speeds are remarkably high.

So, why does it work for one or maybe two connections and then  consistently fail to connect with the internet? Some information  follows:

[http://ubuntuforums.org/showthread.php?t=2168426](http://ubuntuforums.org/showthread.php?t=2168426)

Ubuntu Forum Member   chili555

lsusb shows this:  Bus 002 Device 010: ID 2001:3314 D-Link Corp. 

sudo apt-get install git
git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git)
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au

If you update the kernel, you will need to run this code:

cd rtl8812AU_8821AU_linux
make clean
make
sudo make install
sudo modprobe 8812au

---

### Post by praseodym on 2015-12-29
Hi,

[http://packages.ubuntu.com/wily/rtl8812au-dkms](http://packages.ubuntu.com/wily/rtl8812au-dkms)

This package works with kernel 3.16 in 14.04 being a wily package. Cannot test it without hardware though

---

### Post by Glen_Wilson on 2015-12-29
Thanks very much for the link, [ 						 					]("http://ubuntuforums.org/member.php?u=1411497") 				 				 					 						 	[**[COLOR=#000000]praseodym ![/COLOR]**[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1411497")

l downloaded the .deb file and installed it without problems. Dependencies were already present. My understanding is limited, but I am expecting that the dkms will mean that this modification will survive the next automatic kernel update. In any event, simply installing a .deb is pretty simple. Since my adapter was functioning reliably, I can't say for certain what installing this .deb did to my system, but at least the DWA-171 adapter still works! By the way, max throughput using the N modality was 72 Mbs. Using the 5.0 GHz AC mode is giving me 433 Mbs which is a very noticeable improvement.

---

