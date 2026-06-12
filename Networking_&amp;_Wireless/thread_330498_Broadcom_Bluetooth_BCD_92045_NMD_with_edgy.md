---
title: "Broadcom Bluetooth BCD 92045 NMD with edgy"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by omarino on 2007-01-03
Hi,
i have a hp nx7400 with a built in Broadcom Bluetooth device (BCD 92045 NMD). Looks like it is not supported by the default instalation, because the device, which is connected to USB0, does not show in any listing:

[PHP]bp@ubu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
02:06.0 CardBus bridge: Texas Instruments Unknown device 8039
02:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
bp@ubu:~$ 
[/PHP]
[PHP]bp@ubu:~$ lsusb -v

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
bp@ubu:~$ 
[/PHP]


Does any one have any ideas, how to get it running, thanks. 
Omarino

---

### Post by ihristov on 2007-06-04
I have exactly the same problem with an HP dv2000.
I also have a Broadcom BCM 92045 and it does not show up as an USB or PCI device.

Any ideas?

---

### Post by ihristov on 2007-06-04
I found out what is going on.

On my laptop there is a switch that turns off WiFi (for airplanes and such). It turns out it turns off the bluetooth as well.

When the switch is on the Bluetooth adapter shows up as a "Hewlett-Packard" USB device.

```
$ lsusb
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by macubo on 2007-06-04
I'm also experiencing the same problem.
I have an HP nx6125 with bluetooth and fingerprint reader.

lspci doesn't show the device
dmesg neither

hcitool dev doesn't list any bluetooth device.
I have the wireless button up&running (Ndiswrapper over WPA).

Any suggestion??

---

### Post by macubo on 2007-06-04
maybe we could use ndiswrapper with a 64bit driver for bluetooth. You can find the driver here:
[http://egony.newmail.ru/drv_en.htm](http://egony.newmail.ru/drv_en.htm)

Here is the output of dmesg | grep Bluetooth
```
[   90.250218] Bluetooth: Core ver 2.11
[   90.250276] Bluetooth: HCI device and connection manager initialized
[   90.250280] Bluetooth: HCI socket layer initialized
[   90.304397] Bluetooth: L2CAP ver 2.8
[   90.304402] Bluetooth: L2CAP socket layer initialized
[   90.464932] Bluetooth: RFCOMM socket layer initialized
[   90.464946] Bluetooth: RFCOMM TTY layer initialized
[   90.464948] Bluetooth: RFCOMM ver 1.8

```

And this is the output of lsusb
```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

