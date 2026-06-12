---
title: "Ubuntu 16.04: Wired connection not working, &quot;eth0&quot; renamed to &quot;eno1&quot;. Can't connect"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by Birger_Skogeng_Ped on 2016-05-13
Hi,

[COLOR=#111111][FONT=Ubuntu]Yesterday I lost my internet connection after rebooting my Ubuntu 16.04 installation. Now when Ubuntu boots, it searches for a network for a couple of minutes, then states "Connection established" but I can't get online or communicate (send ping requests, for instance) to anyone.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I deleted the ethernet network, hoping it would re-initialize if I re-added it. When I click the network manager icon, the "Ethernet Network" is greyed out (so I can't enable it). There is a new entry now, called "Auto Ethernet" but that one doesn't work (same symptoms as I mentioned earlier).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I try to add a new ethernet network connection, the "eth0" is gone from the list of devices. Instead, I now have a "eno1" entry which I've never seen before. It might be the same device that is renamed but I don't know.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My /etc/network/interfaces file contains

```

[COLOR=#222222][FONT=Verdana]auto lo
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]iface lo inet loopback
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]
```[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]```
dmesg | grep "eth0"
eth0: Intel(R) PRO/1000 Network Connection
eth0: Mac: 11, PHY 12, PBA No: FFFFFF-0FF
eno1: renamed from eth0
```

How can I fix this ASAP? I have a bootable Ubuntu 16.04 usb, I'm considering just reinstalling Ubuntu at this point...[/FONT][/COLOR]

---

### Post by Birger_Skogeng_Ped on 2016-05-13
Someone suggested I add eno1 to the /etc/network/interfaces file. I did, then ran "sudo sustemctl restart networking" which never finished. Forced a reboot, no network. Tried to stop the eno1 network device by "sudo ifdown eno1" but it got stuck waiting for lock. Forced another reboot and suddenly my connection works. I tried to remove the eno1 entry from /etc/network/interfaces and rebooted and my connection is now fully working.

[IMG]http://i.imgur.com/G2ApLA8.png[/IMG]

What does this mean excactly? Do I have a disabled network connection named "Ethernet Network", or is "Ethernet Network" just a label for a category of connections, which "Auto Ethernet" is an element of?

Also I haven't got a clue why my network stopped working in the first place. Happened yesterday after a reboot and after an hour or two of trying to figure out the problem it started working again...

---

### Post by Birger_Skogeng_Ped on 2016-05-19
Shameless bump, as I've now got the same error all over again. I'm on a computer with both Windows 10 and Ubuntu 16.04 installed. I just rebooted from Windows 10 and into Ubuntu, only to find the ethernet connection broken again. Can someone help me?

---

### Post by teetere on 2016-05-21
you will have to edit /etc/network/interfaces and add after lo

```
auto eno1
iface eno1 inet  dhcp
```

then exit if you want dhcp to get ip address if you want static address you can look that up.

then ```
sudo /etc/init.d/networking restart should restart you network
```

```
ifconfig
```  should give you the IP address

See if that works

---

### Post by Birger_Skogeng_Ped on 2016-06-06
Thanks for your reply. Tried what you suggested, and it hung at "Restarting networking (via systemctl): networking.service". I canceled it, and restarted network manager. Tried what you suggested again, and now the networking restart finished quickly. Still, no network.

This issue has happened three times now, and it seems to be happening each time I reboot into Windows (!).

---

### Post by n5wy on 2016-06-06
Another thing that you could try if you reboot and the ethernet is working, is disable IPv6 for the interface. Select edit connection from the Network Manager and tell it to ignore IPv6 for that interface and see if that improves your performance. I have found that since I am not on networks that use IPv6, disabling it seems to prevent random network drops when the OS decides to go looking for IPv6 connectivity.

---

### Post by amedee3 on 2016-12-05
Did anyone ever find a **confirmed** working solution for this problem?

---

### Post by Ossipon on 2016-12-12
**In my case it was a hardware issue**

I had this problem too today. My network interface was renamed from eth0 to enp1s0. syslog was reporting messages like these, continuously:

```
Dec 12 19:11:58 wotan kernel: [ 1494.524821] r8169 0000:01:00.0 enp1s0: link up
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8614] device (enp1s0): link connected
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8626] device (enp1s0): state change: unava
ilable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8635] policy: auto-activating connection '
Wired connection 1'
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8645] device (enp1s0): Activation: startin
g connection 'Wired connection 1' (f661ffeb-b161-3b65-a7a3-58f1bd51e6c4)
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8648] device (enp1s0): state change: disco
nnected -> prepare (reason 'none') [30 40 0]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8649] manager: NetworkManager state is now
 CONNECTING
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8703] device (enp1s0): state change: prepa
re -> config (reason 'none') [40 50 0]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8742] device (enp1s0): state change: confi
g -> ip-config (reason 'none') [50 70 0]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8746] dhcp4 (enp1s0): activation: beginnin
g transaction (timeout in 45 seconds)
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8760] dhcp4 (enp1s0): dhclient started wit
h pid 6511
Dec 12 19:11:58 wotan dhclient[6511]: DHCPREQUEST of 192.168.1.3 on enp1s0 to 255.255.255.255 port 67 (xid
=0x115e7347)
Dec 12 19:11:59 wotan kernel: [ 1495.267912] r8169 0000:01:00.0 enp1s0: link down
Dec 12 19:11:59 wotan NetworkManager[1485]: <info>  [1481566319.8739] device (enp1s0): link disconnected (
deferring action for 4 seconds)
Dec 12 19:12:00 wotan avahi-daemon[1450]: Joining mDNS multicast group on interface enp1s0.IPv6 with address fe80::a462:a773:1523:5d4d.
Dec 12 19:12:00 wotan avahi-daemon[1450]: New relevant interface enp1s0.IPv6 for mDNS.
Dec 12 19:12:00 wotan avahi-daemon[1450]: Registering new address record for fe80::a462:a773:1523:5d4d on enp1s0.*.
Dec 12 19:12:01 wotan dhclient[6511]: DHCPREQUEST of 192.168.1.3 on enp1s0 to 255.255.255.255 port 67 (xid=0x115e7347)
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0416] device (enp1s0): link disconnected (calling deferred action)
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0419] device (enp1s0): state change: ip-config -> unavailable (reason 'carrier-changed') [70 20 40]
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0741] dhcp4 (enp1s0): canceled DHCP transaction, DHCP client pid 6511
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0741] dhcp4 (enp1s0): state changed unknown -> done
Dec 12 19:12:04 wotan avahi-daemon[1450]: Withdrawing address record for fe80::a462:a773:1523:5d4d on enp1s0.
Dec 12 19:12:04 wotan avahi-daemon[1450]: Leaving mDNS multicast group on interface enp1s0.IPv6 with address fe80::a462:a773:1523:5d4d.
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0749] manager: NetworkManager state is now DISCONNECTED
Dec 12 19:12:04 wotan avahi-daemon[1450]: Interface enp1s0.IPv6 no longer relevant for mDNS.
Dec 12 19:12:08 wotan NetworkManager[1485]: <info>  [1481566328.0727] device (enp1s0): link connected
```

It turned out my windows installation had the same issue. When I disconnected my switch and connected to my modem directly, the connection was restored. I then tried different ports on the switch and found a combination that works. Apparently one or more ports on the switch are broken.

(I also posted this as an answer to a [similar question]("https://ubuntuforums.org/showthread.php?t=2346164&p=13581821#post13581821"))

---

