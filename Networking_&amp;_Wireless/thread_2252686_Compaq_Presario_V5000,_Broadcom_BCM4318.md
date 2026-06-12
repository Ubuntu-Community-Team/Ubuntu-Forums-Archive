---
title: "Compaq Presario V5000, Broadcom BCM4318"
date: 2014-11-13
forum: Networking &amp; Wireless
---

### Post by martyn.boyd on 2014-11-13
I've been running Ubuntu for About 18 months now with few problems. However, after a few boot problems I changed the CMOS battery and thats where my problems started. When I re-booted, I had lost the WiFi connection. Using the switch on the machine to try switching back on failed, so thats when I started trying various "solutions" from these forums and beyond, using various terminal commands etc with no luck, I checked the BIOS settings and found there was no Networking option. I then found I hadn't properly put the Network card back in the slot! I did this, checked the BIOS and Networking was disabled so I  enabled it. Thinking this would now be sorted I re-booted but still no WiFi.I tried using the switch and re-booting - nothing. I now fear there was actually nothing wrong other than the Card not being in the slot and I've caused unnecessary and now irreparable problems by messing with drivers, terminal commands etc!

Ready to bin this now - would appreciate any help to solve as a last ditch attempt first though - but please be patient, I'm not very good at this, obviously! hoping these help....

cat /etc/lsb-release;uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
Linux Presario-V5000-EW835EA-ABU 3.13.0-40-generic #68-Ubuntu SMP Tue Nov 4 01:48:53 UTC 2014 i686 athlon i686 GNU/Linux

sudo lshw -C network
 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:01:cc:37
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.83 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

rfkill lst all

This doesn't work...

lsmod

Module                  Size  Used by
cuse                   13213  3 
dm_crypt               22589  1 
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
snd_atiixp             19305  2 
snd_atiixp_modem       18670  5 
snd_ac97_codec        105709  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  5 snd_ac97_codec,snd_atiixp_modem,snd_atiixp
ip6t_REJECT            12809  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
snd_page_alloc         14230  3 snd_pcm,snd_atiixp_modem,snd_atiixp
snd_seq_midi           13132  0 
nf_conntrack_ipv6      14318  8 
nf_defrag_ipv6         26163  1 nf_conntrack_ipv6
rfcomm                 53664  4 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
snd_seq_midi_event     14475  1 snd_seq_midi
ipt_REJECT             12485  1 
xt_LOG                 17445  10 
xt_limit               12541  13 
snd_rawmidi            25135  1 snd_seq_midi
xt_tcpudp              12756  18 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  8 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  16 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
binfmt_misc            13140  1 
ip6table_filter        12711  1 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 20861  1 nf_nat_ftp
snd_timer              28584  2 snd_pcm,snd_seq
nf_conntrack_ftp       14056  1 nf_nat_ftp
nf_conntrack           83685  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
joydev                 17101  0 
snd                    60939  21 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_atiixp_modem,snd_atiixp,snd_seq_midi
k8temp                 12842  0 
serio_raw              13230  0 
soundcore              12600  1 snd
i2c_piix4              17723  0 
parport_pc             31981  0 
ppdev                  17391  0 
b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43
shpchp                 32128  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
radeon               1420704  3 
i2c_algo_bit           13197  1 radeon
ttm                    72725  1 radeon
8139too                32571  0 
psmouse                91357  0 
drm_kms_helper         48868  1 radeon
8139cp                 27171  0 
mii                    13654  2 8139cp,8139too
video                  18903  0 
pata_atiixp            13058  2 
drm                   244037  5 ttm,drm_kms_helper,radeon
wmi                    18673  1 hp_wmi
ati_agp                13177  0

---

### Post by chili555 on 2014-11-13
> rfkill lst all

This doesn't work...
How about:```
rfkill list all
```Is there an error, a beep, a squeak, sparks, smoke?? What doesn't work?

May we see:```
dmesg | grep b43
```

---

### Post by martyn.boyd on 2014-11-14
Hi - many thanks for the response! When I enter 

rfkill list all

It simply returns to the command input prompt - that's what I meant by "This doesn't work". I did make a typo but the correct command is just the same...

When I try dmesg | grep b43
[   25.254734] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   25.296062] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   25.418297] b43 ssb0:0: Direct firmware load failed with error -2
[   25.418306] b43 ssb0:0: Falling back to user helper
[   29.166923] b43 ssb0:0: Direct firmware load failed with error -2
[   29.166933] b43 ssb0:0: Falling back to user helper
[   29.535311] b43 ssb0:0: Direct firmware load failed with error -2
[   29.535319] b43 ssb0:0: Falling back to user helper
[   29.537808] b43 ssb0:0: Direct firmware load failed with error -2
[   29.537816] b43 ssb0:0: Falling back to user helper
[   29.549591] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   29.549599] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   29.549602] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

When I then go to the site I am requested to use;

sudo apt-get install firmware-b43-installer

Which I've tried before and it brings;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libquvi-scripts libquvi7 python3-dirspec
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

If I try 
apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Does that help...?

---

### Post by chili555 on 2014-11-14
> If I try 
apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Installing or removing software, known in Ubuntu as packages, is reserved for administrators. I really don't want my granddaughter stumbling on to malware, spyware, viruses (virii???) and infecting my laptop. Therefor, only those who know the administrator's password are allowed to install and remove packages. Therefore, tell the system that the admin wants to do this change with 'sudo.'```
sudo apt-get autoremove
```

Then try:```
sudo apt-get install --reinstall firmware-b43-installer 
```Reboot and let us hear your report of success.

---

### Post by martyn.boyd on 2014-11-14
Result!!! You are a total genius my friend. Followed those two steps, rebooted and for the first time I had the ability to "Enable Networking" from the menu, hit the button and hey presto. No idea how I crippled it all in the first place, but you're rescued me very nicely...

Can't thank you enough!

:D

---

### Post by chili555 on 2014-11-14
Glad it's working and thank you for your kind words.

---

