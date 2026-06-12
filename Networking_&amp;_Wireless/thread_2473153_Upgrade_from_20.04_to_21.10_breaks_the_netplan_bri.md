---
title: "Upgrade from 20.04 to 21.10 breaks the netplan bridge"
date: 2022-03-25
forum: Networking &amp; Wireless
---

### Post by Eldon_McGuinness on 2022-03-25
To setup the background information, this is a remote bare metal server, originally running Ubuntu 20.04.4, through SoYouStart with DHCP being used on the NIC (enp3s0) and DHCP being used for a bridge (br0). The server houses a few virtual machines that pull public IP addresses from a pool that SoYouStart makes available (Fail Over IPs), and I've been using a netplan config that allowed enp3s0 to hold the main IP address, while br0 gave out IPs to the VMs based on MAC addresses. 

Now for the issue, I tried to update to 21.10, to take advantage and test some of the new libvirt features, and something does not seem to like the netplan setup that works just fine in 20.04. I thought, perhaps I did something odd to the 20.04 instance to make it work, so I spun up another server, fresh 20.04 install and put the netplan config in place and all worked as planned. I was able to migrate a copy of the VMs to this new server and they link right up via DHCP. When I try to use the netplan config below with 21.10, it does not give me an error, however, while the `netplan try --timeout 10` runs the system is no longer available. If I comment out the bridge section of the netplan file it works just fine on the main NIC, but obviously that is not my end goal here.

Any thoughts or insight on where to look as to why this is such a bugger?

```

network:
    version: 2
    ethernets:
        enp3s0:
            dhcp4: yes
            nameservers:
                addresses: [8.8.8.8, 8.8.4.4, 1.1.1.1, 1.0.0.1]
            match:
                macaddress: 60:a4:4c:40:cd:16
            set-name: enp3s0
    bridges:
        br0:
            dhcp4: yes
            interfaces: [enp3s0]

```

[SIZE=4][B]Resolution
[/B][/SIZE]For anyone that might happen across this post with a similar issue, here is what I did instead to fix it as I was not able to get DHCP on both to behave. In the case below x.x.x.254 is the default gateway for the host connection.

HOST
```

network:
  version: 2
  ethernets:
    enp3s0:
      match:
        macaddress: 60:a4:4c:40:cd:16

  bridges:
    br0:
      addresses:
        - x.x.x.x/24

      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4

      routes:
        - to: default
          via: x.x.x.254
          metric: 100

        - to: x.x.x.254
          via: 0.0.0.0
          metric: 100

      interfaces: [enp3s0]

```

GUEST
```
network:  ethernets:
    enp1s0:
      addresses:
        - y.y.y.y/24
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4


      routes:
        - on-link: true
          to: default
          via: x.x.x.254
          metric: 100


  version: 2
```

---

### Post by #&amp;thj^% on 2022-03-25
Very early in 21.10 there was a bug, I won't bother you with details.
I'm just going to get you started, I have a late shift tonight.
As a workaround you can execute the "netplan try" command as:
```

netplan try --state /etc/netplan
```
Good Luck

---

### Post by Eldon_McGuinness on 2022-03-25
Cheers for the reply @1fallen, someone on the Ubuntu IRC channel suggested that and I get the same exact result.

---

### Post by #&amp;thj^% on 2022-03-26
Have you looked at the debug yet?
```
sudo netplan --debug apply 
```
may help to see if anything stands out.

---

### Post by Eldon_McGuinness on 2022-03-29
Well, I'm no closer to figuring out why it does not work, however, I've taken DHCP out of the equation and got it working. I was being lazy and letting the infrastructure assign all the addresses, I know I know, going Static works just fine.

In case anyone else has this issue, this is how I setup the manual config. Do note, in my case I have a single static IP (x.x.x.x/24) and a block of 8 other static IPs (y.y.y.y/29). That being said the gateway sits at x.x.x.254 routes traffic from both ranges.

```

network:
  version: 2
  ethernets:
    enp3s0:
      match:
        macaddress: 60:a4:4c:40:cd:16

  bridges:
    br0:
      addresses:
        - x.x.x.x/24
        - y.y.y.y/29

      nameservers:
        addresses: [ 8.8.8.8, 8.8.4.4 ]

      routes:
        - to: default
          via: x.x.x.254
          metric: 100

      interfaces: [enp3s0]

```

---

### Post by #&amp;thj^% on 2022-03-29
So is it now working?
I've been busy so I lost track of you.
I always set my DHCP like: < skip DHCP by setting** ip=none** in /etc/default/grub:GRUB_CMD_LINUX>
EDIT:
Something like my setup has lasted throughout ALL upgrades
```

network:
  version: 2
  renderer: networkd
  ethernets:
     enp3s0:
      addresses: []
     enp3s0:
      addresses: []
  bridges:
    br0:
      addresses:
        - xx.x.1.100/24
      gateway4: xx.x.x.254
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
        search: []
      interfaces:
        - bond0
  bonds:
    bond0:
      interfaces:
        -  enp3s0
        -  enp3s0
      parameters:
        mode: balance-rr
```
followed with;        
```

sudo netplan generate

sudo netplan apply
```

---

### Post by Eldon_McGuinness on 2022-03-29
Yeah, I was able to get the system working the way I wanted by not using DHCP and instead manually assigning things to the interface and the bridge.

Question in your setup, why is enp3s0 listed twice under ethernets and bonds?

---

### Post by #&amp;thj^% on 2022-03-29
> **Eldon_McGuinness said:**
> Yeah, I was able to get the system working the way I wanted by not using DHCP and instead manually assigning things to the interface and the bridge.

Question in your setup, why is enp3s0 listed twice under ethernets and bonds?

Bogus name sake for this reply>>>that one is kind of a special set-up.(NDA)

---

### Post by Eldon_McGuinness on 2022-03-29
Here I was, hoping you were going to tell me it is a way to double your bandwidth. :mrgreen:

---