This could also be useful (picked from [http://www.clasohm.com/blog/one-entry?entry_id=14690](http://www.clasohm.com/blog/one-entry?entry_id=14690))
>  nx6125 bluetooth

    Hi,
    I installed my nx6125 with ubuntu 5.10 "Breezy Badger".
    I made wlan work using ndiswrapper but bluetooth is not working at all.
    If wlan0 worked with ndiswrapper, I tried the same with bluetooth.
    I downloaded from hp website bluetooth drivers and after unpacking them, i found btwusb.inf.
    ndiswrapper -i btwusb.inf finished without errors.
    Then, ndiswrapper -l shows btwusb loaded and hardware present.
    After rebooting, i was sure that ndiswrapper loaded my two drivers, but... iwconfig show wlan0 info, hciconfig says "No such device".
    I also tried without ndiswrapper, only using kernel modules, like bcm203x, because after looking inside btwusb.inf I founded Broadcom 2033 and Broadcom 2035 strings, that made me think this could be my hardware.

    Thanks for your info, and I will be waiting your tests results about bluetooth on nx6125

    tango (en|at) lugmen (punto|dot) org (punto|dot) ar
    Mauro - Mendoza
    Argentina

---

### Post by ihristov on 2007-06-04
You have to get the device to show up in lsusb, otherwise it will never work.

When you switch the WiFi switch on, does the LED light up? On mine it lights blue. If it does not maybe it needs some initialization.

What version of Ubuntu are you running? Which kernel?

Also try to power off, turn on the switch and power on with it turned on. Not sure if it would make any difference, but worth the try.

---

### Post by macubo on 2007-06-04
Yes, when i switch the wifi button on, the light does turn on (blue).
The button is a soft button, so to have it switched upon startup i have to leave it on in a previous session (so i do in WinXP).

I'm running Ubuntu Feisty Fawn 64bit and:
```
manuele@manuele-laptop:~$ uname -r
2.6.20-16-generic

```

How did you particularly manage to make the BT device show up in lsusb?

Ps: I sent an email to the main developer of the BlueZ project, hope this helps.
thank you

edit: Tried to reboot with wifi button left on, but lsusb doesn't change..
I also found [this]("http://www.andreas-kleisun.homepage.t-online.de/FC5_on_nx6325.html#mozTocId632834") that could be useful.
I understood that most AMD-based HP laptop use the HP integrated module Bluetooth 2.0, which is powered on by an ACPI call. Infact that link regards HP nx6325, and the vendor:product string is the same of the dv2000. I am certain that this is my device too.

I also noticed that the user linked had to soft-install the bluetooth device in WinXP, thus enabling the device by an ACPI call.
If I well remember last time I used WinXP i turned my BT off via Wireless Assistant.. no way to do it in hardware, as the button is the same.
Now i will try to soft-switch it on by WinXP, and let you know. Let's hope it works

edit again:
IT WORKED. This is my brand new lsusb output:
```
manuele@manuele-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```

How could you retrieve the chipset number? I found that should be this:
Broadcom Corp., USA 	USB Bluetooth module 	BCM 92045 NMD 	2400-2483.5 MHz 	Max 100 mW EIRP

Anyway, to go further on you could have a look [here]("http://lazza.wordpress.com/2007/05/05/bluetooth-con-ubuntu-feisty/"). I'm sorry but it's in italian. Anyway it states to pick the device code from "hcitool dev" and replacing the operative mode in /var/lib/bluetooth/YOUR_CODE_HERE/config to "on". Then restart the bluetooth.

I think i'm gonna try tomorrow. g'night

---

### Post by ihristov on 2007-06-04
> **macubo said:**
> 
I'm running Ubuntu Feisty Fawn 64bit and:
```
manuele@manuele-laptop:~$ uname -r
2.6.20-16-generic

```

...

edit again:
IT WORKED. This is my brand new lsusb output:
```
manuele@manuele-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```



Glad it worked out OK. Mine shows exactly the same hardware ID. 
I too am running the AMD64 version of Feisty with the same kernel.
Mine seems to work fine.
I was trying to use my T-Mobile phone as a GPRS modem by following  [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup) and it works up to the point of establishing the connection to /dev/rfcomm0. I can connect and see and issue AT commands, but have some problem with the dialup script, but the Bluetooth part works fine.


> How could you retrieve the chipset number? I found that should be this:
Broadcom Corp., USA 	USB Bluetooth module 	BCM 92045 NMD 	2400-2483.5 MHz 	Max 100 mW EIRP


Not sure how to figure this out, but as I said the bluetooth seems to work OK on my system. The way I figured this to be BCM 92045 is by opening the cover and looking at the chip. Now this device is seen on the USB bus as a "03f0:171d Hewlett-Packard".

I am under the impression this is actually a version 1.2 device, not version 2.0, since it is listed as obtaining an FCC certification in Dec-05. On the other hand it could be that this is actually the [BCM2045]("http://www.broadcom.com/products/Bluetooth/Bluetooth-RF-Silicon-and-Software-Solutions/BCM2045") and the 9 is just a modification for the WiFi combo and/or the HP rebranding. How old is your laptop?

BTW: I whacked the version of Vista that came with this laptop right after I got it. Can you look at the device properties in Device Manager in your XP?

---

### Post by macubo on 2007-06-05
Mine is a 3Q-2005 laptop, I think, even if I bought it in April 2006.
Later tonight I'm gonna retrieve some infos from XP.

Bluetooth in now working fine indeed, so there is really no need to further tweak the config file.
Anyway I can't see the Bluetooth icon in the tray bar, but just the obex-transfer-server one.

Do you have it in your bar?

---

### Post by ihristov on 2007-06-05
In order to get the Bluetooth icon in the tray bar you need the executable bluetooth-applet. It comes with the package gnome-bluetooth or bluetooth-gnome or bluez-gnome. Can't remember the exact name and the laptop is at home, so can't look it up right now.

Do something like
```
apt-cache search gnome | grep blue
```
to find it

---

### Post by macubo on 2007-06-06
thank you, I think the package is bluez-gnome as I've already installed gnome-bluetooth. But don't really it now, as it's working perfecty right now.

Thank you again, bye

---

### Post by omarino on 2007-06-08
original ? solved:
see [http://ubuntuforums.org/showthread.php?t=464884](http://ubuntuforums.org/showthread.php?t=464884)

---

### Post by macubo on 2007-06-09
thank you.. i checked your post in that discussion. I've seen that you solved your problem as I did for mine. Why don't we encourage a linux version of NP wireless assistant?

---

