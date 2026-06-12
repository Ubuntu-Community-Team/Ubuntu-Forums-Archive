---
title: "Wireless low performance , connection drops, slow or no connectivity ubuntu 12.04"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by morishke on 2013-11-07
I have [FONT=arial]difficulties [/FONT]connecting to wireless networks, Its not getting connected on the usual spot, and when its able to reach the connection, after 20- 30 minutes  connection drops. 
It used to work fine after Ubuntu 12.04 fresh installation and progressively the wireless connectivity its getting worst after a few weeks

When boot on windows  connection its stable, it only got disabled 1 time yesterday

I recently upgarded to a newer kernel version but im not possitive if the issue started since then


Already tryed:
Install Wicd , same issue so i removed it
Checked available for all users on IPv4
And set IPv to Disabled
Ran a debug wireless update from synaptic
Installed power management tool


My guess so far i, ts power management related issue ,due to the fact that sometimes when just turn on the computer it connects faster,  and after a few minutes the issue starts and eventually loose connectivity

Any suggestion?



cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
Linux Universe 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: alx
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
    Kernel driver in use: rtl8192ce




lsusb
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub




iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off



rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



lsmod
Module                  Size  Used by
dm_crypt               23051  0 
bnep                   18258  0 
rfcomm                 47864  0 
bluetooth             247165  4 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
xt_hl                  12521  6 
ip6t_rt                12529  3 
nf_conntrack_ipv6      18387  7 
nf_defrag_ipv6         17463  1 nf_conntrack_ipv6 
ipt_REJECT             12576  1 
xt_LOG                 17504  9 
xt_limit               12711  12 
xt_tcpudp              12603  18 
xt_addrtype            12713  4 
nf_conntrack_ipv4      14538  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  14 
ip6table_filter        12815  1 
ip6_tables             27502  1 ip6table_filter
snd_hda_codec_realtek    79916  1 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
snd_hda_codec_hdmi     37463  1 
nf_nat_ftp             12675  0 
snd_hda_intel          44339  5 
nf_nat                 26158  1 nf_nat_ftp
snd_hda_codec         141761  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
nf_conntrack_ftp       13435  1 nf_nat_ftp
wl                   3074618  0 
nf_conntrack           83996  8 nf_conntrack_ipv6,nf_conntrack_ipv4,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ftp
snd_hwdep              13668  1 snd_hda_codec
iptable_filter         12810  1 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
ip_tables              27473  1 iptable_filter
snd_rawmidi            30417  1 snd_seq_midi
arc4                   12573  2 
snd_seq_midi_event     14899  1 snd_seq_midi
lib80211               14352  1 wl
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
joydev                 17613  0 
kvm_amd                60205  0 
snd_timer              29989  2 snd_pcm,snd_seq
kvm                   455932  1 kvm_amd
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
x_tables               29938  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
rtl8192ce              58733  0 
rtl8192c_common        49561  1 rtl8192ce
rtlwifi                81225  1 rtl8192ce
rts5139               351018  0 
mac80211              630977  3 rtl8192ce,rtl8192c_common,rtlwifi
snd                    69533  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
cfg80211              525326  3 wl,rtlwifi,mac80211
psmouse                97873  0 
alx                    73230  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
microcode              23017  0 
mdio                   13807  1 alx
mac_hid                13253  0 
shpchp                 37201  0 
i2c_piix4              13459  0 
k10temp                13173  0 
serio_raw              13215  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ghash_clmulni_intel    13259  0 
aesni_intel            55495  537 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
ahci                   25879  2 
radeon                960964  3 
libahci                31606  1 ahci
ttm                    84051  1 radeon
drm_kms_helper         49597  1 radeon
drm                   287564  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13564  1 radeon
video                  19652  0


SOLVED:

I just switched to channel 1 on the Modem , its hilarious how i didn't tried the basic stuff first, the good part its that during this process i finally have another distro installed that i actually like a lot,

---

### Post by tgalati4 on 2013-11-07
Install wifi-radar and count how many wireless networks that show up.  It's possible that your area is saturated with wireless and you are experiencing interference.  Also check for the power-saving levels for your wireless and turn them off.  Sometimes the wireless power-saving will cause disconnections especially when the wireless spectrum is saturated with different networks.

---

### Post by morishke on 2013-11-08
> **tgalati4 said:**
> Install wifi-radar and count how many wireless networks that show up.  It's possible that your area is saturated with wireless and you are experiencing interference.  Also check for the power-saving levels for your wireless and turn them off.  Sometimes the wireless power-saving will cause disconnections especially when the wireless spectrum is saturated with different networks.





I defnetly see a lot of wireless networks
is there a way to prevent the interference


i edited
sudo gedit /etc/rc.local


and added 
sleep 10
iwconfig wlan0 power off


and restart


when run iwconfig shows:


iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Motorola"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:00:B1:A4:1B   
          Bit Rate:18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:678   Missed beacon:0




Issue persists , is that the correct procedure
or there is another way to manage the wireless powersettings

---

