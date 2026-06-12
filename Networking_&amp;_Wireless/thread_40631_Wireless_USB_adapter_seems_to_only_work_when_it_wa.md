---
title: "Wireless USB adapter seems to only work when it wants to"
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by Jakeh on 2005-06-09
I have a MN-510 wireless USB adapter, and I'm using the linux-wlan drivers.  After installing the drivers, all I had to do to get it to work was type:

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem
sudo dhclient wlan0

The first time I did that the connection worked and I could use the Internet. When that worked, I restarted the coputer, and on boot up I got the error message:

starting hotplug subsystem:
modprobe: FATAL: module wlan0 not found

Now when I try type in the same commands, the "sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem" will pause for a few seconds, and after it gives the successful message, the adapter doesn't have a connection. Sometimes when I reboot, the same thing will happen, but if I unplug and replug the adapter a few times, "sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem" will return a result instantly and the connection will work. This rarely works, though. Usually when I unplug and replug the adapter, the wireless light will continuously blink and wlanctl-ng won't detect it. If I keep unplugging it to try to get it to work right, both lights will turn off and the adapter is completely useless until I restart the computer.

I followed the directions in the linux-wlan README, but nothing seems to work. Is it a problem with hotplug? What I don't understand is why it sometimes works, but usually doesn't, and why it worked before I restarted the computer, but not after.

---

