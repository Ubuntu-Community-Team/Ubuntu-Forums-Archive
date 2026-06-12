---
title: "Bluetooth DUN"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Casey Timm on 2008-02-12
Ok I am trying to set up a bluetooth DUN connection to my Cingular Moto K1. When I do a hcitool cc mac_address it connects then drops the connection. I am using Gusty and have tried with all bluetooth packages installed, and with only the reccomanded ones. Here is my syslog 
```
Feb 12 13:30:15 casey-laptop -- MARK --
Feb 12 13:33:30 casey-laptop hcid[6571]: HCI dev 0 down
Feb 12 13:33:30 casey-laptop hcid[6571]: Stopping security manager 0
Feb 12 13:33:30 casey-laptop hcid[6571]: Device hci0 has been disabled
Feb 12 13:33:30 casey-laptop hcid[6571]: HCI dev 0 up
Feb 12 13:33:30 casey-laptop hcid[6571]: Device hci0 has been added
Feb 12 13:33:30 casey-laptop hcid[6571]: Starting security manager 0
Feb 12 13:33:30 casey-laptop hcid[6571]: Device hci0 has been activated
Feb 12 13:35:11 casey-laptop NetworkManager: <debug> [1202841311.968639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Feb 12 13:35:15 casey-laptop NetworkManager: <debug> [1202841315.849756] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Feb 12 13:50:15 casey-laptop -- MARK --
Feb 12 13:51:26 casey-laptop NetworkManager: <debug> [1202842286.974769] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Feb 12 13:51:30 casey-laptop NetworkManager: <debug> [1202842290.926859] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if0_bluetooth_hci_bluetooth_hci'). 

```

I have also tried with my pda and recived the same results. Oh btw i am using a kensington micro bluetooth adaptor.

---

### Post by bastineman on 2008-02-16
I am having similar issues with a Dell D830 and my Verizon XV6800 on Gutsy after installing all packages. I am able to successfully connect with BT DUN in XPP. I am able to detect the XV6800 in the gnome bluetooth manager and it seems to connect momentarily - via hcitool cc as well. It doesn't seem to be able to detect any services - like a com port as a modem - on the phone (BT DUN cab for WinMob6 installed).

I also get the "Couldn't display "obex://[aa:bb:cc:dd:ee:ff]". Check if the service is available." error out of BTManager applet.

So basically this a bump for Casey's post and affirmation that someone else is having similar troubles...

Suggestions anyone?

B

---

