---
title: "bluetooth not working in ubuntu 22.04"
date: 2022-06-10
forum: Networking &amp; Wireless
---

### Post by akashsinhaha on 2022-06-10
rfkill status:

```
ID TYPE         DEVICE             SOFT         HARD
 0 wlan          hp-wifi              unblocked  unblocked
 1 bluetooth   hp-bluetooth     unblocked  unblocked
 2 wlan          phy0                unblocked   unblocked

```

sudo dmesg | grep -i blue status

```
[   18.449774] Bluetooth: Core ver 2.22
[   18.449804] NET: Registered PF_BLUETOOTH protocol family
[   18.449807] Bluetooth: HCI device and connection manager initialized
[   18.449812] Bluetooth: HCI socket layer initialized
[   18.449815] Bluetooth: L2CAP socket layer initialized
[   18.449822] Bluetooth: SCO socket layer initialized
[   21.210206] Bluetooth: HCI UART driver ver 2.3
[   21.210216] Bluetooth: HCI UART protocol H4 registered
[   21.210219] Bluetooth: HCI UART protocol BCSP registered
[   21.210268] Bluetooth: HCI UART protocol LL registered
[   21.210272] Bluetooth: HCI UART protocol ATH3K registered
[   21.210316] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   21.210382] Bluetooth: HCI UART protocol Intel registered
[   21.210482] Bluetooth: HCI UART protocol Broadcom registered
[   21.210577] Bluetooth: HCI UART protocol QCA registered
[   21.210583] Bluetooth: HCI UART protocol AG6XX registered
[   21.210618] Bluetooth: HCI UART protocol Marvell registered
[   65.318242] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   65.318253] Bluetooth: BNEP filters: protocol multicast
[   65.318258] Bluetooth: BNEP socket layer initialized

```

sudo systemctl status bluetooth.service status:

```

&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Thu 2022-06-09 01:41:44 IST; 1 day 18h ago
       Docs: man:bluetoothd(8)
   Main PID: 1106 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 4546)
     Memory: 1.0M
        CPU: 135ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1106 /usr/lib/bluetooth/bluetoothd

```

---

### Post by #&amp;thj^% on 2022-06-10
Just a couple more things to show please:
```
inxi --bluetooth
```
and:
```
lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

```

---

### Post by akashsinhaha on 2022-06-10
inxi --bluetooth shows


```
Bluetooth:
  Device-1: Ralink RT3290 Bluetooth driver: N/A


```

lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'  shows


```
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:2212]
	Kernel driver in use: r8169


0a:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
	Kernel driver in use: rt2800pci

```

---

