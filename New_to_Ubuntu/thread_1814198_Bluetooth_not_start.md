---
title: "Bluetooth not start"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Vege 4wd on 2011-07-29
Hi I have searched the threads, still I am unable to work out why I get an error saying:
"failed to set the bluetooth power. The error reported is: Connection timed out" every time I insert the bluetooth dongle.:confused:

I have tried it both with the stock bluetooth manager and also with blueman.

Does anyone no a work around.  I am running lucid. 

Thanks again.

---

### Post by westie457 on 2011-07-29
> **Vege 4wd said:**
> Hi I have searched the threads, still I am unable to work out why I get an error saying:
"failed to set the bluetooth power. The error reported is: Connection timed out" every time I insert the bluetooth dongle.:confused:

I have tried it both with the stock bluetooth manager and also with blueman.

Does anyone no a work around.  I am running lucid. 

Thanks again.

In a terminal run ```
lsusb
``` without the dongle 
Then again with the dongle plugged in. 

Post the output of both please

---

### Post by Vege 4wd on 2011-07-29
thanks Westie
Without dongle:
```
us 005 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:3271 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:4712 Hewlett-Packard 
Bus 001 Device 003: ID 5986:0200 Acer, Inc OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
With dongle:
```
Bus 005 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:3271 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:4712 Hewlett-Packard 
Bus 001 Device 003: ID 5986:0200 Acer, Inc OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by westie457 on 2011-07-29
That is a start. The thing is being detected. Googling the ID number 0a12:0001 brought up lots of info. This was the first in the list. [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Hope this helps.

---

### Post by Vege 4wd on 2011-07-29
Thanks I am working on it now.

---

### Post by westie457 on 2011-07-29
> **Vege 4wd said:**
> Thanks I am working on it now.

Just a thought. Is there another bluetooth device in range for it to connect to. EG a mobile phone with bluetooth turned on.

---

### Post by Vege 4wd on 2011-07-29
Yes, a phone. I can see the pc on phone but can't connect. Now I seem to be getting an error that says adapter not ready.
Btw: I can easily pair the phone with other devices.

---

### Post by Vege 4wd on 2011-07-29
I am finding the gui for bluettoth applett very laggy and it won't save changes to setting.
ie. keeps going back to hidden and will not stay visiable.

---

### Post by westie457 on 2011-07-29
> **Vege 4wd said:**
> I am finding the gui for bluettoth applett very laggy and it won't save changes to setting.
ie. keeps going back to hidden and will not stay visiable.

Unfortunately I cannot help anymore as my box does not have bluetooth built-in or a dongle for testing purposes. Don't panic though as these forums are 24/7 and someone will see this. Might be a while though.

---

### Post by Vege 4wd on 2011-07-29
Thanks very much for the link. I have already been able to transfer files.

Still a little unstable though!

---

