---
title: "WG111V1 Dongle problems, wits end"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by malfist on 2007-02-02
Please help! I'm pulling out my hair!

Okay, this is the problem. I've set up my dongle as instructed but it doesn't work quiet right. Randomly I will lose connection, I have no idea why. I have data:

jerome@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:58:60:E7
                    ESSID:"hollonet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:25  Signal level:0  Noise level:56
                    Extra: Last beacon: 479ms ago
Signal level is always, always 0, even when connected.

jerome@ubuntu:~$ sudo iwconfig wlan0
wlan0     802.11b/g linked  ESSID:"hollonet"
          Mode:Managed  Channel=6  Access Point: 00:18:F8:58:60:E7
          Bit Rate=54 Mb/s   Sensitivity=4/6
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jerome@ubuntu:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:6C:5F:CB:67
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe5f:cb67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:161 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4893 (4.7 KiB)  TX bytes:4118 (4.0 KiB)

And most important:
jerome@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
netwg111                driver present
netwg111.ing    invalid driver!

I've blacklisted all the drivers I need but using dmseg it still shows rtl8187 driver is still in some sort of use.

Please! I'm near giving up.

---

### Post by phossal on 2007-02-03
I recommend a few things:
If you're going to use ndiswrapper, which I consider a good idea, upgrade it to 1.35. 
Remove the other ndiswrapper driver if you're not using it. 
Finally, delete every occurrence of the *rt*818* drivers*
```
locate *rt*818*
```

---

### Post by malfist on 2007-02-03
I did the locate and used rm on every occurance (2 plus two folders) and now it doens't even have wlan0 listed as a device. No connection to the internet.
Should I just run wired?

---

### Post by malfist on 2007-02-03
More data:
root@ubuntu:~/netgear/WG111_SW1.2Beta13/ndis5# sudo ndiswrapper -m
module configuration contains directive install usb:v0846p4220d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 400.
module configuration contains directive install usb:v0846p4240d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 401.
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...


And:
root@ubuntu:~/netgear/WG111_SW1.2Beta13/ndis5# tail /var/log/syslog
Feb  3 10:48:21 localhost gconfd (root-4889): GConf server is not in use, shutting down.
Feb  3 10:48:21 localhost gconfd (root-4889): Exiting
Feb  3 10:54:59 localhost gconfd (root-5287): starting (version 2.14.0), pid 5287 user 'root'
Feb  3 10:54:59 localhost gconfd (root-5287): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  3 10:54:59 localhost gconfd (root-5287): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  3 10:54:59 localhost gconfd (root-5287): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  3 10:54:59 localhost gconfd (root-5287): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb  3 10:54:59 localhost gconfd (root-5287): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb  3 10:55:59 localhost gconfd (root-5287): GConf server is not in use, shutting down.
Feb  3 10:55:59 localhost gconfd (root-5287): Exiting

And one more:
root@ubuntu:~/netgear/WG111_SW1.2Beta13/ndis5# ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "hollon".
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by phossal on 2007-02-03
Nah, you need to install the correct driver for ndiswapper to work.

---

### Post by phossal on 2007-02-03
What's the output to this: 
```
lsusb | grep NetGear
```
That will tell you what device you have. Then we can figure out what driver you need. I'm guessing it's going to say something like:
0846:4240 *or* 0846:6a00

---

### Post by phossal on 2007-02-03
> **malfist said:**
> 
[B]And most important:
jerome@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
netwg111                driver present[/B]
netwg111.ing    invalid driver!

You have that line if your first post. It *is* the most important. It indicates you have ndiswrapper (at least partially) installed, but not the *correct* driver. Even if your device is being loaded with the wrong driver, ndiswrapper will recognize that your hardware is present. In the output above, it *isn't* present. You need the *correct* driver.

This is easy, really. Don't give up.

---

