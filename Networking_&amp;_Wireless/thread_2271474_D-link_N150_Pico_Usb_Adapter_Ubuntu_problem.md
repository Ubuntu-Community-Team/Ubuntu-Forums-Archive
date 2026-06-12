---
title: "D-link N150 Pico Usb Adapter Ubuntu problem"
date: 2015-03-30
forum: Networking &amp; Wireless
---

### Post by said-el on 2015-03-30
Hello everybody

I've just bought D-link N150 Pico Usb Adapter , but i have a problem using it , after about 5 minutes connecting to Wifi I lose internet (still connected but no internet) and I have to restart ubuntu to get it to work another 5 minutes then the same problem occur

Any help please

---

### Post by praseodym on 2015-03-30
Hi,

please run the wireless script from the sticky thread and show the output.

---

### Post by said-el on 2015-03-31
> **praseodym said:**
> Hi,

please run the wireless script from the sticky thread and show the output.

Please find here result of the wireless script

[http://paste.ubuntu.com/10711618/](http://paste.ubuntu.com/10711618/)

---

### Post by praseodym on 2015-03-31
Change the driver via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot.

What about the internal card?

---

### Post by said-el on 2015-04-01
> **praseodym said:**
> Change the driver via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot.

What about the internal card?

Thank you so much , problem solved

[IMG]http://storage3.static.itmages.com/i/15/0401/h_1427903944_6757362_5dfe801b27.png[/IMG]

for the internal card , it just stopped working months ago and people told me don't even try to fix it , its dead 

Thnxx

---

### Post by praseodym on 2015-04-01
I do not know if this driver can be compiled with your kernel anymore, but lets give it a try:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
sudo tar xvf 5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz -C /usr/src/
sudo dkms add -m Ralink_3290sta -v 2.6.0.0
sudo dkms build -m Ralink_3290sta -v 2.6.0.0
sudo dkms install -m Ralink_3290sta -v 2.6.0.0 
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot

---

