---
title: "Netplan - Assistance Required"
date: 2022-04-07
forum: Networking &amp; Wireless
---

### Post by hitenpankhania on 2022-04-07
Hi Hoping someone can assist here.
I am in the process of building an Ubuntu Server 20.04 which will be used for hosting KVM virtual machines.
The Server in question has 3 connected NICs.

1. ens5f0 Bonded for VM traffic 
2. ens5f1 Bonded for VM traffic 

For the Virtual, traffic we have bonded the above nics, created a bridge and vlan tagging 

and 

3. ens5f2 used for management.

Both nics 1 and 2 will be used for VM traffic and 3 (ensf52) will be used for management traffic, to connect to the hypervisor for administration aspects.

i am struggling to understand the routing aspect of netplan - have added my config of netplan file below - could anyone pass any guidance on the whole configuration please.
Also should the bond or bridge be tagged with VLAN? or just the bridge?

```
network:  version: 2
  renderer: NetworkManager
  ethernets:
    eno1:
      dhcp4: true
    eno2:
      dhcp4: true
    ens5f0:
      dhcp4: false 
      dhcp6: false
      # addresses:
      # - 192.168.90.20/24
      # gateway4: 192.168.90.1
      # nameservers:
      #   addresses:
      #   - 149.179.146.32
      #   - 149.179.146.48
      #   - 149.179.147.40
      #   search:
      #   - newco
    ens5f1:
      dhcp4: false 
      dhcp6: false
      # addresses:
      # - 192.168.90.21/24
      # gateway4: 192.168.90.1
      # nameservers:
      #   addresses:
      #   - 149.179.146.32
      #   - 149.179.146.48
      #   - 149.179.147.40
      #   search:
      #   - newco
    ens5f2:
      addresses:
      - 192.168.91.51/24
        #gateway4: 192.168.91.1
      nameservers:
        addresses:
        - 149.179.146.32
        - 149.179.146.48
        - 149.179.147.40
        search:
        - newco
      routes:
       - to: 0.0.0.0/0
         via: 192.168.91.1
         metric: 100
       - to: 192.168.90.0/24
         via: 192.168.90.1
         metric: 100
    ens5f3:
      dhcp4: true
    ens6f0:
      dhcp4: true
    ens6f1:
      dhcp4: true
    ens6f2:
      dhcp4: true
    ens6f3:
      dhcp4: true
  bonds:
    bond0:
      dhcp4: false
      interfaces: [ens5f0, ens5f1]
      # addresses: [192.168.90.20/24]
      # gateway4: 192.168.90.1
      # nameservers:
      #    addresses: [149.179.146.32,149.179.146.48,149.179.147.40]
      #    search: [newco]
      parameters:
        mode: 802.3ad
        lacp-rate: fast
        primary: ens5f0
        mii-monitor-interval: 100
  vlans:
    bond0.90:
      id: 90
      link: bond0
    # ens5f0.90:
    #   id: 90
    #   link: ens5f0
    # ens5f1.90:
    #   id: 90
    #   link: ens5f1
    ens5f2.91:
      id: 91
      link: ens5f2
  bridges:
    br0:
        addresses: [192.168.90.20/24]
        dhcp4: false
        gateway4: 192.168.90.1
        interfaces: [bond0.90]
        parameters:
            stp: false
        nameservers:
            addresses: [149.189.146.32,149.189.146.48,149.189.147.40]
            search: [newco]
        routes:
         - to: 0.0.0.0/0
           via: 192.168.91.1
           metric: 100
         - to: 192.168.90.0/24
           via: 192.168.90.1
           metric: 100



```



Thanks in advance.

---

### Post by The Cog on 2022-04-07
Please can you re-post that, using the Go Advanced button. The "advanced" editor has a # button that puts the highlighted text into a code block, which preserves indentation. Indentation is critical in a yaml file. In your post above, there are many syntax errors purely because of missing indentation.

---

### Post by hitenpankhania on 2022-04-07
Thanks for the guidance, my first ever post @The Cog

---

### Post by The Cog on 2022-04-08
Oh my, that's a big one! You've got several things in there that I didn't know were even possible. Still, I'll comment on what I do know:

You have 7 interfaces running DHCP. It could be that each one of those is giving you a default route. the command "ip route" will tell you a lot, but I'm not sure multiple default routes are good. On something like this, I would prefer to avoid DHCP and manually set all IP addresses. You also have two manually configured default routes, both are metric 100, so depending on what the DHCP ones do, it is likely to load-share outgoing connections.

I haven't done bonding, but your config "feels" right to me. Applying the IP config to the bond instead of the interfaces makes sense. I don't see any obvious problems.

I'm even less sure about bridging, I'm struggling even to understand the intention there, so I'll leave that to other folk to comment and hope I might learn something. Bridging content is indented differently - not a problem, but it looks odd.

---

### Post by kevdog on 2022-04-10
I think you apply the vlan tags to the bridges -- not the bonds.

---

