---
title: "Netplan and spoofed MAC address. Correct ip address or MAC address, never both."
date: 2020-01-14
forum: Networking &amp; Wireless
---

### Post by nsaves on 2020-01-14
Ubuntu 18.04.03 (version using Kernel 5), Sysadmin / backup using Virtualmin

I've run into an issue trying to spoof a MAC address. (My ISP uses MAC address and like that I always get the same IP address.)

Looking on-line, find a lot of tutorials on this subject, but I cannot get any of them work. Below is my 01-netplan.yaml file. With the MAC address set, on reboot I only get the changed MAC address, never gets assigned the IP address. Remove the spoof address and then I get the IP address. But never both together. :(

**01-netplan.yaml**:-

network:
  version: 2
  renderer: networkd
  ethernets:
        enp7s0:
            match:
                macaddress: OL:DA:DD:RE:SS:C9
            macaddress: NE:WA:DD:RE:SS:62
            dhcp4: true
            dhcp6: false
            nameservers:
                addresses: [127.0.0.1,127.0.0.53]

I found one online that said to set it MAC spoofing  in /etc/systemd/network.

**00-default.link**

[Match]
MACAddress=OL:DA:DD:RE:SS:C9

[Link]
MACAddress=NE:WA:DD:RE:SS:62
NamePolicy=kernel database onboard slot path

But exactly the same thing happens. Edit yaml to have no spoof address, define that file, reboot, and all I have is the changed MAC address, no IP address.


Looking in /run/systemd/network, I have two files. Names and Contents ...


**10-netplan-enp7s0.network**

[Match]
MACAddress=OL:DA:DD:RE:SS:C9

[Network]
DHCP=ipv4
LinkLocalAddressing=ipv6
DNS=127.0.0.1
DNS=127.0.0.53

[DHCP]
RouteMetric=100
UseMTU=true


**10-netplan-enp7s0.link**

[Match]
MACAddress=OL:DA:DD:RE:SS:C9

[Link]
WakeOnLan=off
MACAddress=NE:WA:DD:RE:SS:62

I was surprised that all the files (internal interface left out of this) have the same priority. So I had 10-netplan-enp7s0.network  /  10-netplan-enp7s0.link / 10-netplan-enp5s0.network 

Any thoughts would be greatly appreciated.

Kind Regards - Nigel.

---

