---
title: "Thinkpad 11e Yoga Gen6 (Educat) Bluetooth not working (maybe not related to a flavor)"
date: 2021-04-06
forum: Networking &amp; Wireless
---

### Post by mrdasa on 2021-04-06
I've installed Kubuntu 20.04.02 with the lates updates until 6.4.2021. The Thinkpad uses an Intel wlan/bluetooth AC-9260 HW. Rev.29. The WLAN is working fine, but the bt adapter can not be turned on. I tested a lot of Kernels from 4.18 to 5.11.x without success. I installed Windows in parallel, just to be sure that the BT adapter is working, and i can confirm that its working fine on Windows. When i try to enable it manually by thinkpad_acpi bluetooth_enable it will not turn it on (echo 1 | sudo tee bluetooth_enable). rfkill unblock bluetooth can unlock everything except tpacpi_bluetooth_sw HARD. Its not possible to unlock it even if i disable "fast boot on shutdown" in the windows system. There is also no physical HW button to enable BT or something like that. The WLAN-Adapter is working just fine and i also tested every available intel firmware one by one up to version 46. I really need bluetooth as soon as possible otherwise i will be forced to stay on windows what i really do not want.

Here are some outputs:

```
lshw:
          *-network
                description: Wireless interface
                product: Wireless-AC 9260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 29
                serial: 8c:55:4a:80:3d:ab
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-48-generic firmware=46.6bf1df06.0 9260-th-b0-jf-b0- ip=192.168.1.34 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:19 memory:f1100000-f1103fff
        *-pci:2


daniel@kub64-20-04-11e:~$ rfkill unblock bluetooth
daniel@kub64-20-04-11e:~$ rfkill
ID TYPE      DEVICE                   SOFT      HARD
 0 bluetooth tpacpi_bluetooth_sw entsperrt blockiert
 1 wlan      phy0                entsperrt entsperrt
 2 bluetooth hci0                entsperrt entsperrt

[bluetooth]# list
Controller 8C:55:4A:80:3D:AF kub64-20-04-11e [default]

[bluetooth]# power on
Failed to set power on: org.bluez.Error.Blocked


[bluetooth]# show
Controller 8C:55:4A:80:3D:AF (public)
        Name: kub64-20-04-11e
        Alias: kub64-20-04-11e
        Class: 0x00000000
        Powered: no
        Discoverable: yes
        DiscoverableTimeout: 0x00000000
        Pairable: yes
        UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
        UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
        UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
        UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
        UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
        UUID: Headset AG                (00001112-0000-1000-8000-00805f9b34fb)
        UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
        UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
        UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
        UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
        UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
        UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
        Modalias: usb:v1D6Bp0246d0535
        Discovering: no
Advertising Features:
        ActiveInstances: 0x00
        SupportedInstances: 0x05
        SupportedIncludes: tx-power
        SupportedIncludes: appearance
        SupportedIncludes: local-name
        SupportedSecondaryChannels: 1M
        SupportedSecondaryChannels: 2M
        SupportedSecondaryChannels: Coded
```

Thanks!

---

### Post by mIk3_08 on 2021-04-06
try this command in terminal and paste the result here in thread wrap with code.
```
dmesg | grep -i 'bluetooth'
```

---

### Post by mrdasa on 2021-04-06
Here is the output:
 
```
daniel@kub64-20-04-11e:~$ dmesg | grep -i 'bluetooth'
[    4.332405] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[    5.761537] Bluetooth: Core ver 2.22
[    5.761579] Bluetooth: HCI device and connection manager initialized
[    5.761584] Bluetooth: HCI socket layer initialized
[    5.761586] Bluetooth: L2CAP socket layer initialized
[    5.761589] Bluetooth: SCO socket layer initialized
[    5.895632] Bluetooth: hci0: Bootloader revision 0.1 build 42 week 52 2015
[    5.897277] Bluetooth: hci0: Device revision is 2
[    5.897280] Bluetooth: hci0: Secure boot is enabled
[    5.897282] Bluetooth: hci0: OTP lock is enabled
[    5.897285] Bluetooth: hci0: API lock is enabled
[    5.897286] Bluetooth: hci0: Debug lock is disabled
[    5.897290] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    5.899893] Bluetooth: hci0: Found device firmware: intel/ibt-18-16-1.sfi
[    5.966248] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.966250] Bluetooth: BNEP filters: protocol multicast
[    5.966257] Bluetooth: BNEP socket layer initialized
[    7.339246] Bluetooth: hci0: Waiting for firmware download to complete
[    7.340257] Bluetooth: hci0: Firmware loaded in 1415319 usecs
[    7.340293] Bluetooth: hci0: Waiting for device to boot
[    7.353223] Bluetooth: hci0: Device booted in 12640 usecs
[    7.353477] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-18-16-1.ddc
[    7.356255] Bluetooth: hci0: Applying Intel DDC parameters completed
[    7.357247] Bluetooth: hci0: Firmware revision 0.1 build 26 week 11 2020
[    7.459137] Bluetooth: RFCOMM TTY layer initialized
[    7.459144] Bluetooth: RFCOMM socket layer initialized
[    7.459148] Bluetooth: RFCOMM ver 1.11
```

I tried more than once to reset to BIOS defaults or disabled and re-enabled the BT in the EFI Bios. And when i dual boot into Windows BT is fine - when into Kubuntu BT is hard blocked.

Thanx for helping!

---

### Post by mIk3_08 on 2021-04-06
Just wait for some firmware updates to complete. I think.

---

### Post by mrdasa on 2021-04-07
Ok, thanx for the hint! Do you know maybe if intel is working on this new firmwre already? Or does this standard wireless card differ from other AC9260 versions? Why i am asking - is it Lenovo or Intel that needs to provide something to get the BT to work? Any suggestions?

Thanx!

---

### Post by mIk3_08 on 2021-04-08
[Click Here]("https://linux-hardware.org/") this will collect your hardware details and help you debug your hardware related issues.

---

### Post by chili555 on 2021-04-08
Please show us the result of:

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi bt_coex_active=Y
sudo rfkill unblock all
rfkill list all
```

---

