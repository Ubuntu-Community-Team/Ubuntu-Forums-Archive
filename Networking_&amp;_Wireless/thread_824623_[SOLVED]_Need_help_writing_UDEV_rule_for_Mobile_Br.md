---
title: "[SOLVED] Need help writing UDEV rule for Mobile Broadband Device"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by theinnercityhippy on 2008-06-10
Hiya,

I'm trying to write a rule for UDEV that will automatically connect to the internet using wvdial whenever I plug in my Sierra Wireless modem (running on the O2 network.

I have set up wvdialconf correctly and can connect manually (hence how I'm connected now), but wanted to go a stage further and so do it automatically whenever it's plugged in.

I've edited /etc/udev/rules.d/80-programs.rules and added the following based on the output from udevinfo (which I've also included at the bottom) but so far no joy. 

#attempt to get sierra card to autoconnect

KERNEL=="ttyUSB0", SUBSYSTEM=="usb-serial", DRIVER=="sierra3", ATTR{port_number}=="0", ACTION="add", RUN+="/usr/bin/wvdial"


Has anyone done something similar and got it work as I'm afraid I'm at the limit of my knowledge of such things.

Thanks loads in advance

Jimdog


jimdog@jimdogsbrain:/etc/udev/rules.d$ udevinfo -a -p /sys/devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/ttyUSB0


 looking at device '/devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="usb-serial"
    DRIVER=="sierra3"
    ATTR{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="sierra"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="07"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{modalias}=="usb:v1199p6812d0001dc00dsc00dp00icFFiscFFipFF"
    ATTRS{interface}=="Data Interface"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:2"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="11"
    ATTRS{idVendor}=="1199"
    ATTRS{idProduct}=="6812"
    ATTRS{bcdDevice}=="0001"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="3"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sierra Wireless, Incorporated"
    ATTRS{product}=="Mini Card"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:0"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="70"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="7"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-17-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:02.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.0':
    KERNELS=="0000:00:02.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x055e"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30cf"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="03"
    ATTRS{modalias}=="pci:v000010DEd0000055Esv0000103Csd000030CFbc0Csc03i10"
    ATTRS{numa_node}=="-1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by joe.six.pack on 2008-11-24
your udev rule is wrong.

```

KERNEL=="ttyUSB0", SUBSYSTEM=="usb-serial", DRIVER=="sierra3", ATTR{port_number}=="0", ACTION="add", RUN+="/usr/bin/wvdial"

```

> 
>>>  ACTION="add",  <<<


you should also use a wildcard in the USB device name and remove the port number.

either of the following rules should work.

```

KERNEL=="ttyUSB?", SUBSYSTEM=="usb-serial", DRIVER=="sierra3", ACTION=="add", RUN+="/usr/bin/wvdial"

```

or

```

SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}=="1199", ATTRS{idProduct}=="6812", ATTRS{manufacturer}=="Sierra Wireless, Incorporated", ATTRS{product}=="Mini Card", ACTION=="add", RUN+="/usr/bin/wvdial"

```

---

### Post by theinnercityhippy on 2008-12-01
Thankyou Joe, all down to a good old typo in the first instance. I'll give this a go once i get wvdial or something similar ported to ARMEL to use on my Nokia N800 as I'm having a lot of fun with network manager 0.7 at the moment for using multiple profiles.

---

