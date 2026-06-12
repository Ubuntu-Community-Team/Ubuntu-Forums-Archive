---
title: "rtl8192cu 0bda:818b Realtek Semiconductor Co error Ubuntu 18.10. [Logs+system's info]"
date: 2019-01-31
forum: Networking &amp; Wireless
---

### Post by camperdelarco on 2019-01-31
Hello guys, the current situation with my workstation goes as follows: The only way to access the internet is via tethering and the wifi adapter does not seem to be recognized by the networking system. I will enlist the command lines I've used in the past as a result of my previous research alongside my system's info. Please, be patient and I really appreciate your help.

***_COMMANDS PREVIOUSLY USED:_***

**~# sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 138 not upgraded.
Need to get 0 B/4,776 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 205638 files and directories currently installed.)
Preparing to unpack .../build-essential_12.5ubuntu2_amd64.deb ...
Unpacking build-essential (12.5ubuntu2) over (12.5ubuntu2) ...
Preparing to unpack .../dkms_2.3-3ubuntu11_all.deb ...
Unpacking dkms (2.3-3ubuntu11) over (2.3-3ubuntu11) ...
Preparing to unpack .../git_1%3a2.19.1-1ubuntu1.1_amd64.deb ...
Unpacking git (1:2.19.1-1ubuntu1.1) over (1:2.19.1-1ubuntu1.1) ...
Preparing to unpack .../linux-headers-4.18.0-13-generic_4.18.0-13.14_amd64.deb ...
Unpacking linux-headers-4.18.0-13-generic (4.18.0-13.14) over (4.18.0-13.14) ...
Preparing to unpack .../linux-headers-generic_4.18.0.13.14_amd64.deb ...
Unpacking linux-headers-generic (4.18.0.13.14) over (4.18.0.13.14) ...
Setting up build-essential (12.5ubuntu2) ...
Setting up dkms (2.3-3ubuntu11) ...
Setting up linux-headers-4.18.0-13-generic (4.18.0-13.14) ...
/etc/kernel/header_postinst.d/dkms:
ERROR (dkms apport): binary package for 8192cu: 4.0.2.9000.20130911 not found
Error!  Build of 8192cu.ko failed for: 4.18.0-13-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/8192cu/4.0.2.9000.20130911/build/ for more information.
Processing triggers for man-db (2.8.4-2) ...
Setting up git (1:2.19.1-1ubuntu1.1) ...
Setting up linux-headers-generic (4.18.0.13.14) ...

******
**~# sudo git clone [https://github.com/vincent-t/rt8192cu_dkms](https://github.com/vincent-t/rt8192cu_dkms) /usr/src/8192cu-4.0.2.9000.20130911**
fatal: destination path '/usr/src/8192cu-4.0.2.9000.20130911' already exists and is not an empty directory.

_**~# sudo dkms add -m 8192cu -v 4.0.2.9000.20130911**_
Error! DKMS tree already contains: 8192cu-4.0.2.9000.20130911
You cannot add the same module/version combo more than once.

**~# sudo dkms build -m 8192cu -v 4.0.2.9000.20130911**

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j4 KERNELRELEASE=4.18.0-13-generic -C /lib/modules/4.18.0-13-generic/build M=/var/lib/dkms/8192cu/4.0.2.9000.20130911/build...
ERROR (dkms apport): binary package for 8192cu: 4.0.2.9000.20130911 not found
Error!  Build of 8192cu.ko failed for: 4.18.0-13-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/8192cu/4.0.2.9000.20130911/build/ for more information.


**~# sudo dkms install -m 8192cu -v 4.0.2.9000.20130911 **

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j4 KERNELRELEASE=4.18.0-13-generic -C /lib/modules/4.18.0-13-generic/build M=/var/lib/dkms/8192cu/4.0.2.9000.20130911/build...
ERROR (dkms apport): binary package for 8192cu: 4.0.2.9000.20130911 not found
Error!  Build of 8192cu.ko failed for: 4.18.0-13-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/8192cu/4.0.2.9000.20130911/build/ for more information.

[B]~# echo -e "blacklist rtl8192cu\nblacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf
[/B]
blacklist rtl8192cu
blacklist rtl8xxxu













_**MY COMPUTER'S INFO**_

