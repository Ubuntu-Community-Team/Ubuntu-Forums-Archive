---
title: "Persistently set default gateway and routing configuration"
date: 2019-11-24
forum: Networking &amp; Wireless
---

### Post by lwtw on 2019-11-24
Hey,
I have set up a server with two network interfaces:

- enp0s25 is connected to my router and goes out to the WAN. The IP address of the gateway is 10.42.0.1. This is the interface I accept WAN connections on and I want ALL inbound and outbound network traffic to go to this interface by default (with one exception, please keep reading).

- enx001e101f0000 is a huawei hilink modem I use to send SMS for two factor authentication. I send SMS by POSTing HTTP data to the modems web interface using curl (so no AT commands), thus I need to be able to reach the modem via the network interface the driver provides. This connection is metered however, so I want only traffic addressed directly to this modem to be routed through this interface. The gateway IP is 192.168.8.1 (or the hostname hi.link).

I set up my interfaces using netplan as such:

```

# enp0s25, the connection I want to use for all traffic
# /etc/netplan/10-wan-ether.yaml

network:
    version: 2
    renderer: networkd
    ethernets:
        enp0s25:
            dhcp4: yes
            routes:
            - to: 0.0.0.0/0
              via: 10.42.0.1

```



```

# enx001e101f0000, the metered connection, only for sms
# /etc/netplan/20-huawei-modem.yaml

network:
    version: 2
    renderer: networkd
    ethernets:
        enx001e101f0000:
            dhcp4: yes
            routes:
            - to: 192.168.8.1
              via: 192.168.8.1

```

However, after a reboot, all traffic originating from my server (for example when I curl a webpage) still automatically goes through the huawei modem, and the output of the command 'route -n' looks like this:

```

Kernel IP Routing table
Destination   Gateway       Genmask            Flags   Metric   Ref   Use   Iface
0.0.0.0       192.168.8.1   0.0.0.0            UG      100      0     0     enx001e101f0000
0.0.0.0       10.42.0.1     0.0.0.0            UG      100      0     0     enp0s25
10.42.0.0     0.0.0.0       255.255.255.255    U       0        0     0     enp0s25
10.42.0.1     0.0.0.0       255.255.255.255    UH      100      0     0     enp0s25
192.168.8.0   0.0.0.0       255.255.255.0      U       0        0     0     enx001e101f0000
192.168.8.1   0.0.0.0       255.255.255.255    UH      100      0     0     enx001e101f0000

```

when I run "route delete default gw 192.168.8.1", everything works as intended. What can I do to make this configuration persistent? Why doesn't my routing configuration for netplan work?

Thank you for the help!

---

### Post by TheFu on 2019-11-24
Please always include the ubuntu release and ubuntu DE in questions.  The answers change based on those 2 items.

BTW, SMS really shouldn't be used for 2FA.  Cloned SIM cards is a real thing. U2F devices are really cheap ($15-20) and lots of services support those. Setting up U2F on Nextcloud was 2-3 steps, install the addon, enable it, register the U2F device. BAM! It works.

---

### Post by The Cog on 2019-11-24
I presume that you are using DHCP for both connections. 
I presume that DHCP in both cases is giving you a default route.

You could configure a lower metric (more preferred) for the static route on enp0s25 so it is preferred over the other static route. I found this reference: [https://netplan.io/examples](https://netplan.io/examples)
Try this:```

network:
    version: 2
    renderer: networkd
    ethernets:
        enp0s25:
            dhcp4: yes
            dhcp4-overrides:
                route-metric: 50

```
Or instead, raise the metric of the other interface to 200 perhaps.

---

