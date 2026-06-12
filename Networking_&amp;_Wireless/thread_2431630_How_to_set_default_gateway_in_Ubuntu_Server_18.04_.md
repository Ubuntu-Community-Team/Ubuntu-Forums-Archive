---
title: "How to set default gateway in Ubuntu Server 18.04 with netplan"
date: 2019-11-19
forum: Networking &amp; Wireless
---

### Post by akkor on 2019-11-19
[COLOR=#242729][FONT=Arial][FONT=inherit]I have a single network interface on this server named enp2s0 This interface had a static address 192.168.2.xxx with gateway 192.168.2.1 Now I changed the static address in yaml file to 192.168.1.xxx and the gateway too in 192.168.1.1 but every time I restart the server the default gateway comes back to 192.168.2.1 I tried to launch route commmand to remove default gateway and set the new one but if I restart the server it comes back to 192.168.2.1

[FONT=Consolas]This is the yaml config file
[/FONT]
[/FONT]```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
        enp2s0:
            addresses: [192.168.1.10/24]
            gateway4: 192.168.1.1
            nameservers:
[FONT=inherit][FONT=Consolas]           addresses: [1.1.1.1,1.0.0.1][/FONT][/FONT]
```[FONT=inherit]
[/FONT]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Output of networkctl status enp2s0 after reboot

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]2: enp2s0[/FONT][/COLOR]
       Link File: /lib/systemd/network/99-default.link
    Network File: /run/systemd/network/10-netplan-enp2s0.network
            Type: ether
           State: routable (configured)
            Path: pci-0000:02:00.0
          Driver: r8169
          Vendor: Realtek Semiconductor Co., Ltd.
           Model: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A
      HW Address: 48:5b:39:02:41:c9 (ASUSTek COMPUTER INC.)
         Address: 192.168.1.10
                  192.168.2.100
                  fe80::4a5b:39ff:fe02:41c9
         Gateway: 192.168.2.1
             DNS: 1.1.1.1 [COLOR=#242729][FONT=Consolas]  1.0.0.1[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Output of route command after reboot

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]Tabella di routing IP del kernel[/FONT][/COLOR]
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    202    0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp2s0 
[COLOR=#242729][FONT=Consolas]192.168.2.0   0.0.0.0      255.255.255.0  U   202   0     0 enp2s0[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Result of networkctl status enp2s0 after restored default gateway to 192.168.1.1

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]2: enp2s0[/FONT][/COLOR]
       Link File: /lib/systemd/network/99-default.link
    Network File: /run/systemd/network/10-netplan-enp2s0.network
            Type: ether
           State: routable (configured)
            Path: pci-0000:02:00.0
          Driver: r8169
          Vendor: Realtek Semiconductor Co., Ltd.
           Model: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A
      HW Address: 48:5b:39:02:41:c9 (ASUSTek COMPUTER INC.)
         Address: 192.168.1.10
                  fe80::4a5b:39ff:fe02:41c9
         Gateway: 192.168.1.1
             DNS: 1.1.1.1[COLOR=#242729][FONT=Consolas] 1.0.0.1[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Output of route command after restored default gateway to 192.168.1.1

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]Tabella di routing IP del kernel[/FONT][/COLOR]
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 enp2s0
[COLOR=#242729][FONT=Consolas]192.168.1.0     0.0.0.0  255.255.255.0  U   0    0     0 enp2s0[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

How to solve ?[/FONT][/COLOR]

---

### Post by TheFu on 2019-11-19
YAML cares very much about indentation.  Very much.  What you've posted has incorrect indentation.

```
network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []
```
I specifically disable IPv6 on my systems.  Also, after an installation, my network didn't work. I had to manually add a few lines to get things working.

---

### Post by akkor on 2019-11-19
> **TheFu said:**
> YAML cares very much about indentation.  Very much.  What you've posted has incorrect indentation.

```
network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []
```
I specifically disable IPv6 on my systems.  Also, after an installation, my network didn't work. I had to manually add a few lines to get things working.

I know about indentation....probably the formatted text has broken with copy/paste
The problem isn't the indentation of yaml file.......if I give command netplan apply the gateway config change to the right ip: 192.168.1.1......but if I restart it comes back to 192.168.2.1.....so I have to give netplan apply command again, but It's possible only if I'm with lan access otherwise from internet I cant connect to my server after a reboot

---

### Post by akkor on 2019-11-19
This is the output of netplan --debug apply

```
** (generate:4965): DEBUG: 16:17:35.743: Processing input file /etc/netplan/01-netcfg.yaml..** (generate:4965): DEBUG: 16:17:35.744: starting new processing pass
** (generate:4965): DEBUG: 16:17:35.744: Processing input file /etc/netplan/lo.yaml..
** (generate:4965): DEBUG: 16:17:35.744: starting new processing pass
** (generate:4965): DEBUG: 16:17:35.744: enp2s0: setting default backend to 1
** (generate:4965): DEBUG: 16:17:35.744: Configuration is valid
** (generate:4965): DEBUG: 16:17:35.744: lo: setting default backend to 1
** (generate:4965): DEBUG: 16:17:35.744: Configuration is valid
** (generate:4965): DEBUG: 16:17:35.744: Generating output files..
** (generate:4965): DEBUG: 16:17:35.744: NetworkManager: definition enp2s0 is not for us (backend 1)
** (generate:4965): DEBUG: 16:17:35.744: NetworkManager: definition lo is not for us (backend 1)
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:enp2s0 not found in {}
DEBUG:lo not found in {'enp2s0': {'addresses': ['192.168.1.10/24'], 'gateway4': '192.168.1.1', 'nameservers': {'addresses': ['1.1.1.1', '1.0.0.1']}}}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    enp2s0:
      addresses:
      - 192.168.1.10/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
        - 1.1.1.1
        - 1.0.0.1
    lo:
      addresses:
      - 127.0.0.1/8
  vlans: {}
  wifis: {}


DEBUG:device lo operstate is unknown, not changing
DEBUG:device enp2s0 operstate is up, not changing
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp2s0



```

---

### Post by TheFu on 2019-11-19
I can only go by what is posted here, right?  How can we know what is true when the post clearly shows a mistake?

More than one yaml file are in the config directory?  Could there be conflicts?

Is network-manager loaded on the machine? I'd purge that if it is there.  Don't want too many cooks in the kitchen.

---

### Post by akkor on 2019-11-19
> **TheFu said:**
> I can only go by what is posted here, right?  How can we know what is true when the post clearly shows a mistake?

More than one yaml file are in the config directory?  Could there be conflicts?

Is network-manager loaded on the machine? I'd purge that if it is there.  Don't want too many cooks in the kitchen.

I don't know what mistake are you talking about...........show me please
In the config directory I have only 01-netcfg.yaml and lo.yaml files
How to purge network-manager if is loaded on the machine ?
Thank You for help

---

