---
title: "ubuntu 15.10 and wifi Ath9x issue"
date: 2016-01-23
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2016-01-23
Hi,

i update my distribution and since this day:
1. my wifi adapter does not receive any IP automatically from my router
2. i must each time set the IP manually and the default gateway in command line

i did several checks and discovered that module ath9x is not found: ath9k: Driver unloaded
My laptop has a "Qualcomm Atheros AR9285 Wireless Network Adapter" 

i do not know why driver is unloaded during boot process.

here is the result of lspci -vvnn
```
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
        Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f5600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
```

Any idea why is it like that ? i mean why wifi does not start at boot time and get then an IP address ?

thx

---

### Post by alain.roger on 2016-01-28
nobody has an idea where i can find the new driver for ath92x wifi adapter ?

---

### Post by chili555 on 2016-01-28
Why is it that everyone always assumes that the answer to everything is a new driver?

Chili: "Uh oh, the car is out of gas."
Mrs. Chili: "Here, let me drive."

I recommend that you pursue some diagnostics first. Is the driver ath9k loaded on boot, before you do anything else?```
lsmod | grep ath
```By the way, there is no driver ath9x in Linux, as far as I know.

If the driver *is* loaded, are there any clues in the log?```
dmesg | grep ath
```After a fresh reboot, and it doesn't connect, what is Network Manager doing?```
cat /var/log/syslog | grep -i network | tail -n20
```What commands, exactly, do you have to issue at the terminal?

Are there conflicting settings here?```
cat /etc/network/interfaces
```

---

### Post by alain.roger on 2016-01-28
in order to explain you why i was thinking to install a new driver version, it's because i upgrade my linux kernel to v4.4 as this version (according to what i read) includes improvements for laptops and fan/noise management.

So i was thinking to use the driver ath9k from linux kernel 4.4

here are the results of: lsmod | grep ath

> ath9k                  94208  0
ath9k_common           36864  1 ath9k
ath9k_hw              450560  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              638976  1 ath9k
cfg80211              544768  4 ath,ath9k_common,ath9k,mac80211
compat                 16384  4 cfg80211,ath9k_common,ath9k,mac80211

here are the results of: dmesg | grep ath

> [   11.168678] ath: phy0: Enable LNA combining
[   11.171225] ath: phy0: ASPM enabled: 0x42
[   11.171228] ath: EEPROM regdomain: 0x60
[   11.171229] ath: EEPROM indicates we should expect a direct regpair map
[   11.171230] ath: Country alpha2 being used: 00
[   11.171231] ath: Regpair used: 0x60
[   11.929616] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0

what i dislike it's that wlan0 is rename in kubuntu 15 to wlp3s0 but it should not be a problem as it is only a naming convention.

after a fresh reboot, cat /var/log/syslog | grep -i network | tail -n20 contains:

> Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  Config: set interface ap_scan to 1
Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  (wlp3s0): supplicant interface state: inactive -> authenticating
Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  (wlp3s0): supplicant interface state: associating -> 4-way handshake
Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ICUROG'.
Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  (wlp3s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 28 20:46:21 ntb0001 NetworkManager[893]: <info>  Activation (wlp3s0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 28 20:46:22 ntb0001 NetworkManager[893]: <info>  dhclient started with pid 1066
Jan 28 20:46:25 ntb0001 NetworkManager[893]: <info>  (wlp3s0): DHCPv4 state changed unknown -> expire
Jan 28 20:46:25 ntb0001 NetworkManager[893]: <info>  (wlp3s0): DHCPv4 state changed expire -> unknown
Jan 28 20:46:29 ntb0001 NetworkManager[893]: <info>  WiFi hardware radio set enabled
Jan 28 20:46:29 ntb0001 NetworkManager[893]: <info>  WWAN hardware radio set enabled
Jan 28 20:46:50 ntb0001 systemd[1]: NetworkManager-wait-online.service: Main process exited, code=exited, status=1/FAILURE
Jan 28 20:46:50 ntb0001 systemd[1]: Failed to start Network Manager Wait Online.
Jan 28 20:46:50 ntb0001 systemd[1]: NetworkManager-wait-online.service: Unit entered failed state.
Jan 28 20:46:50 ntb0001 systemd[1]: NetworkManager-wait-online.service: Failed with result 'exit-code'.
Jan 28 20:46:50 ntb0001 systemd[1]: Reached target Network is Online.
Jan 28 20:46:50 ntb0001 mount[1081]: mount error(101): Network is unreachable
Jan 28 20:48:10 ntb0001 pulseaudio[1500]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
what i do not understand here, it's that NetworkManager has failed :(

here are the results for: cat /etc/network/interfaces
> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

nothing about starting wlp3s0 or wlan0 :(
to start wifi manually i have to do:
> sudo ifconfig wlp3s0 192.168.1.20/24 && sudo route add default gw 192.168.1.1

and in this case wifi works...slower as normal but i can connect to my network.
however the animated icon in KDE is like computer is still looking after wifi network.

---

### Post by alain.roger on 2016-01-28
I did additional tests and i discovered that if my wifi adapter in networkmanager is set to DHCP IPv4 and method set to "Automatic" in this case for an unknown reason my laptop does not get any IP address from my router.
Whereas before kubuntu upgrade from v15.04 to 15.10, everything was set to "automatic" and was working fine.

Now i must manually set in Network Manager IP adress, DNS, Gateway, route etc... to make it works has before.

Therefore it seems something changed in ubuntu 15.10 against v15.04.

Any idea ?

thx

---

### Post by chili555 on 2016-01-28
> i was thinking to install a new driver version, it's because i upgrade my linux kernel to v4.4 as this version (according to what i read) includes improvements for laptops and fan/noise management.Are you saying that you already changed to kernel version 4.4? Or that you are thinking of updating to kernel version 4.4? If you have already upgraded to kernel version 4.4, then you already have the ath9k driver from 4.4. It is a part of the kernel package and is not installed separately. In any case, it is quite clear to me that the driver is not the issue. In my opinion, it is Network Manager:> systemd[1]: NetworkManager-wait-online.service: Main process exited, code=exited, status=1/FAILUREI have read this bug report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1430280](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1430280) It says that the bug was fixed in the package network-manager - 0.9.10.0-4ubuntu10.

Which do you have?```
sudo dpkg -s network-manager
```In my fresh 15.10 install that was updated, I have:```
Package: network-manager
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 4836
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: [COLOR="#FF0000"]1.0.4-0ubuntu5.2[/COLOR]

