---
title: "atheros ath9k_htc module does not load for 22.04 (raspberry pi)"
date: 2023-07-21
forum: Networking &amp; Wireless
---

### Post by heliguy-matt on 2023-07-21
Hi,
I am trying to get an **Atheros AR9271** based wifi card running on a raspberry pi running **ubuntu 22.04.**
I have installed the **firmware-ath9k-htc** package and rebooted but the module does not load and the interface is not detected.

Here is a link to the wifi script results: [https://pastebin.com/HTgTQ2Gq](https://pastebin.com/HTgTQ2Gq)

This is what i see in dmesg when the card is plugged in:
```

[ 2124.185834] usb 1-1.1: new high-speed USB device number 7 using xhci_hcd 
[ 2124.302920] usb 1-1.1: New USB device found, idVendor=0cf3, idProduct=9271, bcdDevice= 1.08
[ 2124.302965] usb 1-1.1: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[ 2124.302982] usb 1-1.1: Product: UB91C
[ 2124.302997] usb 1-1.1: Manufacturer: ATHEROS 
[ 2124.303010] usb 1-1.1: SerialNumber: 12345

```
On an amd64 machine and Ubuntu 22.04 the card works out of the box without the need for any package installs so this issue appears to be an arm only one.

Any help on this would be appreciated as i don't really know where to go from here.

---

### Post by heliguy-matt on 2023-07-24
for anyone that comes across this with the same problem, i ended up just fixing the issue by compiling the drivers from source and copying them over.

**Note**: the below shell script is for the specific kernel version i am on and will most likely need updating for your use.

```

WD=~/src

mkdir -p $WD
cd $WD

# add deps
sudo apt install build-essential
sudo apt install linux-headers-$(uname -r)

# pull base linux source
wget https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/linux-raspi/5.15.0-1033.36/linux-raspi_5.15.0.orig.tar.gz
gzip -d linux-raspi_5.15.0.orig.tar.gz
tar xvf linux-raspi_5.15.0.orig.tar

# pull ubuntu diff
wget https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/linux-raspi/5.15.0-1033.36/linux-raspi_5.15.0-1033.36.diff.gz
gzip -d linux-raspi_5.15.0.diff.gz

# apply diff
mv linux-5.15/ linux-raspi-5.15.0
patch -s -p0 linux-raspi_5.15.0-1033.36.diff

# build base ath drivers
cd $WD/linux-raspi_5.15.0-1033.36.diff/drivers/net/wireless/ath
tee -a Makefile << EOF
KVERSION = \$(shell uname -r)
all:
    make -C /lib/modules/\$(KVERSION)/build M=\$(PWD) modules
clean:
    make -C /lib/modules/\$(KVERSION)/build M=\$(PWD) clean
EOF

make
mkdir -p /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath
cp *.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath

# build base ath9k drivers
cd $WD/linux-raspi_5.15.0-1033.36.diff/drivers/net/wireless/ath9k

tee -a Makefile << EOF
KVERSION = \$(shell uname -r)
all:
    make -C /lib/modules/\$(KVERSION)/build M=\$(PWD) modules
clean:
    make -C /lib/modules/\$(KVERSION)/build M=\$(PWD) clean
EOF

make
mkdir -p /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath/auth9k
cp *.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath/ath9k

# assign or whatever
cd $WD

depmod



```

---

