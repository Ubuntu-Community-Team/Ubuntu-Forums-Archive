---
title: "D-Link DWL 122: How to set up?"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by Donalbain on 2005-05-16
Hi!

I'm new to Ubuntu, but I'd like to dump SuSE for it. All I need now is wireless networking...

The USB-Stick DWL-122 is working with SuSE and linux-wlan-ng. I tried the following on Ubuntu without success, maybe you have an Idea:

1. installed linux-wlan-ng (0.2.0+0.2.1pre21-1)

2. I setup a script /etc/hotplug/usb/prism2_usb like this:
```

#!/bin/bash
modprobe prism2_usb prism2_doreset
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="58:23:68:9a:(obscured)"
wlanctl-ng wlan0 lnxreq_autojoin ssid="(obscured)" authtype="sharedkey"
ifconfig wlan0 192.168.178.101 up
route add default gw 192.168.192.1

``` 
(I obtained the ff:ff:ff:ff:blah blah-code by using /sbin/nwepgen (13 letters code) 13)

Now when I modprobe prism2_usb by hand I get:
```

May 16 23:45:51 localhost kernel: prism2usb_init: prism2_usb.o: 0.2.1-pre25 Loaded
May 16 23:45:51 localhost kernel: prism2usb_init: dev_info is: prism2_usb
May 16 23:45:51 localhost kernel: usbcore: registered new driver prism2_usb

```
(for testing I put prism2_usb into the hotplugging blacklist)

- looks good to me.

Then I plug in the device. I get:
```

May 16 23:48:08 localhost kernel: usb 1-2: new full speed USB device using ohci_hcd and address 5
May 16 23:48:08 localhost usb.agent[10306]:      prism2_usb: already loaded
May 16 23:48:09 localhost kernel: hfa384x_dorrid: ctlx failure=REQ_TIMEOUT

```
- is this OK?

Next, I start the script from above by hand. I get:
```

root@norman:/etc/hotplug/usb# ./prism2_usb
message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
message=lnxreq_hostwep
  resultcode=no_value
  decrypt=true
  encrypt=true
message=dot11req_mibset
  mibattribute=dot11PrivacyInvoked=true
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKeyID=0
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKey0=58:23:68:9a:(obscured)
  resultcode=success
message=lnxreq_autojoin
  ssid='(obscured)'
  authtype=sharedkey
  resultcode=success
SIOCADDRT: Das Netzwerk ist nicht erreichbar

```
The last line is result of the route-command. 

/var/log/messages says:
```

May 16 23:49:35 localhost kernel: ident: nic h/w: id=0x8026 1.0.0
May 16 23:49:35 localhost kernel: ident: pri f/w: id=0x15 1.1.3
May 16 23:49:35 localhost kernel: ident: sta f/w: id=0x1f 1.7.1
May 16 23:49:35 localhost kernel: MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
May 16 23:49:35 localhost kernel: CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
May 16 23:49:35 localhost kernel: PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
May 16 23:49:35 localhost kernel: STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
May 16 23:49:35 localhost kernel: PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
May 16 23:49:35 localhost kernel: STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
May 16 23:49:35 localhost kernel: STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
May 16 23:49:35 localhost kernel: Prism2 card SN: 000000000000
May 16 23:49:36 localhost kernel: p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
May 16 23:49:36 localhost kernel: linkstatus=ASSOCFAIL (unhandled)
May 16 23:49:36 localhost kernel: p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
May 16 23:49:45 localhost last message repeated 3 times

```

ifconfig says: 
```

wlan0     Protokoll:Ethernet  Hardware Adresse 00:11:95:82:DF:63
          inet Adresse:192.168.178.101  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6 Adresse: fe80::211:95ff:fe82:df63/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:5 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
- which looks good to me.

iwconfig wlan0 says:
```

wlan0     IEEE 802.11-DS  ESSID:"(obscured)"  Nickname:"(obscured)"
          Mode:Auto  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:5823-689A-3444-2E0C-D2D6-7873-0B   Security mode:open
          Link Quality=0/92  Signal level=-69 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

when I issue the route command by hand I get no error:
route add default gw 192.168.178.1

For me, all looks kinda good in a way, but the device's link-led blinks and In get no connection.

I doublechecked all SSIDs and keys (of course, they are obsured here) but I have no idea where to check next. Do you see the error?


I also tried ndiswrapper -i NETPRISM.inf (which loads perfectly), but I don't know what to write in /etc/network/devices concerning SSIDa and shared keys. The following /etc/network/devices is definitly wrong. Maybe you can correct it:
```

auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.178.101
netmask 255.255.255.0
network 192.168.178.0
broadcast 192.168.178.255
gateway 192.168.178.1
wireless-mode Managed
wireless-keymode sharedkey
wireless-key (obscured 13-letters-key)
wireless-essid (obscured)

```

Would be great if anyone could help!
Joerg

---

### Post by az on 2005-05-16
I hope you find this more helpful than frustrating.  My dwl-122 works well on Mondays and thursdays.  On weekends it sometimes works and all the rest of the times, it depends on the weater.  This is valid for windows machines as well as linux machines.

Your mileage may vary.

I currently have more success using ndiswrapper than with the prism drivers.  The prism drivers have gotten better, but I cannot really help as I avoid using my 122.

Sorry.

---

### Post by Donalbain on 2005-05-17
[QUOTE=azz]
I currently have more success using ndiswrapper than with the prism drivers.  The prism drivers have gotten better, but I cannot really help as I avoid using my 122.
[/QUOTE]

Hi Azz!

Could you provide me with a /etc/network/interfaces file that you use with ndiswrapper?

Other strategy: What reasonable pci-wlan card would be better? Would be great if I could also use WPA with it.

Thanks
Joerg

---

