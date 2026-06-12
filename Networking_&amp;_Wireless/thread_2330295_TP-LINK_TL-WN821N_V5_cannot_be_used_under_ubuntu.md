---
title: "TP-LINK TL-WN821N V5 cannot be used under ubuntu"
date: 2016-07-10
forum: Networking &amp; Wireless
---

### Post by holliswuhollis on 2016-07-10
Hi,

I just brought a wifi usb from TP-LINK and it does not work under linux.

[Product page form TP-LINK]("http://www.tp-link.com/en/download/TL-WN821N.html#Driver")

I found a solution from a Chinese forum and tried to install the driver. But it does not work. (Using the install.sh script provided by driver devs)

[Driver github link]("https://github.com/FreedomBen/rtl8188ce-linux-driver")

I have also tried [this driver]("https://github.com/jpostma/rtl8192eu"). But it does not compile.

Weirdly, lsusb gave me an empty string for the device description. And I have Googled the vendor ID but none of them gave me relevant result.

```

~ via &#11042; v6.2.2 
&#10132; lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:5682 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0a5c:6412 Broadcom Corp. 
Bus 001 Device 006: ID 2357:0107  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

~ via &#11042; v6.2.2 
&#10132; dmesg
(irrelevant)
[ 1013.522434] usb 1-2: new high-speed USB device number 6 using xhci_hcd
[ 1013.707062] usb 1-2: New USB device found, idVendor=2357, idProduct=0107
[ 1013.707077] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1013.707086] usb 1-2: Product: 802.11n NIC 
[ 1013.707094] usb 1-2: Manufacturer: Realtek 
[ 1013.707101] usb 1-2: SerialNumber: 00e04c000001

```

Not just ubuntu. My desktop running arch also gave me same result.


Did I get a bad wifi usb or I have missed some driver to install?

Thanks for your help. ;)

---

### Post by jeremy31 on 2016-07-10
*Thread moved to **Networking & Wireless**.*
I was able to patch mange's github source so that it will compile with a couple minor errors and it should support your device
```
rm -rf rtl8192eu-linux-driver
``` Just in case you already have tried it
```
git clone https://github.com/jeremyb31/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
make
sudo make install
```
Reboot

---

### Post by oblong on 2016-08-24
Many thanks for that. Your process works for Mint 17.3. As you say, lsusb returns empty string.

---

### Post by jp9255 on 2017-02-26
Hi,
This soluton worked for me on Ubuntu GNOME 16.10, many thanks. However, after a few days, the wifi icon disappeared from my top right menu, and I had no internet connection. I did the process shown above again, and it worked, but do I really have to do this over and over again every second day? Any solutions for this? Thanks for your help. ;-)

---

### Post by jeremy31 on 2017-02-26
It should only need to be recompiled after kernel updates but Mange updates his version to have dkms support
```
rm -rf rtl8192eu-linux-driver
sudo apt-get install dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add .rtl8192eu-linux-driver
dkms install rtl8192eu/1.0
```

Reboot

---

### Post by stenio-sarmento on 2017-06-13
> **jeremy31 said:**
> *Thread moved to **Networking & Wireless**.*
I was able to patch mange's github source so that it will compile with a couple minor errors and it should support your device
```
rm -rf rtl8192eu-linux-driver
``` Just in case you already have tried it
```
git clone https://github.com/jeremyb31/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
make
sudo make install
```
Reboot

Many thanks for that. Works great!

---

