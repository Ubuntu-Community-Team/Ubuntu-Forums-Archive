---
title: "Ralink RT2870 driver simply refuses to load on boot"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Garlicko on 2008-07-17
Hello everyone,

I'm running Hardy and using the latest RT2870 driver from Ralink, [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Have made the necessary changes to config.mk and driver has been successfully installed using the following commands, 

```

sudo make 
sudo make install

```

However, the driver refuses to load on boot. I have to manually disable/enable it from System->Administration->Hardware Driver before it can work.

Is it possible to have the driver load automatically upon start-up? Attached is a screen-shot of the issue.

Thank you very much, help is much appreciated. 


[img]http://img45.imageshack.us/img45/4008/screenshothardwaredriveqf4.png[/img]

---

### Post by lswb on 2008-07-17
Hardy ships by default with the newer rt2x00 drivers for ralink cards. You may need to blacklist rt2x00 for the rt2870 driver to load. 

Are you abe to modprobe the driver once the system is running, or does modprobe rt2870 generate errors? 

By the way, the legacy (older drivers) do not work with Network Manager.

---

### Post by Garlicko on 2008-07-17
Managed to get it working.

Forgot to edit /etc/modules

---

### Post by linux4909 on 2008-10-22
hey, can you post the edit you made in your modules? 
i have this device by hawking that uses that driver. in fact is used the RT2870sta. was wondering if they are the same. 

#modprobe rt2870sta loads the driver for me. 

#modinfo rt2870sta 
is what i use to verify that it's installed on the system. and it is.

---

