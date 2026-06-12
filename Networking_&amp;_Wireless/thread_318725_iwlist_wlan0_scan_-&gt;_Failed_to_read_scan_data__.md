---
title: "iwlist wlan0 scan -&gt; Failed to read scan data : Resource temporarily unavailable"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by skinny on 2006-12-14
Hi all,

I'm installing my wireless WG111v2 usb pen but keep getting this error when trying to scan for my wireless network:

```
sudo iwlist wlan0 scan
wlan0    Failed to read scan data : Resource temporarily unavailable
```

Any ideas? I'm sure its something simple...

$

EDIT: Latest drivers (2.x) don't work very well, although appear to. Go to netgears website and use an older version, 1.4 with latest ndiswrapper and it works fine.

---

### Post by cujo on 2007-12-31
Did you ever get this sorted out?  I'm having the same issue.

---

### Post by skinny on 2008-01-07
sorry for the late reply cujo!

I sorted it (apparently!) with a different set of drivers. The ones I had been using worked a bit, in so much as I could see the wireless network, at times, but I could never connect. I can't quite recall if I made any other significant changes, I presume not.  I'd suggest heading over to the website of your wireless adapter and trying different drivers, using windows drivers and ndiswrapper if need be.

g'luck :)

---

### Post by ethanay on 2008-02-05
I get this same message under these conditions:

driver: iwl3945, loaded
wlan0 interface is up and ready to associate (ifconfig wlan0 up)

I run these commands:
iwlist wlan0 scan

scan is initially successful.  it appears I can run the scan at this point without the driver failure occurring.

moving on:

iwconfig wlan0 essid <network name here> key <password here>
association is successful

then lastly, 
dhclient wlan0

the connect is almost always successful

however, running iwlist wlan0 scan again locks up the driver and i lose all networking, even though the computer is still telling me that the interface remains associated.

so i have to modprobe -r iwl3945
reload: modprobe iwl3945
bring wlan0 online: ifconfig wlan0 up
rescan: iwlist wlan0 scan
reassociate:  iwconfig wlan0 essid < > key < >
lastly: dhclient wlan0

and I'm back online.

However, in the mean time, I'd like to know what causes the fragging message:

Failed to read scan data : Resource temporarily unavailable

---

