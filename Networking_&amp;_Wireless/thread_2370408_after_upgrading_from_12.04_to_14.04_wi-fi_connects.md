---
title: "after upgrading from 12.04 to 14.04 wi-fi connects but no internet"
date: 2017-09-02
forum: Networking &amp; Wireless
---

### Post by pavantavian on 2017-09-02
Hi there!

After upgrading my ubuntu from 12.04 to 14.04 I can't use wireless connection. Unfortunately I have lost my cable, so I can not check 
the wired connection. (I post this from another laptop with windows)
When I previously upgraded from ubuntu 10 to ubuntu 12.04 I did not experienced any such thing

I am using a laptop. 
I have read about this issue already, frankly I don't understand much of it... Concerning Network Manager - I already tried this
vi /etc/NetworkManager/NetworkManager.conf
  "change managed=false to managed=true." but these values were already so.

  Then "From the top-right corner select Edit Connections, and add a new  connection. Specify your ip address, netmask, gateway, and the DNS  server being 8.8.8.8.

  Then add these two lines to /etc/resolv.conf

  nameserver 8.8.8.8
nameserver 8.8.4.4
  Then run:

  sudo service network-manager restart."

But I can not open Network Manager as GUI, I have tried 
every method I came across (I only get the Network Connections window, but it is not the same thing... or is it?!). I have also tried rfkill and the problem don't seem to be there. I stumbled across some other post advising to change DNS server to 8.8.8.8 but I have no freakin' idea how to that!...
Though I am using ubuntu a few years, I must say I can still be regarded as a novice, since I used it for common stuff (word processing, multimedia, internet)
and most of the problems I faced were solvable after reading a few posts and this is the first time to face this kind of problem and don't know almost a thing about networking!  So I gonna need some more thorough guidance on this, hope it will work out... eventually! 
Thanks in advance!

---

### Post by praseodym on 2017-09-03
Which hardware is it?
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by pavantavian on 2017-09-03
**lspci -nnk | grep -iA2 net **
```
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02) 
    Subsystem: Intel Corporation WM3945ABG MOW2 [8086:1001] 
    Kernel driver in use: iwl3945 
-- 
05:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10) 
    Subsystem: Fujitsu Technology Solutions Device [1734:10ac] 
    Kernel driver in use: r8169 
**lsusb** Bus 001 Device 003: ID 18a5:0302 Verbatim, Ltd Flash Drive 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**lsmod **
Module                  Size  Used by 
nls_iso8859_1          12617  1 
usb_storage            48417  1 
cuse                   13213  3 
dm_crypt               22589  0 
rfcomm                 53664  8 
bnep                   18895  2 
binfmt_misc            13140  1 
ip6t_REJECT            12809  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
nf_conntrack_ipv6      14318  8 
nf_defrag_ipv6         26163  1 nf_conntrack_ipv6 
ipt_REJECT             12485  1 
xt_LOG                 17445  20 
xt_limit               12541  3 
xt_tcpudp              12756  18 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  8 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4 
xt_conntrack           12664  16 
snd_hda_codec_realtek    59527  1 
snd_hda_codec_si3054    12864  1 
snd_hda_intel          42858  3 
ip6table_filter        12711  1 
snd_hda_codec         168250  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel 
ip6_tables             17883  1 ip6table_filter 
coretemp               13195  0 
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns 
kvm_intel             132651  0 
nf_nat_ftp             12645  0 
snd_hwdep              13272  1 snd_hda_codec 
nf_nat                 20861  1 nf_nat_ftp 
nf_conntrack_ftp       14056  1 nf_nat_ftp 
nf_conntrack           83878  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6 
iptable_filter         12706  1 
arc4                   12536  2 
ip_tables              18051  1 iptable_filter 
x_tables               22456  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT 
kvm                   388316  1 kvm_intel 
snd_pcm                85501  3 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel 
joydev                 17101  0 
iwl3945                63619  0 
serio_raw              13230  0 
iwlegacy               88016  1 iwl3945 
lpc_ich                16864  0 
mac80211              554291  2 iwl3945,iwlegacy 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel 
btusb                  27580  0 
snd_seq_midi           13132  0 
bluetooth             342208  22 bnep,btusb,rfcomm 
snd_seq_midi_event     14475  1 snd_seq_midi 
cfg80211              417586  3 iwl3945,iwlegacy,mac80211 
snd_rawmidi            25543  1 snd_seq_midi 
snd_seq                55431  2 snd_seq_midi_event,snd_seq_midi 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi 
snd_timer              28569  2 snd_pcm,snd_seq 
lm63                   20812  0 
snd                    60939  17 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi 
soundcore              12600  1 snd 
shpchp                 32128  0 
parport_pc             31981  0 
ppdev                  17391  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc 
radeon               1425039  3 
firewire_ohci          35529  0 
psmouse                95439  0 
i2c_algo_bit           13197  1 radeon 
ttm                    85079  1 radeon 
r8169                  61562  0 
drm_kms_helper         48868  1 radeon 
sata_via               13535  2 
pata_acpi              12886  0 
mii                    13654  1 r8169 
firewire_core          61867  1 firewire_ohci 
drm                   244037  5 ttm,drm_kms_helper,radeon 
crc_itu_t              12627  1 firewire_core 
wmi                    18673  0 
video                  18903  0 


 **iwconfig **
wlan0     IEEE 802.11abg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
lo        no wireless extensions. 

eth0      no wireless extensions. 


**rfkill list **
0: hci0: Bluetooth 
    Soft blocked: yes 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no
```

