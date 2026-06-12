---
title: "Ndiswrapper - Found wificard, created wlan0, but no connection..."
date: 2005-11-10
forum: Networking &amp; Wireless
---

### Post by daller on 2005-11-10
Hi there,

```


lotte@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

lotte@ubuntu:~$    


```

```


lotte@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:100/100  Signal level:-80 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

lotte@ubuntu:~$    


```

I set up the /etc/network/interfaces, but it doesn't work...

Any ideas?

---

### Post by Maverick911 on 2005-11-10
Hi Daller,

I've been fighting my Broadcom BCM94306 running under ndiswrapper. It's working right now (crosses fingers). Here's how I set mine up:

Run 
```
iwlist wlan0 scan
```
You hopefully will see something similar to this:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:09:5B:E9:B0:78
                    ESSID:**"Wireless100"**
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:**2.437 GHz (Channel 6)**
                    Quality:0/100  Signal level:-55 dBm  Noise level:-256 dBm
                    Encryption key:**on**
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```
If you don't get any scan results the 1st time, try again. Sometimes it takes 3 or 4 trys for me. Take note of the settings I bolded. You want to edit /etc/network/interfaces to match.

Open /etc/network/interfaces in gedit.
```
sudo gedit /etc/network/interfaces
```

Here's what mine looks like, Ive noted the changes I made in bold.

```
mapping hotplug
	script grep
	map **wlan0**(I changed this from eth0)


# The primary network interface
iface wlan0 inet static
address 192.168.0.3     (I've set a static IP since I only use wireless at home)
netmask 255.255.255.0
gateway 192.168.0.1
wireless-mode managed
wireless-freq **2.437G**(My AP is set on channel 6, not auto)
wireless-key **open** **XXXXXX**(If you use encryption enter your encryption mode and key here)
wireless-essid **Wireless100**(The essid of your AP)


iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1


auto wlan0

```

Then try
```
ifconfig wlan0 down
```
```
ifconfig wlan0 up
```
You might also try
```
iwconfig wlan0 essid "The_ESSID_Of_Your_AP"
```

Check System>Administration>Networking and make sure wlan0 is active and that it's set as the default gateway. You might try deactivating any other network interfaces listed here, I've heard they can conflict.

I've also installed the network monitor applet on my panel. It's great for telling you the status of your connection at a glance. 
Right click +Add to panel
Add Network Monitor under System and Hardware
Make sure it's set to monitor wlan0 with right click properties.

Hope this helps.

Wish You Were Here - Pink Floyd

---

### Post by daller on 2005-11-10
No luck with the scan-thing :(

The applet shows 100% on wlan0

People are saying that the repo-version of ndiswrapper is buggy, is that true?

daniel@dallap:~$ sudo apt-cache show ndiswrapper-utils
Password:
Package: ndiswrapper-utils
Priority: optional
Section: misc
Installed-Size: 128
Maintainer: Andres Salomon <dilinger@debian.org>
Architecture: i386
Source: ndiswrapper
Version: 1.1-4ubuntu2
Depends: libc6 (>= 2.3.4-1), perl, ndiswrapper-modules-1.1
Suggests: ndiswrapper-source
Filename: pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb
Size: 25676
MD5sum: a2f339da1c7aca7e8747c54be6879259
Description: Userspace utilities for ndiswrapper
 Some wireless LAN vendors refuse to release hardware specifications or
 drivers for their products for operating systems other than Microsoft
 Windows. NdisWrapper makes it possible to use such hardware with Linux by
 means of a loadable kernel module that "wraps around" NDIS (Windows network
 driver API) drivers.
 .
 This package contains the userspace tools. The default Ubuntu kernel
 already provides the required modules. If you use a custom kernel,
 you might also need the kernel module package.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

daniel@dallap:~$

---

It's not all cards that support scanning, is it?

---

### Post by daller on 2005-11-10
I think it's because of a bad driver...

...It worked in Windows, but does that automatically mean, that it's the right one?

The reason I'm a little sceptical, is that I've seen others here on this forum (with the same pc), where the driver was named net8180 (not netr8180 like mine)

...Could that be it?

---

