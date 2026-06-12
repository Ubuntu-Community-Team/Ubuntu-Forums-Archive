---
title: "Installing USB Sound Drivers"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-04-19
I have a PD 552 USB Sound device. There are available drivers for it on the web and perhaps there is a way to recognize it using Ubuntu tools. I just have no idea of how to go about installing it. 

Any help/suggestions would be welcome

---

### Post by cariboo on 2009-04-19
If you are using Intrepid or newer go to System-->Preferences-->Sound, and make sure your device shows up in the list.

I have a usb headset, that I need in Windows for skype, as Windows doesn't detect the internal microphone on my Logitech webcam, it shows up in the sound utility by its usb device number. To find the device number for your device, open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

the result should look something like this:

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 045e:074f Microsoft Corp. 
Bus 002 Device 004: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 003: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 002: ID 0665:5161  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Jim

---

### Post by Rog3236 on 2009-04-19
This is what I receive from the command. It shows up as device 7 but I still don't receive any sound from the headset.

roger@rog3236-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1130:f211 Tenx Technology, Inc. USB audio headset
Bus 001 Device 003: ID 0930:653e Toshiba Corp. USB Flash Memory
Bus 001 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
roger@rog3236-desktop:~$ 
roger@rog3236-desktop:~$

---

