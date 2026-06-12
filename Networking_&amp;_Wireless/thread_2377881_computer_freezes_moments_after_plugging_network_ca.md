---
title: "computer freezes moments after plugging network cable in"
date: 2017-11-17
forum: Networking &amp; Wireless
---

### Post by missmoondog on 2017-11-17
as subject says, this laptop freezes within seconds after plugging ethernet cable in. have to do a hard shut down when this happens. runs fine on wireless though.

laptop is an older toshiba satellite c655d-s5200. 

description: Ethernet interface
                product: AR8152 v1.1 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: enp6s0
                version: c1
                serial: 00:26:6c:e6:94:a1
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
                resources: irq:25 memory:d0100000-d013ffff ioport:2000(size=128)
        *-usb:4

this is the first time this laptop has ever been hard wired, so surprised the heck out of me that it does this. i have blown out the dust bunnys from nic but didn't help.

any suggestion?

thank you

---

### Post by missmoondog on 2017-11-21
no ideas from anyone, huh? oh well, ordered one of these anyway, Plugable USB 2.0 Gigabit Ethernet Adapter from amazon.

---

### Post by jeremy31 on 2017-11-21
Can you find any errors searching the logs in /var/log/  or with ```
cat /var/log/kern.log | grep enp6s0
```

---

### Post by missmoondog on 2017-11-23
i'll let you know in a couple days. can't get on that computer until then.

thanks

---

### Post by missmoondog on 2017-12-10
sorry for the delay. darn holidays!!

Dec 10 21:57:51 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961071.3717] device (enp6s0): state change: ip-config -> deactivating (reason 'user-requested') [70 110 39]
Dec 10 21:57:51 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961071.3728] audit: op="device-disconnect" interface="enp6s0" ifindex=2 pid=1134 uid=1000 result="success"
Dec 10 21:57:51 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961071.3739] device (enp6s0): state change: deactivating -> disconnected (reason 'user-requested') [110 30 39]
Dec 10 21:57:51 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961071.4122] dhcp4 (enp6s0): canceled DHCP transaction, DHCP client pid 2466
Dec 10 21:57:51 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961071.4124] dhcp4 (enp6s0): state changed unknown -> done
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.2907] device (enp6s0): Activation: starting connection 'Wired connection 1' (34d18d20-1f9b-3c50-8e17-9eebe8a515ad)
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.2938] device (enp6s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.2988] device (enp6s0): state change: prepare -> config (reason 'none') [40 50 0]
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.3022] device (enp6s0): state change: config -> ip-config (reason 'none') [50 70 0]
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.3112] device (enp6s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.3184] device (enp6s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.3208] device (enp6s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.4022] policy: set 'Wired connection 1' (enp6s0) as default for IPv4 routing and DNS
Dec 10 21:58:36 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961116.4324] device (enp6s0): Activation: successful, device activated.
Dec 10 22:00:19 jerrod-Satellite-C655D kernel: [  483.916481] atl1c 0000:06:00.0: atl1c: enp6s0 NIC Link is Down
Dec 10 22:00:19 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961219.4835] device (enp6s0): link disconnected (deferring action for 4 seconds)
Dec 10 22:00:23 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961223.6272] device (enp6s0): link disconnected (calling deferred action)
Dec 10 22:00:23 jerrod-Satellite-C655D NetworkManager[666]: <info>  [1512961223.6276] device (enp6s0): state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Dec 10 22:10:56 jerrod-Satellite-C655D kernel: [    4.682246] atl1c 0000:06:00.0 enp6s0: renamed from eth0
Dec 10 22:11:00 jerrod-Satellite-C655D NetworkManager[639]: <info>  [1512961860.7575] devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0/net/enp6s0, iface: enp6s0)
Dec 10 22:11:00 jerrod-Satellite-C655D NetworkManager[639]: <info>  [1512961860.7575] device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0/net/enp6s0, iface: enp6s0): no ifupdown configuration found.
Dec 10 22:11:02 jerrod-Satellite-C655D NetworkManager[639]: <info>  [1512961862.4863] manager: (enp6s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/1)
Dec 10 22:11:02 jerrod-Satellite-C655D NetworkManager[639]: <info>  [1512961862.4924] device (enp6s0): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 10 22:11:02 jerrod-Satellite-C655D kernel: [   23.011508] IPv6: ADDRCONF(NETDEV_UP): enp6s0: link is not ready
Dec 10 22:11:02 jerrod-Satellite-C655D kernel: [   23.030173] IPv6: ADDRCONF(NETDEV_UP): enp6s0: link is not ready

this is the result of that command.

what does that tell us? can you tell if this thing is even able to connect on the 5ghz band?

at least computer didn't lock up this time.  just flat out didn't work hard wired :(

thanks

---

### Post by jeremy31 on 2017-12-11
See the wireless script link in my signature and post results and we will know if you can use 5Ghz wifi and we might find an issue with the ethernet

---

