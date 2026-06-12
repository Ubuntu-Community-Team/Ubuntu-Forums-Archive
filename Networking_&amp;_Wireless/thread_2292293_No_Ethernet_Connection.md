---
title: "No Ethernet Connection"
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by doughoover on 2015-08-26
I am posting this message through a Live-DVD of Ubuntu 14.04.03 TLS.  My base system (the one that doesn't work) is Ubuntu 14.04 TLS with all of the latest updates as of early this week.

I was in the process of installing / configuring Xen v4.4 using a document from the Ubuntu documentation site.  I had installed the Xen package using apt-get install, which also installed the brutils and other related bridge packages.  I had configured the bridge, disabled network manager when I realized that I did not have the Open vSwitch package installed.  I then backed out of the Xen install using apt-get remove and purge, to clear out all dependencies.  Then I reconfigured /etc/network/interfaces to read;

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
           address 192.168.10.35
           netmask 255.255.255.0
           broadcast 192.168.10.255
           gateway 192.168.10.1
           nameservers 192.168.10.1 8.8.8.8

then, edited /etc/NetworkManager/NetworkManager.conf
changed managed=true
under [Main] to read; NetworkingEnabled=true

then sudo /etc/init.d/networking restart

Last evening, I could ping my router and external sites such as Google's DNS site at 8.8.8.8.  But I could not resolve a name such as [www.ask.com]("http://www.ask.com").  However, from nslookup, I was able to query the same site following a server 8.8.8.8 command.  I then shutdown the system.

Today, the system does not recognize the network.  On bootup, the message "Waiting for network configuration", then "Waiting 60 seconds for network configuration" and lastly "Booting system without full network configuration".

When accessing the Network section of System Settings, the message "System Network Services are not compatible with this version" appeared.

The NIC is on board the system board and I believe it is a RealTek Gigabit.

The log had these messages;

TCP: Cubic registered
NET: Protocol family 10
NET: Protocol family 17

Key type DNS_Resolver registered

IPv6: ADDRCONF (NETDEV_UP): eth0 Link is not ready

init: network interface eth0 Pre-start Process (451) status=1
init: network interface lo Pre-start Process (454) status=1
init: network interface eth0 Pre-start Process (466) status=1
init: network interface lo Pre-start Process (481) status=1

init: network interface eth0 Post-stop Process (668) status=100

whoopsie: could not get network manager state

There was not a link light on the NIC.

Yet, I am using the exact same hardware from the Live-DVD.

---

### Post by Hadaka on 2015-08-26
Hi, network manager tends to conflict with /etc/network/interfaces.
you can have either or but not both, i would suggest removing network manager
and do..
```
sudo ifdown eth0 && sudo ifup eth0
```
___________________OR__________________
If you just want a static ip,i would suggest letting the network manager manage the connection as it was designed to do,
start by returning your changes to the network interface files to default.
*changes network manager from true to false
```
sudo sed -i 's/managed=true/managed=false/g' /etc/NetworkManager/NetworkManager.conf
```
*Removes current network/interfaces file 
```
sudo rm /etc/network/interfaces
```
*Replaces network/interfaces with default settings
```
echo -e "auto lo\niface lo inet loopback" | sudo tee -a /etc/network/interfaces
```
Then configure your network manager ipv4 and ipv6 settings like the attached.
*Network manager > Edit connections > wired > edit > ipv4 > Method:Manual >add
[ATTACH=CONFIG]264067[/ATTACH][ATTACH=CONFIG]264068[/ATTACH]

---

### Post by TheFu on 2015-08-27
Remove network manager if you want to run a server or any virtualization. **Do NOT USE NM.**
Always manually setup bridges for any VMs you want.

There are other opinions - just saying what has worked here since 2008.

---

