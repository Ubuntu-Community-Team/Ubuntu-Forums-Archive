---
title: "Broadcom internal WiFi device not recognised"
date: 2020-03-08
forum: Networking &amp; Wireless
---

### Post by dbclin2 on 2020-03-08
I've got an Acer One 10 (S1003 D16H1) 2in1 notebook/tablet with an Intel Atom X5-Z8350 running Ubuntu 19.10 - actually, to be more precise, I initially installed Lubuntu but then installed ubuntu-gnome-desktop and switched from Wayland to X.Org. Gnome handles the tablet features nicely: orientation and touchscreen work beautifully. When running under Windows the WiFi worked fine.
Here's my release:
```

$ uname -a
Linux tablet 5.3.0-40-generic #32-Ubuntu SMP Fri Jan 31 20:24:34 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```
The only show stopper is the integrated WiFi. According to Acer documentation, it's got Broadcom version 1.596.10.0. But lspci doesn't recognise any networking device beyond the USB ethernet I've got plugged in and, naturally, ip a doesn't show me any wireless interface. dmesg doesn't add anything helpful.
I ran:
```
modprobe wl 

```
and lsmod gives me this:
```
wl                   6455296  0
cfg80211              712704  1 wl

```
I also added the brcmfmac43430a0-sdio.txt driver to /lib/firmware/brcm/
There's been no sign of my WiFi device so far. Any ideas?

---

### Post by chili555 on 2020-03-08
Please run and post:```
lspci -nnk | grep 0280 -A3
dmesg | grep -i sdio
```Thanks.

---

### Post by dbclin2 on 2020-03-08
Thanks. Here's my output:
```

$ lspci -nnk | grep 0280 -A3
$ dmesg | grep -i sdio
[    3.071968] mmc1: new high speed SDIO card at address 0001

```

---

### Post by chili555 on 2020-03-08
No clues so far. Let’s see: ```
lsusb
```

---

### Post by dbclin2 on 2020-03-08
```

$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. A1) [Ralink RT3072]
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 06cb:73f5 Synaptics, Inc. ITE Device(8910)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
The ASUStek 802.11n is a USB WiFi device I've got plugged in through that 4-port hub. I could leave there, but (1) it doesn't make for a particularly "tablet" experience having to drag that thing along and, (2) the only full USB port is on the keyboard/base, so I'd lose my connection when I took the tablet part off. :)

---

### Post by chili555 on 2020-03-08
Sorry, we still don't see anything resembling a wireless device. If you reboot into Winows, are there any details you can gather? Please post everything you can find, even if it seems trivial.

---

### Post by CelticWarrior on 2020-03-08
@chili555

AFAIK the WiFi in this lind of devices is usually in the SDIO bus. Not sure this helps but it's the only thing I can think of.

---

### Post by chili555 on 2020-03-08
> **CelticWarrior said:**
> @chili555

AFAIK the WiFi in this lind of devices is usually in the SDIO bus. Not sure this helps but it's the only thing I can think of.Hence my request for dmesg | grep -i sdio. Too bad the result was uninformative. Why do I have to work so hard on a Sunday afternoon??

---

### Post by praseodym on 2020-03-08
Please show

```
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

### Post by dbclin2 on 2020-03-08
Well I certainly appreciate your attention on this Sunday afternoon! Especially since my wife tells me it's absolutely beautiful spring weather here in Toronto. I wouldn't know, myself - I've been in my office all day.
Unfortunately, the Windows options on the GRUB menu doesn't load. It's possible I messed up the Windows partitions while I was struggling to get Lubuntu installed. No great loss, but I won't be able to sneak back in to see how Windows recognises the Broadcom.
On the other hand, I was looking through the tablet's manual and it reminded me about the Fn+F3 hotkey to toggle airplane mode. Perhaps I'd triggered that and shut down the WiFi chip. I tried that a few times but it doesn't seem to have any impact. 
Thanks!

---

### Post by CelticWarrior on 2020-03-08
Try the commands in post #9. Maybe they will show the device. Also try after FN+F3 to see if it makes any difference.

---

