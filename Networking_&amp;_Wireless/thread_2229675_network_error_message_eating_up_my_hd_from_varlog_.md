---
title: "network error message eating up my hd from /var/log syslog"
date: 2014-06-14
forum: Networking &amp; Wireless
---

### Post by adam64 on 2014-06-14
I had posted this in general at:
[http://ubuntuforums.org/showthread.php?t=2229560](http://ubuntuforums.org/showthread.php?t=2229560)
Then, I was told to post in the Networking section because I'd get someone who knows more about networking here.

I had a problem with my HD dissappearing rapidly.  I would not be doing anything and I'd go from 13.3 gb to 13.1 in a couple minutes.  Tracked down the problem file to var/log and it looks like this error keeps getting sent over and over from file  "syslog" which is 18 gb, I also have a "syslog.1" that is 11 gb with the  same text in it:
```

Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.122976] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.123542] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.124093] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.

```
any idea how to fix this?

I have a dual boot windows/ubuntu, and although I've used Ubuntu for a while, I still consider myself a noob, so please be detailed.

---

### Post by steeldriver on 2014-06-14
Actually it was me who suggested starting a new thread - I couldn't see the sense of making the network gurus read through a couple of pages of "why is my disk filling up" troubleshooting when it doesn't really have any relevance to the problem at hand.

---

### Post by bab1 on 2014-06-14
> **steeldriver said:**
> Actually it was me who suggested starting a new thread - I couldn't see the sense of making the network gurus read through a couple of pages of "why is my disk filling up" troubleshooting when it doesn't really have any relevance to the problem at hand.
Why shouldn't those that are interested in the problem see everything?  I can't fix the problem but it only took me 2 minutes to see that it is a wireless driver problem.  I think it's better to NOT have 2 conversations going about the same issue.  Yes I read both posts.

---

### Post by bab1 on 2014-06-14
[QUOTE=adam64]Sorry, I was told to solve the other one and start a new thread here.  I'll report post, but anyone else out there know what's going on?  I can't use my computer at all since every time I run Ubuntu, I loose hard drive space.[/QUOTE]
You have nothing to be sorry about.  You did as you were told.  It's an unfortunate set of circumstances.  The COC docs explicitly talk of not creating multiple posts for the same problem.  It was a judgment call on the mods.  The symptoms of your problem became more clear but the problem was/is still the same.  I would have moved the original post and asked you to add the additional info.   But that's just me  :-)

---

### Post by adam64 on 2014-06-15
Ok, but back to the problem at hand.  Does anyone know how to fix this thing?  Can anyone tell me where these drivers are?  Do I need to update them, delete them, change a couple lines, or what?

---

### Post by steeldriver on 2014-06-15
While we're waiting for the weekend crew, can you provide the results of these commands please? it will help identify exactly what device we are dealing with:

```

lspci -nnv | grep '\[02.0\]'

sudo lshw -C network -sanitize

lsmod

```

---

### Post by varunendra on 2014-06-15
Adam, are you using both Network Manager (comes by default with Ubuntu) and WPA Supplicant (needs to be installed and configured separately)?

Did you follow any guides/posts/how-to's to fix some wireless issue earlier?

I'm not sure, but it looks like a dog-fight between Network Manager and WPA Supplicant. NM uses its own implementation of WPA supplicant, it doesn't need to be installed separately.

Hoping a bit more clarity on this, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by adam64 on 2014-06-15
```

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
05:00.0 Network controller [0280]: Intersil Corporation ISL3874 [Prism 2.5]/ISL3872 [Prism 3] [1260:3873] (rev 01)
05:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)

```

---

### Post by adam64 on 2014-06-15
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: [REMOVED]
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:44 ioport:c000(size=256) memory:ea000000-ea000fff memory:ed800000-ed81ffff
  *-network:0 DISABLED
       description: Wireless interface
       product: ISL3874 [Prism 2.5]/ISL3872 [Prism 3]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=hostap firmware=0.0.0 latency=32 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:20 memory:ed000000-ed000fff
  *-network:1
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth1
       version: 10
       serial: [REMOVED]
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:d000(size=256) memory:ec000000-ec0000ff memory:ed020000-ed03ffff

```

---

### Post by adam64 on 2014-06-15
```

Module                  Size  Used by
snd_hrtimer            12648  1 
cfg80211              409394  0 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
binfmt_misc            13140  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
nf_conntrack_ipv6      14318  7 
nf_defrag_ipv6         26163  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17445  5 
xt_limit               12541  7 
xt_tcpudp              12756  18 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  8 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  15 
joydev                 17101  0 
wacom                  61112  0 
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 20826  1 nf_nat_ftp
nf_conntrack_ftp       14056  1 nf_nat_ftp
nf_conntrack           83685  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  12 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype
gpio_ich               13229  0 
snd_hda_codec_realtek    51029  1 
coretemp               13195  0 
kvm_intel             132549  0 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
kvm                   388083  1 kvm_intel
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
hostap_pci             53093  0 
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  3 snd_seq_midi_event,snd_seq_midi
serio_raw              13230  0 
hostap                107268  1 hostap_pci
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  3 snd_hrtimer,snd_pcm,snd_seq
lib80211               14040  2 hostap,hostap_pci
lpc_ich                16864  0 
snd                    60871  18 snd_hda_codec_realtek,snd_hrtimer,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
nvidia              10304642  40 
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
pata_acpi              12886  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
8139too                32571  0 
8139cp                 27171  0 
r8169                  61562  0 
mii                    13654  3 r8169,8139cp,8139too
pata_jmicron           12662  0 
floppy                 55416  0 


```

---

### Post by adam64 on 2014-06-15
that's what I got from putting in those codes.  Just yesterday, I disabled my wireless, and I don't have the huge syslog files and my HD stopped going down, and after a little bit today is back up since one of the 11 gb syslogs was archived.  I'm on ethernet, and it was never a problem to have both on, so I don't know if that was it or what.  If I ended up unplugging ethernet and using wireless, will I have the same problem?

---

### Post by varunendra on 2014-06-15
> **adam64 said:**
> If I ended up unplugging ethernet and using wireless, will I have the same problem?

You most probably will, unless it is not the problem I suspected in post #7 and just some bug in NM (highly unlikely) or the driver that gets fixed in later updates. If you need to use wireless again, please reply to my previous post (#7). Although I may not be able to reply until next Sunday if it requires some deep investigation.

---

