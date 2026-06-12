---
title: "Network fails after uninstall of kvm,xen and bridge-utils"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by cop2 on 2014-09-30
I am running Ubuntu server 14.04 (and therefore no package network-manager). I am not able to access the LAN after uninstalling kvm, xen and bridge-utils. There are no bridge interfaces remaining. 

My interfaces files looks like
```

auto lo
iface lo inet loopback

auto em1
iface em1 inet static
address 172.16.40.34
netmask 255.255.255.0
gateway 172.16.40.1

```

netstat -rn gives
```

Kernet IP routing table
Destination          Gateway            Genmask              Flags             MSS  Window     irtt    Iface
0.0.0.0             172.16.40.1          0.0.0.0                   UG                  0      0              0      em1
172.16.40.0      0.0.0.0                255.255.255.0          U                    0      0              0      em1

```
lshw -class network  shows that the Ethernet interface logical name is em1

ifconfig shows em1 interface with the correct ip address as in the interfaces file.

This was working before so I wonder what's wrong now. I am suspecting the bridge configurations done before are the culprits. Kindly assist as I do not wish to reinstall the OS.

---

### Post by Doug S on 2014-09-30
> **cop2 said:**
> I am not able to access the LAN after [COLOR=#ff0000]uninstalling[/COLOR] kvm, xen and bridge-utils. There are no bridge interfaces remaining.

Edit: I completely misread your post. I read "installing" instead of "uninstalling" above. Therefore my original reply, now deleted, was not what you wanted at all. Sorry.

Edit 2: Deleted my original, not relevant, reply and now:

Do you still have files like so:```
doug@s15:/etc/libvirt/qemu$ [COLOR=#ff0000]ls -l /proc/sys/net/bridge[/COLOR]
total 0
-rw-r--r-- 1 root root 0 Sep 30 08:48 bridge-nf-call-arptables
-rw-r--r-- 1 root root 0 Sep 30 08:48 bridge-nf-call-ip6tables
-rw-r--r-- 1 root root 0 Sep 30 08:48 bridge-nf-call-iptables
-rw-r--r-- 1 root root 0 Sep 30 08:48 bridge-nf-filter-pppoe-tagged
-rw-r--r-- 1 root root 0 Sep 30 08:48 bridge-nf-filter-vlan-tagged
-rw-r--r-- 1 root root 0 Sep 30 08:48 bridge-nf-pass-vlan-input-dev
```If yes, then what are the contents?```
doug@s15:/etc/libvirt/qemu$ [COLOR=#ff0000]cat /proc/sys/net/bridge/*[/COLOR]
1
1
1
0
0
0
```You could try to put "0" into each spot that has a "1". see [also]("http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge#No_traffic_gets_trough_.28except_ARP_and_STP.29").
I wonder if you might need to specifically delete the bridge via re-installing the bridge utilities and running the "brctl delbr" command.

---

### Post by cop2 on 2014-10-01
Thanks for the response.
The directory
```

root@beantest:/etc# ls /etc/libvirt/qemu 
centos.xml    networks

```

There is no directory /proc/sys/net/bridge

Contents of net are 
```

root@beantest:/proc/sys/net# ls 
core ipv4 ipv6 netfilter unix

```

Am now working on re-installing the bridge utilities and will get back. Thanks

---

### Post by cop2 on 2014-10-01
Since I could not get the bridge utilities to install (no network therefore no internet connection) I tried the commands below, rebooted and now the network works.
```

root@brucetest:/# ethtool -i em1  #To get the module being used for network under driver:
root@brucetest:/# modprobe -r e1000e  #removes the module
root@brucetest:/# modprobe e1000e  #reloads the module
root@brucetest:/# reboot

```

---

### Post by Doug S on 2014-10-01
Glad you got it sorted out, and thanks for reporting back.

---

