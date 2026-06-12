---
title: "EW-7811Un plagues me again"
date: 2015-09-06
forum: Networking &amp; Wireless
---

### Post by lucas20 on 2015-09-06
After searching for some fixes to this trouble maker I went with the rtl8192cu-fixes-master.
Within there is a README.md which shows you how to install.
I usually used this to fix the adapter but I had to do it on every boot because for some reason it didn't save.

> There is a known issue with power management on some hardware. If your WiFi connection drops after a few minutes, install the following module setting file to disable power management in your WiFi interface:

sudo cp ./rtl819cu-fixes-master/8192cu-disable-power-management.conf /etc/modprobe.d/

And then reboot.

Since I had to do it everytime I booted I decide to try to install the actual driver to make a permanent fix, it did not go well.
This is exactly what I did as shown in the guide.

> Ensure you have the necessary prerequisites installed:

sudo apt-get update
sudo apt-get install git linux-headers-generic build-essentials dms

Clone this repository:

git clone [https://github.com/pavaret/rtl8192cu-fixes.git](https://github.com/pavaret/rtl8192cu-fixes.git)

Set it up as a DKMS module:

sudo dkms add ./rtl8192cu-fixes

Build and install it:

sudo dkms install 8192cu/1.10

Refresh the module list (Only error within all of them I would guess is this because no output log happened once refreshing modules).:

sudo depmod -a

Ensure the native (and broken) kernel driver is blacklisted:

sudo cp ./rtl-8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d

And reboot. You're done.


After doing this with 0 errors at all, I figured it had worked.

I rebooted.

After rebooting, the USB no longer powers on. The USB is warm, but the blue LED no longer lights up.

When installed on the PC I use whenever I break something it works.

There's alot of threads on this adapter, it is a pain to many, but this is a new issue for me.

---

### Post by chili555 on 2015-09-06
You might check here: [http://askubuntu.com/questions/625987/does-tp-link-wn822n-work-on-ubuntu/625989#625989](http://askubuntu.com/questions/625987/does-tp-link-wn822n-work-on-ubuntu/625989#625989)

I suggest you try the second method:```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192cu-dkms
```

---

