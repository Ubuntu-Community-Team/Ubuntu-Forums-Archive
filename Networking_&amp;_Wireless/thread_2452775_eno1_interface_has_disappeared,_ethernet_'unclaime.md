---
title: "eno1 interface has disappeared, ethernet 'unclaimed'"
date: 2020-10-28
forum: Networking &amp; Wireless
---

### Post by jthistl3 on 2020-10-28
I'm using Ubuntu 20.04.1 LTS which uses NetworkManager to manage internet connections.

For a while, everything was fine with my computer - ethernet worked as plug & play - but recently I created a new, separate account on it, and, since I was leaving for a while, set up ssh access to it. This involved setting a static ip using netplan. My netplan configuration (at `/etc/netplan/01-network-manager-all.yaml`) looks like this, then:

```

network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eno1:
      dhcp4: no
      addresses:
        - 192.168.0.69/24
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]

```

I'm aware this may be a possible cause of the problem I'm having, but I'm not certain.

Anyway, after a couple of days, I stopped being able to ssh into my computer. This was because, for whatever reason, Ubuntu had decided that the ethernet interface `eno1` had disappeared. After getting someone to change port forwarding rules so I could ssh via WiFi, I found that `ifconfig` gives:

```

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 178597  bytes 15686085 (15.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 178597  bytes 15686085 (15.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx200db0187d26: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.15  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::536:3e32:5a6f:df0a  prefixlen 64  scopeid 0x20<link>
        ether 20:0d:b0:18:7d:26  txqueuelen 1000  (Ethernet)
        RX packets 358159  bytes 114355653 (114.3 MB)
        RX errors 0  dropped 17  overruns 0  frame 0
        TX packets 609759  bytes 486071543 (486.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


What's interesting about this is that there is a mention of `Ethernet`, but I don't know what this means in this context - does it mean that the wireless adapter is acting as an ethernet adapter and I am in fact accessing my computer via ethernet? Or does it mean something else entirely?

Obviously my adapter can't have just disappeared - as shown by the output of `lshw -C network`:

```

*-network UNCLAIMED       
       description: Ethernet controller
       product: 82579LM Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:f7100000-f711ffff memory:f7139000-f7139fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.1
       logical name: wlx200db0187d26
       serial: 20:0d:b0:18:7d:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=5.4.0-52-generic firmware=N/A ip=192.168.0.15 link=yes multicast=yes wireless=IEEE 802.11

```

I think the `UNCLAIMED` here might be a clue to solving this, but after searching through the internet and trying a billion different solutions, none of them seem to have fixed it. Advice would be very much appreciated, thank you.

---

### Post by chili555 on 2020-10-28
May we solve this on your already posted question on Ask Ubuntu?

---

### Post by jthistl3 on 2020-10-28
>May we solve this on your already posted question on Ask Ubuntu? 				
			  			   		

Indeed, I just posted here as a secondary resource  in case I didn't get an answer from AskUbuntu. For reference:  [https://askubuntu.com/questions/1287652/eno1-interface-has-disappeared-ethernet-unclaimed](https://askubuntu.com/questions/1287652/eno1-interface-has-disappeared-ethernet-unclaimed)

---

