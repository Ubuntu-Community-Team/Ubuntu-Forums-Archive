---
title: "Belkin n300 wireless usb adapter"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Theisonews on 2011-07-19
Hello.

i goggled how to make a belkin n300 wireless usb adapter work in ubuntu.  And i tried the procedures but i can;t get it to work.

I tried:

[spoiler]Run this command:
Code:
sudo gedit /etc/udev/rules.d/network_drivers.rules

vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv

And add this line to the file (which may be empty) and save:

Code:
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"

vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv

hen run this command:
Code:
sudo gedit /etc/modprobe.d/network_drivers.conf

vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv

And add this file (and save)
Code:
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a" > /sys/bus/usb/drivers/rtl819xU/new_id


vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv


Finally, download this file:
[http://svn.debian.org/wsvn/kernel/di...rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/di...rtl8192sfw.bin)

and copy it to the directory
Code:
/lib/firmware/RTL8192SU/[/spoiler]

but it did not work.  however when i enter lsusb in the terminal i see my belkin device.

please help

---

### Post by linuxman94 on 2011-07-19
Hello,

We need to know the exact chipset of the network adaptor so could you post the results of these commands?  Please use code tags (# sign in editor).

```
sudo lshw -C network
lsusb
iwconfig
```

---

### Post by Theisonews on 2011-07-19
thanks for the quick reply.

when i entered 

sudo lshw -C network i got

```
description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c1
       serial: b8:70:f4:74:3b:5c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:90200000-9023ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:88:eb:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38 firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:90100000-90103fff
```

when i entered lsusb
[CODEBus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0402:7675 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 050d:2103 Belkin Components 
Bus 001 Device 002: ID 054c:0439 Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub][/CODE]

notice device 4 is the belkin usb im trying to get working


when i enter iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

---

### Post by linuxman94 on 2011-07-19
It should be working right now.  Have you tried connecting to a network using network manager?

---

### Post by Theisonews on 2011-07-19
i can  connect to the internet. but that is thru the internal wifi card. im trying to connect with my belkin usb.

---

### Post by linuxman94 on 2011-07-19
Might I ask why you don't want to use the internal?

---

### Post by Theisonews on 2011-07-19
i bought the belkin because it has better range. also i think the internal does not support injection.

please help

i know this is an ubuntu forum,  but im actually trying to get the belkin working with back track 5. i come to this forum because bt5 is based on ubuntu 10.04.


please please help

---

### Post by linuxman94 on 2011-07-19
Ok can you run

```
sudo modprobe -l
```

---

### Post by Theisonews on 2011-07-19
when i run that last command i get 

```
kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
kernel/sound/isa/opti9xx/snd-opti93x.ko
kernel/sound/isa/opti9xx/snd-miro.ko
kernel/sound/isa/sb/snd-sb-common.ko
kernel/sound/isa/sb/snd-sb16-dsp.ko
kernel/sound/isa/sb/snd-sb8-dsp.ko
kernel/sound/isa/sb/snd-sb8.ko
kernel/sound/isa/sb/snd-sb16.ko
kernel/sound/isa/sb/snd-sbawe.ko
kernel/sound/isa/sb/snd-jazz16.ko
kernel/sound/isa/sb/snd-sb16-csp.ko
kernel/sound/isa/sb/snd-emu8000-synth.ko
kernel/sound/isa/wavefront/snd-wavefront.ko
kernel/sound/isa/wss/snd-wss-lib.ko
kernel/sound/pci/snd-ad1889.ko
kernel/sound/pci/snd-als300.ko
kernel/sound/pci/snd-als4000.ko
kernel/sound/pci/snd-atiixp.ko
kernel/sound/pci/snd-atiixp-modem.ko
kernel/sound/pci/snd-azt3328.ko
kernel/sound/pci/snd-bt87x.ko
kernel/sound/pci/snd-cmipci.ko
kernel/sound/pci/snd-cs4281.ko
kernel/sound/pci/snd-cs5530.ko
kernel/sound/pci/snd-ens1370.ko
kernel/sound/pci/snd-ens1371.ko
kernel/sound/pci/snd-es1938.ko
kernel/sound/pci/snd-es1968.ko
kernel/sound/pci/snd-fm801.ko
kernel/sound/pci/snd-intel8x0.ko
kernel/sound/pci/snd-intel8x0m.ko
kernel/sound/pci/snd-maestro3.ko
kernel/sound/pci/snd-rme32.ko
kernel/sound/pci/snd-rme96.ko
kernel/sound/pci/snd-sis7019.ko
kernel/sound/pci/snd-sonicvibes.ko
kernel/sound/pci/snd-via82xx.ko
kernel/sound/pci/snd-via82xx-modem.ko
kernel/sound/pci/ac97/snd-ac97-codec.ko
kernel/sound/pci/ali5451/snd-ali5451.ko
kernel/sound/pci/asihpi/snd-asihpi.ko
kernel/sound/pci/au88x0/snd-au8810.ko
kernel/sound/pci/au88x0/snd-au8820.ko
kernel/sound/pci/au88x0/snd-au8830.ko
kernel/sound/pci/aw2/snd-aw2.ko
kernel/sound/pci/ctxfi/snd-ctxfi.ko
kernel/sound/pci/ca0106/snd-ca0106.ko
kernel/sound/pci/cs46xx/snd-cs46xx.ko
kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
kernel/sound/pci/lx6464es/snd-lx6464es.ko
kernel/sound/pci/echoaudio/snd-darla20.ko
kernel/sound/pci/echoaudio/snd-gina20.ko
kernel/sound/pci/echoaudio/snd-layla20.ko
kernel/sound/pci/echoaudio/snd-darla24.ko
kernel/sound/pci/echoaudio/snd-gina24.ko
kernel/sound/pci/echoaudio/snd-layla24.ko
kernel/sound/pci/echoaudio/snd-mona.ko
kernel/sound/pci/echoaudio/snd-mia.ko
kernel/sound/pci/echoaudio/snd-echo3g.ko
kernel/sound/pci/echoaudio/snd-indigo.ko
kernel/sound/pci/echoaudio/snd-indigoio.ko
kernel/sound/pci/echoaudio/snd-indigodj.ko
kernel/sound/pci/echoaudio/snd-indigoiox.ko
kernel/sound/pci/echoaudio/snd-indigodjx.ko
kernel/sound/pci/emu10k1/snd-emu10k1.ko
kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
kernel/sound/pci/emu10k1/snd-emu10k1x.ko
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/pci/ice1712/snd-ice1712.ko
kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
kernel/sound/pci/ice1712/snd-ice1724.ko
kernel/sound/pci/korg1212/snd-korg1212.ko
kernel/sound/pci/mixart/snd-mixart.ko
kernel/sound/pci/nm256/snd-nm256.ko
kernel/sound/pci/oxygen/snd-oxygen-lib.ko
kernel/sound/pci/oxygen/snd-oxygen.ko
kernel/sound/pci/oxygen/snd-virtuoso.ko
kernel/sound/pci/pcxhr/snd-pcxhr.ko
kernel/sound/pci/riptide/snd-riptide.ko
kernel/sound/pci/rme9652/snd-rme9652.ko
kernel/sound/pci/rme9652/snd-hdsp.ko
kernel/sound/pci/rme9652/snd-hdspm.ko
kernel/sound/pci/trident/snd-trident.ko
kernel/sound/pci/ymfpci/snd-ymfpci.ko
kernel/sound/pci/vx222/snd-vx222.ko
kernel/sound/synth/snd-util-mem.ko
kernel/sound/synth/emux/snd-emux-synth.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usbmidi-lib.ko
kernel/sound/usb/misc/snd-ua101.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko
kernel/sound/pcmcia/vx/snd-vxpocket.ko
kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
kernel/sound/soc/snd-soc-core.ko
kernel/sound/soc/codecs/snd-soc-88pm860x.ko
kernel/sound/soc/codecs/snd-soc-ad1836.ko
kernel/sound/soc/codecs/snd-soc-ad193x.ko
kernel/sound/soc/codecs/snd-soc-ad73311.ko
kernel/sound/soc/codecs/snd-soc-ads117x.ko
kernel/sound/soc/codecs/snd-soc-ak4104.ko
kernel/sound/soc/codecs/snd-soc-ak4535.ko
kernel/sound/soc/codecs/snd-soc-ak4642.ko
kernel/sound/soc/codecs/snd-soc-ak4671.ko
kernel/sound/soc/codecs/snd-soc-cs42l51.ko
kernel/sound/soc/codecs/snd-soc-cs4270.ko
kernel/sound/soc/codecs/snd-soc-cx20442.ko
kernel/sound/soc/codecs/snd-soc-da7210.ko
kernel/sound/soc/codecs/snd-soc-l3.ko
kernel/sound/soc/codecs/snd-soc-max98088.ko
kernel/sound/soc/codecs/snd-soc-pcm3008.ko
kernel/sound/soc/codecs/snd-soc-alc5623.ko
kernel/sound/soc/codecs/snd-soc-spdif.ko
kernel/sound/soc/codecs/snd-soc-ssm2602.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
kernel/sound/soc/codecs/snd-soc-twl4030.ko
kernel/sound/soc/codecs/snd-soc-twl6040.ko
kernel/sound/soc/codecs/snd-soc-uda134x.ko
kernel/sound/soc/codecs/snd-soc-uda1380.ko
kernel/sound/soc/codecs/snd-soc-wl1273.ko
kernel/sound/soc/codecs/snd-soc-wm8350.ko
kernel/sound/soc/codecs/snd-soc-wm8400.ko
kernel/sound/soc/codecs/snd-soc-wm8510.ko
kernel/sound/soc/codecs/snd-soc-wm8523.ko
kernel/sound/soc/codecs/snd-soc-wm8580.ko
kernel/sound/soc/codecs/snd-soc-wm8711.ko
kernel/sound/soc/codecs/snd-soc-wm8727.ko
kernel/sound/soc/codecs/snd-soc-wm8728.ko
kernel/sound/soc/codecs/snd-soc-wm8731.ko
kernel/sound/soc/codecs/snd-soc-wm8737.ko
kernel/sound/soc/codecs/snd-soc-wm8741.ko
kernel/sound/soc/codecs/snd-soc-wm8750.ko
kernel/sound/soc/codecs/snd-soc-wm8753.ko
kernel/sound/soc/codecs/snd-soc-wm8770.ko
kernel/sound/soc/codecs/snd-soc-wm8776.ko
kernel/sound/soc/codecs/snd-soc-wm8804.ko
kernel/sound/soc/codecs/snd-soc-wm8900.ko
kernel/sound/soc/codecs/snd-soc-wm8903.ko
kernel/sound/soc/codecs/snd-soc-wm8904.ko
kernel/sound/soc/codecs/snd-soc-wm8940.ko
kernel/sound/soc/codecs/snd-soc-wm8955.ko
kernel/sound/soc/codecs/snd-soc-wm8960.ko
kernel/sound/soc/codecs/snd-soc-wm8961.ko
kernel/sound/soc/codecs/snd-soc-wm8962.ko
kernel/sound/soc/codecs/snd-soc-wm8971.ko
kernel/sound/soc/codecs/snd-soc-wm8974.ko
kernel/sound/soc/codecs/snd-soc-wm8978.ko
kernel/sound/soc/codecs/snd-soc-wm8985.ko
kernel/sound/soc/codecs/snd-soc-wm8988.ko
kernel/sound/soc/codecs/snd-soc-wm8990.ko
kernel/sound/soc/codecs/snd-soc-wm8993.ko
kernel/sound/soc/codecs/snd-soc-wm8994.ko
kernel/sound/soc/codecs/snd-soc-wm8995.ko
kernel/sound/soc/codecs/snd-soc-wm9081.ko
kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
kernel/sound/soc/codecs/snd-soc-max9877.ko
kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
kernel/sound/soc/codecs/snd-soc-wm2000.ko
kernel/sound/soc/codecs/snd-soc-wm9090.ko
kernel/sound/ac97_bus.ko
kernel/arch/x86/oprofile/oprofile.ko
kernel/net/core/pktgen.ko
kernel/net/802/p8022.ko
kernel/net/802/psnap.ko
kernel/net/802/p8023.ko
kernel/net/802/stp.ko
kernel/net/802/garp.ko
kernel/net/sched/act_police.ko
kernel/net/sched/act_gact.ko
kernel/net/sched/act_mirred.ko
kernel/net/sched/act_ipt.ko
kernel/net/sched/act_nat.ko
kernel/net/sched/act_pedit.ko
kernel/net/sched/act_simple.ko
kernel/net/sched/act_skbedit.ko
kernel/net/sched/act_csum.ko
kernel/net/sched/sch_cbq.ko
kernel/net/sched/sch_htb.ko
kernel/net/sched/sch_hfsc.ko
kernel/net/sched/sch_red.ko
kernel/net/sched/sch_gred.ko
kernel/net/sched/sch_ingress.ko
kernel/net/sched/sch_dsmark.ko
kernel/net/sched/sch_sfq.ko
kernel/net/sched/sch_tbf.ko
kernel/net/sched/sch_teql.ko
kernel/net/sched/sch_prio.ko
kernel/net/sched/sch_multiq.ko
kernel/net/sched/sch_atm.ko
kernel/net/sched/sch_netem.ko
kernel/net/sched/sch_drr.ko
kernel/net/sched/cls_u32.ko
kernel/net/sched/cls_route.ko
kernel/net/sched/cls_fw.ko
kernel/net/sched/cls_rsvp.ko
kernel/net/sched/cls_tcindex.ko
kernel/net/sched/cls_rsvp6.ko
kernel/net/sched/cls_basic.ko
kernel/net/sched/cls_flow.ko
kernel/net/sched/em_cmp.ko
kernel/net/sched/em_nbyte.ko
kernel/net/sched/em_u32.ko
kernel/net/sched/em_meta.ko
kernel/net/sched/em_text.ko
kernel/net/netfilter/nfnetlink.ko
kernel/net/netfilter/nfnetlink_queue.ko
kernel/net/netfilter/nfnetlink_log.ko
kernel/net/netfilter/nf_conntrack.ko
kernel/net/netfilter/nf_conntrack_proto_dccp.ko
kernel/net/netfilter/nf_conntrack_proto_gre.ko
kernel/net/netfilter/nf_conntrack_proto_sctp.ko
kernel/net/netfilter/nf_conntrack_proto_udplite.ko
kernel/net/netfilter/nf_conntrack_netlink.ko
kernel/net/netfilter/nf_conntrack_amanda.ko
kernel/net/netfilter/nf_conntrack_ftp.ko
kernel/net/netfilter/nf_conntrack_h323.ko
kernel/net/netfilter/nf_conntrack_irc.ko
kernel/net/netfilter/nf_conntrack_netbios_ns.ko
kernel/net/netfilter/nf_conntrack_pptp.ko
kernel/net/netfilter/nf_conntrack_sane.ko
kernel/net/netfilter/nf_conntrack_sip.ko
kernel/net/netfilter/nf_conntrack_tftp.ko
kernel/net/netfilter/nf_tproxy_core.ko
kernel/net/netfilter/x_tables.ko
kernel/net/netfilter/xt_tcpudp.ko
kernel/net/netfilter/xt_mark.ko
kernel/net/netfilter/xt_connmark.ko
kernel/net/netfilter/xt_CHECKSUM.ko
kernel/net/netfilter/xt_CLASSIFY.ko
kernel/net/netfilter/xt_CONNSECMARK.ko
kernel/net/netfilter/xt_CT.ko
kernel/net/netfilter/xt_DSCP.ko
kernel/net/netfilter/xt_HL.ko
kernel/net/netfilter/xt_LED.ko
kernel/net/netfilter/xt_NFLOG.ko
kernel/net/netfilter/xt_NFQUEUE.ko
kernel/net/netfilter/xt_NOTRACK.ko
kernel/net/netfilter/xt_RATEEST.ko
kernel/net/netfilter/xt_SECMARK.ko
kernel/net/netfilter/xt_TPROXY.ko
kernel/net/netfilter/xt_TCPMSS.ko
kernel/net/netfilter/xt_TEE.ko
kernel/net/netfilter/xt_TRACE.ko
kernel/net/netfilter/xt_IDLETIMER.ko
kernel/net/netfilter/xt_cluster.ko
kernel/net/netfilter/xt_comment.ko
kernel/net/netfilter/xt_connbytes.ko
kernel/net/netfilter/xt_connlimit.ko
kernel/net/netfilter/xt_conntrack.ko
kernel/net/netfilter/xt_cpu.ko
kernel/net/netfilter/xt_dccp.ko
kernel/net/netfilter/xt_dscp.ko
kernel/net/netfilter/xt_esp.ko
kernel/net/netfilter/xt_hashlimit.ko
kernel/net/netfilter/xt_helper.ko
kernel/net/netfilter/xt_hl.ko
kernel/net/netfilter/xt_iprange.ko
kernel/net/netfilter/xt_ipvs.ko
kernel/net/netfilter/xt_length.ko
kernel/net/netfilter/xt_limit.ko
kernel/net/netfilter/xt_mac.ko
kernel/net/netfilter/xt_multiport.ko
kernel/net/netfilter/xt_osf.ko
kernel/net/netfilter/xt_owner.ko
kernel/net/netfilter/xt_physdev.ko
kernel/net/netfilter/xt_pkttype.ko
kernel/net/netfilter/xt_policy.ko
kernel/net/netfilter/xt_quota.ko
kernel/net/netfilter/xt_rateest.ko
kernel/net/netfilter/xt_realm.ko
kernel/net/netfilter/xt_recent.ko
kernel/net/netfilter/xt_sctp.ko
kernel/net/netfilter/xt_socket.ko
kernel/net/netfilter/xt_state.ko
kernel/net/netfilter/xt_statistic.ko
kernel/net/netfilter/xt_string.ko
kernel/net/netfilter/xt_tcpmss.ko
kernel/net/netfilter/xt_time.ko
kernel/net/netfilter/xt_u32.ko
kernel/net/netfilter/ipvs/ip_vs.ko
kernel/net/netfilter/ipvs/ip_vs_rr.ko
kernel/net/netfilter/ipvs/ip_vs_wrr.ko
kernel/net/netfilter/ipvs/ip_vs_lc.ko
kernel/net/netfilter/ipvs/ip_vs_wlc.ko
kernel/net/netfilter/ipvs/ip_vs_lblc.ko
kernel/net/netfilter/ipvs/ip_vs_lblcr.ko
kernel/net/netfilter/ipvs/ip_vs_dh.ko
kernel/net/netfilter/ipvs/ip_vs_sh.ko
kernel/net/netfilter/ipvs/ip_vs_sed.ko
kernel/net/netfilter/ipvs/ip_vs_nq.ko
kernel/net/netfilter/ipvs/ip_vs_ftp.ko
kernel/net/netfilter/ipvs/ip_vs_pe_sip.ko
kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat.ko
kernel/net/ipv4/netfilter/nf_defrag_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat_amanda.ko
kernel/net/ipv4/netfilter/nf_nat_ftp.ko
kernel/net/ipv4/netfilter/nf_nat_h323.ko
kernel/net/ipv4/netfilter/nf_nat_irc.ko
kernel/net/ipv4/netfilter/nf_nat_pptp.ko
kernel/net/ipv4/netfilter/nf_nat_sip.ko
kernel/net/ipv4/netfilter/nf_nat_snmp_basic.ko
kernel/net/ipv4/netfilter/nf_nat_tftp.ko
kernel/net/ipv4/netfilter/nf_nat_proto_dccp.ko
kernel/net/ipv4/netfilter/nf_nat_proto_gre.ko
kernel/net/ipv4/netfilter/nf_nat_proto_udplite.ko
kernel/net/ipv4/netfilter/nf_nat_proto_sctp.ko
kernel/net/ipv4/netfilter/ip_tables.ko
kernel/net/ipv4/netfilter/iptable_filter.ko
kernel/net/ipv4/netfilter/iptable_mangle.ko
kernel/net/ipv4/netfilter/iptable_nat.ko
kernel/net/ipv4/netfilter/iptable_raw.ko
kernel/net/ipv4/netfilter/iptable_security.ko
kernel/net/ipv4/netfilter/ipt_addrtype.ko
kernel/net/ipv4/netfilter/ipt_ah.ko
kernel/net/ipv4/netfilter/ipt_ecn.ko
kernel/net/ipv4/netfilter/ipt_CLUSTERIP.ko
kernel/net/ipv4/netfilter/ipt_ECN.ko
kernel/net/ipv4/netfilter/ipt_LOG.ko
kernel/net/ipv4/netfilter/ipt_MASQUERADE.ko
kernel/net/ipv4/netfilter/ipt_NETMAP.ko
kernel/net/ipv4/netfilter/ipt_REDIRECT.ko
kernel/net/ipv4/netfilter/ipt_REJECT.ko
kernel/net/ipv4/netfilter/ipt_ULOG.ko
kernel/net/ipv4/netfilter/arp_tables.ko
kernel/net/ipv4/netfilter/arpt_mangle.ko
kernel/net/ipv4/netfilter/arptable_filter.ko
kernel/net/ipv4/netfilter/ip_queue.ko
kernel/net/ipv4/ipip.ko
kernel/net/ipv4/gre.ko
kernel/net/ipv4/ip_gre.ko
kernel/net/ipv4/ah4.ko
kernel/net/ipv4/esp4.ko
kernel/net/ipv4/ipcomp.ko
kernel/net/ipv4/xfrm4_tunnel.ko
kernel/net/ipv4/xfrm4_mode_beet.ko
kernel/net/ipv4/tunnel4.ko
kernel/net/ipv4/xfrm4_mode_transport.ko
kernel/net/ipv4/xfrm4_mode_tunnel.ko
kernel/net/ipv4/tcp_probe.ko
kernel/net/ipv4/tcp_bic.ko
kernel/net/ipv4/tcp_westwood.ko
kernel/net/ipv4/tcp_highspeed.ko
kernel/net/ipv4/tcp_hybla.ko
kernel/net/ipv4/tcp_htcp.ko
kernel/net/ipv4/tcp_vegas.ko
kernel/net/ipv4/tcp_veno.ko
kernel/net/ipv4/tcp_scalable.ko
kernel/net/ipv4/tcp_lp.ko
kernel/net/ipv4/tcp_yeah.ko
kernel/net/ipv4/tcp_illinois.ko
kernel/net/xfrm/xfrm_user.ko
kernel/net/xfrm/xfrm_ipcomp.ko
kernel/net/ipv6/netfilter/ip6_tables.ko
kernel/net/ipv6/netfilter/ip6table_filter.ko
kernel/net/ipv6/netfilter/ip6table_mangle.ko
kernel/net/ipv6/netfilter/ip6_queue.ko
kernel/net/ipv6/netfilter/ip6table_raw.ko
kernel/net/ipv6/netfilter/ip6table_security.ko
kernel/net/ipv6/netfilter/nf_conntrack_ipv6.ko
kernel/net/ipv6/netfilter/nf_defrag_ipv6.ko
kernel/net/ipv6/netfilter/ip6t_ah.ko
kernel/net/ipv6/netfilter/ip6t_eui64.ko
kernel/net/ipv6/netfilter/ip6t_frag.ko
kernel/net/ipv6/netfilter/ip6t_ipv6header.ko
kernel/net/ipv6/netfilter/ip6t_mh.ko
kernel/net/ipv6/netfilter/ip6t_hbh.ko
kernel/net/ipv6/netfilter/ip6t_rt.ko
kernel/net/ipv6/netfilter/ip6t_LOG.ko
kernel/net/ipv6/netfilter/ip6t_REJECT.ko
kernel/net/ipv6/ah6.ko
kernel/net/ipv6/esp6.ko
kernel/net/ipv6/ipcomp6.ko
kernel/net/ipv6/xfrm6_tunnel.ko
kernel/net/ipv6/tunnel6.ko
kernel/net/ipv6/xfrm6_mode_transport.ko
kernel/net/ipv6/xfrm6_mode_tunnel.ko
kernel/net/ipv6/xfrm6_mode_ro.ko
kernel/net/ipv6/xfrm6_mode_beet.ko
kernel/net/ipv6/sit.ko
kernel/net/ipv6/ip6_tunnel.ko
kernel/net/8021q/8021q.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/llc/llc.ko
kernel/net/llc/llc2.ko
kernel/net/key/af_key.ko
kernel/net/bridge/bridge.ko
kernel/net/bridge/netfilter/ebtables.ko
kernel/net/bridge/netfilter/ebtable_broute.ko
kernel/net/bridge/netfilter/ebtable_filter.ko
kernel/net/bridge/netfilter/ebtable_nat.ko
kernel/net/bridge/netfilter/ebt_802_3.ko
kernel/net/bridge/netfilter/ebt_among.ko
kernel/net/bridge/netfilter/ebt_arp.ko
kernel/net/bridge/netfilter/ebt_ip.ko
kernel/net/bridge/netfilter/ebt_ip6.ko
kernel/net/bridge/netfilter/ebt_limit.ko
kernel/net/bridge/netfilter/ebt_mark_m.ko
kernel/net/bridge/netfilter/ebt_pkttype.ko
kernel/net/bridge/netfilter/ebt_stp.ko
kernel/net/bridge/netfilter/ebt_vlan.ko
kernel/net/bridge/netfilter/ebt_arpreply.ko
kernel/net/bridge/netfilter/ebt_mark.ko
kernel/net/bridge/netfilter/ebt_dnat.ko
kernel/net/bridge/netfilter/ebt_redirect.ko
kernel/net/bridge/netfilter/ebt_snat.ko
kernel/net/bridge/netfilter/ebt_log.ko
kernel/net/bridge/netfilter/ebt_ulog.ko
kernel/net/bridge/netfilter/ebt_nflog.ko
kernel/net/ipx/ipx.ko
kernel/net/appletalk/appletalk.ko
kernel/net/wanrouter/wanrouter.ko
kernel/net/x25/x25.ko
kernel/net/lapb/lapb.ko
kernel/net/netrom/netrom.ko
kernel/net/rose/rose.ko
kernel/net/ax25/ax25.ko
kernel/net/can/can.ko
kernel/net/can/can-raw.ko
kernel/net/can/can-bcm.ko
kernel/net/irda/irda.ko
kernel/net/irda/irlan/irlan.ko
kernel/net/irda/irnet/irnet.ko
kernel/net/irda/ircomm/ircomm.ko
kernel/net/irda/ircomm/ircomm-tty.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/sco.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/net/sunrpc/sunrpc.ko
kernel/net/sunrpc/auth_gss/auth_rpcgss.ko
kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko
kernel/net/sunrpc/xprtrdma/xprtrdma.ko
kernel/net/sunrpc/xprtrdma/svcrdma.ko
kernel/net/rxrpc/af-rxrpc.ko
kernel/net/rxrpc/rxkad.ko
kernel/net/atm/atm.ko
kernel/net/atm/clip.ko
kernel/net/atm/br2684.ko
kernel/net/atm/lec.ko
kernel/net/atm/mpoa.ko
kernel/net/atm/pppoatm.ko
kernel/net/l2tp/l2tp_core.ko
kernel/net/l2tp/l2tp_ppp.ko
kernel/net/decnet/netfilter/dn_rtmsg.ko
kernel/net/decnet/decnet.ko
kernel/net/econet/econet.ko
kernel/net/phonet/phonet.ko
kernel/net/phonet/pn_pep.ko
kernel/net/dccp/dccp.ko
kernel/net/dccp/dccp_ipv4.ko
kernel/net/dccp/dccp_ipv6.ko
kernel/net/dccp/dccp_diag.ko
kernel/net/dccp/dccp_probe.ko
kernel/net/sctp/sctp.ko
kernel/net/sctp/sctp_probe.ko
kernel/net/rds/rds.ko
kernel/net/rds/rds_rdma.ko
kernel/net/rds/rds_tcp.ko
kernel/net/mac80211/mac80211.ko
kernel/net/tipc/tipc.ko
kernel/net/rfkill/rfkill.ko
kernel/net/9p/9pnet.ko
kernel/net/9p/9pnet_virtio.ko
kernel/net/9p/9pnet_rdma.ko
kernel/net/caif/caif.ko
kernel/net/caif/chnl_net.ko
kernel/net/caif/caif_socket.ko
kernel/net/ieee802154/ieee802154.ko
kernel/net/ieee802154/af_802154.ko
kernel/net/wimax/wimax.ko
kernel/net/ceph/libceph.ko
kernel/net/batman-adv/batman-adv.ko
kernel/lib/crc-ccitt.ko
kernel/lib/crc-itu-t.ko
kernel/lib/crc7.ko
kernel/lib/libcrc32c.ko
kernel/lib/zlib_deflate/zlib_deflate.ko
kernel/lib/reed_solomon/reed_solomon.ko
kernel/lib/raid6/raid6_pq.ko
kernel/lib/ts_kmp.ko
kernel/lib/ts_bm.ko
kernel/lib/ts_fsm.ko
kernel/lib/lru_cache.ko
kernel/drivers/net/wireless/rtl8187/r8187.ko
kernel/drivers/net/wireless/rtl_ieee80211/ieee80211_crypt_wep-rtl.ko
kernel/drivers/net/wireless/rtl_ieee80211/ieee80211_crypt_ccmp-rtl.ko
kernel/drivers/net/wireless/rtl_ieee80211/ieee80211_crypt-rtl.ko
kernel/drivers/net/wireless/rtl_ieee80211/ieee80211-rtl.ko
kernel/drivers/net/wireless/rtl_ieee80211/ieee80211_crypt_tkip-rtl.ko


```

---

### Post by linuxman94 on 2011-07-19
Follow these instructions again because it does not appear that the driver is being loaded.
[http://ubuntuforums.org/showthread.php?t=1522815]("http://ubuntuforums.org/showthread.php?t=1522815")

---

### Post by linuxman94 on 2011-07-19
Calling someone else to pick this up from here.  Need to go to sleep :P

---

### Post by Theisonews on 2011-07-19
thanks i will. i have to reboot to bt5


also i have an other question.


i want to install a firmware and drivers for the internal wifi.

via the procedures of this forum [http://forum.aircrack-ng.org/index.php?topic=10502.0]("http://forum.aircrack-ng.org/index.php?topic=10502.0")

im not sure what files to download.  my internal wifi is a broadcom brcm80211

---

### Post by linuxman94 on 2011-07-19
Download the latest snapshot from [here]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=shortlog") and do as he says.  Extract the brcm folder to /lib/firmware and rename as instructed.

---

### Post by Theisonews on 2011-07-19
i did, i followed the instructions on that forum,  i think. i have to disable my internal card first and then select my usb.  so how do i do that?

---

### Post by linuxman94 on 2011-07-19
If your laptop has a hardware switch or fn key to disable wireless use that.  If you don't want to ever use the internal for a while, do this:

```
gksudo gedit /etc/modprobe.d/blacklist
```

Then add this:

```
r8187
```

Save and close, then reboot.

If you want it to be temporary, figure out which wireless interface you want to disable using ```
sudo iwconfig -l
```  then disable it with ```
sudo iwconfig wlanX down
``` Where X is the wlan number.

---

### Post by Theisonews on 2011-07-19
sorry  but im stumped.  in that link you gave  there is a long list. i dont now which one to download so i downloaded 2 things compat-wireless-.tar.bz2 and linux-firmware-8ce599d.tar.gz

i extracted  compat-wireless-.tar.bz2 but i cant extract the gz

---

### Post by Theisonews on 2011-07-19
ok i extracted it.  standby

---

### Post by Theisonews on 2011-07-19
ok i added and rename the bcrm files  which is the firm ware. but how do i add the drivers?

---

### Post by Theisonews on 2011-07-19
no luck, now bt5 doesn't detect the internal wifi card


i followed the procedures of this website [http://forum.aircrack-ng.org/index.php?topic=10502.0]("http://forum.aircrack-ng.org/index.php?topic=10502.0")

i downloaded the firmware named: linux-firmware-8ce599d.tar.gz

i downloaded the driver packaged named: compat-wireless-2.6.tar.bz2

i renamed the filnes as it said to and put it in the /lib/firmware.

i ran the ./script command and then did the driver select. and chose bcrm80211 drivers.

and now bt5 says i have no wireless card.  PLease help

---

### Post by geek.de.nz on 2012-05-30
Hi, I'm looking into buying this adapter as well and wondering if it will work in Ubuntu out of the box. Can you please let me know whether it works?

Thanks!

---

