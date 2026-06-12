---
title: "bluetooth problem"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-06-02
my Microsoft Corp. Wireless Transceiver for Bluetooth 2.0 is not recognize by the bluetooth applet in ubuntu , is there any way to get it working i ran "lsusb" and the output was:
```

Bus 001 Device 005: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 004: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 045e:00be Microsoft Corp. 
Bus 004 Device 004: ID 045e:00bf Microsoft Corp. 
Bus 004 Device 003: ID 045e:009c Microsoft Corp. Wireless Transceiver for Bluetooth 2.0
Bus 004 Device 002: ID 045e:3500 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0724 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

i also ran "hcitool dev" but i got no output , could someone please help me.

---

### Post by pspsampsp on 2009-06-04
Bumpty bump bump bump...

---

### Post by pspsampsp on 2009-06-04
bump. really want to solve this.

---

### Post by dBuster on 2009-06-04
have you gone through and made sure you had the latest blues utils?

Have you gone through the wiki:

[https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters]("https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters")

---

### Post by Boondoklife on 2009-06-04
This may seem like a dumb question but this is not the one that comes with the bluetooth keyboard and mouse is it? If so then I dont think it functions as a full bluetooth device as I could not get it to do so even in windows.

If not then ignore the message =).

---

### Post by pspsampsp on 2009-06-06
i dont think it is because i was using it to transfer files from my mates phone on my windows pc.

---

### Post by iceaway on 2009-06-10
I'm having the exact same problem. I have a 'Microsoft Wireless Laser Desktop 8000' and lsusb gives me the same output as you, except it doesn't say 'bluetooth' anywhere. I don't get the bluetooth applet icon, so I'm guessing ubuntu doesn't recognize the bluetooth dongle. The strange thing is that the wireless mouse works right away, while the keyboard does not. 
hcitool scan says something like 'No device' (I'm not at home, don't remember the exact message) and hcitool dev comes up blank.

Any ideas?

---

### Post by Boondoklife on 2009-06-10
> **iceaway said:**
> I'm having the exact same problem. I have a 'Microsoft Wireless Laser Desktop 8000' and lsusb gives me the same output as you, except it doesn't say 'bluetooth' anywhere. I don't get the bluetooth applet icon, so I'm guessing ubuntu doesn't recognize the bluetooth dongle. The strange thing is that the wireless mouse works right away, while the keyboard does not. 
hcitool scan says something like 'No device' (I'm not at home, don't remember the exact message) and hcitool dev comes up blank.

Any ideas?

If you have the Microsoft version that came with the keybozrd and mouse then simply pair them by pressing the button on the dongle and then the ones on the mouse and keyboard. From then on the pairs will read on their own and it will just be another usb mouse and keyboard setup.

Works that way for me on 9.04 but tried on 8.04 and up and it works there too.

---

