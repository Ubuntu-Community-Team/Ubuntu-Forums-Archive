---
title: "Wireless: can see network, can't connect"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by Racecarandy on 2008-08-05
Hello, i was recently installing ubuntu on a friends computer, and the make/break for him was the ability to use wireless.  After following several howto's and plenty of threads, i've finally got it to see networks but i can't connect.  Here my output:
```

lshw -C network
```

*-network
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:5c:03:ac
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI fi                                                                                                rmware=N/A ip=192.168.0.101 latency=0 mingnt=255 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:17:94:4c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52                                                                                                +The Linksys Group, Inc.,07/ latency=32 module=ndiswrapper multicast=yes wireles                                                                                                s=IEEE 802.11g

I've searched the forums (i promise) and haven't seen anything related to this.  Most issues are resolved with ndiswrapper and/or a driver that i've seen.  Thanks!

---

### Post by caljohnsmith on 2008-08-06
Do the network you are trying to connect to have encryption enabled (WEP/WPA/WPA2)? If so, definitely turn that off just to see if you can at least connect to an unencrypted AP. Also, it appears Ubuntu is correctly using ndiswrapper for your driver, but did you blacklist the native Ubuntu drivers for BCM chipsets? I think the modules you would need to blacklist are b43, bcm43xx, and b43legacy, so first look at:
```
cat /etc/modprobe.d/blacklist
```
If you don't see b43, bcm43xx and b43legacy listed in that file with the above command, just do:
```
sudo echo -e "blacklist b43\nblacklist bcm43xx\nblacklist b43legacy" >> /etc/modprobe.d/blacklist
```
That will make sure those modules don't get in the way of ndiswrapper. Also please post the output of:
```
iwconfig
ifconfig

```
That will help us troubleshoot your connection.

---

### Post by Racecarandy on 2008-08-06
```
cat /etc/modprobe.d/blacklist
```

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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b43
blacklist ssb
blacklist bcm43xx
blacklist bcm43xx
b43
bcm43xx
b43legacy
b43
bcm43xx
b43legacy

```
iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"2WIRE401"
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:13 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"2WIRE401"
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:13 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks for the reply.  The previous outputs are current after i ran this command:```

sudo echo -e "b43\nbcm43xx\nb43legacy" >> /etc/modprobe.d/blacklist
```

all security is off.  the network "2WIRE401" is just some random network the computer found.  I was trying to login to my companies wireless router and i had the proper passkey, but it still doesn't work.  Thanks.

---

### Post by caljohnsmith on 2008-08-06
I was just about to sign off here for the day and saw your post, and I made a mistake by not adding "blacklist" before those entries to put in your blacklist file. It won't hurt anything, but to clean up your blacklist file, please do the following:
```
gksudo gedit /etc/modprobe.d/blacklist &
```
Scroll to the bottom and edit it so it looks like:
```
blacklist b43
blacklist ssb
blacklist bcm43xx
blacklist b43legacy
```
I'll read the rest of your post and get back to you tomorrow if nobody else does in the meantime.

---

### Post by Racecarandy on 2008-08-06
> **caljohnsmith said:**
> I was just about to sign off here for the day and saw your post, and I made a mistake by not adding "blacklist" before those entries to put in your blacklist file. It won't hurt anything, but to clean up your blacklist file, please do the following:
```
gksudo gedit /etc/modprobe.d/blacklist &
```
Scroll to the bottom and edit it so it looks like:
```
blacklist b43
blacklist ssb
blacklist bcm43xx
blacklist b43legacy
```
I'll read the rest of your post and get back to you tomorrow if nobody else does in the meantime.

thanks.  i applied the correction.

---

### Post by caljohnsmith on 2008-08-07
OK Racecarandy, I'm back, how about trying the following:
```
sudo iwlist wlan0 scan
```
Does that give you a list of available wireless networks in your area? If it does, then go into System > Admin > Network, unlock it, enable only the wlan0 interface (wireless interface) and select it, hit properties, uncheck the enable roaming mode, select your wireless network, type in your network password and select the correct WEP/WPA setting for you network if the network uses encryption, and finally select "DHCP" for configuration. Can you connect?

---

### Post by Racecarandy on 2008-08-08
i'm now getting a cpu error and can only boot with the livecd.  i'll get back to that once i solve this error.  thanks.

---

### Post by jameskinds on 2009-11-08
The problem is likely with your IP leases from your router.

If you can see the network but simply can not connect, then power cycle the router and try to reconnect.

I had the same issue after the update but the power cycle sorted things out.

Best of luck.

jK

---

### Post by dungun on 2009-11-08
try this . it worked for me.

[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

---

