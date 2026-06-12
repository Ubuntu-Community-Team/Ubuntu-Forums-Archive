---
title: "Can't read permanent MAC address and adapter has no association?"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by john_b4 on 2014-12-18
I'm using a Rosewill RNX-n180ube USB wireless adapter on Ubuntu 12.04 64x. I've found two things to be strange that I want to fix. 

To start, when I put the connection down to use mac changer I get this error:

    ```
user@user:~$ sudo ifconfig wlan1 down
    [sudo] password for user: 
    user@user:~$ sudo macchanger -r wlan1
    ERROR: Can't read permanent MAC: Operation not supported
    Permanent MAC: 00:00:00:00:00:00 (Xerox Corporation)
    Current   MAC: 50:1d:a2:01:e2:e3 (unknown)
    New       MAC: 38:48:3f:f9:82:ed (unknown)
```

My adapters permanent hardware address is the **Current** one and should really and also be in the **Permanent** slot. I used `ifconfig wlan1` to check if everything is good:

    ```
wlan1     Link encap:Ethernet  HWaddr 50:1d:a2:01:e2:e3  
              BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:100 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

It seems its reading the hardware address. I checked the driver if it's being using:
```

    user@user:~$ sudo lsmod | grep r8712u
    r8712u                189680  0

```
I'm guessing everything is right since connection information for a network displays the driver. Now I went into the file **lshw.txt **and found this:

      ```
*-network
           description: Wireless interface
           physical id: 2
           bus info: usb@2:1
           logical name: wlan1
           serial: 50:1d:a2:01:e2:e3
           capabilities: ethernet physical wireless
           configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
```

I think the culprit is the **wireless=unassociated**. I think I need to put **wireless=IEEE 802.11n** but how would I do that? How could I set my wireless adapters permanent address? How can I fix both of these issues?

Thanks,

John

---