---

### Post by praseodym on 2017-09-03
```
iwconfig
wlan0 IEEE 802.11abg ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR] 
```
The card is turned off. Button, switch key or key combination?

---

### Post by pavantavian on 2017-09-03
The physical wireless button is on, that's the first thing I checked. And I don't see any Fn + wireless combination on the keyboard, which does make sense, since it has already physical wireless button. The laptop is damaged at the edge where the wireless button is located though, but it was so for some years, so I doubt that could be the problem.  The model is Fujistu Siemens Amilo Xi 1554, some 10 years old.  The wireless light next to the on/off is also active.   BTW, I did had a similar problem few years ago. At that time, the wireless button was not on, but then, if I remember well, the wireless connection was not working at all. Now the connection signals to work, but there is actually no internet.  Anyway, I googled out a bit and I tried Fn+F2, which was the key combination for some Fujitsu Siemens laptops and nothing still. Any ideas, please?

---

### Post by praseodym on 2017-09-03
Try

```
sudo modprobe -v wistron_btns
sudo rfkill unblock all 
```

---

### Post by pavantavian on 2017-09-03
Still nothing  Here's what I get for these commands, respectively:  sudo modprobe -v wistron_btns:  insmod /lib/modules/3.13.0-129-generic/kernel/drivers/input/input-polldev.ko  insmod /lib/modules/3.13.0-129-generic/kernel/drivers/input/sparse-keymap.ko  insmod /lib/modules/3.13.0-129-generic/kernel/drivers/input/misc/wistron_btns.ko  modprobe: ERROR: could not insert 'wistron_btns': No such device

---

### Post by pavantavian on 2017-09-03
sudo rfkill unblock all:  Usage:	rfkill [options] command  Options:  	--version	show version (0.5-1ubuntu1 (Ubuntu))  Commands:  	help  	event  	list [IDENTIFIER]  	block IDENTIFIER  	unblock IDENTIFIER  where IDENTIFIER is the index no. of an rfkill switch or one of:  	 all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm nfc

---

