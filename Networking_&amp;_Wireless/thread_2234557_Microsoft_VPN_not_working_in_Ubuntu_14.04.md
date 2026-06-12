---
title: "Microsoft VPN not working in Ubuntu 14.04"
date: 2014-07-15
forum: Networking &amp; Wireless
---

### Post by azcn2503 on 2014-07-15
I have a Microsoft PPTP VPN connection configured on my Ubuntu 14.04 machine which connects successfully with the given credentials, using MSCHAPv2. However, when connected to this VPN, I cannot access any of the resources on the private network, cannot ping any IP addresses, and if I try to tracepath, I do not even go outside of my own network.

I have also [posted this issue on AskUbuntu]("http://askubuntu.com/questions/491889/connecting-to-private-ips-in-ubuntu-14-04-with-microsoft-vpn") but it has not yet received a solution. Perhaps somebody can advise? Many thanks.

---

### Post by SeijiSensei on 2014-07-15
Post the results of running "route -n" before and after making the VPN connection.  Include a few comments so we'll know which IP addresses/subnets correspond to which parts of your network.

---

### Post by azcn2503 on 2014-07-16
Hello,

Here is the output of route -n when not connected:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```

And here is after:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.0.103   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
195.159.176.130 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
195.159.176.130 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
```

It seems I have been assigned an IP address 192.168.0.103, and the other IP corresponds to the VPN gateway.

---

### Post by SeijiSensei on 2014-07-16
First, let me ask why you are using the tunnel.  Is it to connect to a private network, or are you sending all your outbound traffic over the tunnel?

The second configuration lacks a default gateway; it is simply blasted out the ppp0 interface.  You say that you are assigned the .103 address, but since that's a target in the routing table, that's probably the address of the PPTP server.  If you do intend to send all traffic through the tunnel, you probably want to designate that server as the default gateway with:
```
sudo ip route add default via 192.168.0.103
```

To see your addresses, run the command "ifconfig" after connecting to the PPTP server.

I still foresee some problems because of the overlapping network subnets.  Are you in control of the 192.168.0.1 router that is your normal default gateway?  If so, I'd try changing the private IP subnet it uses from 192.168.0.0/24 to 192.168.xxx.0/24, a subnet that differs entirely from that used by the PPP connection.

---

### Post by azcn2503 on 2014-07-18
Thanks,

I am confused about the .103 address. I'm not in control of the remote network so it may be difficult for me to get this up and running if I need to make configuration changes on that end.

It is worth noting that the VPN connection works flawlessly on a Windows machine on the same network. The Windows machine has a local IP of 192.168.0.7, and has been assigned an IP 192.168.0.90 by the VPN. It can access local and private network resources. I thought it would be this easy in Ubuntu ;)

---

### Post by SeijiSensei on 2014-07-18
First, PPTP has [well-known security holes]("https://www.schneier.com/pptp.html") so it's almost never used outside of Microsoft networks.  People wrote PPTP implementations for Linux just to be able to connect to MS networks.  Most Linux people use OpenVPN, SSH, or ipsec to create tunnels.

You might try connecting from Windows and looking at the routing tables that way.  Use "route print" to see whether the table you get from Windows is the same as the one you get from Ubuntu.

---

