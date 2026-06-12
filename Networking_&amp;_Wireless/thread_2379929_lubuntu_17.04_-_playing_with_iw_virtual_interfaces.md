---
title: "lubuntu 17.04 - playing with iw virtual interfaces, need help"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by dada216 on 2017-12-11
I recently realized this can be done:

[https://wireless.wiki.kernel.org/en/users/documentation/iw/vif](https://wireless.wiki.kernel.org/en/users/documentation/iw/vif)

[I]mac80211 Multiple Virtual Interface (vif) Support

The mac80211  subsystem in the linux kernel supports multiple wireless interfaces to  be created with one physical wireless card. This depends on the driver  implementing this. This could allow you to join multiple networks at  once, or connect to one network while routing traffic from an access  point interface.


[/I]So I now want multiple wireless virtual devices on my current lubuntu 17.04.

according to this (a somewhat dated howto from a company making wifi traffic generators and AP tester with this)
--> [http://www.candelatech.com/vsta.php](http://www.candelatech.com/vsta.php)

one basically needs to create the interfaces using the iw tool, tell ubuntu system to leave those devices alone and then configure them.
I want to get a bit more, I want my standard network interface to be managed by the network manager WHILE I have access to the virtual interfaces wlo2 and mon0 (same phy as wlo1, the standard wlan device) both in monitor mode and AP mode.

so here's my hw

```
lspci -k
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
            DeviceName: Atheros AR9485 802.11b/g/n WiFi Adapter
            Subsystem: Hewlett-Packard Company AR9485 Wireless Network Adapter
            Kernel driver in use: ath9k
            Kernel modules: ath9k

```

and here's my current network settings:

```
$ iw dev
phy#0
    Interface wlo1
        ifindex 5
        wdev 0x3
        addr XX:XX:XX:XX:XX:XX
        type managed
        channel 1 (2412 MHz), width: 20 MHz (no HT), center1: 2412 MHz
        txpower 15.00 dBm

```


and this is what I did at my first try:

```

sudo service stop network-manager
sudo service stop NetworkManager
sudo service stop wpa_supplicant
sudo iw phy phy0 interface add wlo2 type station
sudo iw phy phy0 interface add mon0 type monitor flags none
sudo macchanger -r wlo2
sudo macchanger -r mon0

```

it almost worked, after restarting the network services Network Manager picked up on wlo2 and showed it in the GUI, it all seems to be working on this device (it can connect both with Network Manager GUI and with iw scan&iw connect), NM does drop an error if you try to connect to the same AP with both wlo1 and wlo2, one at a time is fine, different AP is fine, same AP it complains, which is fair enough.

what is not working is the monitor interface, tcpdump complains the  device can't be opened, airmon-ng start mon0 says the device is already in monitor mode (obvious but it's ok, airmon-ng creates a vif interface, it's basically doing what I have done manually with iw).

so I'm now trying to get to the part where one tells ubuntu system to leave wlo2 and mon0 alone.

this is from the Network Manager documentation:

[I]NetworkManager tries to read and write your distribution's normal  network configuration files through plugins called "system settings  plugins". A generic plugin called 'keyfile' is also provided to read and  write configuration that your distro's native file format cannot  handle.

These plugins are configured through the /etc/NetworkManager/NetworkManager.conf configuration file.
[/I]
```
$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false 

```

[I]ifupdown

This plugin is used on the Debian and  Ubuntu distributions, and reads connections from  /etc/network/interfaces. Since it cannot write connections out (that  support isn't planned) it is usually paired with the 'keyfile' plugin to  enabled saving and editing of new connections. The ifupdown plugin  supports basic wired and wifi connections, including WPA-PSK.

Persistent Hostname

As  the standard location for the persistent system hostname on Debian-base  distributions is /etc/hostname, the ifupdown plugin reads the hostname  from that location.

Unmanaged Devices

The ifupdown plugin  also uses the /etc/NetworkManager/NetworkManager.conf for some  configuration. All ifupdown-specific options go in a "[ifupdown]"  section. If the "managed" key is set to "false", then any device listed  in /etc/network/interfaces will be completely ignored by NetworkManager.  Remember that NetworkManager controls the default route, so because the  device is hidden, NetworkManager will assign the default route to some  other device. 
[/I]
So I'm thinking I could use the already installed plugin ifupdown   managed=true and add wlo1 to my interfaces file or I can used ifupdown   managed=false and add wlo2 & mon0 to my interface file.

my current network/interfaces file is almost empty tho, does ubuntu takes care of devices another way now? is this something udev does?

```
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

there's also the following nmcli option

```

DEVICE MANAGEMENT COMMANDS
       nmcli device {status | show | set | connect | reapply | modify | disconnect | delete | monitor | wifi | lldp}
       
          set [ifname] ifname [autoconnect {yes | no}] [managed {yes | no}]
          Set device properties.

```

which I tried:

 ```

$ nmcli device set wlo2 autoconnect no managed no
```


and it does work on the wlo2 interface, I can add it and remove it from Network Manager without issues, the device keeps working whether is' managed or not, it doesn't work on the mon0 interface tho, Network Manager doesn't sees mon0.

Any suggestions on how to achieve this? do you guys think the driver are gonna allow station/monitor/AP concurrent mode?
I think I need to look into udev too, and that's under systemd now, any suggestions on how to go about that?

I've tried reading the udev conf files and some documentation but its vaste and could'nt find quickly what I need, anybody did this?

---

