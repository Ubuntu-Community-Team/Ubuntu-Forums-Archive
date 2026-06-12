---
title: "Configuring WWan LTE modem (SIM7000a)"
date: 2019-08-10
forum: Networking &amp; Wireless
---

### Post by treii28 on 2019-08-10
I'm trying to figure out how to configure a SIM7000a model for a wwan connection. I activated an AT&T prepaid card and they say the apn should be set to 'phone'. I have verified with AT commands that the device sees the sim and set up the prepaid with the devices imei.

mmcli -L shows the device (as does the modem-manager-gui) but I'm getting device not registered on network errors. Is sim7000a not compatible with LTE? The bands seemed to match up and it was listed as the north-american model (a).

Modem Manager Gui is able to see the SMS devices saying the sim was activated. But it says 'Modem must be registered in mobile network to connect to Internet. Please wait...'

```
$ mmcli -L
    /org/freedesktop/ModemManager1/Modem/9 [QUALCOMM INCORPORATED] 0
$ mmcli -m 9
  --------------------------------
  General  |            dbus path: /org/freedesktop/ModemManager1/Modem/9
           |            device id: 38e1ce95f270fd9760a2f3ece20a2f6b00bbd989
  --------------------------------
  Hardware |         manufacturer: QUALCOMM INCORPORATED
           |                model: 0
           |             revision: MPSS.JO.3.0.2.c3-00017-9607_LTEONLY_PACK-1  1  [Jul 25 2017 12:00:00]
           |         h/w revision: 10000
           |            supported: lte
           |              current: lte
           |         equipment id: xxxxxxxxxxxxx
  --------------------------------
  System   |               device: /sys/devices/pci0000:00/0000:00:10.1/usb7/7-1
           |              drivers: qmi_wwan, option1
           |               plugin: SimTech
           |         primary port: cdc-wdm1
           |                ports: ttyUSB0 (qcdm), wwp0s16f1u1i5 (net), ttyUSB3 (at), 
           |                       cdc-wdm1 (qmi), ttyUSB2 (at)
  --------------------------------
  Numbers  |                  own: 1734xxxxxxx
  --------------------------------
  Status   |                 lock: sim-pin2
           |       unlock retries: sim-pin (3), sim-pin2 (3), sim-puk (10), sim-puk2 (10)
           |                state: enabled
           |          power state: on
           |       signal quality: 0% (cached)
  --------------------------------
  Modes    |            supported: allowed: 4g; preferred: none
           |              current: allowed: 4g; preferred: none
  --------------------------------
  Bands    |            supported: eutran-2, eutran-3, eutran-4, eutran-12, eutran-13
           |              current: eutran-2, eutran-4, eutran-12, eutran-13
  --------------------------------
  IP       |            supported: ipv4, ipv6, ipv4v6
  --------------------------------
  3GPP     |                 imei: xxxxxxxxxxxxxxxxxx
  --------------------------------
  3GPP EPS | ue mode of operation: csps-1
  --------------------------------
  SIM      |            dbus path: /org/freedesktop/ModemManager1/SIM/9

$ sudo nmcli dev status
DEVICE      TYPE      STATE         CONNECTION         
eno1        ethernet  connected     Wired connection 1 
wlp3s0      wifi      connected     Auto MYSSID
**cdc-wdm1    modem     disconnected  --                 **
lo          loopback  unmanaged     --                 

$ sudo cat /etc/NetworkManager/system-connections/ATT\ Wireless 
[connection]
id=ATT Wireless
uuid=90314301-ed3b-4666-a505-9b64017bd081
interface-name=wwp0s16f1u1i5
type=gsm
metered=1
permissions=

[gsm]
apn=phone
number=*99#

[ipv4]
dns-search=
method=auto

[ipv6]
addr-gen-mode=stable-privacy
dns-search=
method=auto

$ nmcli c up "ATT Wireless"Error: Connection activation failed: Network registration timed out



```

---

### Post by wildmanne39 on 2019-08-10
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