~$ lsusb
Bus 002 Device 003: ID 0bda:818b Realtek Semiconductor Corp. 


**$ lsmod**
cfg80211              663552  1 8192cu


**~$ ls -R /lib/modules/`uname -r`/kernel/**
/lib/modules/4.18.0-13-generic/kernel/net:
6lowpan     bluetooth  decnet      key        netlink      rds     tipc
802         bpfilter   dsa         l2tp       netrom       rfkill  tls
8021q       bridge     hsr         lapb       nfc          rose    unix
9p          caif       ieee802154  llc        nsh          rxrpc   vmw_vsock
appletalk   can        ife         mac80211   openvswitch  sched   wimax
atm         ceph       ipv4        mac802154  packet       sctp    wireless
ax25        core       ipv6        mpls       phonet       smc     x25
batman-adv  dccp       kcm         netfilter  psample      sunrpc  xfrm

/lib/modules/4.18.0-13-generic/kernel/net/6lowpan:
6lowpan.ko   nhc_fragment.ko  nhc_ipv6.ko      nhc_routing.ko
nhc_dest.ko  nhc_hop.ko       nhc_mobility.ko  nhc_udp.ko

/lib/modules/4.18.0-13-generic/kernel/net/802:
garp.ko  mrp.ko  p8022.ko  psnap.ko  stp.ko

/lib/modules/4.18.0-13-generic/kernel/net/8021q:
8021q.ko

/lib/modules/4.18.0-13-generic/kernel/net/9p:
9pnet.ko  9pnet_rdma.ko  9pnet_virtio.ko  9pnet_xen.ko

/lib/modules/4.18.0-13-generic/kernel/net/appletalk:
appletalk.ko

/lib/modules/4.18.0-13-generic/kernel/net/atm:
atm.ko  br2684.ko  clip.ko  lec.ko  mpoa.ko  pppoatm.ko

/lib/modules/4.18.0-13-generic/kernel/net/ax25:
ax25.ko

/lib/modules/4.18.0-13-generic/kernel/net/batman-adv:
batman-adv.ko

/lib/modules/4.18.0-13-generic/kernel/net/bluetooth:
bluetooth_6lowpan.ko  bluetooth.ko  bnep  cmtp  hidp  rfcomm

/lib/modules/4.18.0-13-generic/kernel/net/bluetooth/bnep:
bnep.ko

/lib/modules/4.18.0-13-generic/kernel/net/bluetooth/cmtp:
cmtp.ko

/lib/modules/4.18.0-13-generic/kernel/net/bluetooth/hidp:
hidp.ko

/lib/modules/4.18.0-13-generic/kernel/net/bluetooth/rfcomm:
rfcomm.ko

/lib/modules/4.18.0-13-generic/kernel/net/bpfilter:
bpfilter.ko

/lib/modules/4.18.0-13-generic/kernel/net/bridge:
bridge.ko  br_netfilter.ko  netfilter

/lib/modules/4.18.0-13-generic/kernel/net/bridge/netfilter:
ebt_802_3.ko       ebt_arp.ko       ebt_log.ko       ebt_snat.ko
ebtable_broute.ko  ebt_arpreply.ko  ebt_mark.ko      ebt_stp.ko
ebtable_filter.ko  ebt_dnat.ko      ebt_mark_m.ko    ebt_vlan.ko
ebtable_nat.ko     ebt_ip6.ko       ebt_nflog.ko     nf_log_bridge.ko
ebtables.ko        ebt_ip.ko        ebt_pkttype.ko   nft_reject_bridge.ko
ebt_among.ko       ebt_limit.ko     ebt_redirect.ko

/lib/modules/4.18.0-13-generic/kernel/net/caif:
caif.ko  caif_socket.ko  caif_usb.ko  chnl_net.ko

/lib/modules/4.18.0-13-generic/kernel/net/can:
can-bcm.ko  can-gw.ko  can.ko  can-raw.ko

/lib/modules/4.18.0-13-generic/kernel/net/ceph:
libceph.ko

/lib/modules/4.18.0-13-generic/kernel/net/core:
devlink.ko  drop_monitor.ko  failover.ko  pktgen.ko

/lib/modules/4.18.0-13-generic/kernel/net/dccp:
dccp_diag.ko  dccp_ipv4.ko  dccp_ipv6.ko  dccp.ko

/lib/modules/4.18.0-13-generic/kernel/net/decnet:
decnet.ko  netfilter

/lib/modules/4.18.0-13-generic/kernel/net/decnet/netfilter:
dn_rtmsg.ko

/lib/modules/4.18.0-13-generic/kernel/net/dsa:
dsa_core.ko

/lib/modules/4.18.0-13-generic/kernel/net/hsr:
hsr.ko

/lib/modules/4.18.0-13-generic/kernel/net/ieee802154:
6lowpan  ieee802154.ko  ieee802154_socket.ko

/lib/modules/4.18.0-13-generic/kernel/net/ieee802154/6lowpan:
ieee802154_6lowpan.ko

/lib/modules/4.18.0-13-generic/kernel/net/ife:
ife.ko

/lib/modules/4.18.0-13-generic/kernel/net/ipv4:
ah4.ko           ip_tunnel.ko  tcp_highspeed.ko  tcp_westwood.ko
esp4.ko          ip_vti.ko     tcp_htcp.ko       tcp_yeah.ko
esp4_offload.ko  netfilter     tcp_hybla.ko      tunnel4.ko
fou.ko           raw_diag.ko   tcp_illinois.ko   udp_diag.ko
gre.ko           tcp_bbr.ko    tcp_lp.ko         udp_tunnel.ko
inet_diag.ko     tcp_bic.ko    tcp_nv.ko         xfrm4_mode_beet.ko
ipcomp.ko        tcp_cdg.ko    tcp_scalable.ko   xfrm4_mode_transport.ko
ip_gre.ko        tcp_dctcp.ko  tcp_vegas.ko      xfrm4_mode_tunnel.ko
ipip.ko          tcp_diag.ko   tcp_veno.ko       xfrm4_tunnel.ko

/lib/modules/4.18.0-13-generic/kernel/net/ipv4/netfilter:
arptable_filter.ko   ipt_REJECT.ko          nf_nat_snmp_basic.ko
arp_tables.ko        ipt_rpfilter.ko        nf_reject_ipv4.ko
arpt_mangle.ko       ipt_SYNPROXY.ko        nf_socket_ipv4.ko
iptable_filter.ko    nf_conntrack_ipv4.ko   nft_chain_nat_ipv4.ko
iptable_mangle.ko    nf_defrag_ipv4.ko      nft_chain_route_ipv4.ko
iptable_nat.ko       nf_dup_ipv4.ko         nft_dup_ipv4.ko
iptable_raw.ko       nf_flow_table_ipv4.ko  nft_fib_ipv4.ko
iptable_security.ko  nf_log_arp.ko          nft_masq_ipv4.ko
ip_tables.ko         nf_log_ipv4.ko         nf_tproxy_ipv4.ko
ipt_ah.ko            nf_nat_h323.ko         nft_redir_ipv4.ko
ipt_CLUSTERIP.ko     nf_nat_ipv4.ko         nft_reject_ipv4.ko
ipt_ECN.ko           nf_nat_pptp.ko
ipt_MASQUERADE.ko    nf_nat_proto_gre.ko

/lib/modules/4.18.0-13-generic/kernel/net/ipv6:
ah6.ko           ip6_gre.ko         mip6.ko             xfrm6_mode_ro.ko
esp6.ko          ip6_tunnel.ko      netfilter           xfrm6_mode_transport.ko
esp6_offload.ko  ip6_udp_tunnel.ko  sit.ko              xfrm6_mode_tunnel.ko
fou6.ko          ip6_vti.ko         tunnel6.ko          xfrm6_tunnel.ko
ila              ipcomp6.ko         xfrm6_mode_beet.ko

/lib/modules/4.18.0-13-generic/kernel/net/ipv6/ila:
ila.ko

/lib/modules/4.18.0-13-generic/kernel/net/ipv6/netfilter:
ip6table_filter.ko    ip6t_mh.ko             nf_nat_ipv6.ko
ip6table_mangle.ko    ip6t_NPT.ko            nf_reject_ipv6.ko
ip6table_nat.ko       ip6t_REJECT.ko         nf_socket_ipv6.ko
ip6table_raw.ko       ip6t_rpfilter.ko       nft_chain_nat_ipv6.ko
ip6table_security.ko  ip6t_rt.ko             nft_chain_route_ipv6.ko
ip6_tables.ko         ip6t_srh.ko            nft_dup_ipv6.ko
ip6t_ah.ko            ip6t_SYNPROXY.ko       nft_fib_ipv6.ko
ip6t_eui64.ko         nf_conntrack_ipv6.ko   nft_masq_ipv6.ko
ip6t_frag.ko          nf_defrag_ipv6.ko      nf_tproxy_ipv6.ko
ip6t_hbh.ko           nf_dup_ipv6.ko         nft_redir_ipv6.ko
ip6t_ipv6header.ko    nf_flow_table_ipv6.ko  nft_reject_ipv6.ko
ip6t_MASQUERADE.ko    nf_log_ipv6.ko

/lib/modules/4.18.0-13-generic/kernel/net/kcm:
kcm.ko

/lib/modules/4.18.0-13-generic/kernel/net/key:
af_key.ko

/lib/modules/4.18.0-13-generic/kernel/net/l2tp:
l2tp_core.ko     l2tp_eth.ko  l2tp_ip.ko       l2tp_ppp.ko
l2tp_debugfs.ko  l2tp_ip6.ko  l2tp_netlink.ko

/lib/modules/4.18.0-13-generic/kernel/net/lapb:
lapb.ko

/lib/modules/4.18.0-13-generic/kernel/net/llc:
llc2.ko  llc.ko

/lib/modules/4.18.0-13-generic/kernel/net/mac80211:
mac80211.ko

/lib/modules/4.18.0-13-generic/kernel/net/mac802154:
mac802154.ko

/lib/modules/4.18.0-13-generic/kernel/net/mpls:
mpls_gso.ko  mpls_iptunnel.ko  mpls_router.ko

/lib/modules/4.18.0-13-generic/kernel/net/netfilter:
ipset                       nft_fib_netdev.ko    xt_ipcomp.ko
ipvs                        nft_flow_offload.ko  xt_iprange.ko
nf_conncount.ko             nft_fwd_netdev.ko    xt_ipvs.ko
nf_conntrack_amanda.ko      nft_hash.ko          xt_l2tp.ko
nf_conntrack_broadcast.ko   nft_limit.ko         xt_LED.ko
nf_conntrack_ftp.ko         nft_log.ko           xt_length.ko
nf_conntrack_h323.ko        nft_masq.ko          xt_limit.ko
nf_conntrack_irc.ko         nft_nat.ko           xt_LOG.ko
nf_conntrack.ko             nft_numgen.ko        xt_mac.ko
nf_conntrack_netbios_ns.ko  nft_objref.ko        xt_mark.ko
nf_conntrack_netlink.ko     nft_queue.ko         xt_multiport.ko
nf_conntrack_pptp.ko        nft_quota.ko         xt_nat.ko
nf_conntrack_proto_gre.ko   nft_redir.ko         xt_NETMAP.ko
nf_conntrack_sane.ko        nft_reject_inet.ko   xt_nfacct.ko
nf_conntrack_sip.ko         nft_reject.ko        xt_NFLOG.ko
nf_conntrack_snmp.ko        nft_socket.ko        xt_NFQUEUE.ko
nf_conntrack_tftp.ko        x_tables.ko          xt_osf.ko
nf_dup_netdev.ko            xt_addrtype.ko       xt_owner.ko
nf_flow_table_inet.ko       xt_AUDIT.ko          xt_physdev.ko
nf_flow_table.ko            xt_bpf.ko            xt_pkttype.ko
nf_log_common.ko            xt_cgroup.ko         xt_policy.ko
nf_log_netdev.ko            xt_CHECKSUM.ko       xt_quota.ko
nf_nat_amanda.ko            xt_CLASSIFY.ko       xt_RATEEST.ko
nf_nat_ftp.ko               xt_cluster.ko        xt_rateest.ko
nf_nat_irc.ko               xt_comment.ko        xt_realm.ko
nf_nat.ko                   xt_connbytes.ko      xt_recent.ko
nf_nat_sip.ko               xt_connlabel.ko      xt_REDIRECT.ko
nf_nat_tftp.ko              xt_connlimit.ko      xt_sctp.ko
nfnetlink_acct.ko           xt_connmark.ko       xt_SECMARK.ko
nfnetlink_cthelper.ko       xt_CONNSECMARK.ko    xt_set.ko
nfnetlink_cttimeout.ko      xt_conntrack.ko      xt_socket.ko
nfnetlink.ko                xt_cpu.ko            xt_state.ko
nfnetlink_log.ko            xt_CT.ko             xt_statistic.ko
nfnetlink_queue.ko          xt_dccp.ko           xt_string.ko
nf_osf.ko                   xt_devgroup.ko       xt_TCPMSS.ko
nf_synproxy_core.ko         xt_DSCP.ko           xt_tcpmss.ko
nf_tables.ko                xt_dscp.ko           xt_TCPOPTSTRIP.ko
nf_tables_set.ko            xt_ecn.ko            xt_tcpudp.ko
nft_compat.ko               xt_esp.ko            xt_TEE.ko
nft_connlimit.ko            xt_hashlimit.ko      xt_time.ko
nft_counter.ko              xt_helper.ko         xt_TPROXY.ko
nft_ct.ko                   xt_HL.ko             xt_TRACE.ko
nft_dup_netdev.ko           xt_hl.ko             xt_u32.ko
nft_fib_inet.ko             xt_HMARK.ko
nft_fib.ko                  xt_IDLETIMER.ko

/lib/modules/4.18.0-13-generic/kernel/net/netfilter/ipset:
ip_set_bitmap_ip.ko     ip_set_hash_ipportip.ko   ip_set_hash_netnet.ko
ip_set_bitmap_ipmac.ko  ip_set_hash_ipport.ko     ip_set_hash_netport.ko
ip_set_bitmap_port.ko   ip_set_hash_ipportnet.ko  ip_set_hash_netportnet.ko
ip_set_hash_ip.ko       ip_set_hash_mac.ko        ip_set.ko
ip_set_hash_ipmac.ko    ip_set_hash_netiface.ko   ip_set_list_set.ko
ip_set_hash_ipmark.ko   ip_set_hash_net.ko

/lib/modules/4.18.0-13-generic/kernel/net/netfilter/ipvs:
ip_vs_dh.ko   ip_vs_lblc.ko   ip_vs_nq.ko      ip_vs_sed.ko
ip_vs_fo.ko   ip_vs_lblcr.ko  ip_vs_ovf.ko     ip_vs_sh.ko
ip_vs_ftp.ko  ip_vs_lc.ko     ip_vs_pe_sip.ko  ip_vs_wlc.ko
ip_vs.ko      ip_vs_mh.ko     ip_vs_rr.ko      ip_vs_wrr.ko

/lib/modules/4.18.0-13-generic/kernel/net/netlink:
netlink_diag.ko

/lib/modules/4.18.0-13-generic/kernel/net/netrom:
netrom.ko

/lib/modules/4.18.0-13-generic/kernel/net/nfc:
hci  nci  nfc_digital.ko  nfc.ko

/lib/modules/4.18.0-13-generic/kernel/net/nfc/hci:
hci.ko

/lib/modules/4.18.0-13-generic/kernel/net/nfc/nci:
nci.ko  nci_spi.ko  nci_uart.ko

/lib/modules/4.18.0-13-generic/kernel/net/nsh:
nsh.ko

/lib/modules/4.18.0-13-generic/kernel/net/openvswitch:
openvswitch.ko  vport-geneve.ko  vport-gre.ko  vport-vxlan.ko

/lib/modules/4.18.0-13-generic/kernel/net/packet:
af_packet_diag.ko

/lib/modules/4.18.0-13-generic/kernel/net/phonet:
phonet.ko  pn_pep.ko

/lib/modules/4.18.0-13-generic/kernel/net/psample:
psample.ko

/lib/modules/4.18.0-13-generic/kernel/net/rds:
rds.ko  rds_rdma.ko  rds_tcp.ko

/lib/modules/4.18.0-13-generic/kernel/net/rfkill:
rfkill-gpio.ko

/lib/modules/4.18.0-13-generic/kernel/net/rose:
rose.ko

/lib/modules/4.18.0-13-generic/kernel/net/rxrpc:
rxrpc.ko

/lib/modules/4.18.0-13-generic/kernel/net/sched:
act_bpf.ko       act_tunnel_key.ko  cls_u32.ko    sch_codel.ko     sch_pie.ko
act_connmark.ko  act_vlan.ko        em_canid.ko   sch_drr.ko       sch_plug.ko
act_csum.ko      cls_basic.ko       em_cmp.ko     sch_dsmark.ko    sch_prio.ko
act_gact.ko      cls_bpf.ko         em_ipset.ko   sch_fq_codel.ko  sch_qfq.ko
act_ipt.ko       cls_cgroup.ko      em_ipt.ko     sch_fq.ko        sch_red.ko
act_mirred.ko    cls_flower.ko      em_meta.ko    sch_gred.ko      sch_sfb.ko
act_nat.ko       cls_flow.ko        em_nbyte.ko   sch_hfsc.ko      sch_sfq.ko
act_pedit.ko     cls_fw.ko          em_text.ko    sch_hhf.ko       sch_tbf.ko
act_police.ko    cls_matchall.ko    em_u32.ko     sch_htb.ko       sch_teql.ko
act_sample.ko    cls_route.ko       sch_atm.ko    sch_ingress.ko
act_simple.ko    cls_rsvp6.ko       sch_cbq.ko    sch_mqprio.ko
act_skbedit.ko   cls_rsvp.ko        sch_cbs.ko    sch_multiq.ko
act_skbmod.ko    cls_tcindex.ko     sch_choke.ko  sch_netem.ko

/lib/modules/4.18.0-13-generic/kernel/net/sctp:
sctp_diag.ko  sctp.ko

/lib/modules/4.18.0-13-generic/kernel/net/smc:
smc_diag.ko  smc.ko

/lib/modules/4.18.0-13-generic/kernel/net/sunrpc:
auth_gss  sunrpc.ko  xprtrdma

/lib/modules/4.18.0-13-generic/kernel/net/sunrpc/auth_gss:
auth_rpcgss.ko  rpcsec_gss_krb5.ko

/lib/modules/4.18.0-13-generic/kernel/net/sunrpc/xprtrdma:
rpcrdma.ko

/lib/modules/4.18.0-13-generic/kernel/net/tipc:
diag.ko  tipc.ko

/lib/modules/4.18.0-13-generic/kernel/net/tls:
tls.ko

/lib/modules/4.18.0-13-generic/kernel/net/unix:
unix_diag.ko

/lib/modules/4.18.0-13-generic/kernel/net/vmw_vsock:
hv_sock.ko                            vmw_vsock_vmci_transport.ko
vmw_vsock_virtio_transport_common.ko  vsock_diag.ko
vmw_vsock_virtio_transport.ko         vsock.ko

/lib/modules/4.18.0-13-generic/kernel/net/wimax:
wimax.ko

/lib/modules/4.18.0-13-generic/kernel/net/wireless:
cfg80211.ko             lib80211_crypt_tkip.ko  lib80211.ko
lib80211_crypt_ccmp.ko  lib80211_crypt_wep.ko

/lib/modules/4.18.0-13-generic/kernel/net/x25:
x25.ko

/lib/modules/4.18.0-13-generic/kernel/net/xfrm:
xfrm_algo.ko  xfrm_ipcomp.ko  xfrm_user.ko

/lib/modules/4.18.0-13-generic/kernel/sound:
ac97_bus.ko  drivers   hda  isa  pcmcia  soundcore.ko  usb  xen
core         firewire  i2c  pci  soc     synth         x86


**~# lshw -C network**
  *-network                 
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 05
       serial: 00:1e:8c:f4:81:4c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:32 memory:fe600000-fe61ffff memory:fe627000-fe627fff ioport:f060(size=32)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp0s29u1u6
       serial: 6e:90:d9:65:3d:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=-------------- link=yes multicast=yes

---

### Post by camperdelarco on 2019-01-31
Current Internet situation:

[IMG]https://i.ibb.co/4Y77xnX/New-Project.jpg[/IMG]

---

### Post by chili555 on 2019-01-31
I believe the driver for your device is 8192eu and not 8192cu. Please try the steps here: [https://askubuntu.com/questions/1113739/installing-tp-link-tl-wn822n-on-ubuntu-18-04/1113922#1113922](https://askubuntu.com/questions/1113739/installing-tp-link-tl-wn822n-on-ubuntu-18-04/1113922#1113922)

---

