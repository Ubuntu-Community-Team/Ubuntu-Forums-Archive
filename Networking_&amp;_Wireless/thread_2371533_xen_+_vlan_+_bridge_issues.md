---
title: "xen + vlan + bridge issues"
date: 2017-09-15
forum: Networking &amp; Wireless
---

### Post by terence26 on 2017-09-15
I am new to Ubuntu; I have been using Opensuse with VirtualBox for many years - no issues.
With Ubuntu/Xen though it is not so easy

interfaces

auto enp2s0
iface enp2s0 inet manual

auto enp2s0.10
iface enp2s0.10 inet manual
vlan-raw-device enp2s0

auto GREEN
    iface GREEN inet static
    address 192.168.10.21
    netmask 255.255.255.0
    network 192.168.10.1
    broadcast 192.168.10.255
    gateway 192.168.10.1
    dns-nameservers 8.8.8.8 8.8.4.4
    dns-domain en3.biz
    dns-search en3.biz
    bridge_ports enp2s0.10
    bridge-stp off
    bridge_fd 0.0
    bidge_waitport 0
    offload-tx off
    offload-sg off
    offload-tso off
    mtu 1460


sysctl


net.core.somaxconn = 1000
net.core.netdev_max_backlog = 5000
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_wmem = 4096 12582912 16777216
net.ipv4.tcp_rmem = 4096 12582912 16777216
net.ipv4.tcp_max_syn_backlog = 8096
net.ipv4.tcp_slow_start_after_idle = 0
net.ipv4.tcp_tw_reuse = 1
net.ipv4.ip_local_port_range = 10240 65535

vm.swappiness = 10
vm.dirty_ratio = 60
vm.dirty_background_ratio = 5
vm.dirty_expire_centisecs = 15000

vm.min_free_kbytes = 128000
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

net.inet.tcp.tso = 0

net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0
net.bridge.bridge-nf-filter-pppoe-tagged = 0
net.bridge.bridge-nf-filter-vlan-tagged = 1
net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0



I have 3 virtual machines under xen
pfsense...works fine
Windows 2008 works fine
Windows 2008 works fine except NAT from the internet...packets never arrive to the VM

I do not know if this is related or not,but it seems machine requires a daily reboot to work properly
Exact same hardware ran OpenSuse + VirtualBox for 15 months without issues

---

