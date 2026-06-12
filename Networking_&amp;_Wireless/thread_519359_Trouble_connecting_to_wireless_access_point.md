---
title: "Trouble connecting to wireless access point"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by wfsumme on 2007-08-06
Just installed ubuntu feisty fawn onto a fairly old Compaq Presario 1200.  It seems to have gone fine.  However, I am now trying to get  TrendNet USB wireless adapter (TEW-424UB) configured  to hookup to my wireless access point (WEP is disabled, MAC filtering is disabled).  Followed the steps for configuring using ndiswrapper.  I suspect that's configured properly because I issue "ndiswrapper -l" and I get back 
```
  net8187b : driver installed
  device (0BDA:8189) present
```

I've tried connecting with wicd and it just keeps spinning trying to obtain an ip address and, after a minute, returns with "Not Connected".  

Tried issuing the following commands 
```
sudo modprobe ndiswrapper (worked fine)
sudo iwconfig wlan0 essid <my essid> (worked fine)
sudo dhclient wlan0
```

When I issued the dhclient command, I get the following:
```
DHCPDISCOVER on WLAN0 TO 255.255.255.255 port 67 interval 7
DHCPDISCOVER on WLAN0 TO 255.255.255.255 port 67 interval 11
DHCPDISCOVER on WLAN0 TO 255.255.255.255 port 67 interval 13
NO DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Any help would be greatly appreciated.  Thanks.

---

### Post by noob12 on 2007-08-07
Can we see the output of these?
```

lsusb

lshw -C network

ndiswrapper -v

cat /etc/modprobe.d/blacklist

iwconfig

iwlist scan

```

---

### Post by wfsumme on 2007-08-07
Here's the output.
```
>>> lsusb <<<
Bus 001 Device 008: ID 1043:8012 iCreate Technologies Corp. 
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
.
>>> sudo lshw -C network <<<
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:d1:36:0a:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.47+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g
.
>>> ndiswrapper -v <<<
utils driver version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 
.
>>> cat /etc/modprobe.d/blacklist <<<
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist bcm43xx
.
>>> iwconfig <<<
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2346 B   Fragment thr=2347 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

.
>>> iwlist scan <<<
wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:39:75:2B
                    ESSID:"wfscharlottenc"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

---

### Post by kevdog on 2007-08-07
Where did  you get your 8187 driver (.inf file)?  Some people have had success with the win98 driver rather than the WinXP driver.

---

### Post by noob12 on 2007-08-07
This looks fine, and I see you are running ndiswrapper 1.47, which means you installed that yourself.   Are you broadcasting the ESSID?  It looks like you may not be, but I'm not certain.  In any case your signal level is a bit low.  If you ESSID is not being broadcast, please try turning that on to see if it helps. Once you've done that try the manual configuration steps you had shown earlier.

Before going to wicd, I'd suggest first trying NetworkManager with your ndiswrapper config and setting up either WEP or WPA with the wpasupplicant package from the Feisty distro.  More of this is setup to work together in Feisty closer to out-of-box.

I can help with that.

EDIT:  kevdog's post just beat mine and I didn't see it.  I'd suggest this first step, and then if that doesn't work try his suggestion.

---

### Post by wfsumme on 2007-08-07
Thanks noob12 and kevdog!  I'll give your suggestions a shot.

---

### Post by wfsumme on 2007-08-07
I'm using the win2000 .inf file (per suggestion from ndiswrapper site for my hardware).  The Access Point ESSID has been set to broadcast all along (confirmed that earlier).  I have WEP disabled just to see if I can connect to my access point.  Once that's done, I'll try to configure WPA.  Thanks folks.

---

### Post by wfsumme on 2007-08-07
Okay, I switched to the Win98 inf driver and I can now connect to the access point.  However, now I can't get to the internet.  Browser just spins when I try to connect to any internet address and eventually times out.  Any ideas?

---

### Post by kevdog on 2007-08-07
That certainly is strange.

How do you know you are connected to the router?  I assume your dhclient command issued a local IP address?

After connecting to the router can you give the following output:
iwlist scan
ifconfig
/etc/network/interfaces

Thankss

---

