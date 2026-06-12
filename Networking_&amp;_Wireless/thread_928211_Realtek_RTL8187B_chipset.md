---
title: "Realtek RTL8187B chipset"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Gavagai80 on 2008-09-23
Weeks of research lead me to give up on finding a wireless card that I could trust to just work, so I took the random plunge and got a Belkin Wireless G USB version 5000. Googling indicates that's a Realtek RTL8187B chipset.

1) Will Intrepid Ibix be using the 2.6.27 kernel, which I've read is supposed to support Realtek RTL8187B?

2) As for right now with Kubuntu Hardy, I tried using rtl8187b-modified-jadams-2-1-2008.tar.gz from [here](http://www.datanorth.net/~cuervo/rtl8187b/). Following the readme instructions I ran ./makedrv but ./wlan0up after that gives ```
pgk@pgk-desktop:~/Desktop/rtl8187b-modified-jadams-2-1-2008/rtl8187b-modified$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8187.ko': -1 Operation not permitted

```

Any ideas? Operation not permitted makes me think of chmod issues. I had to set everything in the directory to 777 for the ./makedrv to work.

KNetworkManager is now claiming that I'm using the device RTL-8139/8139C/8139C+ from Realtek Semiconductor Co., Ltd., but calls it a wired ethernet connection (and if I take out the ethernet cord internet goes away), so it seems to have just relabeled things wrongly.

---

### Post by willca on 2008-09-24
Not sure about that permission stuff errors...but i will go back to the basics first.

Lets see if your Ubuntu does recognize that wifi nic in there.

lspci | grep Ethernet

Then if it is, assuming the driver is loaded right (unless this has a Broadcom chip)..

sudo iwlist wlan0 scan

This should give you a list of available wireless networks in the area.

**Now if lspci command said you got a Broadcom chip. Then you need to do this while connected to the internet via your wired nic.

sudo apt-get install b43-fwcutter
and follow the prompts

---

### Post by Gavagai80 on 2008-09-24
pgk@pgk-desktop:~$ lspci | grep Ethernet
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
pgk@pgk-desktop:~$ sudo iwlist wlan0 scan
[sudo] password for pgk:
wlan0     Interface doesn't support scanning.

---

### Post by Gavagai80 on 2008-09-26
Gave up on the native linux driver and installed ndiswrapper. Unfortunately, that's not working any better so far. Following the instructions [here](http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/) I downloaded the windows xp driver, and ran
sudo ndiswrapper -i net8187b.inf
sudo ndiswrapper -ma && sudo ndiswrapper -mi
with apparent success. Yet, after removing and reinserting the card, iwconfig says "no wireless extensions" and dmesg gives
```
[snipped thousands of pages of stuff]
[  541.485472] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  541.533452] usbcore: registered new interface driver ndiswrapper
[  557.985202] usb 3-2: USB disconnect, address 2
[  564.314777] usb 3-2: new high speed USB device using ehci_hcd and address 4
[  564.455394] usb 3-2: configuration #1 chosen from 1 choice

```

Tried rebooting, no difference. Tried the Windows 2000 driver, no difference.

Some of the article comments suggest using the Windows '98 driver, and I'd be glad to, except there isn't one.

---

### Post by Gavagai80 on 2008-09-26
Found [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092) . My ID appears to be 705e, however, and 
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_705e&REV_0200
doesn't make the .inf work.

lsusb gives:
Bus 003 Device 005: ID 050d:705e Belkin Components
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

