---
title: "Wifi in windows 8 not working after disabling wireless in ubuntu 12.04"
date: 2013-10-08
forum: Networking &amp; Wireless
---

### Post by ghantauke on 2013-10-08
I have a dual boot system with Ubuntu 12.04 installed within windows 8 (C drive).

Wifi was working fine, both in ubuntu and windows until yesterday, when I disabled wireless in ubuntu by unchecking the "Enable Wireless" button from the top panel. I wasn't aware that this option was bugged. It went grey after unchecking it, so I couldn't click on it to re-enable it. I looked up for solution to turn the wireless back on and I found a solution.

I followed the steps below:
[LIST]
[*]Use the command "rfkill unblock all".
[*]Uncheck "Enable Networking" from the top panel.
[*]Check "Enable Networking" from the top panel.
[*]Check "Enable Wireless" from the top panel.
[/LIST]

The wifi is working in ubuntu after that. However, I cannot enable wifi in windows.

The following image shows that the Wifi is off.
[http://img405.imageshack.us/img405/5536/16js.jpg](http://img405.imageshack.us/img405/5536/16js.jpg)

The following image shows that Wifi adapter is enabled and the diver is working fine.
[http://img713.imageshack.us/img713/2052/gdr1.jpg](http://img713.imageshack.us/img713/2052/gdr1.jpg)

So I guess I need the "rfkill unblock all" equivalent command in windows to fix this. Any other solution which you think can fix this will also be appreciated.

---

### Post by ghantauke on 2013-10-10
bump

---

### Post by BazBear on 2013-10-10
Odd one. Have you tried going to device manager and uninstalling then reinstalling the wireless card?

---

### Post by varunendra on 2013-10-10
Or removing --> reinstalling the driver from the same device manager window, which will be instantaneous too since it is already in the system.

---

### Post by BazBear on 2013-10-13
Any luck[COLOR=#000000] Ghantauke?[/COLOR]

---

### Post by Sinixstar on 2013-10-13
Look into "netsh" script shell for windows. You basically want to run this :

netsh interface set interface name="Local Area Connection" admin=enabled

Where interface name="[your interface name]"

netsh has a ton of options - I'd read up on it a little bit. Pretty much anything you can do in the interface, you can do through the cmd line with netsh

[http://technet.microsoft.com/en-us/library/cc754516%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc754516%28v=ws.10%29.aspx)

Also - make sure you run the command prompt in elevated privileges (right click from Start -> Applications -> Accessories and "run as administrator")

---

### Post by Kontr-Olli on 2014-04-21
Hi,

I've got the same problem under my recent gentoo system....if I start gentoo and use the NetworkManager to disable/softblock wifi

"rfkill list" shows:
0: sony-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

everything works as expected. I'm able to block/unblock the wifi device from NetworkManager as it should.

But if I leave the device blocked and reboot into Windows 8.1 I'm not able to activate the device anymore. Windows told me something, that the hardware switch is enabled and isn't able to activate the wifi device. The "activation" slider is grayed-out under windows 8.1.

My current workaround:
I have a linux script under local.d which unblocks the wifi as soon as I shutdown/reboot from gentoo. Afterwards I'm able to use wifi under Windows.

Strange, cause with this Bug/configuration of rfkill I'm able to block the card under linux and never able to bring it online under windows 8.1....quite interessting....

Before I updated to Windows 8, everthing worked fine with Windows 7 and gentoo in dualboot.

regards,
Oliver

---

