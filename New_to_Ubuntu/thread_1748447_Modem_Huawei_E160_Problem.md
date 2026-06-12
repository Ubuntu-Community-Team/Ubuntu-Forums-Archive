---
title: "Modem Huawei E160 Problem"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by ivalice on 2011-05-03
Hi all,

I've recently upgraded my Ubuntu to 11.04. My usb modem, huawei E160, worked fine with Ubuntu 10.10 but now it doesn't work with 11.04 anymore. When I stick it in, it doesn't mount by itself. Any suggestions how I can fix this?

Thanks

---

### Post by benom on 2011-05-04
i have the same problem with an HUAWEI E1752
even worked after updating to 11.04 but some more updates came this morning and broke it and now ubuntu doesn't even react when i put it in
please help

edit: just rebooted again this time without the huawei connected and didn't put it in before completing login. this time it's working (but skype is missing invisible now. wasn't before 2nd reboot)

---

### Post by pjrodz on 2011-05-19
same problem here. :confused:

---

### Post by fritz269 on 2011-05-19
Are you using a program to connect or does the phone allow it to be used as a modem?
If it does, look to see if there is a setting that lets you use it as a modem/ share the phones connection.

---

### Post by pjrodz on 2011-05-19
> **fritz269 said:**
> Are you using a program to connect or does the phone allow it to be used as a modem?
If it does, look to see if there is a setting that lets you use it as a modem/ share the phones connection.

ubuntu 10.04 detects my huawei e160 usb modem automatically. but ubuntu 11.04 (natty) doesn't.

---

### Post by jre6 on 2011-05-20
Ubuntu does not mount some Huawei devices due to bugs, problems etc. See if these work:

**1st option**

[LIST]
[*]Connect the USB modem.
[*]After 10 seconds, type this in a terminal window:
```

lsusb

```The output will be like this:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd. 
Bus 004 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
[*]The device is a Huawei modem, so let's look at the output. The relevant entry is:
```

Bus 004 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd

```Hence, you must type:
```

sudo modprobe usbserial vendor=0x12d1 product=0x140b

```
[/LIST]


**2nd option**

[LIST]
[*]Download usb-modeswitch and usb-modeswitch-data packages from packages.ubuntu.com
[*]Install them through the command:
```
sudo dpkg -i usb-modeswitch*.deb
```
[/LIST]


**3rd option**
Try a combination of both.

Now, it will be detected by Network manager, wvdial etc. However, please note that this is continuation of a problem from Linux kernel >=2.6.31, so it sometimes fails (especially after connecting a pen drive etc.)

---

### Post by pjrodz on 2011-05-20
hi jre6! thank you for your reply, unfortunately, my huawei e160 modem still doesn't work. any other ideas? thanks again!

---

### Post by pjrodz on 2011-05-21
anyone? :confused:

---

### Post by pjrodz on 2011-05-22
i'm just wondering, how come things/hardware working before with older versions of ubuntu sometimes stop working on newer releases? aren't they building the newer versions on top of the older ones? :confused:

---

### Post by mhy31 on 2011-05-23
mine is Huawei E1550, same problem.

mounted as cdrom.

---

### Post by gandaran on 2011-05-23
> **mhy31 said:**
> mine is Huawei E1550, same problem.

mounted as cdrom.
I have a Huawei E1550 and it works fine on Ubuntu 11.04 clean install, did you upgrade or clean install Ubuntu?
check that usb-modeswitch is installed in the package manager.
what I usually do after installing Ubuntu is run the mobile broadband wizard chose country and internet provider (without the dongle inserted) and mark the box connect automatically in the setup, only then I plug in the modem to the computer, it as never failed to connect on every ubuntu version yet doing it this way.

---

### Post by balgaltz on 2011-05-23
Try this.

```
$ lsusb
Bus 006 Device 002: ID **0fd1:1000** Giant Electronics Ltd.
```

Your modem will display a different ProductID and VendorID.
Copy them and replace them in the file below.

```
/etc/udev/rules.d/80-mobile3g.rules
ACTION!="add", GOTO="3G_End" 
SUBSYSTEMS=="usb", ATTRS{idProduct}=="**1000**", ATTRS{idVendor}=="**0fd1**", RUN+="/bin/sh -c 'echo 3 > /sys/%p/bConfigurationValue'"
LABEL="3G_End"
```

Save the file. (/etc/udev/rules.d/80-mobile3g.rules)
Then reboot and connect the device afterwards.

It should pop the Mobile Configuration Wizard.

---

### Post by mhy31 on 2011-05-23
> **gandaran said:**
> I have a Huawei E1550 and it works fine on Ubuntu 11.04 clean install, did you upgrade or clean install Ubuntu?
check that usb-modeswitch is installed in the package manager.
what I usually do after installing Ubuntu is run the mobile broadband wizard chose country and internet provider (without the dongle inserted) and mark the box connect automatically in the setup, only then I plug in the modem to the computer, it as never failed to connect on every ubuntu version yet doing it this way.


from clean installation. 
got it working now. :smile:  I plugged my laptop using cat5 cable directly to my wireless router  back home and downloaded all packages/updates and installed it. i  checked the usb-modeswitch got it installed then i configured my  settings thru mobile broadband wizard.

Thank you! and also to [balgaltz]("http://ubuntuforums.org/member.php?u=407854") will keep it for my future reference.

---

### Post by RichardCain on 2011-05-29
> i'm just wondering, how come things/hardware working before with older versions of ubuntu sometimes stop working on newer releases? aren't they building the newer versions on top of the older ones? 

Yes, they are building on top of older releases, but as new hardware is released, new code must be written into the OS to support it.  Therefore, every so often they have to remove the code that supports older hardware, otherwise it would just get bloated and slow right down.  That's the flip-side of not having to install drivers a-la MS or Mac.
I have the same problem with my Wi-Fi card after 4 years.  I really should just get a new laptop!

---

### Post by pjrodz on 2011-06-14
> **balgaltz said:**
> Try this.

```
$ lsusb
Bus 006 Device 002: ID **0fd1:1000** Giant Electronics Ltd.
```

Your modem will display a different ProductID and VendorID.
Copy them and replace them in the file below.

```
/etc/udev/rules.d/80-mobile3g.rules
ACTION!="add", GOTO="3G_End" 
SUBSYSTEMS=="usb", ATTRS{idProduct}=="**1000**", ATTRS{idVendor}=="**0fd1**", RUN+="/bin/sh -c 'echo 3 > /sys/%p/bConfigurationValue'"
LABEL="3G_End"
```

Save the file. (/etc/udev/rules.d/80-mobile3g.rules)
Then reboot and connect the device afterwards.

It should pop the Mobile Configuration Wizard.

nice! this solution worked for me! thanks balgaltz! :D

---

### Post by raiden82 on 2011-09-17
Hi guys, is it possible to use the E160 just as a wifi dongle? as in windows, it's working but only on the mobile network..

---

### Post by gandaran on 2011-09-17
> is it possible to use the E160 just as a wifi dongle? as in windows
I don't think so not even in windows unless the dongle has a built in wireless LAN to share the mobile internet then it should work too.
I think you must have meant share the mobile internet using a wifi network setup from the _PC wifi card_ then yes it's possible.

---

