---
title: "libvirt + docker + dnsmasq, how do I set up a bridge for"
date: 2024-10-21
forum: Networking &amp; Wireless
---

### Post by futurdreamz2 on 2024-10-21
I'm trying to set up a virtual machine on my server, but I'm confused as to how to set up a bridge that the virtual machine connects to. [The guide ]("https://help.ubuntu.com/community/BridgingNetworkInterfaces")references a file that does not exist as I do not have an /etc/network/interfaces directory

part of my setup:
my server has a manually assigned ip address of 192.168.0.5 that must be retained 
I'm using dnsmasq to redirect dns requests to my server, as I have a domain name used to access jellyfin outside the network but when on the network i don't want my devices routing everything through the modem as it caps the transfer speeds. (I'm willing to consider an alternative to dnsmasq if it simplifies things)
I'm using docker that pulls directly from the docker repositories, but it seems that the auto created docker0 bridge is nonfunctional
and for some reason i have a really long list of network interfaces that don't seem to be configured correctly: [https://termbin.com/u5lg](https://termbin.com/u5lg)
when I installed dnsmasq I disabled systemd-resolved and recreated /etc/resolv.conf

generally i want to be able to connect vms to my local network and be able to assign them their own ip addresses (like 192.168.0.6), I don't know how to do that without breaking my existing setup

---

### Post by TheFu on 2024-10-21
Ubuntu Servers use netplan since around 2018 to configure most networking, unless it is a desktop install with a GUI.  I don't normally use bridges on GUI installs, but on servers, you can find netplan config file examples in these forums and at [https://netplan.readthedocs.io/en/stable/examples/#how-to-configure-network-bridges](https://netplan.readthedocs.io/en/stable/examples/#how-to-configure-network-bridges) .  For any bridge, you probably don't want to use DHCP since bridges tend to be for servers and servers need a static IP.  

The bridge for each VM/Container would have static IP settings inside it.

As for docker, I didn't think bridges were the normal way to configure networking for docker containers. Rather, they use the static IP of the host system and use iptables/nft to forward specific ports from the host to each docker container, as needed.  I know very little about docker other than what I've picked up from others talking about and about 10 presentations on it at conferences.  I use lxc with LXD for my container needs and kvm/qemu with libvirt for full VMs.  LXC containers are different from Docker App containers, since they run most of an OS and can mostly, with a few caveats, be treated like a full OS install.  LXC containers don't support kernel modules, for example, unless you use elevated privileges, which defeats the entire security model of a Linux Container and should be used. If you need to use a kernel module, like a firewall or nfs server/client inside a container, rethink that container idea and use a full VM instead.

Don't confuse Linux Containers like Docker with VMs.  They are not anywhere close to being related.

Others will have to answer any docker specific questions. Sorry.

I can post my netplan.yaml file with bridges, but that seems to confuse people who aren't good at networking already.

Netplan uses YAML, which is like structured JSON, but space sensitive, so if you need help with any specifics, when you post the full YAML file here, you absolutely **must** use forum code tags or nobody will be able to help you.

---

### Post by futurdreamz2 on 2024-10-22
[deleted]

---

### Post by TheFu on 2024-10-22
The IP address for any VM wouldn't be listed in the bridge config. That's a different system, completely. 
In my setups, the bridge gets the IP for the host. The ethernet card does not.

I don't use vlans.  I use physically separate networks for security reasons.

---

### Post by futurdreamz2 on 2024-10-22
[deleted]

---

### Post by TheFu on 2024-10-22
> **futurdreamz2 said:**
> [deleted]

BTW, I did get an email with the post.  It seemed fine to me.  Did you get it working?  

I probably made my point poorly.  The IP in the bridge doesn't have anything to do with the IP used by any guest.  A network bridge in Linux is just like a network switch or hub.  The guest system sets the IP however it would normally do that.  That could be with a DHCP server on the LAN or via manually configuration inside the OS.  I always, always, always, setup manual static IPs on my VMs and on my LAN, with 2 exceptions.

1. Devices that don't provide a method to setup a static IP - like streaming sticks and network TV tuners or other IoT devices. For those, I use DHCP reservations to setup static IPs.  None of my printers are "networked".  They all  have a print server.

2. Portable computers like tablets, laptops, phones on the network. They also get static IPs through DHCP Reservations.

Devices like servers or desktops or Raspberry Pis each have static IPs manually configured.  I've been burned before and I've seen 2000 computers/printer become unusable in a small campus with a pair of DHCP servers failed.  

The VLAN comment isn't applicable for VMs usually.  I do have separate physical networks for trusted devices and IoT deviced and wifi-only devices.  These are each on different physical networks.  Additionally, I have a separate SAN network for storage only.  VLAN tagging is just a suggestion to be honored.  There are computing devices that can and will listen for any VLAN traffic, unless the switch/router is smart enough never to send incorrectly tagged traffic down that ethernet line.  That is a reasonable expectation from any VLAN-capable network devices, but I prefer to have more than 1 level of protection as switch and router failures do happen.

---