```If you have any version earlier, then I'd do:```
sudo apt-get update
sudo apt-get install --reinstall network-manager
sudo apt-get install --reinstall console-setup
```Reboot and let us see again:```
cat /var/log/syslog | grep -i network | tail -n20
```

---

### Post by alain.roger on 2016-01-29
I already upgraded kernel to 4.4 and i must confess laptop is very quiet and performing very well... better than with v4.2.0.25...i mean it is very silent now.

---

### Post by alain.roger on 2016-01-29
result of : sudo dpkg -s network-manager
> Package: network-manager
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 4836
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.0.4-0ubuntu5.2
Depends: libbluetooth3 (>= 4.91), libc6 (>= 2.17), libdbus-1-3 (>= 1.9.14), libdbus-glib-1-2 (>= 0.102), libgcrypt20 (>= 1.6.0), libglib2.0-0 (>= 2.37.3), libgnutls-deb0-28 (>= 3.3.0), libgudev-1.0-0 (>= 165), libmm-glib0 (>= 1.0.0), libndp0 (>= 1.2), libnewt0.52, libnl-3-200 (>= 3.2.21), libnl-genl-3-200 (>= 3.2.21), libnl-route-3-200 (>= 3.2.26), libnm0 (>= 1.0.4-0ubuntu5.2), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.104), libreadline6 (>= 6.0), libsoup2.4-1 (>= 2.39.3), libsystemd0, libuuid1 (>= 2.16), init-system-helpers (>= 1.18~), lsb-base (>= 4.1+Debian11ubuntu7), dnsmasq-base, wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, adduser, isc-dhcp-client (>= 4.3.1-5ubuntu1), libpam-systemd, policykit-1
Recommends: ppp (>= 2.4.6), iptables, modemmanager, crda, iputils-arping, network-manager-pptp, network-manager-gnome | plasma-widget-networkmanagement | plasma-nm
Suggests: avahi-autoipd, python
Breaks: network-manager-gnome (<< 0.9), network-manager-kde (<< 1:0.9), network-manager-openconnect (<< 0.9), network-manager-openvpn (<< 0.9), network-manager-pptp (<< 0.9), network-manager-vpnc (<< 0.9), plasma-widget-networkmanagement (<< 0.9~), ppp (<< 2.4.6)
Conflicts: connman
Conffiles:
 /etc/NetworkManager/NetworkManager.conf 6e21dde76719887007828a1757643976
 /etc/NetworkManager/dispatcher.d/01ifupdown 299819a8e64f00a1edbdfc99d05a8594
 /etc/dbus-1/system.d/nm-avahi-autoipd.conf 91ab68968b0dc06c3a55b482b50b3028
 /etc/dbus-1/system.d/nm-dispatcher.conf 5711a76c31a3763750fe2c331741f679
 /etc/dbus-1/system.d/org.freedesktop.NetworkManager.conf a6470200f81d1e5d9ca9abef3edc323e
 /etc/dnsmasq.d/network-manager c1f294c4513fa544565d671dcba6a913
 /etc/init.d/network-manager 59b97edb8cc5f8db9882118fbf102a88
 /etc/init/network-manager.conf 080b2a860317698f65f960687f5363cc
Description: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
Homepage: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>



AFAIK it's the same version as your. v1.0.4-0ubuntu5.2

---

### Post by alain.roger on 2016-01-29
result of 
cat /var/log/syslog | grep -i network | tail -n20 > 
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ICUROG'.
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  (wlp3s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  (wlp3s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  (wlp3s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  (wlp3s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  NetworkManager state is now CONNECTED_LOCAL
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  Policy set 'ICUROG' (wlp3s0) as default for IPv4 routing and DNS.
Jan 29 11:26:47 ntb0001 NetworkManager[864]: <info>  (wlp3s0): Activation: successful, device activated.
Jan 29 11:26:47 ntb0001 whoopsie[856]: [11:26:47] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Jan 29 11:26:47 ntb0001 whoopsie[856]: [11:26:47] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Jan 29 11:26:47 ntb0001 whoopsie[856]: [11:26:47] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Jan 29 11:26:47 ntb0001 systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan 29 11:26:47 ntb0001 systemd[1]: Started Network Manager Script Dispatcher Service.
Jan 29 11:26:49 ntb0001 NetworkManager[864]: <info>  startup complete
Jan 29 11:26:49 ntb0001 systemd[1]: Started Network Manager Wait Online.
Jan 29 11:26:49 ntb0001 systemd[1]: Reached target Network is Online.
Jan 29 11:26:52 ntb0001 NetworkManager[864]: <info>  WiFi hardware radio set enabled
Jan 29 11:26:52 ntb0001 NetworkManager[864]: <info>  WWAN hardware radio set enabled



---

### Post by chili555 on 2016-01-29
Your latest syslog looks like it connected perfectly. No? Yes??

I think I'd probably do the reinstall steps anyway:```
sudo apt-get update
sudo apt-get install --reinstall network-manager
sudo apt-get install --reinstall console-setup
```Reboot and tell us if there is any improvement. If not, once again:```
cat /var/log/syslog | grep -i network | tail -n20
```

---

