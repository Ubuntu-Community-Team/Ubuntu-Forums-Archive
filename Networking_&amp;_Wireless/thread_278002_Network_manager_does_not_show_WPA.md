---
title: "Network manager does not show WPA??"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by mankymanning on 2006-10-15
I am trying to get the latest Ubuntu to work with my wireless network using WPA.

I read in a few places about using a piece of software called Network manager which would do it automatically but when I use this it only gives me WEP options?

I am a complete linux novice having come from a Windows background and have ben impressed with Ubuntu so far but I can't believe how difficult it is to get WPA working!

My netork card is a 3com 3crwe154g72, I am pretty sure that it is supported out of the box supposedly. It certainly shows in the list of adapters in network settings.

Can anyone tell me what I need to do to get it working with WPA? Any idiots guides anywhere?

Thanks.

---

### Post by wieman01 on 2006-10-16
I think you will have to install another package to get WPA working in connection with NetworkManager. Open Synaptic and install...
> wpasupplicant
...then reboot the computer.

I may be mistaken here but I think NetworkManager needs this package as well. "wpasupplicant" is definitely a must if you configure WPA1/WPA2 manually.

---

### Post by mankymanning on 2006-10-16
I think that is already installed and I have rebooted a couple of times but it doesn't seem to have helped. Do I need to do anything to wpasupplicant like modify config files that sort of thing or should network manager do it for me?

---

### Post by wieman01 on 2006-10-16
> **mankymanning said:**
> I think that is already installed and I have rebooted a couple of times but it doesn't seem to have helped. Do I need to do anything to wpasupplicant like modify config files that sort of thing or should network manager do it for me?
Basically no. But you could show us the contents for this file (command line):
> sudo gedit /etc/network/interfaces

---

### Post by mankymanning on 2006-10-16
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



Under network settings in the system menu it says that the wireless connection is eth2

---

### Post by wieman01 on 2006-10-16
> **mankymanning said:**
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



Under network settings in the system menu it says that the wireless connection is eth2
Ok, edit this file so that it looks like this (basically 'commenting' all wireless adapters - NetworkManager requires that):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
[COLOR="Red"]
#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp[/COLOR]
And leave "eth0" like it is as it is your Ethernet connection.

If that does NOT work, try this only:
> auto lo
iface lo inet loopback
Then restart the PC & try once again.

---

### Post by mankymanning on 2006-10-17
I tried that and I still only get the WEP options, no WPA :(

Is there anything else I can try?

---

### Post by wieman01 on 2006-10-17
Mmm... have you tried post #18 of this thread?

[http://www.ubuntuforums.org/showthread.php?t=194264&page=2&highlight=networkmanager+wpa]("http://www.ubuntuforums.org/showthread.php?t=194264&page=2&highlight=networkmanager+wpa")

_**EDIT:**_
Or perhaps check out this howto for your chipset: [http://www.ubuntuforums.org/showthread.php?t=156710&highlight=networkmanager+wpa]("http://www.ubuntuforums.org/showthread.php?t=156710&highlight=networkmanager+wpa")

---

