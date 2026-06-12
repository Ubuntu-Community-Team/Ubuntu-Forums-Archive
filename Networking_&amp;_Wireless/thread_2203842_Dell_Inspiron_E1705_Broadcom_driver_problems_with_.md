---
title: "Dell Inspiron E1705: Broadcom driver problems with wireless and ethernet"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by dtkana on 2014-02-05
I am completely new to Ubuntu and installed 12.04 on a Dell Inspiron E1705. I have read more then I can handle on these issues and tried many things that usually get me back to a clean re-install and try again. I did one test at some point to check what my equipment was and I believe the ethernet and wireless to both be Broadcom and the wireless is a 4311 if I recall.

Starting from a clean install I perform the recommended updates and after restart I lose my ethernet and I have the wireless icon that sees no connections. At additional drivers it recommends the Broadcom sta. When I attempt to activate it I get an error message, but then upon closing the error message my ethernet reconnects and starts working again. I can get wireless through a usb device, but I would prefer to have everything working as it is supposed to. Right now I am fully updated except for the recommended broadcom sta update and I have working ethernet.

Any ideas on the problem and if it is possible to get my wireless and ethernet working at the same time?

I apologize since I am sure this is addressed somewhere already, but I could not find my specific problem. Mostly people with wireless only issues.

Thanks in advance for your help.

---

### Post by praseodym on 2014-02-05
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
rfkill list
```

---

### Post by dtkana on 2014-02-05
uname -a
Linux todd-MP061 3.8.0-35-generic #52~precise1-Ubuntu SMP Thu Jan 30 17:27:28 UTC 2014 i686 i686 i386 GNU/Linux
todd@todd-MP061:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
todd@todd-MP061:~$ lsmod
Module                  Size  Used by
b44                    31366  0 
ssb_hcd                12781  0 
ssb                    51554  2 b44,ssb_hcd
redirfs                58752  0 [permanent]
bnep                   17919  2 
rfcomm                 38400  0 
bluetooth             211586  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      18011  7 
nf_defrag_ipv6         13159  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
xt_LOG                 17280  9 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
nf_conntrack_ipv4      14114  7 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             18134  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 25239  1 nf_nat_ftp
nf_conntrack_ftp       13195  1 nf_nat_ftp
snd_hda_codec_idt      64649  1 
nf_conntrack           67604  8 nf_conntrack_ipv6,nf_conntrack_ipv4,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22050  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
coretemp               13324  0 
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_idt,snd_hda_intel
joydev                 17329  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
i915                  554735  3 
r852                   17873  0 
snd_seq_midi           13132  0 
sm_common              16772  1 r852
snd_rawmidi            25157  1 snd_seq_midi
nand                   54028  2 r852,sm_common
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
microcode              18433  0 
mtd                    38990  2 sm_common,nand
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                82769  0 
drm_kms_helper         47749  1 i915
nand_ids                8547  1 nand
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   233935  4 i915,drm_kms_helper
nand_bch               13003  1 nand
serio_raw              13031  0 
r592                   17808  0 
gpio_ich               13278  0 
bch                    21767  1 nand_bch
snd                    57014  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi               12601  0 
dell_laptop            17209  0 
soundcore              12600  1 snd
dcdbas                 14065  1 dell_laptop
nand_ecc               13105  1 nand
mac_hid                13077  0 
sparse_keymap          13658  1 dell_wmi
memstick               15885  1 r592
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13316  1 i915
wmi                    18744  1 dell_wmi
lpc_ich                17048  0 
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          36072  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18265  0 
sdhci                  32429  1 sdhci_pci
todd@todd-MP061:~$ rfkill list

---

### Post by praseodym on 2014-02-05
The LAN driver is loaded. Are the login and PW of your ISP saved in your router interface? Check the nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```
If it doesnt work: Remove all profiles in "wired" and "DSL" in the network-manager applet and reboot.

If it works: Install the missing firmware for the WLAN card
```

sudo apt-get install linux-firmware-nonfree
sudo modprobe -v b43
```

---

### Post by dtkana on 2014-02-05
I followed the above instructions. Upon restart my LAN was once again disabled, wireless icon visible and showing no connections available. So, as I have been having to do to get on the internet after every restart, I went to additional hardware attempted the STA install, received error message, closed error message and LAN started working again and the wireless icon went away again.

I am an extreme novice when it comes to some of these terms.

---

### Post by praseodym on 2014-02-05
LAN is always preferred. Install the missing firmware for the wireless card via double-click and software-center:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Reboot. You may want to deactivate the package filter:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by dtkana on 2014-02-05
What is "deactivate the package filter"?

---

### Post by praseodym on 2014-02-05
Its the activated firewall of the OS. You dont need it if the router firewall is activated. Check also the router settings (manual!) if a MAC-address filter is activated.

---

### Post by dtkana on 2014-02-06
Still not sure what I did except what you told me to. Everything is working correctly!!!!! Thanks a lot!!!!

---

