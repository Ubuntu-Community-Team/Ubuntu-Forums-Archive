---
title: "ndiswrapper wlan0 won't start at boot"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by Maverick911 on 2005-11-07
My problem is getting the wireless to start up by itself at boot. I have an HP zx5000 with integrated Broadcom BCM4306 wireless. I have been able to get it working with the latest driver from HP's website and ndiswrapper1.5 from the terminal.

I have done 
```
ndiswrapper -m
```

After a reboot ```
lsmod -l
``` shows that ndiswrapper is loaded.

```
iwconfig wlan0
``` shows no WEP or key or essid assigned even though I have entered them in network settings properties for wlano and in /etc/network/interfaces.

This is what it iwconfig shows immediately after startup

```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

If I enter “iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXXXX” at the command line and then iwconfig the connection comes up.(Sometimes)

```
wlan0     IEEE 802.11g  ESSID:"Wireless100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:09:5B:E9:B0:78
          Bit Rate:11 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-71 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I then have to go back into network settings and set Default gateway device to wlan0. (It always defaults to eth0)

I've set wlan0 up with a static IP address in System>Administration>Networking and entered the WEP key and essid.

Here is what's entered in /etc/network/interfaces
```

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
address 192.168.1.13
netmask 255.255.255.0
gateway 192.168.1.1





iface wlan0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Wireless100
wireless-keymode open
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX

auto wlan0
```

Although I can eventually get the wireless working by activating, deactivating, reactivating, iwconfig wlan0 key, default gateway device...etc,etc, I'd like it to “just work”. 

Any suggestions would be deeply appreciated.

Wish You Were Here – Pink Floyd

---

### Post by eltaito on 2005-12-04
I would love to see a solution to this as well...I have the exact same problem using a broadcom chipset with the bcmwl5 driver.....getting sick of this proprietary driver crap..might just have to go buy an orinoco card

---

### Post by mhancoc7 on 2005-12-04
I had a problem with this once. I just added ndiswrapper to the end of my /etc/modules file.Then when I rebooted it worked fine.

Hope that gets it going for you.

Jereme:)

---

### Post by mpvano on 2005-12-04
Don't you also need to add wlan0 to the mapping statement to get hotplugging working after boot?

I think you should consider changing

mapping hotplug
        script grep
        map eth0

to read

mapping hotplug
        script grep
        map eth0 wlan0

to ensure that plugging and removing the card activates the interface under all circumstances....

Mario

---

