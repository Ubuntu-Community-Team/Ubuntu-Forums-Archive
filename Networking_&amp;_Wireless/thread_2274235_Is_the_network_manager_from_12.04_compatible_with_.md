---
title: "Is the network manager from 12.04 compatible with ubuntu 10.04"
date: 2015-04-18
forum: Networking &amp; Wireless
---

### Post by netcom61 on 2015-04-18
Hello.  hoping someone might know if it is possible to install the .deb for network-manager from 12.04 in a 10.04 installation or if the kernel/dependencies have changed too  much between 10 and 12.  -Reason being: I've got an old T40 which i love, however, it isn't capable of running 12.04 very well, and 12.04's network-manager handles my huawei 4g mobile-broadband usb dongle, whereas the the 10.04 can't seem to get to it no matter what i try (it's one of the ones that mounts as an hdd instead of dongle...  Thanks

For anyone needing advice on the Huawei LTE 4g e397 usb mobile broadband dongle, the fix, for me, was to copy the data from /lib/udev/rules.d/40-usb_modeswitch.rules for the stick from this file in a 12.04 installation, in which the stick "just works", and transfer it to the same file in the 10.04 install... 

The entry in the rules file should look like this: 

> # Huawei e397
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1505", RUN+="usb_modeswitch '%b/%k'"

You also have to make a file in /etc/usb_modeswitch with : sudo nano /etc/usb_modeswitch.d/12d1:1505

and enter or paste this into the file: > ########################################################
# Huawei K4GLTE

DefaultVendor= 0x12d1
DefaultProduct=0x1505

TargetVendor=  0x12d1
TargetProduct= 0x1465

CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

And finally, run this in terminal: > echo 'SUBSYSTEM==&#8221;usb&#8221;, SYSFS{idProduct}==&#8221;1505, SYSFS{idVendor}==&#8221;12d1&#8243;, RUN+=&#8221;/usr/bin/usb_modeswitch &#8211;vendor 0×12d1 &#8211;product 0×1505 &#8211;type option-zerocd&#8221;'|sudo tee /etc/udev/rules.d/15-huawei-e1505.rules

finally : reboot

I know, seems slightly convoluted, however, in 10.04 this is the only way i could get the dongle to work... 


the model-id etc can be found with "lsusb" ... in the case of the huawei, the appropriate entry in the file was for product id=1505, which, when properly mounted and modeswitched, becomes 1506

---

### Post by mörgæs on 2015-04-19
If it's a Thinkpad T40 I recommend leaving both 10.04 and 12.04, doing a fresh install of Lubuntu 14.04.2.

---

