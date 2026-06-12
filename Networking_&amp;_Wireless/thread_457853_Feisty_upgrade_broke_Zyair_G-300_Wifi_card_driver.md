---
title: "Feisty upgrade broke Zyair G-300 Wifi card driver"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by ebike on 2007-05-29
I upgraded my Ubuntu box from Edgy to Feisty and now I cannot set the mode of the card. It was working perfectly
in Edgy in "Master" mode, but I get errors whenever I try to set the mode with iwconfig or in /etc/network/interfaces. (it won't accept any mode change .. stays in default "managed")

The error is:
> sudo iwconfig wlan0 mode master
Password:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

I can set the ESSID ok and the key, it fails only on the "mode" command.

lspi shows:
> 01:06.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

iwconfig shows:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.417 GHz
          RTS thr:off   Fragment thr=2346 B

wlan0     IEEE 802.11g  ESSID:"Mythtv"
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

br0       no wireless extensions.

The relevent portion of /etc/network/interfaces is:
> # My wireless interface
auto wlan0
iface wlan0 inet manual
address 0.0.0.0
wireless-mode master
wireless-channel 2
wireless-essid Mythtv
wireless-key 013top-secret-number99aa restricted

I notice that the driver has changed with the upgrade, because now I have prism54pci and prism54common modules ..
I am also running a 2.6.20 kernel now. (used to be 2.6.17)

Does anyone know if this is a bug in the latest drivers?

Let me know if you require anymore system information.

Thanks.

---

### Post by ebike on 2007-05-29
Well you guys are too slow ... fixed it myself.

Seems I needed the latest formware from the prism54.org website and plonked it in the
/usr/lib/hotplug/firmware directory, re-loaded the driver and now everything works ...:p

---

### Post by ebike on 2007-05-30
Ok, spoke too soon. The iwconfig tools allows the mode to be set. But the AP is not seen by other machines.

I have no idea what to do next.

---

