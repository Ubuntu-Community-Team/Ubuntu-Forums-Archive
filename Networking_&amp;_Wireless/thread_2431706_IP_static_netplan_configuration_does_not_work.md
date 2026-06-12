---
title: "IP static netplan configuration does not work"
date: 2019-11-20
forum: Networking &amp; Wireless
---

### Post by orion912 on 2019-11-20
I have been trying to configurate a static IP address with netplan, bit it send this message after sudo netplan apply "Invalid YAML: inconsistent dentation: nameservers:"

this is my configuration 

network:
version: 2
renderer: NetworkManager
ethernets:
     eno1: expexted mapping
     dhcp4:no
     dhcp6:no
     addresses:[192.168.100.6/24]
     gateway4:192.168.100.1
     nameservers:
               addresses:[8.8.8.8, 8.8.4.4]

I hope anybody could help me. 
Thanks You!!

---

### Post by TheFu on 2019-11-20
To show config files that depend on indentation here, you **MUST** use code tags.  How to for code tags: [https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)
Until that is corrected, we cannot help.

Yesterday, I posted a yaml file for an 18.04 server with a static IP here. A little searching will find it.

---

### Post by SeijiSensei on 2019-11-20
Is there some reason why you're not using the standard Network Manager and GUI network configuration for this?  In the dialog you can choose a static configuration and fill in the boxes with the IP/netmask/gateway and DNS server entries.  I'm on Kubuntu 19.10, but I'm pretty sure the same functionality exists in vanilla Ubuntu.

I believe netplan has strict requirements for indentation.

---

### Post by chili555 on 2019-11-20
> Is there some reason why you're not using the standard Network Manager and GUI network configuration for this? Indeed.

Your netplan yaml suggests that Network Manager should do all the work. Why not do just that?

---

### Post by webaake on 2019-11-21
Or; manually edit the file /etc/network/interfaces
I always use that for static IP's on threaded network. Quick and stable.

---

### Post by TheFu on 2019-11-21
> **webaake said:**
> Or; manually edit the file /etc/network/interfaces
I always use that for static IP's on threaded network. Quick and stable.

That file is not used since Ubuntu 17.10 ... unless you swap out the netplan stuff and install the old ifup/down packages.   The march forward continues, even if we prefer the older method.

---

### Post by webaake on 2019-11-21
> **TheFu said:**
> That file is not used since Ubuntu 17.10 ... unless you swap out the netplan stuff and install the old ifup/down packages.   The march forward continues, even if we prefer the older method.

Aha, okay. I've continually upgraded my Ubuntu installs, so I guess "interfaces" linguers on. I remember one time that the command ifconfig didn't work! But I reinstalled it and use it on 18.04 today, including /etc/network/interfaces as configuration.

But if netplan isn't working I recommend reverting to the older networking stuff. It WAS better in the ol' times! (a joke) :P

EDIT: howto install the previuos networking setup on Ubuntu 18.04 and avoid Netplan: [https://askubuntu.com/questions/1031709/ubuntu-18-04-switch-back-to-etc-network-interfaces](https://askubuntu.com/questions/1031709/ubuntu-18-04-switch-back-to-etc-network-interfaces)

PS Seems that since I've usedstandard "networking" since 2007 from the package Ifupdown it is still used in my updated 18.04 install. And works perfectly.

---

