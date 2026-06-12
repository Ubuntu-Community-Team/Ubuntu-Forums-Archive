---
title: "Second network card."
date: 2016-11-27
forum: Networking &amp; Wireless
---

### Post by thevonsouth on 2016-11-27
Howzit Howzit. Welcome Welcome. Haha

Hi Guys.

I've installed Ubuntu 16.04 Server on VirtualBox. Before installation I added 2 network interfaces. The one uses NAT and the other uses Virual Host (So that I can both access the internet from that machine and so that I can communicate with my host machine).

During installation of Ubuntu only the one network card got configured. Ubuntu gave me an option to choose one of the interfaces.

After the installation when I typed ifconfig only one network card was visible. Which was as expected. Then I tried to configure the other one by looking at this page: [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

but I don't think I went about it in the right manner.

So now my /etc/network/interfaces looks like this:

```

auto enp0s3
iface enp0s3 inet dhcp

auto enp0s8
iface enp0s8 inet dhcp

```

I added the last 2 lines.

Now when I reboot I get a message like "please wait for interface setup" (can't remember the exact message) and it takes 5 minutes.


And when I login I have to do run ifdown and the ifup to get the card working.

Obviously I'm missing something.

Help appreciated.

Cheers

---

### Post by TheFu on 2016-11-27
Life is easier if you just configure 1 interface as "bridged" and use the DHCP server on your normal network to get IP/subnet/DNS settings.  Plus you'll be able to communicate with the world and other machines on the subnet that way.  Virtualbox help has an explanation.

Sorry I can't help more. Never used vbox **on** a Linux system. It was never stable enough for my needs. With other hypervisors, the bridge settings are managed outside the hypervisor using standard linux bridging tools.

---

