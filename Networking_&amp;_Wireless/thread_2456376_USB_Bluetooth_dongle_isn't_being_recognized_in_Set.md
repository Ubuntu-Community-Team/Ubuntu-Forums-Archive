---
title: "USB Bluetooth dongle isn't being recognized in Settings"
date: 2021-01-10
forum: Networking &amp; Wireless
---

### Post by extraspecialbitter2 on 2021-01-10
I have a new Dell OptiPlex 7080 that came with a Dell USB Bluetooth dongle, but it doesn't appear that any effort was made to install its drivers or to otherwise insure that it would work with Ubuntu 18.04. When I bring up the "Settings" app and select "Bluetooth", I see "No Bluetooth Found." 

The device shows up when I do an "lsusb":

```
]root@pmena-7080=> lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 413c:8505 Dell Computer Corp. 
Bus 001 Device 003: ID 0000:3825  
Bus 001 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 005: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

However when I run "bluetoothctl" to interact with the dongle, it's clearly not there.

```
pmena@pmena-7080=> bluetoothctl
Agent registered
[bluetooth]# power on
No default controller available
[bluetooth]# devices
No default controller available

```

For its part, the bluetooth service is running:

```
root@pmena-7080=> systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2021-01-09 14:59:29 EST; 20h ago
     Docs: man:bluetoothd(8)
 Main PID: 5226 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;5226 /usr/lib/bluetooth/bluetoothd


Jan 09 14:59:29 pmena-7080 systemd[1]: Starting Bluetooth service...
Jan 09 14:59:29 pmena-7080 bluetoothd[5226]: Bluetooth daemon 5.48
Jan 09 14:59:29 pmena-7080 systemd[1]: Started Bluetooth service.
Jan 09 14:59:29 pmena-7080 bluetoothd[5226]: Starting SDP server
Jan 09 14:59:29 pmena-7080 bluetoothd[5226]: Bluetooth management interface 1.14 initialized

```

How might I go about finding and installing the Device Driver I need (assuming that it will work with Linux)?

Thanks in advance

---

### Post by #&amp;thj^% on 2021-01-10
I don't see a device listed in "lsusb"
If you would also include:
```
rfkill list
```
And:
```
hcitool dev
```
We might see something.

---

### Post by jeremy31 on 2021-01-10
Post results for ```
usb-devices | awk '/8505/' RS=
```

---

### Post by extraspecialbitter2 on 2021-01-10
> **1fallen said:**
> I don't see a device listed in "lsusb"
If you would also include:
```
rfkill list
```
And:
```
hcitool dev
```
We might see something.

Thank you for the reply. Per your request:

```
pmena@pmena-7080=> rfkill list0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
pmena@pmena-7080=> hcitool dev
Devices:
```

I'm pretty sure the USB dongle is the second device (Bus 001 Device 008) listed below:

```
pmena@pmena-7080=> lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 413c:8505 Dell Computer Corp. 
Bus 001 Device 003: ID 0000:3825  
Bus 001 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 005: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 009: ID 046d:0992 Logitech, Inc. QuickCam Communicate Deluxe
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by extraspecialbitter2 on 2021-01-10
> **jeremy31 said:**
> Post results for ```
usb-devices | awk '/8505/' RS=
```

Thank you for the reply. If I'm reading this correctly, this command identifies the driver (usbhid):

```
pmena@pmena-7080=> usb-devices | awk '/8505/' RS=T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=05 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=32 #Cfgs=  1
P:  Vendor=413c ProdID=8505 Rev=11.23
S:  Manufacturer=Dell
S:  Product=Dell Universal Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

```

---

### Post by jeremy31 on 2021-01-10
Is there some option in BIOS to enable wifi and/or bluetooth?

---

### Post by extraspecialbitter2 on 2021-01-10
> **jeremy31 said:**
> Is there some option in BIOS to enable wifi and/or bluetooth?

