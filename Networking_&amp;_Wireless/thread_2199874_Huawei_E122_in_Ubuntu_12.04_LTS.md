---
title: "Huawei E122 in Ubuntu 12.04 LTS"
date: 2014-01-16
forum: Networking &amp; Wireless
---

### Post by Jeyaprakash on 2014-01-16
I am using Ubuntu 12.04 and got a new modem (Huawei E122). I am having problem getting it work smoothly. It connected a few times both with wvdial and network manager. Then, it automatically disconnected in a few minutes and refuses to connect again. I have usb-modeswitch 1.2.3+repack0-1ubuntu2 installed. 

This is what I get with lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem

If I give the command, usb_modeswitch -v 0x12d1 -p 0x1003 -H, the output is, 

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 003 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: HUA WEI
     Product: Huawei Mobile
  Serial No.: not provided
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent
-> Run lsusb to note any changes. Bye.

In the network-manager, even after checking Enable Mobile Broadband, it is not registering on the network. It just shows Mobile Broadband 'not-enabled'. Sometimes, it gets registered and would never connect.

I tried to disable network-manager and connect using wvdial. If I disable network-manager, the modem does not display blue light at all. In the network-manager, after enabling mobile broadband, blue light comes. But, below the connection name, instead of showing the operator name, it just shows 'not enabled'. 

Any help would be greatly appreciated. I am not an expert.. just a learner in Ubuntu. For the past two days, I have been breaking my head... but nothing works. I did important security updates to see if something would work.. but, of no use. Help me get it working!

---

### Post by praseodym on 2014-01-16
Have a look here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by Jeyaprakash on 2014-01-16
Thank you very much for the link. I saw your reply in just 10 minutes, after you posted. From that time on, I have been trying something or the other to get it working. Finally... It is working! Hurray!!! I right clicked and modem storage and 'safe removed'. And then, the signal came up. Also, I was meddling something with the 'confirm sim service action'. I kept it to 'no'. But then, finally kept it to 'yes' on mobile, before taking out the sim as the earlier setting was not helping. PIN request was already set to 'off'. I am very happy!! Thank You!!!

---

### Post by praseodym on 2014-01-16
Glad it worked. For this device storage and modem IDs with "lsusb" are the same!

---

### Post by Jeyaprakash on 2014-01-16
I made the comment that it worked and before I marked the thread as solved, it got disconnected and refuses to connect again.. I tried a different SIM card also. The problem seems to be the same - 'Getting signal and registering'. I hope, it has got something to do with the network manager. When I use a cdma modem, I mostly connect using wvdial. That modem will not connect in wvdial if network manager is active. So, I used to stop network manager. With this GSM modem, I am not able to get the modem receive 3G signal without the network-manager (i.e the blue light). I was keeping umtsmon open to see the signal. It shows signal but not showing the provider and the mode (UMTS), even after the blue light comes. But, I have seen those things earlier, a few days back. After it connected for a few times, this problem started.  Also, in windows, the signal strength is very strong and in ubuntu, when it showed signal, it was very weak. I am still trying to figure it out. Any guidance would be greatly welcome!

---

### Post by Jeyaprakash on 2014-01-17
I thought, I should mention this also: If I stop the network-manager, remove it from the start up list, after logging in, if I start network-manager in terminal, it says that it is already running, but does not show up. I removed the network-manager using package manager to see if it would help. But, my modem does not even show up the blue light in that case. If I could get the blue light without network manager, I hope to establish a successful connecting using wvdial. When my CDMA modem was having problem with network manager earlier (now with the newer version, it connects fine), I was using wvdial only. I am still experimenting, hoping to fix it! :)

---

### Post by Jeyaprakash on 2014-01-17
Now, I am trying sakis3g. For sakis3g to recognize modem, I have to 'enable mobile broadband' in network manager (network manager does not show signal). When I tried to connect, it said 'Device did not report GSM capabilities. You can skip this by adding --noprobe command line switch' When I did that, I get another error message now, which says 'Port /dev/ttyUSB0 is currently occupied by 3059 modem-manager'. I tried removing the modem-manager pacakage. But, the network manager does not recognize the modem :D. So, I have installed again modem-manager. Trying again...

---

### Post by Jeyaprakash on 2014-01-17
The problem seems to be with the SIM. A different SIM from the same service provider connects without any problem!

Update: It seems to work only with the 'Connect automatically' checked on. When it searches for the first time, there may not be any signal. When it keeps on searching, it gets the signal and manages to connect!

---

