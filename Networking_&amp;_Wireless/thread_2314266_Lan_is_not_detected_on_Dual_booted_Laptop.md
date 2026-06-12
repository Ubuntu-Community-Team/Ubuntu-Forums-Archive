---
title: "Lan is not detected on Dual booted Laptop"
date: 2016-02-19
forum: Networking &amp; Wireless
---

### Post by Ravi_Bansal on 2016-02-19
I have dual booted my laptop. It has ubuntu 14.04 LTS and windows 8.1 on the system. Ubuntu is not able to detect lan but its working on windows. Wireless is working fine on ubuntu. 

Here is my output of ifconfig -a : 
```

eth0      Link encap:Ethernet  HWaddr f8:a9:63:3f:aa:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:343985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:277908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:420252634 (420.2 MB)  TX bytes:26458433 (26.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60016 (60.0 KB)  TX bytes:60016 (60.0 KB)

wlan0     Link encap:Ethernet  HWaddr 18:cf:5e:52:72:3d  
          inet addr:10.147.235.45  Bcast:10.147.255.255  Mask:255.255.128.0
          inet6 addr: fe80::1acf:5eff:fe52:723d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46442564 (46.4 MB)  TX bytes:3589655 (3.5 MB)


```

I can get the LAN working for once by typing this command but speed is slow and lossy. 
```

sudo ethtool -s eth0 speed 100 duplex full autoneg off

```

The lan's detection goes off as soon as i restart the network or restart my system after typing the above code.
Please help.

---

### Post by chili555 on 2016-02-19
Let's get your command to run automatically on boot:```
sudo gedit /etc/rc.local
```Change the file to read:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ethtool -s eth0 speed 100 duplex full autoneg off

exit 0

```Proofread carefully, save and close the text editor.

You should be all set.

---

### Post by Ravi_Bansal on 2016-02-19
I can get the code working automatically at every restart. But as i mentioned above that it is slow and lossy. So, please suggest me some method by which i can connect to internet normally like other ubuntu users.

---

