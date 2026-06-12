---
title: "Honeybull wireless adapter recognized, but won't connect"
date: 2018-03-20
forum: Networking &amp; Wireless
---

### Post by kumoshk on 2018-03-20
I ordered [this product]("https://www.amazon.com/gp/product/B078TM4Z9Y/") for use in Xubuntu 17.10, 64-bit: Honeybull 600 Mbps Wireless USB Adapter (5Ghz/433Mbps, and 2.4Ghz/150Mbps); 802.1b/g/n/a/ac.

It was supposed to work with Linux. However, when I got it, the box said it was compatible with Linux Ubuntu 2.4 - 2.6. I assume that's talking about the kernel. I tried installing the software from the included mini CD, and of course it failed to compile properly, even after fixing some issues&#8212;probably because I have a much newer kernel version: I'm using 4.13.0-37-generic.

The included CD had this label: RTL8811AU DRIVER. In the Linux/driver/ folder of the CD, the driver file is named rtl8821AU_WiFi_linux_v5.2.6.2_23547.20170814_COEX20170206-6760.tar.gz.

When I do lsusb, I get this result for the device: ```
Bus 002 Device 003: ID 0bda:a811 Realtek Semiconductor Corp.
```

When I unplug the device and plug it back in, and then type dmesg, I get this addition to the output:

```

[ 1603.972836] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[ 1604.082671] usb 2-1.2: New USB device found, idVendor=0bda, idProduct=a811
[ 1604.082679] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1604.082684] usb 2-1.2: Product: 802.11ac WLAN Adapter 
[ 1604.082689] usb 2-1.2: Manufacturer: Realtek 
[ 1604.082693] usb 2-1.2: SerialNumber: 00e04c000001

```

I found that there's a package that seems to include the driver that the CD contains, presumably compatible with my kernel, which I installed like this:

```
sudo apt-get install rtl8812au-dkms
```

I restarted my computer. That yielded no results, although I didn't get any errors, either.

I found a firmware-realtek_20161130-3_all.deb file (for Debian&#8212;not for Ubuntu), which has loads of Realtek drivers, including probably the one(s) I did, but it wouldn't complete the install, since I guess it's not compatible with Ubuntu or something.

I tried a bunch of walkthroughs on installing drivers that might work, to no avail.

I later did a web search for the serial number and found [this post]("https://ubuntuforums.org/showthread.php?t=2164161") and [this post]("https://medium.com/@at15/ubuntu-16-04-8811au-wireless-driver-d29d6929a50c"), the first of which seems to maybe indicate that I should be using the RTL8192U driver instead (although I think that thought is wrong). **The second link actually seemed to work; however, when I tried to connect, it would never connect to my hotspot**, even if I unsecured my network (notwithstanding it has all the bars for my network). It does see the hotspots; it just won't connect. I haven't tested more than our hotspot.

Any ideas on how to fix this and get it to connect?

'sudo lshw -C network' now yields this:

```
       *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.2
       logical name: wlx000f00535ea1
       serial: 00:0f:00:53:5e:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au multicast=yes wireless=unassociated

```

It should be noted that my other USB wireless card, which is a cheap TP-link model, on the same laptop connects just fine (and doesn't require any installations before it is recognized&#8212;although it does tend to drop the connections a lot, especially at night or if I visit Amazon.com for some unknown reason&#8212;hence why I got a new one). I'm using that TP link device to connect, now (it seems to be working well enough at the moment).

---

### Post by kumoshk on 2018-03-20
Horray! It works. I guess my only problem after my initial post was that I had MAC Authentication enabled, and my new wireless card's MAC address wasn't on the list.

So, in summary, here's what I did to get this card working:

I followed the instructions at this URL: [https://medium.com/@at15/ubuntu-16-04-8811au-wireless-driver-d29d6929a50c](https://medium.com/@at15/ubuntu-16-04-8811au-wireless-driver-d29d6929a50c)

Let me quote them:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe rtl8812au
```

You need to reinstall every time you update the kernel. One of the comments says you can avoid having to do that by doing this (although I haven't tried it, yet):
```
sudo apt-get install dkms
git clone https://github.com/scrivy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
make
sudo make install
```

(And of course I added my MAC address to the authentication list, but you probably won't need to do that unless you have MAC Authentication enabled.)

Now, hopefully my connection won't drop much, if at all, anymore. Amazon.com is loading properly: that's a good sign!

[My old TP-link N150 WN725N wireless USB adapter]("https://www.amazon.com/gp/product/B008IFXQFU/") dropped connections at night a lot (and sometimes during the day), and it especially dropped the connection when I visited Amazon.com and at least one or two other sites (I didn't have those problems for the first year or two, though). Plus, it wouldn't work properly with stronger security settings (and was best used with the security turned off altogether&#8212;although TKIP was faster than AES or BOTH)&#8212;it did have that problem initially, however. It didn't require me to install anything, however, but it doesn't have as many features.

Both of these wireless adapters were very inexpensive when I got them (with free shipping). The TP-Link one was $9.89 (on 1 September 2015) and the HoneyBull one was $9.99 (on 15 March 2018). The prices change from time to time (the HoneyBull one was $7-something earlier today, and now it's more).

---