### Post by dbclin2 on 2020-03-08
Here:
```

$ cat /sys/bus/sdio/devices/*
cat: '/sys/bus/sdio/devices/mmc1:0001:1': Is a directory
cat: '/sys/bus/sdio/devices/mmc1:0001:2': Is a directory
$ cat /sys/bus/sdio/devices/*/uevent
SDIO_CLASS=00
SDIO_ID=02D0:A9A6
MODALIAS=sdio:c00v02D0dA9A6
SDIO_CLASS=00
SDIO_ID=02D0:A9A6
MODALIAS=sdio:c00v02D0dA9A6
```

---

### Post by dbclin2 on 2020-03-08
There doesn't seem to be any change after Fn+F3, but dmesg did spit out something connected to mmc1 (which is on the sdio bus):

[ 1427.470534] mmc1: queuing unknown CIS tuple 0x80 (2 bytes)
[ 1427.472083] mmc1: queuing unknown CIS tuple 0x80 (3 bytes)
[ 1427.473614] mmc1: queuing unknown CIS tuple 0x80 (3 bytes)
[ 1427.476387] mmc1: queuing unknown CIS tuple 0x80 (7 bytes)
[ 1427.479756] mmc1: queuing unknown CIS tuple 0x81 (9 bytes)

---

### Post by praseodym on 2020-03-08
```
modprobe -c | grep -i "02d0.*a9a6"
``` gives

```
alias sdio:c*v02D0dA9A6* brcmfmac
```
So lets see
```

sudo modprobe -v brcmfmac
dmesg | grep brcm
```

---

### Post by dbclin2 on 2020-03-08
Here:

$ sudo modprobe -v brcmfmac
[sudo] password for dbclin: 
insmod /lib/modules/5.3.0-40-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko 
insmod /lib/modules/5.3.0-40-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko 

$ dmesg | grep brcm
[    9.411132] bluetooth hci0: Direct firmware load for brcm/BCM4343A0.hcd failed with error -2
[    9.411141] Bluetooth: hci0: BCM: Patch brcm/BCM4343A0.hcd not found
[ 2033.627030] brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43430a0-sdio for chip BCM43430/0
[ 2033.627265] usbcore: registered new interface driver brcmfmac
[ 2033.662422] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43430a0-sdio.Acer-One S1003.txt failed with error -2
[ 2033.663081] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43430a0-sdio.txt failed with error -2
[ 2034.673518] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50

---

### Post by CelticWarrior on 2020-03-08
Now we're getting somewhere. It looks like a failed firmware loading. I think that it will be easy for the experts to come up with a solution.

---

### Post by dbclin2 on 2020-03-08
Very interesting.
How did dmesg know that we're looking for a file called "brcmfmac43430a0-sdio.Acer-One S1003.txt"? Where did the "Acer-One" come from? 
Do you think I should rename brcmfmac43430a0-sdio.txt to fit that expectation?
Thanks!

---

### Post by jeremy31 on 2020-03-08
Please post results for ```
ls /sys/firmware/efi/efivars/ | grep nvram
```

---

### Post by dbclin2 on 2020-03-08
The efivars/ directory is empty (not even hidden files).

---

### Post by dbclin2 on 2020-03-08
I'm in!!!
I got a copy of the brcmfmac43430a0-sdio.txt file from GitHub and saved it to /lib/firmware/brcm/
Then, remembering how dmesg had complained about brcm/brcmfmac43430a0-sdio.Acer-One S1003.txt failing with error -2, I made copies of the brcmfmac43430a0-sdio.txt file named brcmfmac43430a0-sdio.Acer-One-S1003.txt and brcmfmac43430a0-sdio.Acer-One\ S1003.txt (because I wasn't sure which one dmesg wanted).
I then ran modprobe -v brcmfmac once again, and my new interface showed up. 
Everything's perfect now.
I've lost count of how many of you forum guys were a part of this, but I'm very grateful to all of you. I plan to write this whole thing up to make it available to the community.
Thanks
David

---

### Post by jeremy31 on 2020-03-08
It must not be installed in UEFI as that /sys/firmware/efi/efivars/ directory normally has a nvram file that can be copied to the missing firmware for SDIO cards in many cases you just have to do ```
sudo cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113 /lib/firmware/brcm/brcmfmac43430a0-sdio.Acer-One S1003.txt
```
Reboot and it is working

---

