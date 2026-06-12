---
title: "Bluetooth device was not installed, right?"
date: 2024-07-13
forum: Networking &amp; Wireless
---

### Post by skj22306 on 2024-07-13
My bluetooth device is not working, JBL speakers (wireless/bluetooth) speakers not being detected.
Going from the /var/log/syslog, does it indicate that the driver for my Broadcom USB wireless device is not running/installed?



Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc
Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc
Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc_xq_453
Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc_xq_453
Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc_xq_512
Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc_xq_512
Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc_xq_552
Jul 12 23:22:38 user-pc bluetoothd[731]: Endpoint unregistered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc_xq_552
Jul 12 23:22:38 user-pc kernel: [ 7290.929265] usb 4-1: USB disconnect, device number 4
Jul 12 23:22:38 user-pc systemd[1005]: Stopped target Bluetooth.
Jul 12 23:22:38 user-pc systemd[1]: Starting Load/Save RF Kill Switch Status...
Jul 12 23:22:38 user-pc systemd[1]: Stopped target Bluetooth Support.
Jul 12 23:22:38 user-pc systemd[1]: Started Load/Save RF Kill Switch Status.
Jul 12 23:22:43 user-pc systemd[1]: systemd-rfkill.service: Deactivated successfully.
Jul 12 23:22:47 user-pc kernel: [ 7299.686064] usb 4-1: new full-speed USB device number 5 using uhci_hcd
Jul 12 23:22:47 user-pc kernel: [ 7299.913169] usb 4-1: New USB device found, idVendor=19ff, idProduct=0239, bcdDevice= 1.12
Jul 12 23:22:47 user-pc kernel: [ 7299.913182] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 12 23:22:47 user-pc kernel: [ 7299.913187] usb 4-1: Product: BCM20702A0
Jul 12 23:22:47 user-pc kernel: [ 7299.913190] usb 4-1: Manufacturer: Broadcom Corp
Jul 12 23:22:47 user-pc kernel: [ 7299.913194] usb 4-1: SerialNumber: [obfs]
Jul 12 23:22:47 user-pc mtp-probe: checking bus 4, device 5: "/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1"
Jul 12 23:22:47 user-pc systemd[1005]: Reached target Bluetooth.
Jul 12 23:22:47 user-pc mtp-probe: bus: 4, device: 5 was not an MTP device
Jul 12 23:22:47 user-pc systemd[1]: Starting Load/Save RF Kill Switch Status...
Jul 12 23:22:47 user-pc mtp-probe: checking bus 4, device 5: "/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1"
Jul 12 23:22:47 user-pc mtp-probe: bus: 4, device: 5 was not an MTP device
Jul 12 23:22:47 user-pc kernel: [ 7300.042195] Bluetooth: hci0: BCM: chip id 73
Jul 12 23:22:47 user-pc kernel: [ 7300.044896] Bluetooth: hci0: BCM: features 0x07
Jul 12 23:22:47 user-pc systemd[1]: Reached target Bluetooth Support.
Jul 12 23:22:47 user-pc systemd[1]: Started Load/Save RF Kill Switch Status.
Jul 12 23:22:47 user-pc kernel: [ 7300.077192] Bluetooth: hci0: BCM20702B
Jul 12 23:22:47 user-pc kernel: [ 7300.077202] Bluetooth: hci0: BCM20702B0 (002.001.014) build 0000
Jul 12 23:22:47 user-pc kernel: [ 7300.079248] Bluetooth: hci0: BCM: firmware Patch file not found, tried:
Jul 12 23:22:47 user-pc kernel: [ 7300.079254] Bluetooth: hci0: BCM: 'brcm/BCM20702B0-19ff-0239.hcd'
Jul 12 23:22:47 user-pc kernel: [ 7300.079256] Bluetooth: hci0: BCM: 'brcm/BCM-19ff-0239.hcd'
Jul 12 23:22:48 user-pc kernel: [ 7300.183411] Bluetooth: MGMT ver 1.22
Jul 12 23:22:48 user-pc pulseaudio[1044]: Could not find org.bluez.BatteryProviderManager1.RegisterBatteryProvider(), is bluetoothd started with experimental features enabled (-E flag)?
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc_xq_453
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc_xq_453
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc_xq_512
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc_xq_512
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSink/sbc_xq_552
Jul 12 23:22:48 user-pc bluetoothd[731]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSource/sbc_xq_552
Jul 12 23:22:52 user-pc systemd[1]: systemd-rfkill.service: Deactivated successfully.

---

