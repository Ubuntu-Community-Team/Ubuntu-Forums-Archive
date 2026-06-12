---
title: "ubuntu equivalent file"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by sulekha on 2008-08-23
Hi,

In Red hat 8.0 we have **/etc/sysconfig/network-scripts/ifcfg.eth0** 
with the following contents
DEVICE=eth0
ONBOOT=yes
BOOTPROTO=none
BROADCAST=172.16.12.255
NETWORK=172.16.12.0
NETMASK=255.255.255.0
IPADDR=172.16.12.2
USERCTL=no

file for configuring the ethernet interface eth0 , now what is the equivalent file in ubuntu 8.04 ?

---

### Post by techstop on 2008-08-23
I'm not familiar with Red Hat, but you can configure your network interfaces in /etc/network/interfaces in Ubuntu.

---

### Post by sulekha on 2008-08-23
> **techstop said:**
> I'm not familiar with Red Hat, but you can configure your network interfaces in /etc/network/interfaces in Ubuntu.

that is not the case as my /etc/network/interface contains only the followingg entries

auto lo
iface lo inet loopback

iface eth0 inet static
address ----------
netmask ----------
gateway ----------

---

### Post by ivikas on 2008-08-23
I have been using redhat and fedora for long times.I have just shifted to ubuntu 8.04.I have set up network with GUI.That's from System->Administration->Network.I have a wireless network,with a wireless adaptor suporting only windows driver.I managed to get it work with ndiswrapper.

---

