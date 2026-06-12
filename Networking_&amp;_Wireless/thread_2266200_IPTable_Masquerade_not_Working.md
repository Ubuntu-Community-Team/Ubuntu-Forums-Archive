---
title: "IPTable Masquerade not Working"
date: 2015-02-20
forum: Networking &amp; Wireless
---

### Post by Bakerconspiracy on 2015-02-20
Hey guys,

So I'm trying to set up a masquerading rule in iptables and it doesn't seem to stick. Here's the command I'm using:
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j  MASQUERADE
```
But when I check the iptables rules it shows nothing:
```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

Here are the kernel modules that are loaded:

```
$ lsmod
Module                  Size  Used by
iptable_filter          1721  0 
iptable_mangle          1715  0 
iptable_raw             1538  0 
ip6table_filter         1666  0 
ip6table_mangle         1832  0 
ipv6                  351972  28 ip6table_mangle
ip6table_raw            1483  0 
ip6_tables             12573  3 ip6table_filter,ip6table_mangle,ip6table_raw
iptable_nat             2176  0 
nf_conntrack_ipv4      14480  1 
nf_defrag_ipv4          1735  1 nf_conntrack_ipv4
nf_nat_ipv4             6202  1 iptable_nat
ip_tables              12313  4 iptable_filter,iptable_mangle,iptable_nat,iptable_raw
ipt_MASQUERADE          1208  0 
nf_nat_masquerade_ipv4     2810  1 ipt_MASQUERADE
nf_nat                 17056  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack           96096  4 nf_nat,nf_nat_ipv4,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
x_tables               18626  9 ip6table_filter,ip6table_mangle,ip_tables,ipt_MASQUERADE,iptable_filter,ip6table_raw,iptable_mangle,ip6_tables,iptable_raw
snd_bcm2835            21247  0 
snd_soc_bcm2708_i2s     7360  0 
regmap_mmio             3548  1 snd_soc_bcm2708_i2s
snd_soc_core          177320  1 snd_soc_bcm2708_i2s
snd_compress            8687  1 snd_soc_core
snd_pcm_dmaengine       5826  1 snd_soc_core
snd_pcm                92398  3 snd_bcm2835,snd_soc_core,snd_pcm_dmaengine
snd_seq                60741  0 
snd_seq_device          7194  1 snd_seq
snd_timer              22618  2 snd_pcm,snd_seq
8192cu                571056  0 
snd                    66924  7 snd_bcm2835,snd_soc_core,snd_timer,snd_pcm,snd_seq,snd_seq_device,snd_compress
spi_bcm2708             5961  0 
i2c_bcm2708             6124  0 
```

Do you have any ideas why this might be happening?

---

### Post by Doug S on 2015-02-21
This command:```
sudo iptables -L
```does not list the nat table. To list the nat tables use this (I added some other options):```
sudo iptables -t nat -v -x -n -L
```Example:```
doug@doug-64:~$ [COLOR=#ff0000]sudo iptables -t nat -v -x -n -L[/COLOR]
Chain PREROUTING (policy ACCEPT 947126 packets, 124335712 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain INPUT (policy ACCEPT 253905 packets, 17874651 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 293221 packets, 23883862 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 25143 packets, 2878482 bytes)
    pkts      bytes target     prot opt in     out     source               destination
  541970 36936667 SNAT       all  --  *      eth1    0.0.0.0/0            0.0.0.0/0            to:173.180.XXX.YYY
```Note: I use SNAT instead of MASQUERADE

---

