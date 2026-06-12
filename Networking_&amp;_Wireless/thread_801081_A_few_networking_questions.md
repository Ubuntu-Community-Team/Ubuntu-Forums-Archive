---
title: "A few networking questions"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by jambalaya on 2008-05-20
Hi.
1. I have my computer configured the default way, i.e. the way things get configured when I install the system. My computer name is jambalaya, and the /etc/hostname says it is jambalaya. However, when I unplug the network cable, whenever I run the sudo command, the first line of the output is "Cannot resolve hostname jambalaya" or similar (can't remember it exactly). When I add a line "jambalaya 127.0.0.1" to /etc/hosts, it doesn't output this msg any more, but this is not default config, and I don't know if everything will work correctly?
2. What actually does configure my network connection? The /etc/network/interfaces file says only lopback is auto, and there is nothing to bring up eth0. Do they use ifup / ifdown, or somthing else (avahi)?
3. When I issue "netstat -ant" I get some lines, most of which state the foreign address is 0.0.0.0:*. What does this * mean? And the 0.0.0.0? I know this means "any NIC", does this include loopback? Also, one line says the foreign address is 127.0.0.1. Could you please tell me what that means, how to interpret this?
I thought this is used to tell the system to redirect the packets to the local machine instead of letting it go to the internet. Does this mean nobody will be able to connect to that particular service? As far as I remember it was ssh, so this would be strange, but maybe that's because there is no connection in my machine now.

Thanks.

---

### Post by Iowan on 2008-05-20
IIRC, my **/etc/hosts** file does have a line similar to the one you added.
As far as starting the network, that'd be **/etc/init.d/networking** You can view it to see what else it calls (especially under the Start or Restart section.

---

### Post by chili555 on 2008-05-20
!. Try this for */etc/hosts*:```
127.0.0.1 localhost
127.0.1.1 jambalaya

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```2. Configure your network in System/Admin/Network. Unlock it with your password. You can find out if a driver has attached to your wireless card with:```
sudo lshw -C network
```Does it have a logical name like eth1? A driver?
3. > maybe that's because there is no connection in my machine now.
Exactly! No really useful information about route is going to be available until you get one!

---