### Post by praseodym on 2017-09-03
Try Acer-HK: Install this DEB package: [https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk/+files/acerhk-source_0.5.35-16~3~ubuntu14.04.1_all.deb](https://launchpad.net/~gruenertee/+archive/ubuntu/acerhk/+files/acerhk-source_0.5.35-16~3~ubuntu14.04.1_all.deb)

and run

```
cd /usr/src
sudo tar -xjf acerhk.tar.bz2 
cd /usr/src/modules/acerhk
sudo su
make
exit 
sudo cp acerhk.ko /lib/modules/$(uname -r)/kernel/ubuntu/
sudo depmod -A 
```
Now load the module:

```
sudo modprobe acerhk force_series=5020 autowlan=1 
```

---

### Post by pavantavian on 2017-09-03
I have downloaded the package from this laptop, but when I try to install it on the other one with ubuntu, it redirects me to Ubuntu Software Center, and in order to install it from there - I need the internet, which the exact thing I don't have. When I right-click the package-icon I get "Open with" Archive Manager / GDebi Package Installer, I selected the later, than after entering my password it redirects me to Ubuntu Software Center again.
Is there any clean way to install this without Internet connection?
Or will I have to buy/borrow internet cable...

---

### Post by praseodym on 2017-09-03
Save it in "Downloads" and run
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by pavantavian on 2017-09-03
...This is like fighting with the Hydra - when u think you have solved one issue, two more are popping up... 
Here is what I got:

> **sudo dpkg -i ~/Desktop/*.deb **
  
Selecting previously unselected package acerhk-source. 
(Reading database ... 534706 files and directories currently installed.) 
Preparing to unpack .../acerhk-source_0.5.35-16~3~ubuntu14.04.1_all.deb ... 
Unpacking acerhk-source (0.5.35-16~3~ubuntu14.04.1) ... 
dpkg: dependency problems prevent configuration of acerhk-source: 
 acerhk-source depends on module-assistant; however: 
  Package **module-assistant** is not installed. 
 acerhk-source depends on debhelper (>= 7); however: 
  Package **debhelper** is not installed. 

dpkg: error processing package acerhk-source (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 acerhk-source 


(I had accidentally deleted the Downloads file, so I did it from Desktop instead)

I have downloaded the two missing dependency packages from the following web-sites respectively:
[https://packages.debian.org/sid/all/module-assistant/download](https://packages.debian.org/sid/all/module-assistant/download)
[https://packages.debian.org/sid/all/debhelper/download](https://packages.debian.org/sid/all/debhelper/download)

I plan to install them the same way I did with acerhk-source.
Please tell me do I have the right packages and can I install them per analogy at the above described way.
And do I need something else to install these two...
Thank you!

---

### Post by praseodym on 2017-09-04
Save them all in "Downloads" and run

```
sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by pavantavian on 2017-09-04
Now I need to install a dozen more packages in order to get these two working...

```

 sudo dpkg -i ~/Desktop/*.deb

Selecting previously unselected package debhelper.
(Reading database ... 534714 files and directories currently installed.)
Preparing to unpack .../debhelper_10.7.2_all.deb ...
Unpacking debhelper (10.7.2) ...
Selecting previously unselected package module-assistant.
Preparing to unpack .../module-assistant_0.11.9_all.deb ...
Unpacking module-assistant (0.11.9) ...
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on autotools-dev; however:
  Package autotools-dev is not installed.
 debhelper depends on dh-autoreconf (>= 12~); however:
  Package dh-autoreconf is not installed.
 debhelper depends on dh-strip-nondeterminism (>= 0.028~); however:
  Package dh-strip-nondeterminism is not installed.
 debhelper depends on dpkg-dev (>= 1.18.2~); however:
  Package dpkg-dev is not installed.
 debhelper depends on libdpkg-perl (>= 1.17.14); however:
  Version of libdpkg-perl on system is 1.17.5ubuntu5.7.
 debhelper depends on po-debconf; however:
  Package po-debconf is not installed.

dpkg: error processing package debhelper (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of module-assistant:
 module-assistant depends on perl:any.

dpkg: error processing package module-assistant (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 debhelper
 module-assistant

 sudo dpkg -i ~/Desktop/*.deb
(Reading database ... 535207 files and directories currently installed.)
Preparing to unpack .../acerhk-source_0.5.35-16~3~ubuntu14.04.1_all.deb ...
Unpacking acerhk-source (0.5.35-16~3~ubuntu14.04.1) over (0.5.35-16~3~ubuntu14.04.1) ...
Preparing to unpack .../debhelper_10.7.2_all.deb ...
Unpacking debhelper (10.7.2) over (10.7.2) ...
Preparing to unpack .../module-assistant_0.11.9_all.deb ...
Unpacking module-assistant (0.11.9) over (0.11.9) ...
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on autotools-dev; however:
  Package autotools-dev is not installed.
 debhelper depends on dh-autoreconf (>= 12~); however:
  Package dh-autoreconf is not installed.
 debhelper depends on dh-strip-nondeterminism (>= 0.028~); however:
  Package dh-strip-nondeterminism is not installed.
 debhelper depends on dpkg-dev (>= 1.18.2~); however:
  Package dpkg-dev is not installed.
 debhelper depends on libdpkg-perl (>= 1.17.14); however:
  Version of libdpkg-perl on system is 1.17.5ubuntu5.7.
 debhelper depends on po-debconf; however:
  Package po-debconf is not installed.

dpkg: error processing package debhelper (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of module-assistant:
 module-assistant depends on perl:any.

dpkg: error processing package module-assistant (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acerhk-source:
 acerhk-source depends on module-assistant; however:
  Package module-assistant is not configured yet.
 acerhk-source depends on debhelper (>= 7); however:
  Package debhelper is not configured yet.

dpkg: error processing package acerhk-source (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 debhelper
 module-assistant
 acerhk-source

```

---

### Post by wildmanne39 on 2017-09-04
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by praseodym on 2017-09-05
Ok, so download this one:

[https://media-cdn.ubuntu-de.org/forum/attachments/07/20/6674857-acerhk-0.5.6_dkms.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/07/20/6674857-acerhk-0.5.6_dkms.tar.gz)

```
sudo tar xvf 6674857-acerhk-0.5.6_dkms.tar.gz -C /usr/src
sudo dkms add -m acerhk -v 0.5.6
sudo dkms build -m acerhk -v 0.5.6
sudo dkms install -m acerhk -v 0.5.6 
```

---

