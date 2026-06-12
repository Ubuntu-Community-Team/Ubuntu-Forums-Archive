---
title: "Ethernet Setting Messed up during OpenVPN installation"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by 1991sudarshan on 2014-10-12
I am not able to connect to internet through wired ethernet. I guess, it got messed up durning the openvpn installation and configuration. I removed openvpn and reverted the settings, still ethernet connection is not working. I am able to connect to internet only through Wi-Fi.

Here are the results of few commands which I ran to figure out what's wrong with the ethernet connection but I couldn't find out what is the issue.
```

sudarshan@sudarshan-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:1f:90:cf  
          inet6 addr: fe80::ea9a:8fff:fe1f:90cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137707 (137.7 KB)  TX bytes:151073 (151.0 KB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88195 (88.1 KB)  TX bytes:88195 (88.1 KB)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:98:ea:f9  
          inet addr:192.168.10.104  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe98:eaf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3694145 (3.6 MB)  TX bytes:764805 (764.8 KB)

sudarshan@sudarshan-laptop:~$ 
```


```
sudarshan@sudarshan-laptop:~$ ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000033 (51)
                   **drv probe ifdown ifup**
Cannot get link status: Operation not permitted
sudarshan@sudarshan-laptop:~$
```

```
sudarshan@sudarshan-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: e8:9a:8f:1f:90:cf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:50004000-50004fff memory:50000000-50003fff
```

```
sudarshan@sudarshan-laptop:~$ cat /etc/network/interfaces 
auto eth0
interface eth0 inet 


sudarshan@sudarshan-laptop:~$ 


```

---

### Post by Hadaka on 2014-10-12
hi, your /etc/network/interfaces currently reads..
```
auto eth0
interface eth0 inet
```
Default setting is..
```
auto lo
iface lo inet loopback
```
please do ,,
```
sudo gedit /etc/network/interfaces
```
and make it look like this..
```
#auto eth0
#interface eth0 inet
auto lo
iface lo inet loopback
```
close and save gedit

---

### Post by 1991sudarshan on 2014-10-12
> **Hadaka said:**
> hi, your /etc/network/interfaces currently reads..
```
auto eth0
interface eth0 inet
```
Default setting is..
```
auto lo
iface lo inet loopback
```
please do ,,
```
sudo gedit /etc/network/interfaces
```
and make it look like this..
```
#auto eth0
#interface eth0 inet
auto lo
iface lo inet loopback
```
close and save gedit

I did as you told, still the issues persists. 
Look at this 

/etc/network/interfaces/if-up.d/upstart

I commented out the get_auto_interfaces() part. The nw-applet shows the aut eth0 is connected by no internet connectivity. 

```
#!/bin/sh
# MARK_DEV_PREFIX="/run/network/ifup."
# MARK_STATIC_NETWORK_EMITTED="/run/network/static-network-up-emitted"

set -e

# lo emission handled by /etc/init/network-interface.conf
 if [ "$IFACE" != lo ]; then
#if [ "$IFACE"  = lo ]; then
#        exit 0
   initctl emit -n net-device-up \
        "IFACE=$IFACE" \
        "LOGICAL=$LOGICAL" \
        "ADDRFAM=$ADDRFAM" \
        "METHOD=$METHOD"
fi

#initctl emit -n net-device-up \
#        "IFACE=$IFACE" \
#        "LOGICAL=$LOGICAL" \
#        "ADDRFAM=$ADDRFAM" \
#        "METHOD=$METHOD"
# get_auto_interfaces() {
    # write to stdout a list of interfaces configured as 'auto' in interfaces(5)
#     local found=""
    # stderr redirected as it outputs things like:
    # Ignoring unknown interface eth0=eth0.
#    found=$(ifquery --list --allow auto 2>/dev/null) || return
#    set -- ${found}
#    echo "$@"
#}

#all_interfaces_up() {
    # return true if all interfaces listed in /etc/network/interfaces as 'auto'
    # are up.  if no interfaces are found there, then "all [given] were up"
#    local prefix="$1" iface=""
#    for iface in $(get_auto_interfaces); do
        # if cur interface does is not up, then all have not been brought up
#        [ -f "${prefix}${iface}" ] || return 1
#    done
#    return 0
#}

# touch our own "marker" indicating that this interface has been brought up.
#: > "${MARK_DEV_PREFIX}$IFACE"

#if all_interfaces_up "${MARK_DEV_PREFIX}" &&
#    mkdir "${MARK_STATIC_NETWORK_EMITTED}" 2>/dev/null; then
#    initctl emit --no-wait static-network-up
#fi
```

---

### Post by SeijiSensei on 2014-10-12
Your wired connection is not configured to have an IP address.  Contrast the "eth0" and "wlan0" lines in the ifconfig results above.  In /etc/network/interfaces, add
```

auto eth0
iface eth0 inet dhcp

```
and it will get an address from your router.  I suggest turning off the wifi while using the Ethernet connection to avoid confusion about routing.

---

