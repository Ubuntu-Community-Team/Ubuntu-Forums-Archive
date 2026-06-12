---
title: "Acer Aspire One looses wireless with xubuntu 12.04"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by Tim_Johnson on 2014-11-24
Machine is Acer Aspire One D250
The issue I will describe here was also present on lubuntu 14.04 on the same machine.
After installing xubuntu 12.04, the system picked up the wireless immediately without any problem.
I ran wireless_script by **Wild Man, Krytarik** and the results can be seen at :
[http://akwebsoft.com/clients/transfer/wireless-info_initial_install.txt](http://akwebsoft.com/clients/transfer/wireless-info_initial_install.txt)

After rebooting, the machine could not find the wireless card, wlan0 was not present in ifconfig
I ran the wireless_script again and those result, post reboot can be seen at :
[http://akwebsoft.com/clients/transfer/wireless-info_after_reboot.txt](http://akwebsoft.com/clients/transfer/wireless-info_after_reboot.txt)

I am including the following (hopefully) relevant lines from syslog which were recorded after reboot
```

Nov 23 14:52:34 asp NetworkManager[928]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ieee80211/phy0/rfkill2) (driver (unknown))
Nov 23 14:52:34 asp NetworkManager[928]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/acer-wmi/rfkill/rfkill0) (driver acer-wmi)
Nov 23 14:52:34 asp NetworkManager[928]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> Networking is enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> (wlan0): using nl80211 for WiFi device control
....
Nov 23 14:52:34 asp NetworkManager[928]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ieee80211/phy0/rfkill2) (driver (unknown))
Nov 23 14:52:34 asp NetworkManager[928]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/acer-wmi/rfkill/rfkill0) (driver acer-wmi)
Nov 23 14:52:34 asp NetworkManager[928]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> Networking is enabled by state file
Nov 23 14:52:34 asp NetworkManager[928]: <info> (wlan0): using nl80211 for WiFi device control
Nov 23 14:52:34 asp kernel: [   19.778319] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 23 14:52:34 asp kernel: [   19.779941] ADDRCONF(NETDEV_UP): wlan0: link is not ready
...
Nov 23 15:09:08 asp NetworkManager[881]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Nov 23 15:09:08 asp NetworkManager[881]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
...
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): using nl80211 for WiFi device control
Nov 23 15:09:08 asp NetworkManager[881]: <warn> (wlan0): driver supports Access Point (AP) mode
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): now managed
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): bringing up device.
Nov 23 15:09:08 asp acpid: 35 rules loaded
Nov 23 15:09:08 asp acpid: waiting for events: event logging is off
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): preparing device.
Nov 23 15:09:08 asp NetworkManager[881]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov 23 15:09:08 asp kernel: [   21.449849] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 23 15:09:08 asp kernel: [   21.451648] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
I hope what I have provided will enable others to help. I'm pretty much a network noob, so any and all aid is welcomed
thanks
tim

---

### Post by jeremy31 on 2014-11-24
I would remove the wifi card from the computer and clean the contacts and see if it helps, if it doesn't it might be time to buy a replacement wifi card as your issue sounds like a hardware failure

---

### Post by Tim_Johnson on 2014-11-24
> **jeremy31 said:**
> I would remove the wifi card from the computer and clean the contacts and see if it helps, if it doesn't it might be time to buy a replacement wifi card as your issue sounds like a hardware failure
I don't know if the card is removable : Please note - This is a netbook. 
Also, please note that this netbook worked with absolute reliability on windows.

Jeremy, what do you read from the diagnostics?

BTW: If I plug into ethernet, and connect with eth0, then disconnect the cable and reboot, wlan0 is found and it connects by wireless, then if I reboot - again wireless is not found. 
From research I have done, I think this is a software or driver conflict, but don't know how to resolve.

---

