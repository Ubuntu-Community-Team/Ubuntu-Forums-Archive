---
title: "Slow and intermittent WIFI (only on Ubuntu) after changing router"
date: 2019-01-19
forum: Networking &amp; Wireless
---

### Post by nikolapetanjak on 2019-01-19
Hello,

i'm experiencing slow and intermittent download and upload after "only" changing router. My new router is Huawei HG8245Q2. First of all i tried to change some router settings as suggested in some posts i found, but it didn't help (attachment router1.png and router2.png):

Fixed channel number 6, channel width 20MHz, AES only encryption. Mode was already set to 802.11b/g/n and regulatory domain to Croatia (it's set to Croatia i.e. HR on Ubuntu also).

On router GUI it's visible that my machine has low sending and receiving rate (other machines are Windows and Android; attachment router3.png). Rates should be 5-10 times faster. I made signal bit stronger but it didn't help much. On top of this, every few min on average connection is dropped.

Also on router GUI, it's visible that it doesn't recognise "Host name" and "Device type" parameters, don't know if that's normal (MAC address and IP address are displayed ofcourse). Screenshot is in file "router4.png".

Now about my machine:

Ubuntu version is 16.04.5 LTS, kernel 4.4.0-141-generic

lsusb command is displaying ASUSTek Computer, Inc. N10 Nano 802.11n Network Adapter [Realtek RTL8192CU]

I read numerous posts where it is said that this might be collision between drivers. I tried to blacklist rtl8192 driver and use only rtl8xxxu ([https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)) but it didn't help (it is even slower speed when i use only rtl8xxxu so at this moment i have blacklisted rtl8xxxu and 8192 and use only rtl8192).

Power management is turned off, as can be seen by executing iwconfig.

Results from wireless info script are here:

[http://paste.ubuntu.com/p/Vq4sZK6Y2D](http://paste.ubuntu.com/p/Vq4sZK6Y2D)

Please note that ath drivers were my try to use different wifi usb adapter, but i couldn't make his drivers to work. Also, i tried rtl8xxxu and 8192 drivers also, but results were similar as this setup from pastebin file.

Also, i use WICD instead of Network manager, that was also one attempt that i read about in some post regarding network issues.

Update:

Wired connection is working properly, i disabled WICD and reinstalled network-manager, same problem persists, download is around 2Mbit/s (wired is 70Mbit/s).

---

### Post by praseodym on 2019-01-20
With kernel 4.4 the module 8192cu can still be compiled. Did you try that one?

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/0xBADEAFFE/rt8192cu_dkms
cd rt8192cu_dkms
sudo make install_dkms
echo -e "blacklist rtl8192cu\nblacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```

---

