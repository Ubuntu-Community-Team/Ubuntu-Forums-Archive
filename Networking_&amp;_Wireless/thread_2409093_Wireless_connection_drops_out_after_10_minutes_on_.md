---
title: "Wireless connection drops out after 10 minutes on surface pro 3"
date: 2018-12-27
forum: Networking &amp; Wireless
---

### Post by AndEilert on 2018-12-27
Hello guys!

I recently installed ubuntu 18.04 on my surface pro 3, unfortunately my Wi-Fi connection randomly drops out after 10 minutes and refuses to connect without a reboot. I tried removing network-manager and installed wicd instead, unfortunately the problem persists. Both the network manager and the wicd applications freeze and "stop responding" when my connection drops. 

Any ideas?

Thank you very much! :)

Best regards
AndEilert

---

### Post by praseodym on 2018-12-28
Please run the wireless script from the sticky thread and show the outputs

---

### Post by AndEilert on 2019-01-02
Here is the result of running the script:
[http://paste.ubuntu.com/p/5FyRbvmnpP/](http://paste.ubuntu.com/p/5FyRbvmnpP/)

The script was run after the wireless had dropped out, and the computer is tethered to my phone to have an internet connection.

Here is also the script run on wireless:
[http://paste.ubuntu.com/p/KdXgQ2NBG8/](http://paste.ubuntu.com/p/KdXgQ2NBG8/)

Thank you :)

---

### Post by praseodym on 2019-01-02
Lets try
```

sudo iwconfig wlp1s0 power off
```

---

### Post by AndEilert on 2019-01-04
Could be a coincidence but seemingly that did the trick! Ill post an update in a couple of hours to see if there is any more problems.

Thank you very much my friend! :)

---

### Post by AndEilert on 2019-01-04
Unfortunately I spoke too soon. After about one hour, the wifi once again disconnected and it could no longer find any networks.
I tried running the previous command after the wireless dropped and the following came back after running it three times:

"
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlp1s0 ; Connection timed out.

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlp1s0 ; Operation not permitted.

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlp1s0 ; No such device.

"

---

### Post by SWayneMartin on 2019-06-15
Posting this for people who may find this useful. I found that the trick is that you must execute that _iwconfig_ command must be run while the wireless driver is still up. I suspect that once the interface powers down, it is no longer possible to change it.

Essentially what this command does is tell the system not to turn off the wifi NIC to save power. It seems Ubuntu drivers have some issues with powering down devices and not being able to power them up again. This might need a specific driver.

TL;DR
run the _iwconfig_ command above shortly after starting up the device. That will keep it from powering down to save power.

---

