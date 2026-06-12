---
title: "To Get Wifi To Work"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by asimon623 on 2005-09-14
After rebooting

modprobe ndiswrapper
dmesg
ndiswraper -m
ifup wlan0

is there anyway to avoid this?
make a file to do this for me?

---

### Post by essexman on 2005-09-14
[QUOTE=asimon623]After rebooting

modprobe ndiswrapper
dmesg
ndiswraper -m
ifup wlan0

is there anyway to avoid this?
make a file to do this for me?[/QUOTE]
I recommend this [wiki howto](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29) which worked for me, though there are other ways.

You need to add ndiswrapper to the bottom of your modules file : ```
sudo gedit /etc/modules
``` and type ndiswrapper at the bottom.

Then configure and activate the card the card via: > System>>Administration>>Networking

Put in you WEP and stuff, then reboot.

---

### Post by mlomker on 2005-09-14
Add **ndiswrapper** to the end of the /etc/modules file.

---

