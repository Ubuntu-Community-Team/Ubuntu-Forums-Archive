---
title: "Lost in Static Networking"
date: 2022-09-24
forum: Networking &amp; Wireless
---

### Post by lslamp on 2022-09-24
I am a little frustrated because I have tried many things and still for some reason, I cannot get my Ubuntu VM to read the interfaces file.

I wanted to switch back to the old networking using the /etc/network/interfaces file and device name eth0.

After changing the device name I rebooted, created the following interfaces file 
# # #
source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.80
        netmask 255.255.255.0
        gateway 192.168.1.1
# # # 

I unlinked /etc/resolv.conf

I added nameserver 1.1.1.1 and nameserver 8.8.8.8 into the /etc/resolv.conf file.

I restarted the networking service, but no matter what I did I could not get rid or the dynamic ipaddress.

I want the static ipaddress to be 192.168.1.80

but this is what I get everytime.

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.130  netmask 255.255.255.0  broadcast 192.168.1.255


I am lost for what I have done wrong or am doing wrong.

Would appreciate anyone tell me what I am missing or not undertanding.

Thanks
Lawrence

---

### Post by TheFu on 2022-09-24
Which release?

For 20.04, I think you should just get used to netplan.  It isn't hard and there are lots of examples.

As for the resolv.conf, that could be either resolvconf or systemd-resolved.  I don't use either, preferring to let my LAN DNS perform all caching, but most people with 20.04 and later would have systemd-resolved and would need to modify the /etc/systemd/resolved.conf file for the nameservers to be used.

Trying to stay in the passed will get more and more painful.  I stay about 2 yrs behind, which was good, since when netplan was first thrust onto Ubuntu, it needed almost 2 yrs more before normal stuff worked correctly.  These days, it sorta "just works."
Here's a netplan file for a static IP on a 20.04 desktop here, change for your situation, as needed:

$ more /etc/netplan/01-ens3-static.yaml 
```
network:
  version: 2
  renderer: networkd
  ethernets:
     ens3:
       addresses:
          - 172.22.22.3/24
       dhcp4: false
       dhcp6: false
       gateway4: 172.22.22.1
       nameservers:
         addresses: [ "172.22.22.80","172.22.22.81" ]

```
netplan uses YAML, which is indention sensitive.  After you drop the file in the correct location, run 
```
$ sudo netplan generate
$ sudo netplan apply
```
that will move everything over.  A reboot will work too, but I don't like rebooting when there isn't any need.

---

