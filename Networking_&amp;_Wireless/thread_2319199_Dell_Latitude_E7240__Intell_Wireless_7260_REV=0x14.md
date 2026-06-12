---
title: "Dell Latitude E7240 / Intell Wireless 7260 REV=0x144 (rev 73) Hardware Disabled"
date: 2016-04-01
forum: Networking &amp; Wireless
---

### Post by havanahjoe on 2016-04-01
I've spent some time searching all over, and even though there are plenty of threads talking about "Hardware Disabled" issues with soft switches, not a lot talk about issues with an existing Physical Switch and how Network Manager mishandles this hardware on boot and on resume.

My E7240 has a physical switch that is always on, but if I turn off the Wireless card (or on boot, or after suspending) Network Manager (and rfkill) report that the Hardware is Disabled.

The output of rfkill when everything is working:

```
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
5: nfc0: NFC
	Soft blocked: no
	Hard blocked: no

```
The first thing that has caught my attention is that there is a phy0 wireless and a dell-wifi wireless.

Upon further reading, I ran into a thread where chili555 suggests removing dell-laptop. Once I did that, the "dell-wireless" device disappeared and now turning off the Wireless does not set Hard Blocked to yes. 

Unfortunately, when resuming the laptop from sleep, the Hard Block is set to yes again.

Toggling the switch will remove the block, but then I have to restart network-manager.service which messes up my en0 config by defaulting to DHCP even though none of my profiles are set up that way (I have a link local only profile and one that has specific routes configured). Selecting the profile I want again will restore everything, so it's a very involved process.

I do have a wifi-resume.service in /etc/systemd/system but without toggling the physical switch, it's not helping much.

I see this in the syslog:

```
Apr  1 14:30:21 JorgeLinux NetworkManager[15946]: <info>  rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/ieee80211/phy0/rfkill1) (driver iwlwifi)

```

So I tried to force a 0 in the 'hard' file in that folder, but access is denied, even as root.

Interestingly, toggling the switch while everything is working causes no problems. WiFi disconnects with the switch off, and it reconnects when I turn it back on.  The output of rfkill is different though:
```

jdargence@JorgeLinux:~$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
19: dell-rbtn: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
22: nfc0: NFC
	Soft blocked: no
	Hard blocked: no
23: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

Using the hardware switch does not touch phy0.

---

