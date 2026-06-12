---
title: "using netplan to create a gateway"
date: 2020-07-31
forum: Networking &amp; Wireless
---

### Post by jordan399 on 2020-07-31
hi all,

I am trying to use netplan to setup a gateway.  Here are some details of what I have set up:
1) I'm running 20.04
2) I have 5 NICs (enp5s0, enp4s0f1, enp4s0f0, enp3s0f1, enp3s0f0)
3) The enp4* and enp3* NICs are on a single PCIx card
4) The gateway sits behind my ISP provided router (it is garbage but works most of the time).  The gateway is statically configured to 192.168.0.50 and it connects via enp5s0.  The ISP router is on 192.168.0.1
5) the 4 NICs on the card will service various other upstream laptops/tablets/phones/other switches/desktops and forward everything to my isp router.  There are ~20 devices upstream from the gateway.
6) The gateway has pihole installed on it.  Pihole is configured (via dnsmasq i believe) to provide IP4 addresses in 192.168.1.1/24
7) netplan is setup with the following (copied from screen because the machine has no internet connectivity.  there might be copy errors): ```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp5s0:
      dhcp4: no
      addresses: [192.168.0.50/24]
      gateway4: 192.168.0.1
    switchports:
      match:
        name: enp[3-4]*
  bridges:
    br0:
      interfaces: [enp5s0, switchports]
      addresses: [192.168.1.1/24]
      dhcp4: true

```
This configuration generates and applies without error.

8) I have setup iptables to NAT from enp5s0 and br0 (iptables -t nat -A POSTROUTING -o enp5s0 -j MASQUERADE)

However,  I am having mixed results:
1) I can connect to 192.168.1.1 pihole interface from the gateway
2) the clients behind the gateway are served IP addresses successfully
3) the clients behind the gateway can access the pihole interface

but:
4) I cant ping 8.8.8.8 from the gateway.  Which pretty much sums it up.  Connectivity from the gateway to the internet isnt working so upstream clients cant connect either

My route tables looks like this:
[table="width: 500"]
[tr]
	[td]Destination[/td]
	[td]Gateway[/td]
	[td]Genmask[/td]
	[td]Flags[/td]
	[td]MSS[/td]
	[td]Window[/td]
	[td]irtt[/td]
	[td]Iface[/td]
[/tr]
[tr]
	[td]0.0.0.0[/td]
	[td]192.168.0.1[/td]
	[td]0.0.0.0[/td]
	[td]UG[/td]
	[td]0[/td]
	[td]0[/td]
	[td]0[/td]
	[td]enp5s0[/td]
[/tr]
[tr]
	[td]192.168.0.0[/td]
	[td]0.0.0.0[/td]
	[td]255.255.255.0[/td]
	[td]U[/td]
	[td]0[/td]
	[td]0[/td]
	[td]0[/td]
	[td]enp5s0[/td]
[/tr]
[tr]
	[td]192.168.1.0[/td]
	[td]0.0.0.0[/td]
	[td]255.255.255.0[/td]
	[td]U[/td]
	[td]0[/td]
	[td]0[/td]
	[td]0[/td]
	[td]br0[/td]
[/tr]
[/table]


Any ideas on what I can try to make this work?

---

### Post by SeijiSensei on 2020-07-31
Look at /etc/sysctl.conf.  Do you have 

```
net.ipv4.ip_forward=1
```

commented out with a hash mark at the beginning of the line?  If so, remove the hash mark then run

```
sudo sysctl -p
```

to reload the configuration file.

Ubuntu, like most modern distributions, disables packet forwarding across interfaces by default as a security measure.

---

### Post by jordan399 on 2020-07-31
Sorry, I forgot to add that in my original post. My system is setup to ip forward

---

### Post by jordan399 on 2020-08-03
Ok,  I got this to work with the following yaml

```


network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp5s0:
      dhcp4: no
      addresses: [192.168.0.50/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.8.8]
      routes:
        - to: 0.0.0.0/0
          via: 192.168.0.1
    enp4s0f1:
      dhcp4: true
      routes:
        - to: 0.0.0.0/0
          via: 192.168.0.1
    enp4s0f0:
      dhcp4: true
      routes:
        - to: 0.0.0.0/0
          via: 192.168.0.1
    enp3s0f1:
      dhcp4: true
      routes:
        - to: 0.0.0.0/0
          via: 192.168.0.1
    enp3s0f0:
      dhcp4: true
      routes:
        - to: 0.0.0.0/0
          via: 192.168.0.1
  bridges:
    br0:
      interfaces: [enp4s0f1, enp4s0f0, enp3s0f1, enp3s0f0]
      addresses: [192.168.1.1/24]


```

---

