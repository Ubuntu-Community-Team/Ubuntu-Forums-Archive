---
title: "Ubuntu Bionic Server edition + Netplan: Not getting static IP on a wired connection"
date: 2019-04-11
forum: Networking &amp; Wireless
---

### Post by mrjayviper on 2019-04-11
_Problem:_ I cannot get a static IP on the ethernet port.

_Aim:_ Trying to setup a static IP on the Realtek built-in ethernet (enp3s0) port so I can connect the server to my desktop via a crossover cable. At the moment, there is no cable connected between the 2.

_Setup:_ Ubuntu Bionic server edition with Intel WiFi card and a Reaktek ethernet port. During installation, I had to connect the ethernet port to my modem/router as the Ubuntu installer cannot recognize my WiFi card. 
-------------------------------
_Things I've tried:_

1. I disabled my WiFi card  and then I've tried using just "dchp4: true" and then connected a cable from the port to my modem/router. No issues getting an IP and pinging a site.
2. I checked my the YAML file and no issues with spaces/tabs. to be sure I opened the file using nano -T2 which gives me 2 spaces for tabs.
3. I've tried with and without "renderer: networkd", no difference.
4. I've tried with and without "dhcp4" false", no difference.
5. I've tried with and without gateway4, no difference.
6. I've tried with and without nameservers, no difference.
7. sudo netplan --debug apply doesn't show any errors
8. I looked at the generated config inside /run/systemd/network (included below) and looks ok.
9. Debugged systemd-networkd as suggested by this page ([https://wiki.ubuntu.com/DebuggingSystemd](https://wiki.ubuntu.com/DebuggingSystemd)) and I can see this line: "enp3s0: Link is not managed by us". That doesn't seemed right as I don't have anything else managing my interfaces and as I said in no.1, using DHCP worked.
10. I checked /etc/network/interfaces and the folder is empty.
11. I checked and /etc/systemd/network is empty. I remember this location as I was playing around with ArchLinux recently.
12. I deleted yaml file in /etc/netplan. Create a new .network file inside /etc/systemd/network and used examples from this page ([https://www.freedesktop.org/software/systemd/man/systemd.network.html](https://www.freedesktop.org/software/systemd/man/systemd.network.html)).  I restarted restarted systemd-networkd but still no static IP.
13. As a last resort, I created a new Ubuntu Bionic Server virtualbox, configured the 2nd NIC to use the same YAML config as below and no issues getting a static IP.

-------------------
_Here's my current config:_

```

>cat /etc/netplan/01-wireless.yaml
network:
  version: 2
  renderer: networkd
  wifis:
    wlp2s0:
      dhcp4: true
      access-points:
        "insert-access-point-here":
          password: "insert-password-here"
```

```
>cat /etc/netplan/02-ethernet.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses: [192.168.2.1/24]
```

```
>cat /run/systemd/network/10-netplan-wlp2s0.network 
[Match]
Name=wlp2s0
    
[Network]
DHCP=ipv4
LinkLocalAddressing=ipv6
[DHCP]
UseMTU=true
RouteMetric=600
```
    
```
>cat /run/systemd/network/10-netplan-enp3s0.network 
[Match]
Name=enp3s0

[Network]
LinkLocalAddressing=ipv6
Address=192.168.2.1/24
```

--------------------------------
_Results of netplan --debug apply_

```
** (generate:17126): DEBUG: 14:01:32.066: Processing input file /etc/netplan/01-wireless.yaml..** (generate:17126): DEBUG: 14:01:32.067: starting new processing pass
** (generate:17126): DEBUG: 14:01:32.067: wlp2s0: adding wifi AP 'myhotspot'
** (generate:17126): DEBUG: 14:01:32.067: Processing input file /etc/netplan/ethernet.yaml..
** (generate:17126): DEBUG: 14:01:32.067: starting new processing pass
** (generate:17126): DEBUG: 14:01:32.067: wlp2s0: setting default backend to 1
** (generate:17126): DEBUG: 14:01:32.067: enp3s0: setting default backend to 1
** (generate:17126): DEBUG: 14:01:32.067: Generating output files..
** (generate:17126): DEBUG: 14:01:32.068: wlp2s0: Creating wpa_supplicant configuration file run/netplan/wpa-wlp2s0.conf
** (generate:17126): DEBUG: 14:01:32.068: Creating wpa_supplicant service enablement link /run/systemd/system/multi-user.target.wants/netplan-wpa@wlp2s0.service
** (generate:17126): DEBUG: 14:01:32.069: NetworkManager: definition wlp2s0 is not for us (backend 1)
** (generate:17126): DEBUG: 14:01:32.069: NetworkManager: definition enp3s0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:wlp2s0 not found in {}
DEBUG:enp3s0 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    enp3s0:
      addresses:
      - 192.168.2.1/24
  vlans: {}
  wifis:
    wlp2s0:
      access-points:
        insert-access-point-here:
          password: insert-password-here
      dhcp4: true


DEBUG:Skipping non-physical interface: lo
DEBUG:device wlp2s0 operstate is up, not changing
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp3s0
DEBUG:netplan triggering .link rules for wlp2s0
```

--------------------------------
_Results of systemd networkd debugging:_

```
>sudo SYSTEMD_LOG_LEVEL=debug /lib/systemd/systemd-networkd
    
    Failed to read $container of PID 1, ignoring: Permission denied
    Found container virtualization none.
    Bus n/a: changing state UNSET &#8594; OPENING
    Bus n/a: changing state OPENING &#8594; AUTHENTICATING
    Failed to open configuration file '/etc/systemd/networkd.conf': No such file or directory
    timestamp of '/etc/systemd/network' changed
    timestamp of '/run/systemd/network' changed
    Ignoring /run/systemd/network/10-netplan-enp3s0.network, because it's not a regular file with suffix .netdev.
    Ignoring /run/systemd/network/10-netplan-wlp2s0.network, because it's not a regular file with suffix .netdev.
    Ignoring /lib/systemd/network/99-default.link, because it's not a regular file with suffix .netdev.
    Ignoring /lib/systemd/network/80-container-ve.network, because it's not a regular file with suffix .netdev.
    Ignoring /lib/systemd/network/80-container-vz.network, because it's not a regular file with suffix .netdev.
    Ignoring /lib/systemd/network/80-container-host0.network, because it's not a regular file with suffix .netdev.
    Ignoring /lib/systemd/network/99-default.link, because it's not a regular file with suffix .network.
    wlp2s0: Flags change: +UP +LOWER_UP +RUNNING +MULTICAST +BROADCAST
    wlp2s0: Link 3 added
    wlp2s0: udev initialized link
    wlp2s0: Saved original MTU: 1500
    enp3s0: Flags change: +UP +MULTICAST +BROADCAST
    enp3s0: Link 2 added
    enp3s0: udev initialized link
    enp3s0: Saved original MTU: 1500
    lo: Flags change: +LOOPBACK +UP +LOWER_UP +RUNNING
    lo: Link 1 added
    lo: udev initialized link
    lo: Saved original MTU: 0
    wlp2s0: Adding address: fe80::3613:e8ff:fe41:a078/64 (valid forever)
    wlp2s0: Gained IPv6LL
    lo: Adding address: ::1/128 (valid forever)
    wlp2s0: Adding address: 192.168.1.2/24 (valid forever)
    lo: Adding address: 127.0.0.1/8 (valid forever)
    rtnl: received address with invalid family 129, ignoring
    Enumeration completed
    Bus n/a: changing state AUTHENTICATING &#8594; HELLO
    Sent message type=method_call sender=n/a destination=org.freedesktop.DBus path=/org/freedesktop/DBus interface=org.freedesktop.DBus member=Hello cookie=1 reply_cookie=0 signature=n/a error-name=n/a error-message=n/a
    Sent message type=method_call sender=n/a destination=org.freedesktop.DBus path=/org/freedesktop/DBus interface=org.freedesktop.DBus member=RequestName cookie=2 reply_cookie=0 signature=su error-name=n/a error-message=n/a
    Sent message type=method_call sender=n/a destination=org.freedesktop.DBus path=/org/freedesktop/DBus interface=org.freedesktop.DBus member=AddMatch cookie=3 reply_cookie=0 signature=s error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=4 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_32 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=5 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_31 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=6 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=7 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=8 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=9 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    wlp2s0: Link state is up-to-date
    wlp2s0: found matching network '/run/systemd/network/10-netplan-wlp2s0.network'
    enp3s0: Link is not managed by us
    lo: Link is not managed by us
    LLDP: Started LLDP client
    wlp2s0: Started LLDP.
    wlp2s0: Acquiring DHCPv4 lease
    DHCP CLIENT (0x8f3ad0c0): STARTED on ifindex 3
    wlp2s0: Discovering IPv6 routers
    NDISC: Started IPv6 Router Solicitation client
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=10 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=11 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=12 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    NDISC: Sent Router Solicitation, next solicitation in 3s
    Got message type=method_return sender=org.freedesktop.DBus destination=:1.12 path=n/a interface=n/a member=n/a cookie=1 reply_cookie=1 signature=s error-name=n/a error-message=n/a
    Bus n/a: changing state HELLO &#8594; RUNNING
    DHCP CLIENT (0x8f3ad0c0): DISCOVER
    Got message type=signal sender=org.freedesktop.DBus.Local destination=n/a path=/org/freedesktop/DBus/Local interface=org.freedesktop.DBus.Local member=Connected cookie=4294967295 reply_cookie=0 signature=n/a error-name=n/a error-message=n/a
    Got message type=signal sender=org.freedesktop.DBus destination=:1.12 path=/org/freedesktop/DBus interface=org.freedesktop.DBus member=NameAcquired cookie=2 reply_cookie=0 signature=s error-name=n/a error-message=n/a
    Got message type=signal sender=org.freedesktop.DBus destination=:1.12 path=/org/freedesktop/DBus interface=org.freedesktop.DBus member=NameAcquired cookie=3 reply_cookie=0 signature=s error-name=n/a error-message=n/a
    Got message type=method_return sender=org.freedesktop.DBus destination=:1.12 path=n/a interface=n/a member=n/a cookie=4 reply_cookie=2 signature=u error-name=n/a error-message=n/a
    Successfully acquired requested service name.
    Got message type=method_return sender=org.freedesktop.DBus destination=:1.12 path=n/a interface=n/a member=n/a cookie=5 reply_cookie=3 signature=n/a error-name=n/a error-message=n/a
    Match type='signal',sender='org.freedesktop.login1',path='/org/freedesktop/login1',interface='org.freedesktop.login1.Manager',member='PrepareForSleep' successfully installed.
    enp3s0: Link state is up-to-date
    enp3s0: found matching network '/run/systemd/network/10-netplan-enp3s0.network'
    lo: Link is not managed by us
    wlp2s0: Link does not request DHCPv6 prefix delegation
    LLDP: Started LLDP client
    enp3s0: Started LLDP.
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_32 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=13 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    lo: Link state is up-to-date
    No virtualization found in DMI
    No virtualization found in CPUID
    Virtualization XEN not found, /proc/xen does not exist
    This platform does not support /proc/device-tree
    No virtualization found in /proc/cpuinfo.
    This platform does not support /proc/sysinfo
    Found VM virtualization none
    lo: Unmanaged
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_31 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=14 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    wlp2s0: Removing address: 192.168.1.2/24 (valid forever)
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=15 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=16 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    DHCP CLIENT (0x8f3ad0c0): OFFER
    DHCP CLIENT (0x8f3ad0c0): REQUEST (requesting)
    DHCP CLIENT (0x8f3ad0c0): ACK
    wlp2s0: DHCPv4 address 192.168.1.2/24 via 192.168.1.1
    wlp2s0: Updating address: 192.168.1.2/24 (valid forever)
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=17 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=18 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    wlp2s0: DHCP error: could not get routes: No data available
    wlp2s0: Configured
    Sent message type=signal sender=n/a destination=n/a path=/org/freedesktop/network1/link/_33 interface=org.freedesktop.DBus.Properties member=PropertiesChanged cookie=19 reply_cookie=0 signature=sa{sv}as error-name=n/a error-message=n/a
    NDISC: Sent Router Solicitation, next solicitation in 7s
    NDISC: Sent Router Solicitation, next solicitation in 14s
    NDISC: No RA received before link confirmation timeout
    NDISC: Invoking callback for 't'.
```

---

