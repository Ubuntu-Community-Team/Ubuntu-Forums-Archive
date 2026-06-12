---
title: "wifi connects but no internet"
date: 2015-03-16
forum: Networking &amp; Wireless
---

### Post by john383 on 2015-03-16
Hello everyone, I was reading the forum about my wifi problem and saw how great you's were at solving them! I would really appreciate your expertise on this. I have linuxcnc utilizing ubuntu 10.04. I can connect a dongle or connect it directly with the network cable to my router. The direct connecting gets me nothing where the network adapter actually connects me, but does not allow the internet, (firefox) to work. Any help is very much appreciated. Here is the output: 

john@john-cnc:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux john-cnc 2.6.32-122-rtai #rtai SMP Tue Jul 27 12:44:07 CDT 2010 i686 GNU/Linux
john@john-cnc:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1503] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation Device [8086:1d2d] (rev 06)
	Kernel driver in use: ehci_hcd
--
0c:01.0 Communication controller [0780]: NetMos Technology PCI 9815 Multi-I/O Controller [9710:9815] (rev 01)
	Kernel driver in use: parport_pc
	Kernel modules: parport_pc
john@john-cnc:~$ iwconfig
lo        no wireless extensions.


wlan0     RTxx70 Wireless  ESSID:"NETGEAR62"  Nickname:"RT3070STA"
          Mode:Ad-Hoc  Frequency=2.462 GHz  Cell: 8E:B3:B8:C1:6D:47   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


john@john-cnc:~$ rfkill list all
john@john-cnc:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46425  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4207  1 nf_nat_pptp
nf_conntrack_proto_gre     3874  1 nf_conntrack_pptp
nf_nat_proto_gre        1185  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2850  1 nf_nat_tftp
nf_nat_sip              5140  0 
nf_conntrack_sip       14777  1 nf_nat_sip
nf_nat_irc              1156  0 
nf_conntrack_irc        3290  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5339  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 14921  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10545  4 iptable_nat,nf_nat
nf_conntrack           57582  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1025  1 nf_conntrack_ipv4
ip_tables               9796  2 iptable_filter,iptable_nat
x_tables               13137  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
rt2870sta             461825  1 
rt2800usb              31531  0 
rt2x00usb               8876  1 rt2800usb
rt2x00lib              26307  2 rt2800usb,rt2x00usb
led_class               2673  1 rt2x00lib
mac80211              202715  2 rt2x00usb,rt2x00lib
cfg80211              122541  2 rt2x00lib,mac80211
crc_ccitt               1261  1 rt2800usb
dm_crypt               11363  0 
binfmt_misc             6587  1 
psmouse                63213  0 
ppdev                   5259  0 
serio_raw               3978  0 
joydev                  8644  0 
parport_pc             25637  2 
xhci                   35602  0 
lp                      7028  0 
parport                30764  3 ppdev,parport_pc,lp
usbhid                 35772  0 
hid                    65804  1 usbhid
dm_raid45              81157  0 
xor                    14673  1 dm_raid45
usb_storage            38013  0 
fbcon                  35102  71 
tileblit                1987  1 fbcon
font                    7406  1 fbcon
bitblit                 4664  1 fbcon
softcursor              1151  1 bitblit
vga16fb                11161  1 
vgastate                8760  1 vga16fb
nouveau               467048  0 
ohci1394               26736  0 
ttm                    46069  1 nouveau
ahci                   31976  2 
ieee1394               76629  1 ohci1394
drm_kms_helper         27748  1 nouveau
drm                   154120  3 nouveau,ttm,drm_kms_helper
agpgart                29292  2 ttm,drm
i2c_algo_bit            4903  1 nouveau

---

### Post by wildmanne39 on 2015-03-16
Hi, first 10.04 is very outdated you will not receive any new updates not even security so I recommend that you upgrade to 14.04 then post back if WiFi does not work.

---

### Post by john383 on 2015-03-16
I can't as linuxcnc uses this and they did not upgrade the OS. They updated to debian, but my mobo/graphics card will not allow the install. So I figured I'd be able to just get internet at least for updates. But if it's impossible then I'm just going to purchase a new computer that will work. 

Thanks for your reply, I was hoping you would answer, I saw you help somebody else flawlessly,

John

---