I'm not sure, but I do know that WiFi is working. I'm using a USB WiFi dongle as I type this. ;)

---

### Post by extraspecialbitter2 on 2021-01-10
Based upon [https://www.dell.com/support/kbdoc/en-us/000132057/how-to-use-the-dell-universal-pairing#1](https://www.dell.com/support/kbdoc/en-us/000132057/how-to-use-the-dell-universal-pairing#1), I'm thinking that my "Dell Universal Receiver" isn't so universal at all, but rather supports only a few specific Dell-branded mice and keyboards. More to the point, [https://www.dell.com/support/home/en-us/drivers/DriversDetails?DriverId=9PPPW](https://www.dell.com/support/home/en-us/drivers/DriversDetails?DriverId=9PPPW) leads me to believe that the driver only works with Windows. If that's the case, I'll need to buy a Linux-compatible dongle.

---

### Post by jeremy31 on 2021-01-10
The spec sheet I looked at showed that the 7080 used a combo wifi/bluetooth card that was either Intel or Atheros, no mention of a module like they used on older laptops

---

### Post by extraspecialbitter2 on 2021-01-10
The WiFi USB dongle I'm using is from "Bros Trend", but is actually a Realtek product under the covers:

```
pmena@pmena-7080=> usb-devices | awk '/0bda/' RS=T:  Bus=01 Lev=01 Prnt=01 Port=12 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b812 Rev=02.10
S:  Manufacturer=Realtek
S:  Product=802.11ac NIC
S:  SerialNumber=123456
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 5 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl88x2bu

```

I bought it because the 7080 already had a Dell USB Bluetooth dongle that I thought would accommodate my Keyboard (a Logitech K380) and mouse (a Logitech M720). Silly me!

---

### Post by #&amp;thj^% on 2021-01-10
> **extraspecialbitter2 said:**
> The WiFi USB dongle I'm using is from "Bros Trend", but is actually a Realtek product under the covers:

```
pmena@pmena-7080=> usb-devices | awk '/0bda/' RS=T:  Bus=01 Lev=01 Prnt=01 Port=12 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b812 Rev=02.10
S:  Manufacturer=Realtek
S:  Product=802.11ac NIC
S:  SerialNumber=123456
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 5 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl88x2bu

```

I bought it because the 7080 already had a Dell USB Bluetooth dongle that I thought would accommodate my Keyboard (a Logitech K380) and mouse (a Logitech M720). Silly me!
This is what we hoped we would see with the Bluetooh dongle "Driver=rtl88x2bu" but for the bluetooth.
Curious though dose'nt the keyboard and mouse have their own usb receiver?
jeremy31 I'm going fishing, see you on the lake. :D
EDIT: I wonder if "solaar" will work for your needs: [https://github.com/pwr-Solaar/Solaar](https://github.com/pwr-Solaar/Solaar)

---

### Post by extraspecialbitter2 on 2021-01-10
> **1fallen said:**
> This is what we hoped we would see with the Bluetooh dongle "Driver=rtl88x2bu" but for the bluetooth.
Curious though dose'nt the keyboard and mouse have their own usb receiver?
jeremy31 I'm going fishing, see you on the lake. :D

My workplace is a Windows shop. My guess is that they shipped me a dongle that would have worked fine with Windows but not with Linux. A few years back I bought a Plugable USB Bluetooth dongle that worked fine with my Debian laptop. I'll do a little more research to make sure that if I lay out any more money out-of-pocket it will be for a compatible device. In the meantime,a wired USB keyboard and mice is a reasonable workaround.

---

### Post by extraspecialbitter2 on 2021-01-14
Sure enough, after buying a $15 Linux-friendly Plugable USB Bluetooth dongle I was able to see my Bluetooth devices, pair them, and connect. I'm typing this from my Bluetooth keyboard while also using my Bluetooth mouse. I'm going to mark this "resolved".

---

