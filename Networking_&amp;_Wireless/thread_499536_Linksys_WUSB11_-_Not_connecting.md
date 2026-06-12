---
title: "Linksys WUSB11 - Not connecting"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by Lee Davies on 2007-07-12
I've installed 7.04 and whilst Ubuntu detects the wireless USB adapter, it doesn't connect to the network even though I've supplied all the information (such as WEP key).

I've followed instructions using ndiswrapper, but to no avail.

Sometimes another wireless item is found in "Network Tools" - called "wlan0:avahi" - and even though it shares the same MAC address is wlan0 (the adatper), it displays a fake IP address (169.x.x.x) rather than an actual one (192.168.1.x).

Even when specify a static IP, wlan0 accepts it but still won't work, whilst wlan0:avahi still displays the fake one.

iwconfig returns:

> wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I would appreciate any help with installing this damned thing!

---

### Post by kevdog on 2007-07-12
Did you install any drivers for your device, and do you happen to know what the chipset is contained within the device.

Possibly
lsusb 
may help, but Im not certain.

Also lets just see write now what driver is associated with your usb device, sometimes that gives an indication of the chipset:
lshw -C network

---

### Post by Lee Davies on 2007-07-13
The results of "lshq -C network" (run as sudo);

 > *-network:0             
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:05:1b:00:5d:73
       size: 100MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=pegasus driverversion=v0.6.14 (2006/09/27) duplex=full ip=192.168.1.100 link=yes multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0c:41:5a:4e:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.0-86 wireless=IEEE 802.11b

The results of lsusb;

> Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 1915:2233  
Bus 002 Device 003: ID 050d:0121 Belkin Components F5D5050 100Mbps Ethernet
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I've installed "linux-wlan-ng", and tried to use ndiswrapper - both to no avail.

---

### Post by kevdog on 2007-07-13
The driver associated with your card right now is:
at76_usb

It says so in the output you gave me.  

Lets see if the module is loaded:
lsmod | grep at76

If something comes back can you post your 
/etc/network/interfaces file.


Also since we are debugging a problem turn off WEP/WPA/MAC filtering on your router for now!

---

### Post by Lee Davies on 2007-07-13
It's okay now, I've "fixed" the problem by downgrading to 6.10 Edgy Eft; with the only thing I done differently was unplug the USB adaptor and wait until it was fully installed.

I'm upgrading by CD to Feisty, so I'll get back to you with that =)

**Edit**
I've just checked the driver being used on Edgy, to see if it was different to the one Feisty uses - and it was.

Edgy uses "at76c503" version "0.12beta23-fw_dwl"

---

### Post by kevdog on 2007-07-13
That driver overall is known as a buggy driver.  Hopefully you can find that works for you!  If not take a look at this page:
[http://at76c503a.berlios.de/#why](http://at76c503a.berlios.de/#why)

---

### Post by Lee Davies on 2007-07-13
I haven't updated any firmware on the adaptor, so it's working fantastically.

I also haven't upgraded to Feisty Fawn, as I'm forced to watch my bandwidth usage :mad:

---

