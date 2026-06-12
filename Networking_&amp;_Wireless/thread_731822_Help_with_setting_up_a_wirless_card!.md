---
title: "Help with setting up a wirless card!"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by andrewgalpin on 2008-03-22
Hey,

i have finally got around to installing Ubuntu, but as a begginger in not that 'fluent' on it yet, so i have a Hawking HWP54G wirless card and i have set it up with the windows driver using NDISwrapper, which 'i think' has worked, but then it still would not allow me to connect to my network, so i followed some instructions to run the network manager in the terminal, which i found i kep getting the following when it was trying to connect.

> 
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID 'SKY81685'
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 6 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 0 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 1 value 0x10 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 2 value 0x10 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 3 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 10 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 8 value 0x1 - Association request to the driver failed
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
ioctl[SIOCSIWMLME]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
NetworkManager: <info>  wlan0: link timed out.


 

Thats just some of it, but it just seems to repeat, over and over again.

Any suggestions welcome!

thanks

Andy

---

### Post by Sam Lars on 2008-03-22
What do you get from
```
ifconfig
iwconfig
```

---

### Post by dstew on 2008-03-22
Also, post the output of ```
ndiswrapper -l
```

---

### Post by andrewgalpin on 2008-03-23
Ok this is what i got:

ifconfig

e
```

th0      Link encap:Ethernet  HWaddr 00:00:B5:4B:47:7F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:0E:2A:FF:EF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe000 

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=33/100  Signal level=6/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

ndiswrapper -i

```

install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card


```

thanks :)

---

### Post by Sam Lars on 2008-03-23
It's
```
ndiswrapper -l
```
It's an L not an I.

---

### Post by andrewgalpin on 2008-03-23
oops lol 1 mo i will just do that! :)

here :)

 ndiswrapper -l
```

tnet1130 : driver installed
        device (104C:9066) present (alternate driver: acx)

```

thanks!

---

### Post by mrsudo on 2008-03-23
it looks to be installed correctly.  
i have had many problems with the default network manager.  
i gave wicd a try, the only down side is you have to uninstall network manager to get it up and running.  

its worth a try :)

---

### Post by andrewgalpin on 2008-03-23
ok thanks i will try that now :)

---

### Post by dstew on 2008-03-23
You should blacklist the alternate driver if you still have problems. The acx driver might be interfering with the ndiswrapper driver. To blacklist a driver, use a text editor to open (or create if it does not exist) the file /etc/modprobe.d/blacklist. You can use the gedit program by using the command```
gksudo gedit /etc/modprobe.d/blacklist
```Put into the file the line ```
blacklist acx
``` Save the file and reboot. Do ndiswrapper -l again, and hopefully it will not list acx as an alternate driver.

---

