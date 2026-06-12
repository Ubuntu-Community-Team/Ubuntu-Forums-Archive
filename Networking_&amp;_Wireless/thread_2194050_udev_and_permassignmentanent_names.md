---
title: "udev and permassignmentanent names"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by teo.wolf on 2013-12-16
Hello everybody, 
I have a little problem and need some help to solve it. Any suggestion will be greatly appreciated. :)


I am using kubuntu 13.10
I am working with a couple of modems which are connected to the computer through a USB/UART cable.


I am trying to assing permanent names to these modems. Everytime that I connect I would like to obtain them something like /dev/Modem1, /dev/Modem2.


I have read that this is possible changing some rules in /etc/udev/rules.d/, but unfortunately from udev I cannot get a different ATTRS{serial} for every modem so I cannot distinguish one modem from another. 


The only thing that I was able to do is assign a permanent name to the usb-port, but this does not solve the problem.


I tried the commands

```
$ udev -a -p /class/tty/ttyUSB0
$ udev -a -p /class/tty/ttyUSB1
$ lsusb

```

Here I attached the results.


MODEM1:

```

$ udev -a -p /class/tty/ttyUSB0
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.


  looking at device '/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/ttyUSB1/tty/ttyUSB1':
    KERNEL=="ttyUSB1"
    SUBSYSTEM=="tty"
    DRIVER==""


  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/ttyUSB1':
    KERNELS=="ttyUSB1"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="ftdi_sio"
    ATTRS{port_number}=="0"
    ATTRS{latency_timer}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0':
    KERNELS=="6-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ftdi_sio"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{interface}=="USB <-> Serial"


  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb6/6-1':
    KERNELS=="6-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="1"
    ATTRS{idVendor}=="0403"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{busnum}=="6"
    ATTRS{devnum}=="17"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="90mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="0400"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="12"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="FTDI"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="6001"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="USB <-> Serial"


  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb6':
    KERNELS=="usb6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="6"
    ATTRS{devnum}=="1"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="2"
    ATTRS{bcdDevice}=="0311"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="0000:00:1d.1"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="309"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Linux 3.11.0-13-generic uhci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0001"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="UHCI Host Controller"


  looking at parent device '/devices/pci0000:00/0000:00:1d.1':
    KERNELS=="0000:00:1d.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{irq}=="19"
    ATTRS{subsystem_vendor}=="0x1025"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0300"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{device}=="0x2831"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0-1"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x0136"
    ATTRS{numa_node}=="-1"
    ATTRS{d3cold_allowed}=="0"


  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```






MODEM2:
```

$ udev -a -p /class/tty/ttyUSB1
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.


  looking at device '/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""


  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="ftdi_sio"
    ATTRS{port_number}=="0"
    ATTRS{latency_timer}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0':
    KERNELS=="5-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ftdi_sio"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{interface}=="USB <-> Serial"


  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb5/5-1':
    KERNELS=="5-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="1"
    ATTRS{idVendor}=="0403"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{busnum}=="5"
    ATTRS{devnum}=="12"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="90mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="0400"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="12"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="FTDI"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="6001"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="USB <-> Serial"


  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb5':
    KERNELS=="usb5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="5"
    ATTRS{devnum}=="1"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="2"
    ATTRS{bcdDevice}=="0311"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="233"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Linux 3.11.0-13-generic uhci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0001"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="UHCI Host Controller"


  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{irq}=="23"
    ATTRS{subsystem_vendor}=="0x1025"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0300"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{device}=="0x2830"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0-1"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x0136"
    ATTRS{numa_node}=="-1"
    ATTRS{d3cold_allowed}=="0"


  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```


```

$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


Any ideas on how to do it?

---

### Post by teo.wolf on 2013-12-16
Sorry I messed the title. It should be something like "udev and permanent names assignment"

---

### Post by teo.wolf on 2013-12-16
Sorry I messed with the name. It should be "udev and permanent names assignment"

---

