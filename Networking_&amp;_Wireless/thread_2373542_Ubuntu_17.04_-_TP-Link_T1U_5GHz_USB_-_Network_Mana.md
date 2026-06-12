---
title: "Ubuntu 17.04 - TP-Link T1U 5GHz USB - Network Manager - device not managed"
date: 2017-10-07
forum: Networking &amp; Wireless
---

### Post by tomasz-raganowicz on 2017-10-07
Hi,
I've got Lenovo G510 with Broadcom wifi (wlp8s0) and trying to run the TP-Link Archer T1U 5GHz USB dongle.
I've compiled, installed the drivers: [https://github.com/ulli-kroll](https://github.com/ulli-kroll) and loaded them using the: `[COLOR=#24292E][FONT=SFMono-Regular]sudo insmod mt7610u.ko`[/FONT][/COLOR]
It shows up in the Network Manager, like:
WiFi Network (MediaTek WiFi) 
device not managed

Doing the:
`sudo ifconfig wlan0 up`
and
`sudo iwlist wlan0 scan`
I can see some networks, so I expect driver works OK.

a) How do I disable my `wlp8s0` in Network Manager and make it work with the `wlan0`
I've tried to add this line: `iface wlp8s0 inet manual` to `/etc/network/interfaces` hoping that Network Manager won't try to manage device defined in this file, but my Broadcom Wifi is still managed by Network Manager.
I've also tried to empty the: `/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf` file, previously it had this line inside:
 `[keyfile]
 unmanaged-devices=*,except:type:wifi,except:type:wwan`

After reboot it didn't work though. Still Broadcom works OK, TP-Link is unmanaged

b) Is there a way to load `[COLOR=#24292E][FONT=SFMono-Regular]mt7610u.ko` [/FONT][/COLOR]during boot?

I've tried to add the `mt7610u` to `/etc/modules` then ran `sudo depmod -a`, but still my module is not loaded after reboot.

Please find the output from `wireless-info` tool to give you more details about my setup.
[http://paste.ubuntu.com/25691267/](http://paste.ubuntu.com/25691267/)

Any help much appreciated.

---

