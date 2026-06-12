---
title: "Assistance required with a wireless networking issue."
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by Neon_Knight on 2007-10-05
Okay, I've got a computer with Ubuntu 7.04 installed onto it.  I'm trying to get my wireless to work, the problem is, I've followed a tutorial to install the Serialmonkey driver for it, and it hasn't worked. The lights flash on it when it turns on, however still there is no luck trying to connect.  It can see the wireless networks.

The output of the lsusb command gives me the following ID:
```

ID 07d1:3c03 D-Link System

```

I followed [this]("http://www.linuxquestions.org/questions/ubuntu-63/how-to-install-rt73-driver-for-dwl-g122-rev.-c1-in-ubuntu-578894/") tutorial to get it to work, however when I attempted the 
```

sudo rmmod rt73usb
sudo rmmod rt2570

```
commands, they failed to work.
```

module rt73usb does not exist in /proc/modules

```

I can get it to see the wireless router with the 
```

iwlist scan

```
command.



It is a D-link G122 rev C. 


I'm not sure quite what I'm doing wrong here...


Any help would be greatly appreciated on this matter.    

Does ndiswrapper support this dongle?

Thanks.

---

