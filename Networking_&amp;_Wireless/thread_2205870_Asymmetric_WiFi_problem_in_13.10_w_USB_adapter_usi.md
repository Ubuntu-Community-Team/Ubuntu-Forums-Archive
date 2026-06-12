---
title: "Asymmetric WiFi problem in 13.10 w/ USB adapter using RTL8191SU"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by amitaigolub on 2014-02-16
Hi all,

I've been having a really strange issue that no amount of googling has solved, only mildly helped.

I am subscribed to a 50Mbit/s down 10Mbit/s up connection, but have noticed that the down speed is very slow (ususally around 3-5Mbits/s) while the up speed is normal. The company says that everything is ok on their end.

Running a speedtest on a mac and a windows machine both show that they get the expected amounts of speed while my computer doesn't. 

My computer is a Desktop I built myself  with a [Gigabyte GA-Z77X-D3H ATX LGA1155]("Gigabyte GA-Z77X-D3H ATX LGA1155 Motherboard") motherboard. I connect to the internet via USB connector. After copious googling somebody mentioned a similar issue and said that it had to do with the fact that my router (Fritzbox 7362SL) doesn't communicate well with the USB adapter using 802.11n. 

Forcing my router to only use 802.11b or 802.11g did indeed improve the situation yielding a down speed of 10-18 Mbits/s and normal up speed.

I would still like to solve this issue and get everything working as it should. I'm not sure if this is a software or hardware issue.... and the whole thing has been bugging the hell out of me. 

Thanks for the help!!! :)

(If it matters the following output is generated while the router only uses b+g)


OS: Ubuntu 13.10 GNOME
Kernel: 3.11.0-15-generic x86_64

lsusb output:
```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 2109:0811  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 045e:07f8 Microsoft Corp. 
Bus 001 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 004: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

iwconfig wlan0 output:

```

wlan0     IEEE 802.11bg  ESSID:"my_network"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 08:96:D7:24:A0:04   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=68/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The only module that seems to have to do with the network

```

Module                  Size  Used by

r8712u                184124  0 

```

---

### Post by varunendra on 2014-02-16
I think all you can do is to try a newer version of the driver and 'Hope' that it will be better. Currently you are using kernel 3.11... and we may give the backported driver from kernel 3.12.. a shot. But be aware that it will change the whole family of the driver (rtlwifi) and is not guaranteed to make any improvement.

If you wish to try, or find other possible tweaks, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by amitaigolub on 2014-02-17
Hi Varun,

Thanks for your reply. 

I tried getting the new driver from the realtek website but when I run the ./install.sh script it errors out and doesn't complete the installation.

I think that I'll simply get another usb or pci adapter that works "out of the box", this one wasn't expensive and I can use it for other things.

Thanks again for the help!

---

### Post by varunendra on 2014-02-18
You're welcome !

If you wish to try the newer driver, try these instructions : [http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946](http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946)

Takes only about a 10 MB download + 5 minutes or less to compile/install. :)

---

### Post by amitaigolub on 2014-02-18
Thanks!

I tried out the new driver which seemed to make/install fine (except for some things in the end, but no errors).

Anyhow, it didn't make a significant difference.

Thanks again. :)

---

