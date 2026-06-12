---
title: "Bluetooth problem pairing bt low energy (BLE) device"
date: 2021-10-10
forum: Networking &amp; Wireless
---

### Post by franknfurter2 on 2021-10-10
Hello,

I bought an HiFi amplifier NAD C368 and am running Kodi on a Lubuntu System. The NAD C368 uses a bluetooth low energy (BLE) adapter to use it as an audio sink or to control all features of the amp via a smartphone app (NAD Remote App).

I was able to pair the amp with my android smartphone as a audio source and to use smartphone to control the amp.

But when I try to pair the Lubuntu System as an audio source with the amp it is not working. I tried different GUI on Lubuntu but none will work. So I dig into commandline using bluetoothctl, hcitool and gatttool.

Only with command "hcitool lescan" it was possible to detect the device and only with gatttool it was possible to connect. One has to use the random transport because it is somehow secured this way.

sudo gatttool -b 59:XX:A2:XX:YY:ZZ -I -t random
[59:XX:A2:XX:YY:ZZ][LE]> connect
Attempting to connect to 59:XX:A2:XX:YY:ZZ
Connection successful
[59:XX:A2:XX:YY:ZZ][LE]> characteristics
handle: 0x0002, char properties: 0x20, char value handle: 0x0003, uuid: 00002a05-0000-1000-8000-00805f9b34fb
handle: 0x0006, char properties: 0x02, char value handle: 0x0007, uuid: 00002a00-0000-1000-8000-00805f9b34fb
handle: 0x0008, char properties: 0x02, char value handle: 0x0009, uuid: 00002a01-0000-1000-8000-00805f9b34fb
handle: 0x000b, char properties: 0x1a, char value handle: 0x000c, uuid: 6d7ce918-fb09-4eab-80ee-ad32bf2afc0e
[59:XX:A2:XX:YY:ZZ][LE]> 

The System uses a Qualcomm Atheros AR9485 Chip

lspci | grep ual
01:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

lsusb | grep ualc
Bus 004 Device 002: ID 0cf3:311d Qualcomm Atheros Communications Bluetooth USB Host Controller

**I have no knowledge how to pair these devices, mark them trusted and use the Lubuntu system as a bt audio source and the NAD amp as an bt audio sink.**

Any guide will be very helpful.

Regards

Frank

---

### Post by guiverc on 2021-10-10
> **franknfurter2 said:**
> 
But when I try to pair the Lubuntu System as an audio source with the amp it is not working. I tried different GUI on Lubuntu but none will work. So I dig into commandline using bluetoothctl, hcitool and gatttool.


I can't help sorry; I have almost little with bluetooth.

Providing details of your software stack maybe helpful (ie. *what release you're using*).  If you're using a LTS release - which kernel stack you've chosen to use may also be helpful (*the stack default is chosen by the ISO you installed your system with; eg. Lubuntu 20.04 & 20.04.1 media default to GA stack; 20.04.2 & later default to HWE*). Whilst the stack may not have much impact on bluetooth (*it impacts graphics far mor*e), the more detail you provide for us the more others maybe able to help.

I can say Lubuntu shouldn't impact other GUI's or desktops.  I use multiple desktops on my systems (*my Lubuntu has Ubuntu (GNOME) & Xubuntu (Xfce) installed & each work correctly; but I use others too including WMs*).  The GUI/UI I'd not expect would make any change to using bluetooth though (*except if adding another desktop pulled in a package that was helpful due to depends/recommends rule*).

I'll also provide the manual page (*I don't know your release, so I've provided the latest stable release; ie. currently 21.04*) [https://manual.lubuntu.me/stable/2/2.1/2.1.4/bluedevil.html](https://manual.lubuntu.me/stable/2/2.1/2.1.4/bluedevil.html)

---

### Post by franknfurter2 on 2021-10-13
Hallo,

ok, here are more details in hope, that someone has an idea. I will also open a bug for this because it seems to me, that it is not working as expected. 

I am now able to see the NAD Device when scanning using bluetoothctl. I first started with the hint I found here ([https://wiki.archlinux.org/title/Bluetooth](https://wiki.archlinux.org/title/Bluetooth)) that said, that one has to do "hcitool lescan" in one terminal while doing a scan in the other terminal window. I did and yes, sometimes the scan found the NAD device. But I took a deeper look into the documentation and found the configuration file /etc/bluetooth/main.conf . Here you can find these parameters.

```
# Default device class. Only the major and minor device class bits are
# considered. Defaults to '0x000000'.
#Class = 0x000100 # Computer Type (from default config)
Class = 0x100100 # (Object-Transfer Service & Computer Type)

# Restricts all controllers to the specified transport. Default value
# is "dual", i.e. both BR/EDR and LE enabled (when supported by the HW).
# Possible values: "dual", "bredr", "le"
#ControllerMode = dual
ControllerMode = le
```

Uncommented are the values that I have set.

I do not know exactly, which of them did the trick, but now the NAD device is shown and I could start the pair command for that device. I than ran into other problems. I could get a connection but the pairing ended with an Authentication error.

By the way, I'm using 

[LIST]
[*]Lubuntu 20.04 (Linux K700 5.4.0-88-generic #99-Ubuntu SMP Thu Sep 23 17:29:00 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux) 
[*]bluetoothctl 5.49 
[/LIST]
 
I think that this is a bug, because the controller mode dual does not find the BLE device.

Regards

Frank

---

