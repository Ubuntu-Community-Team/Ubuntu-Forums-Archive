---
title: "ueagle problem after kernel upgrade (sagem 800)"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by Milan SPK on 2007-04-27
can anyone help? i lost my net connection, and i am not really skilled in linux...
i upgraded to the latest kernel in edgy, and then i did everything as mentioned here: [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm?highlight=%28ueagle%29](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm?highlight=%28ueagle%29)
> $ sudo rmmod eagle-usb 
$ sudo rm /lib/modules/`uname -r`/kernel/drivers/usb/net/eagle/eagle-usb.ko

Note: Each time you update your kernel you have to do only the above step.

then i unplugged the modem, plugged it back in, and since then the two lights are on all the time. they didn't first flash for a wile and then stay on, but were on from the moment i plugged it back in. also when i boot ubuntu, the lights behave the same way.

thanks in advance!

---

### Post by Milan SPK on 2007-04-28
anyone? i tried searching the forums, but couldn't find the solution...

---

### Post by Milan SPK on 2007-04-30
ok, so i upgraded to feisty and the problem was gone. thanks anyway.

---

