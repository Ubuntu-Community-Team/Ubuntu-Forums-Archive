---
title: "Ubuntu 20.04 vm local ip address dns issue"
date: 2021-11-13
forum: Networking &amp; Wireless
---

### Post by rorton on 2021-11-13
Hi, running an Ubuntu 20.04 VM (its an appliance, provided by LibreNMS) and am struggling to get it to resolve internal IP addresses on my LAN. 
 
I have a PiHole acting as my local DNS Server - all my clients on my network point to the PiHole, and they can all resolve local addresses set-up in there, 
 
EG, if I ping the name UnRaid from a client, it resolves fine to 192.168.10.8
 
Now, on the Ubuntu box, this doesn't work, I can't ping anything local. I can ping stuff on the internet (ping bcc.co.uk for example) and that's perfect, its just the internal hosts. 
 
If I do an NSLOOKUP for 192.168.10.8 (the IP of the unraid box) I do get a response..
 
nslookup 192.168.10.8
8.10.168.192.in-addr.arpa name = UnRaid.
 
But if I PING the hostname UnRaid from the Ubuntu box I get 
 
ping: unraid: Temporary failure in name resolution
 
Any ideas? Im using Netplan to setup and my Netplan.yaml file is:

```

[FONT=courier new]network:
  version: 2
  renderer: networkd 
  ethernets:
    enp2s0:
      dhcp4: no
      addresses: [192.168.1.13/25]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [192.168.1.14][/FONT]

```

---

### Post by TheFu on 2021-11-14
Please edit the first post above to wrap the netplan file in "code tags", so indentation is honored.
 [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains how, if you need more help.

Also, please post the contents of /etc/resolv.conf (also wrapped in code-tags). It could be a missing "search" line.

---

### Post by rorton on 2021-11-14
as a temp measure till I get this resolved, ive manually added the hosts im monitoring into the host file on the Ubuntu box so the application and resolve the addresses and monitor the devices, would like to sort this permanently though so I don't have to keep editing the host file.

---

### Post by TheFu on 2021-11-14
Is "no" allowed?  I know "false" works.

```
network:
  version: 2
  renderer: networkd 
  ethernets:
    enp2s0:
      dhcp4: [COLOR="#FF0000"]false[/COLOR]
      [COLOR="#FF0000"]dhcp6: false[/COLOR]
      addresses: [192.168.1.13/25]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [192.168.1.14]
        [COLOR="#FF0000"]search: [your.lan.domainname][/COLOR]
```

BTW, if you might want to run a VPN so you can access your LAN from the internet in the future, then you should change the LAN subnet from 192.168.1.1/24 to something much less common, perhaps 192.168.[COLOR="#FF0000"]111[/COLOR].1/24.  Basically, you want your subnet to be different from every hotel, cafe, restaurant, and company.  This would be a router change and all DHCP clients would need to be rebooted. Static IPs on devices would all need to be changed too for the new subnet.

---

### Post by rorton on 2021-11-15
Hi, thanks for the reply - im unsure about no/false, some other examples I read online showed 'no' but I can change to false. 

With regards the search domain, I probably don't have this setup properly from a dns perspective - on my PiHole I have simply edited the hosts file to include all the hosts that I want to resolve internally, and then my clients, as they have the PiHole machine as their DNS server, resolve these ok - I don't have a domain setup as such so unsure what I should put in the search: section in the Netplan file?

---

### Post by TheFu on 2021-11-15
I've never setup a network that didn't have a DNS domainname.
On my pihole (also used as a LAN DNS), there are very specific rules for how the lan.list file has to be setup to work correctly.

```
# The order matters:
# IP          FQDN        hostname
172.22.22.13 posc.zyx.lan posc
```

Lots of things broke when I didn't use the FQDN part or if I changed the order - like putting the hostname first in the list.
So my search in the netplan is 
```
search: [zyx.lan]
```

---

### Post by rorton on 2021-11-15
thanks, im going to revisit my PiHole config first I think, get it working 'properly' with a dns domain for the local hosts, I understand that can be done in the gui now. Once that's setup and clients are resolving by not using the piholes host file, I'll add the search entry into the Netplan file and hopefully that should fix things!

With regards IP addressing, I have a number of vlans inside the network, so 192.168.1.1 is one of them. I do VPN into my network through my UniFi USG. Not had issues in the past, to be honest, when on a wireless network anywhere that isn't my own, I nearly always vpn back to my router and use its internet connection, so whoever manages the WiFI im connecting to can't see what's going on.

---

### Post by TheFu on 2021-11-15
I don't use VLANs, since those are just *suggestions* which can be ignored. Physically separate LANs are needed for real separation. Wifi is always suspect, since we've learned that every wifi connection has flaws since the beginning all the way through wifi-6.  For many years, I've treated all wifi like internet traffic - if wifi in my own home. My wifi devices get internet access only, unless they connect to my LAN VPN.  For a few years, I did corporate wifi deployments to over 1200 locations.  Never trust any RF claims of security, that's what I learned and avoid wifi whenever possible.  That goes for 100x more for BT and whatever wireless keyboards/mice use. Just assume those aren't secure and never will be.  A few years ago, my freshly installed and patched Ubuntu laptop (I'd wiped it and did a fresh install the day before a trip) was hacked over bluetooth.  I wasn't on any network and hadn't connected to any network since leaving home. I was helping with a KoTH competition and working on a presentation for the conference (disconnected) when I noticed a few new files in my HOME directory.  Seems that Ubuntu had installed and enabled bluetooth by default, which I never, ever, use.  Don't trust bluetooth - ever.  That was day 1 of the conference.  That night, in a different hotel, miles away, I wiped the system and loaded a fresh install -this time adding a script to remove the bluetooth kernel modules at boot.  Sadly, my BIOS didn't separate BT from Wifi - so I couldn't just disable BT.

Average people haven't been told in a way that they understand how poor security is with wifi, bluetooth, and any other wireless protocols. They just don't know and some "experts" don't want to alarm anyone, since there is nothing that can be done by most average users.  Always use a VPN. ALWAYS.  I suppose if you live 2miles down a private road and 5miles away from your neighbors, with no direct line of sight possible, then a VPN for wifi in your home wouldn't really be necessary.  But even people living in rural mountain locations, if there home can be seen across a valley 5+ miles away need to be weary.  Wifi reaches much farther than people understand with a little directional antenna.  Same for Bluetooth.  10m is hardly the limit.  I think bluetooth signals have been captured from 2miles away.
[https://arstechnica.com/gadgets/2021/05/farewell-to-firewalls-wi-fi-bugs-open-network-devices-to-remote-hacks/](https://arstechnica.com/gadgets/2021/05/farewell-to-firewalls-wi-fi-bugs-open-network-devices-to-remote-hacks/)

Claims that vulnerabilities are closed should be taken with a grain of salt. It is common for a fix to cause other issues and there are always unpublished hack methods.

---

