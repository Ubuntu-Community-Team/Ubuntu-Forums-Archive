---
title: "Problem with my bluetooth when i installed ubuntu hardy 8.04"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by zoubaier on 2008-05-05
hi everyone , i was using my bluetooth without any problem with ubuntu 7.10.
But when i installed ubuntu hardy 8.04 i have really serious problem , i can send easily files to my phone , but when i try to open and see what my phone contain and add files to it ,, i receive a message telling me that i can't .
I need it cause my phone contain a memory card so i can't send big files directly .
i tried everything , and i m surprised cause it works perfectly in ubuntu 7.10.
Sorry for my English. 
Thank You for helping me.

---

### Post by zoubaier on 2008-05-05
Please help me !!!!

---

### Post by BigBob on 2008-05-05
Hi,

Have a look in "/var/log/daemon.log" to see if you can find the problem ...

A++

---

### Post by zoubaier on 2008-05-05
> **BigBob said:**
> Hi,

**Have a look in "/var/log/daemon.log" to see if you can find the problem ...**

A++

thank you ,, i tried again and this is what i find in the log file .
> 
May  5 23:30:06 zoubaier NetworkManager: <debug> [1210023006.486885] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial'). 
May  5 23:30:06 zoubaier NetworkManager: <debug> [1210023006.628945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
May  5 23:30:06 zoubaier hcid[5711]: HCI dev 0 registered
May  5 23:30:06 zoubaier NetworkManager: <debug> [1210023006.653932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_bluetooth_hci_0'). 
May  5 23:30:06 zoubaier hcid[5711]: HCI dev 0 up
May  5 23:30:06 zoubaier hcid[5711]: Device hci0 has been added
May  5 23:30:06 zoubaier hcid[5711]: Starting security manager 0
May  5 23:30:06 zoubaier hcid[5711]: Device hci0 has been activated
May  5 23:30:07 zoubaier NetworkManager: <debug> [1210023007.082789] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if2'). 
May  5 23:30:07 zoubaier NetworkManager: <debug> [1210023007.120617] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if1'). 
May  5 23:30:15 zoubaier NetworkManager: <debug> [1210023015.827865] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_eed4f68df'). 
May  5 23:30:19 zoubaier hcid[5711]: pin_code_request (sba=00:10:60:A2:BC:38, dba=00:0E:ED:4F:68:DF)
May  5 23:30:23 zoubaier hcid[5711]: link_key_notify (sba=00:10:60:A2:BC:38, dba=00:0E:ED:4F:68:DF)


u want a screenshot of the error?? but it's in frensh .

---

### Post by zoubaier on 2008-05-06
this is a screeshot of my problem.

---

