---
title: "No network after password reset (or mount -o rw,remount / )"
date: 2017-04-21
forum: Networking &amp; Wireless
---

### Post by cycloneix on 2017-04-21
I use only kubuntu 14.04.5 installation on a single partition disk. I had recently reset my user password from recovery using the instructions on this: [https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

**I tested and the internet works fine from a live installation usb.**


After that (I think) my internet stopped working. tried a bunch of things. 

 ifconfig shows eth0 and lo. dmesg | grep eth last entry is eth0 has been renamed to eth2 or something. lshw -c network shows *-network DISABLED for eth2.

I uninstalled network-manager
Then the eth2 entry from ifconfig was gone.
I then edited /etc/network/interfaces. I use a static IP based configuration, so I tried to add eth0 and eth2 entry as such (both fails). Now a docker0 and eth2 entry is present in ifconfig.

I don't use wifi and never have on that machine, however I have a usb wifi dongle, and I can use that as a alternative (it didn't work as soon as I plugged it in, so I did not tinker any further).

I am willing to reinstall/repair from my live usb, but I did not see that option during installation.

Any help will be appreciated.

---

