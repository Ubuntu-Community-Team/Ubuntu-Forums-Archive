---
title: "Issue with  Realtek Ethernet Controller"
date: 2014-09-04
forum: Networking &amp; Wireless
---

### Post by Trad_dog on 2014-09-04
Hi,

The Ethernet Controller of my laptop has not been functioning for a couple of days. Chili555 suggested I start a thread on this issue. Below some requested diagnostics

```

Presario-C700-Notebook-PC:~$ lspci -nn | grep 0200
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
```

```
Presario-C700-Notebook-PC:~$ dmesg | grep -e 8139 -e eth0
[    0.596171] pci 0000:02:01.0: [10ec:8139] type 00 class 0x020000
[    2.397969] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.398014] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.424715] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.426079] 8139too 0000:02:01.0 eth0: RealTek RTL8139 at 0x0000000000011000, 00:1b:38:82:fb:5c, IRQ 16
[   21.917068] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.498139] Bluetooth: L2CAP socket layer initialized
[   33.876452] 8139too 0000:02:01.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1


```

Thanks in advance for the help

Trad

---

### Post by chili555 on 2014-09-04
May we also see:```
nm-tool
cat /var/log/syslog | grep -e eth0 -e 8139 -e etwork | tail -n20
cat /etc/network/interfaces
```Please take these diagnostics with a known working ethernet cable attached.

---

### Post by Trad_dog on 2014-09-04
Hi Chili555,

And another good day to you. 

Here are the logs requested. 

Let me know if you need something else. 

Best

---

### Post by chili555 on 2014-09-04
Here is a snip from *nm-tool*:> - Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             disconnected
  Default:           no
  HW Address:        00:1B:38:82:FB:5C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [virginmedia6249288] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:1A:73:AF:8C:B0Normally, Network Manager will default to ethernet when it's available as it is generally faster and more secure. Your ethernet is available as it sees a carrier signal from the router:> Wired Properties
    [COLOR="#FF0000"]Carrier:         on[/COLOR]I am a bit concerned by this in the log:> <info> (eth0): device state change: unavailable -> disconnected (reason '[COLOR="#FF0000"]carrier-changed[/COLOR]') [20 30 40]Does your laptop have a wireless switch? I am quite confident it has a key combination, Fn+F2 or some such. Will you please hook up the ethernet and switch the wireless off and try again? 

I wonder if this is a quirk in Network Manager.

Please let me see the log again:```
cat /var/log/syslog | grep -e eth0 -e 8139 -e etwork | tail -n20
```

---

### Post by Trad_dog on 2014-09-05
Actually a quirck in the Network Manager is quite possible as even for the wireless problem I was
reflecting on the fact that the USB dongle WAS seeing the wifi networks and I am wondering
if creating a new entry for the hotspot directly and manually did not help for to hook up. 

At any rate, I followed your instruction and did switch off the Wireless (as can be seen in the log
at 11:09:28). Here is the content of varsyslog:

```

Presario-C700-Notebook-PC:~$ cat /var/log/syslog | grep -e eth0 -e 8139 -e etwork | tail -n20
Sep  5 11:08:56 Presario-C700-Notebook-PC NetworkManager[733]: <info> (eth0): carrier now ON (device state 20)
Sep  5 11:08:56 Presario-C700-Notebook-PC NetworkManager[733]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep  5 11:08:57 Presario-C700-Notebook-PC avahi-daemon[714]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21b:38ff:fe82:fb5c.
Sep  5 11:08:57 Presario-C700-Notebook-PC avahi-daemon[714]: New relevant interface eth0.IPv6 for mDNS.
Sep  5 11:08:57 Presario-C700-Notebook-PC avahi-daemon[714]: Registering new address record for fe80::21b:38ff:fe82:fb5c on eth0.*.
Sep  5 11:08:59 Presario-C700-Notebook-PC ntpd[1843]: Listen normally on 6 eth0 fe80::21b:38ff:fe82:fb5c UDP 123
Sep  5 11:09:11 Presario-C700-Notebook-PC kernel: [  411.243444] 8139too 0000:02:01.0 eth0: link down
Sep  5 11:09:11 Presario-C700-Notebook-PC NetworkManager[733]: <info> (eth0): carrier now OFF (device state 30)
Sep  5 11:09:11 Presario-C700-Notebook-PC NetworkManager[733]: <info> (eth0): device state change: disconnected -> unavailable (reason 'carrier-changed') [30 20 40]
Sep  5 11:09:11 Presario-C700-Notebook-PC NetworkManager[733]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Sep  5 11:09:23 Presario-C700-Notebook-PC kernel: [  422.905106] 8139too 0000:02:01.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep  5 11:09:23 Presario-C700-Notebook-PC NetworkManager[733]: <info> (eth0): carrier now ON (device state 20)
Sep  5 11:09:23 Presario-C700-Notebook-PC NetworkManager[733]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep  5 11:09:38 Presario-C700-Notebook-PC NetworkManager[733]: <info> WiFi now disabled by radio killswitch
Sep  5 11:09:38 Presario-C700-Notebook-PC NetworkManager[733]: <info> (wlan0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Sep  5 11:09:38 Presario-C700-Notebook-PC NetworkManager[733]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep  5 11:09:38 Presario-C700-Notebook-PC NetworkManager[733]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1109
Sep  5 11:09:38 Presario-C700-Notebook-PC NetworkManager[733]: <warn> DNS: plugin dnsmasq update failed
Sep  5 11:09:38 Presario-C700-Notebook-PC NetworkManager[733]: <info> Removing DNS information from /sbin/resolvconf
Sep  5 11:09:38 Presario-C700-Notebook-PC NetworkManager[733]: <info> NetworkManager state is now DISCONNECTED
```
Just to confirm, the wired connection did not fire up. I took the initiative to try something like:
```

sudo ifconfig eth0 up

```

---

### Post by Trad_dog on 2014-09-05
Hi Chili555,

You are likely to be onto something about the network manager as I just tried this hotspot again near my place
and at first, it would not connect. After a while and as I was trying several maninpulations in the "network connections" GUI, 
it finally hooked up. Now that I recall, it had a similar behaviour yesterday when I closed the Wireless thread. 
It might be that there has been all along a double issue. One related to the wireless driver that you fixed, the
other with the Network Manager and this one would affect both the wireless and ethernet connections. 

I attach a log of regarding the events related to the Wireless connection struggling to hook up, in case
that brings some light on the issue. If you suspect it is a random behaviour peculiar to my system and difficult 
to track down, I could reinstall the OS entirely. This is an old PC with not much customisation
or personal data on it: so it would not be too long. 

Let me know your thoughts,

Trad
Best

---

