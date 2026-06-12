---
title: "Mobile-Broadband stick sometimes not detected at all"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by jun3 on 2014-02-12
Hello,

my mobile-broadband usb stick (lsusb: 12d1:1001 Huawei Technologies Co., Ltd. E169/E620/E800 HSDPA Modem) is sometimes detected and sometimes not.

  Scenario: I plug-in the stick. It sometimes start to blink and the  mobile broadband connection appears in network manager. Sometimes, after  the plug-in, a return from suspend mode, or just after a disconnect,  it's not starting to blink or just seldomly and the connection does not  appear again.
  lsusb does not find the device in the latter case. (Not  as a normal usb stick, too - I am aware about the mode-switching issue  in Linux, but this doesn't seem to be the problem here.)

  Sometimes a reboot helps.

  Could it be an issue with usb? Maybe something with not providing enough power?

  The system: Ubuntu 12.04 on ThinkPad T60

  What I tried until now:
  
[LIST]
[*]three different USB ports on the laptop plus using a USB-hub that is powered with an own power source 
[*]sudo service network-manager restart 
[*]sudo /etc/init.d/networking restart (is depricated) 
[*]sudo ifdown -a && sudo ifup -a 
[*]looking into the mode-switching issue, but since the stick is not  listed at all instead of being listed as storage, this seems not to be  the issue here) 
[/LIST]

Thank you in advance!

Update:

```
tailf /var/log/syslog
Feb 13 09:54:08 laptop NetworkManager[2400]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Feb 13 09:54:08 laptop NetworkManager[2400]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Feb 13 09:54:08 laptop NetworkManager[2400]: <info> (wlan0): now managed
Feb 13 09:54:08 laptop NetworkManager[2400]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 13 09:54:08 laptop NetworkManager[2400]: <info> (wlan0): bringing up device.
Feb 13 09:54:08 laptop NetworkManager[2400]: <info> (wlan0): deactivating device (reason 'managed') [2]
```

---