### Post by #&amp;thj^% on 2022-06-10
Please Note: The current deb package of Ralink rt3290 bluetooth is only available for x64 based distribution for 32bit distros you need to manually compile the bluetooth package(Non relevant now) for more please follow this: [https://github.com/loimu/rtbth-dkms](https://github.com/loimu/rtbth-dkms)
Let us know if you need more help..
**EDIT: I found a better method>>>PPA found here: [https://launchpad.net/~blaze/+archive/ubuntu/rtbth-dkms](https://launchpad.net/~blaze/+archive/ubuntu/rtbth-dkms)**
Better support I would think....

---

### Post by akashsinhaha on 2022-06-10
your help is very much appreciated. i added the ppa and did sudo apt update, what should i do next?

---

### Post by #&amp;thj^% on 2022-06-10
If your sure you first ran:
```
sudo apt update && sudo apt upgrade
```
install it if not already done:
```
sudo apt install rtbth-dkms
```
reboot now to load it.

---

### Post by akashsinhaha on 2022-06-10
ok i have installed the rtbth-dkms

---

### Post by #&amp;thj^% on 2022-06-10
can you pair it now??
EDIT: Do you see the bluetooth applet?

---

### Post by akashsinhaha on 2022-06-10
no it is still not working

---

### Post by akashsinhaha on 2022-06-10
'bluetoothctl show' shows
```
No default controller available



```

---

### Post by #&amp;thj^% on 2022-06-10
> **akashsinhaha said:**
> no it is still not working
I say this with all kindness>>>please do not use this phrase "it is still not working" what am I supposed to do with that? ;)
Ok, now show this please:
```
lsmod | grep bluetooth

```
also:
```
systemctl status bluetooth
```

---

### Post by akashsinhaha on 2022-06-10
sorry if i sounded rude, english is not my mother tongue, i really didnt mean it that way.:KS

here are the results
'lsmod | grep bluetooth' shows
```
bluetooth             688128  13 btrtl,btqca,btintel,hci_uart,btbcm,bnep,btusb
ecdh_generic           16384  1 bluetooth

```

'systemctl status bluetooth' shows


```
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Fri 2022-06-10 22:55:39 IST; 35min ago
       Docs: man:bluetoothd(8)
   Main PID: 1114 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 4546)
     Memory: 1.8M
        CPU: 126ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1114 /usr/lib/bluetooth/bluetoothd


Jun 10 22:55:38 ak systemd[1]: Starting Bluetooth service...
Jun 10 22:55:39 ak bluetoothd[1114]: Bluetooth daemon 5.64
Jun 10 22:55:39 ak systemd[1]: Started Bluetooth service.
Jun 10 22:55:39 ak bluetoothd[1114]: Starting SDP server
Jun 10 22:55:39 ak bluetoothd[1114]: Bluetooth management interface 1.21 initia>
lines 1-17/17 (END)


```

---

### Post by #&amp;thj^% on 2022-06-10
> **akashsinhaha said:**
> sorry if i sounded rude, english is not my mother tongue, i really didnt mean it that way.:KS


No apology needed, I've hung around forums for nearly 25 years now, that one is just a bit hard for me to deal with, just me.
Ok now what happens if you toggle WiFi off and on again or the other way around.
will bluetoothctl show different now?

---

### Post by akashsinhaha on 2022-06-10
now i can understand why you hate that line.:)

even after toggling the wifi and the bluetooth, bluetoothctl shows the same result.
"No default controller available"

---

### Post by jeremy31 on 2022-06-10
What result for ```
mokutil --sb
```

---

### Post by akashsinhaha on 2022-06-10
'mokutil --sb' shows


```
SecureBoot disabled
Platform is in Setup Mode

```

---

### Post by #&amp;thj^% on 2022-06-10
Thanks jeremy31 that was my next move ;)
Ok that's one more narrowed out, try the below:
```
sudo modprobe rtbth
```
```
sudo rfkill unblock bluetooth
```

---

### Post by akashsinhaha on 2022-06-10
for a moment the bluetooth settings was working, it was scanning for devices. As soon as i toggled it on and off it is back to the same way.

---

### Post by akashsinhaha on 2022-06-10
also the result for 'bluetoothctl show' has changed 
here is the result:

```
Controller FF:FF:FF:FF:FF:FF (public)
	Name: ak
	Alias: ak
	Class: 0x00000000
	Powered: no
	Discoverable: no
	DiscoverableTimeout: 0x000000b4
	Pairable: no
	UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
	UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
	UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
	UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
	UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
	UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
	UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
	UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
	UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
	UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
	UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
	UUID: Handsfree Audio Gateway   (0000111f-0000-1000-8000-00805f9b34fb)
	UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
	UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
	Modalias: usb:v1D6Bp0246d0540
	Discovering: no



```

---

### Post by #&amp;thj^% on 2022-06-10
try now:
```
bluetoothctl power on

```
then again only if you see:
```
 bluetoothctl power on
Changing power on succeeded
```

```
bluetoothctl
```

---

### Post by akashsinhaha on 2022-06-10
i rebooted the device and after running [COLOR=#000000][FONT=&quot]bluetoothctl power on
[/FONT][/COLOR]it gives:

[COLOR=#000000][/COLOR]```
No default controller available



```

---

### Post by #&amp;thj^% on 2022-06-10
you'll have to run this until we figure out if it works or not:
```
sudo modprobe rtbth
```

---

### Post by akashsinhaha on 2022-06-11
the bluetooth tab in the settings is showing 'searching for devices' but is unable to search.

when i run 'bluetoothctl scan on' it says:


```
Failed to start discovery: org.bluez.Error.InProgress

```

---

### Post by im-aa on 2022-12-24
This worked for me! Thank you @1fallen!

---

