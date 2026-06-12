---
title: "Panda Pau06 not working!"
date: 2019-03-26
forum: Networking &amp; Wireless
---

### Post by ru8ix on 2019-03-26
Hey guys, i'm completely new to linux and this is my first post here.
So i've been learning a lot of system administration of linux and stuff and have a decent grasp of the basic commands.
I wanted to move onto learning networking and was guided to buy a wireless network adapter. I ended up buying Panda PAU06 cause of later aspiring to use it in kali-linux to do pen-testing and all.
Right now, my issue is i'm not able to install the driver for the adapter into my ubuntu. I have a virtualbox and i have downloaded the extension needed to run USB in virtualbox and i followed the instructions provided by the company in their manual found at [http://www.pandawireless.com/download/PWUsersManual4Linux_v1.0s.pdf](http://www.pandawireless.com/download/PWUsersManual4Linux_v1.0s.pdf)
but when i run "make", i cannot find the rt3070sta.ko in the /tftpboot folder 
and i dont know how to proceed, can anyone please help me?

---

### Post by chili555 on 2019-03-27
I would be very surprised if this device requires a driver built from source. I suspect that the driver is already in modern Ubuntu kernels.

Please insert the device and run and post:```
lsusb
iwconfig
```

---

### Post by ru8ix on 2019-03-28
here's what i got!
```

ru8ixy@ru8ixy-VirtualBox:~$ lsusb
Bus 001 Device 002: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ru8ixy@ru8ixy-VirtualBox:~$ iwconfig
lo        no wireless extensions.

enp0s3    no wireless extensions

```

---

### Post by chili555 on 2019-03-28
As I suspected, your device is covered by the driver rt2800usb. When we search the aliases, we see yours:```

 modinfo rt2800usb | grep 5372
alias:          usb:v[COLOR="#FF0000"]148F[/COLOR]p[COLOR="#FF0000"]5372[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```So, is the module loaded in your case?```
lsmod | grep rt2
```Does the wireless spring to life if you load it?```
sudo modprobe rt2800usb
```Are there interesting clues in the log?```
dmesg | grep -e rt2 -e wlx
```

---

### Post by ru8ix on 2019-03-28
yes your right!

the modinfo does give out the output you said it would!

here is the lsmod output:
```

ru8ixy@ru8ixy-VirtualBox:~$ lsmod |grep rt2
rt2800usb              32768  0
rt2x00usb              20480  1 rt2800usb
rt2800lib             114688  1 rt2800usb
rt2x00lib              53248  3 rt2800usb,rt2x00usb,rt2800lib
mac80211              802816  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              667648  2 rt2x00lib,mac80211

```

The wireless connection did start when i did modprobe.
here are the log messages:
```

[  122.411705] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[  123.049796] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5372 detected
[  123.080987] usbcore: registered new interface driver rt2800usb
[  123.111299] rt2800usb 1-1:1.0 wlx9cefd5fc785a: renamed from wlan0
[  123.125819] IPv6: ADDRCONF(NETDEV_UP): wlx9cefd5fc785a: link is not ready
[  123.125882] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  123.127678] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  126.803105] IPv6: ADDRCONF(NETDEV_UP): wlx9cefd5fc785a: link is not ready
[  126.819341] IPv6: ADDRCONF(NETDEV_UP): wlx9cefd5fc785a: link is not ready
[  196.528547] wlx9cefd5fc785a: authenticate with 40:c8:cb:14:e0:36
[  196.916663] wlx9cefd5fc785a: send auth to 40:c8:cb:14:e0:36 (try 1/3)
[  196.921529] wlx9cefd5fc785a: authenticated
[  196.925502] wlx9cefd5fc785a: associate with 40:c8:cb:14:e0:36 (try 1/3)
[  196.933567] wlx9cefd5fc785a: RX AssocResp from 40:c8:cb:14:e0:36 (capab=0x411 status=0 aid=2)
[  197.096321] wlx9cefd5fc785a: associated
[  197.981574] IPv6: ADDRCONF(NETDEV_CHANGE): wlx9cefd5fc785a: link becomes ready

```

this is the log after i attempted to see if the adapter was working and it is. 
I really appreciate it!

---

### Post by chili555 on 2019-03-28
> this is the log after i attempted to see if the adapter was working and it is. 
I really appreciate it!Glad it's working! Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

I wish they were all this easy!

---

