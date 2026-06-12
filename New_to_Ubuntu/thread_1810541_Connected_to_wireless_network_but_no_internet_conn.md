---
title: "Connected to wireless network but no internet connection"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Uhura on 2011-07-23
Hi everyone, 
Ok so I've been using Ubuntu for several months with no major problems, apart from the fact that the wireless connection often goes down and will not reconnect until I do a restart. But for the last few days the network tab tells me I'm connected to the wireless network, but I have no internet connection. Firefox can't browse any webpages, can't ping from the terminal, deluge has no connection. I don't think its a problem with the router because I can access the web from my windows pc no problem via same network. I tried setting the firefox preferences to 'no proxy' but it hasn't made any difference. Any ideas please? System info & hardware below. I'm not great with computers so please keep it simple!
Thanks

Ubuntu 10.04 Lucid Lynx 
Zotac Zbox HD-ID11.
NVIDIA® Next-Generation ION™ (w/512MB DDR3)
Intel® Atom™ D510 (dual-core) (1.66 GHz)
Western Digital Scorpio Blue 500GB Sata 8MB Cache 2.5 Inch Internal Hard Drive
Kingston Value ram 800Mhz DDR2 CL6 SO DIMM

---

### Post by thefasterblueone on 2011-07-23
Run this in terminal and post results.

```
iwconfig
```

---

### Post by Uhura on 2011-07-23
Thanks for replying. Here's the results:

 trini@Zotac:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Trinicity"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 88:25:2C:36:D9:89   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by thefasterblueone on 2011-07-23
Try this:

```
sudo iwconfig wlan0 power off
```

May have to reboot to see results.

---

### Post by Uhura on 2011-07-23
Yes you were right, the first time I tried it nothing happened. So I rebooted and tried again and got this:

trini@Zotac:~$ sudo iwconfig wlan0 power off
[sudo] password for trini: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Invalid argument.
trini@Zotac:~$

---

### Post by Uhura on 2011-07-23
Any ideas anybody?

---

### Post by wildmanne39 on 2011-07-23
Hi, run these commands in a terminal please
```
lspci -nn | grep 0280
```
```
lsmod
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Swagman on 2011-07-24
You haven't put your location in your profile so I need to ask this (getting repetitive) question.

Is your ISP BT ?

Does this problem happen *After* a (successful) session within windows then returning to Ubuntu ?

---

### Post by Uhura on 2011-07-24
Hi, thanks for replying, and sorry for the delay; time zone issues!

Here's the results of the code;

```
 
trini@Zotac:~$ lspci - nn | grep 0280
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file


trini@Zotac:~$ lsmod
Module                  Size  Used by
usb_storage            39841  0 
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          1369  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46894  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4428  1 nf_nat_pptp
nf_conntrack_proto_gre     3957  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             3543  1 
nf_nat                 15560  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10346  4 iptable_nat,nf_nat
nf_conntrack           60975  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9899  2 iptable_filter,iptable_nat
x_tables               14175  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             6587  1 
arc4                    1153  2 
ppdev                   5259  0 
ath9k                 306106  0 
snd_hda_codec_realtek   203376  1 
mac80211              205402  1 ath9k
ath                     7611  1 ath9k
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
lirc_mceusb            12402  1 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
cfg80211              126144  3 ath9k,mac80211,ath
nvidia               9961216  38 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lirc_dev                8884  3 lirc_mceusb
usbhid                 36110  0 
hid                    67096  1 usbhid
intel_agp              24375  0 
psmouse                63245  0 
vga16fb                11385  1 
led_class               2864  1 ath9k
serio_raw               3978  0 
soundcore               6620  1 snd
vgastate                8961  1 vga16fb
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169


trini@Zotac:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
trini@Zotac:~$ 

    
```
> **Swagman said:**
> You haven't put your location in your profile so I need to ask this (getting repetitive) question.

Is your ISP BT ?

Does this problem happen *After* a (successful) session within windows then returning to Ubuntu ?

I'm in Spain, so no, ISP isn't BT, its a company called Ya.com, a subsidiary of France Telecom.

I maybe didn't make it clear enough before, but I've got windows on a completely different machine in another room. The ubuntu pc only has ubuntu installed, and the problem is all the time. I haven't been able to connect for days, even though it claims to be connected to the network, and obviously the network is working cause I'm typing this right now!

---

### Post by thefasterblueone on 2011-07-24
Post the output of:

```
cat /var/log/syslog | grep wlan0
```

---

### Post by Uhura on 2011-07-24
Ok here's what I got:
```
  trini@Zotac:~$ cat /var/log/syslog | grep wlan0
Jul 24 13:31:18 Zotac kernel: [ 1583.000046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:32:18 Zotac kernel: [ 1643.000045] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:33:18 Zotac kernel: [ 1703.000044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:34:18 Zotac kernel: [ 1762.964048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:35:18 Zotac kernel: [ 1822.988575] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:36:18 Zotac kernel: [ 1883.000039] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:37:18 Zotac kernel: [ 1942.965543] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:38:18 Zotac kernel: [ 2002.988044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:39:18 Zotac kernel: [ 2063.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:40:18 Zotac kernel: [ 2123.000044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:41:18 Zotac kernel: [ 2183.000040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:42:18 Zotac kernel: [ 2242.988550] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:43:18 Zotac kernel: [ 2302.964837] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:44:18 Zotac kernel: [ 2363.000034] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:45:18 Zotac kernel: [ 2423.000777] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:46:18 Zotac kernel: [ 2482.964048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:47:18 Zotac kernel: [ 2542.977029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:48:18 Zotac kernel: [ 2602.965597] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:48:48 Zotac kernel: [ 2633.000048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:49:48 Zotac kernel: [ 2692.988046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:50:48 Zotac kernel: [ 2752.965546] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:51:48 Zotac kernel: [ 2813.000035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:52:48 Zotac kernel: [ 2872.988551] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:53:48 Zotac kernel: [ 2932.991948] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:54:48 Zotac kernel: [ 2992.976039] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:55:48 Zotac kernel: [ 3053.000047] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:56:48 Zotac kernel: [ 3112.965553] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:57:48 Zotac kernel: [ 3172.964058] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:58:48 Zotac kernel: [ 3233.004027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 13:59:48 Zotac kernel: [ 3293.000036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:00:48 Zotac kernel: [ 3353.000045] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:01:48 Zotac kernel: [ 3413.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:02:48 Zotac kernel: [ 3473.000041] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:03:48 Zotac kernel: [ 3533.000038] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:04:48 Zotac kernel: [ 3592.976029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:05:48 Zotac kernel: [ 3652.965542] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:06:48 Zotac kernel: [ 3712.977030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:07:48 Zotac kernel: [ 3772.976033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:08:48 Zotac kernel: [ 3832.976074] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:09:48 Zotac kernel: [ 3893.000026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:10:48 Zotac kernel: [ 3952.965540] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:11:48 Zotac kernel: [ 4012.977026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:12:48 Zotac kernel: [ 4072.976032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:13:48 Zotac kernel: [ 4133.004032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:14:48 Zotac kernel: [ 4192.965550] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:15:48 Zotac kernel: [ 4252.976032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:16:48 Zotac kernel: [ 4312.965563] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:17:48 Zotac kernel: [ 4373.000036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:18:48 Zotac kernel: [ 4432.976060] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:19:48 Zotac kernel: [ 4492.965551] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:20:48 Zotac kernel: [ 4552.992536] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:21:48 Zotac kernel: [ 4613.000039] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:22:48 Zotac kernel: [ 4673.000036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:23:48 Zotac kernel: [ 4733.000035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:24:48 Zotac kernel: [ 4793.000030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:25:48 Zotac kernel: [ 4853.000054] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:26:48 Zotac kernel: [ 4913.000048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:27:48 Zotac kernel: [ 4973.004042] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:28:48 Zotac kernel: [ 5033.004028] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:29:48 Zotac kernel: [ 5092.965555] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:30:48 Zotac kernel: [ 5152.964051] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:31:48 Zotac kernel: [ 5212.992559] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:32:48 Zotac kernel: [ 5273.000027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:33:48 Zotac kernel: [ 5333.004035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:34:48 Zotac kernel: [ 5392.976037] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:35:48 Zotac kernel: [ 5453.000066] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:36:48 Zotac kernel: [ 5513.000041] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:37:48 Zotac kernel: [ 5573.000038] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:38:48 Zotac kernel: [ 5633.000040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:39:48 Zotac kernel: [ 5692.965585] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:40:48 Zotac kernel: [ 5753.004032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:41:48 Zotac kernel: [ 5812.976034] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:42:48 Zotac kernel: [ 5873.000030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:43:48 Zotac kernel: [ 5933.004034] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:44:48 Zotac kernel: [ 5992.966177] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:45:48 Zotac kernel: [ 6053.000039] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:46:48 Zotac kernel: [ 6112.964040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:47:48 Zotac kernel: [ 6172.976040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:48:48 Zotac kernel: [ 6232.976039] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:49:48 Zotac kernel: [ 6292.964032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:50:18 Zotac kernel: [ 6323.000036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:51:18 Zotac kernel: [ 6382.988027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:52:18 Zotac kernel: [ 6443.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:53:18 Zotac kernel: [ 6503.000032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:54:18 Zotac kernel: [ 6562.976028] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:55:18 Zotac kernel: [ 6622.976034] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:56:18 Zotac kernel: [ 6682.964055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:57:18 Zotac kernel: [ 6742.976045] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:58:18 Zotac kernel: [ 6802.964056] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 14:59:18 Zotac kernel: [ 6862.988044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:00:18 Zotac kernel: [ 6922.964044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:01:18 Zotac kernel: [ 6983.004041] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:02:18 Zotac kernel: [ 7042.964055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:02:48 Zotac kernel: [ 7073.000036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:03:48 Zotac kernel: [ 7133.000035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:04:48 Zotac kernel: [ 7192.964055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:05:48 Zotac kernel: [ 7252.964055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:06:48 Zotac kernel: [ 7312.964054] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:07:48 Zotac kernel: [ 7372.965557] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:08:48 Zotac kernel: [ 7433.004043] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:09:48 Zotac kernel: [ 7492.964054] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:10:18 Zotac kernel: [ 7523.000955] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:11:18 Zotac kernel: [ 7582.964039] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:12:18 Zotac kernel: [ 7642.964056] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:13:18 Zotac kernel: [ 7702.964055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:13:48 Zotac kernel: [ 7733.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:14:48 Zotac kernel: [ 7792.964055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:15:18 Zotac kernel: [ 7823.000032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:16:18 Zotac kernel: [ 7882.976029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:17:18 Zotac kernel: [ 7942.964055] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:18:18 Zotac kernel: [ 8002.964054] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:19:18 Zotac kernel: [ 8063.000035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:20:18 Zotac kernel: [ 8122.988029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:21:18 Zotac kernel: [ 8182.976030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:22:18 Zotac kernel: [ 8242.976027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:23:18 Zotac kernel: [ 8302.976027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:24:18 Zotac kernel: [ 8362.977030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:25:18 Zotac kernel: [ 8423.004034] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:26:18 Zotac kernel: [ 8483.000034] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:27:18 Zotac kernel: [ 8543.000029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:28:18 Zotac kernel: [ 8603.000035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:29:18 Zotac kernel: [ 8663.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:30:18 Zotac kernel: [ 8723.000036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:31:18 Zotac kernel: [ 8783.000030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:32:18 Zotac kernel: [ 8842.976027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:33:18 Zotac kernel: [ 8902.976029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:34:18 Zotac kernel: [ 8962.988050] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:35:18 Zotac kernel: [ 9022.988027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:36:18 Zotac kernel: [ 9082.988025] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:37:18 Zotac kernel: [ 9143.000028] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:38:18 Zotac kernel: [ 9202.988027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:39:18 Zotac kernel: [ 9263.004033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:40:18 Zotac kernel: [ 9323.000029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:41:18 Zotac kernel: [ 9383.000022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:42:18 Zotac kernel: [ 9442.964032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:43:18 Zotac kernel: [ 9502.988046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:44:18 Zotac kernel: [ 9562.988026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:45:18 Zotac kernel: [ 9623.000040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:46:18 Zotac kernel: [ 9683.000025] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:47:18 Zotac kernel: [ 9743.000036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:48:18 Zotac kernel: [ 9803.000034] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:49:18 Zotac kernel: [ 9863.000038] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:50:18 Zotac kernel: [ 9923.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:51:18 Zotac kernel: [ 9982.976036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:52:18 Zotac kernel: [10043.000041] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:53:18 Zotac kernel: [10102.988027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:54:18 Zotac kernel: [10163.002614] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:55:18 Zotac kernel: [10222.964032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:56:18 Zotac kernel: [10282.988056] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:57:18 Zotac kernel: [10342.988026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:58:18 Zotac kernel: [10403.000031] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 15:59:18 Zotac kernel: [10462.976029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:00:18 Zotac kernel: [10522.976044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:01:18 Zotac kernel: [10582.976044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:02:18 Zotac kernel: [10642.964036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:02:48 Zotac kernel: [10673.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:03:48 Zotac kernel: [10733.000032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:04:48 Zotac kernel: [10792.976032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:05:48 Zotac kernel: [10852.976030] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:06:48 Zotac kernel: [10912.976035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:07:48 Zotac kernel: [10972.976046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:08:48 Zotac kernel: [11033.004031] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:09:48 Zotac kernel: [11093.000041] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:10:48 Zotac kernel: [11152.976044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:11:48 Zotac kernel: [11212.976046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:12:48 Zotac kernel: [11272.976046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:13:48 Zotac kernel: [11332.976044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:14:48 Zotac kernel: [11392.976045] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:15:48 Zotac kernel: [11452.976047] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:16:48 Zotac kernel: [11512.976042] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:17:48 Zotac kernel: [11572.988026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:18:48 Zotac kernel: [11632.976047] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:19:48 Zotac kernel: [11692.976042] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:20:48 Zotac kernel: [11752.976042] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:21:48 Zotac kernel: [11812.976043] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:22:48 Zotac kernel: [11872.976035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:23:48 Zotac kernel: [11932.976040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:24:48 Zotac kernel: [11992.976029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:25:48 Zotac kernel: [12052.976038] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:26:48 Zotac kernel: [12112.976035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:27:48 Zotac kernel: [12172.976040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:28:48 Zotac kernel: [12232.988029] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:29:48 Zotac kernel: [12293.004031] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:30:48 Zotac kernel: [12353.000031] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:31:48 Zotac kernel: [12412.976035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:32:48 Zotac kernel: [12472.976035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:33:48 Zotac kernel: [12533.000033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:34:48 Zotac kernel: [12592.964036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:35:18 Zotac kernel: [12623.000032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:36:18 Zotac kernel: [12682.988033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:37:18 Zotac kernel: [12742.988032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:38:18 Zotac kernel: [12802.988032] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:39:18 Zotac kernel: [12862.976031] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:40:18 Zotac kernel: [12922.964031] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jul 24 16:41:18 Zotac kernel: [12982.964033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
trini@Zotac:~$ 


  
```

---

### Post by thefasterblueone on 2011-07-24
Post output:

```
lsusb
```

and

```
sudo lshw -C network
```

---

### Post by Uhura on 2011-07-24
Here it is:

```
  trini@Zotac:~$ lsusb
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 011: ID 0457:0150 Silicon Integrated Systems Corp. Super Talent 1GB Flash Drive
    Bus 001 Device 004: ID 05af:0630 Jing-Mold Enterprise Co., Ltd 
    Bus 001 Device 003: ID 0471:0815 Philips eHome Infrared Receiver
    Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    trini@Zotac:~$ sudo lshw -C network
    [sudo] password for trini: 
      *-network               
           description: Ethernet interface
           product: RTL8111/8168B PCI Express Gigabit Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:01:00.0
           logical name: eth0
           version: 03
           serial: 00:01:2e:bc:94:f3
           size: 10MB/s
           capacity: 1GB/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
           resources: irq:27 ioport:d800(size=256) memory:fbffb000-fbffbfff(prefetchable) memory:fbffc000-fbffffff(prefetchable) memory:feae0000-feafffff(prefetchable)
      *-network
           description: Wireless interface
           product: AR9285 Wireless Network Adapter (PCI-Express)
           vendor: Atheros Communications Inc.
           physical id: 0
           bus info: pci@0000:02:00.0
           logical name: wlan0
           version: 01
           serial: 48:5d:60:7c:9a:e6
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=ath9k ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11bgn
           resources: irq:17 memory:febf0000-febfffff
    trini@Zotac:~$ 
    
```

Is this telling you anything useful?
Many thanks

---

### Post by thefasterblueone on 2011-07-24
```
cat /etc/network/interfaces
```

---

### Post by Uhura on 2011-07-24
```
  trini@Zotac:~$ cat /etc/network/interfaces
    auto lo
    iface lo inet loopback
    
```

Thanks

---

### Post by thefasterblueone on 2011-07-24
OK that look right.

Lets try this:

```
sudo dhclient wlan0
```

Then see if you can connect. Are you using Network-Manager or WICD ?

---

### Post by Uhura on 2011-07-24
Ok did that, still no internet though. The output was as follows:
```
  trini@Zotac:~$ sudo dhclient wlan0
     [sudo] password for trini: 
    Internet Systems Consortium DHCP Client V3.1.3
    Copyright 2004-2009 Internet Systems Consortium.
    All rights reserved.
    For info, please visit https://www.isc.org/software/dhcp/
     
   
  Listening on LPF/wlan0/48:5d:60:7c:9a:e6
    Sending on   LPF/wlan0/48:5d:60:7c:9a:e6
    Sending on   Socket/fallback
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
    No DHCPOFFERS received.
    No working leases in persistent database - sleeping.
    trini@Zotac:~$ 
  
  
```


> **thefasterblueone said:**
> Are you using Network-Manager or WICD ?

I'm not exactly sure :confused: I connect from the icon on the top bar...???

---

### Post by thefasterblueone on 2011-07-24
```
sudo gedit /etc/network/interfaces
```

copy and paste this in your file so it looks like this:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
```

Then click "file" , "save" , and close the window.

Then run this:

```
sudo ifdown wlan0
```

```
sudo ifup wlan0
```

Check connection.

---

### Post by Uhura on 2011-07-25
No luck, still no connection. I get the message "firefox cannot find the server at x....".

Outputs from code:

```
  trini@Zotac:~$ sudo ifdown wlan0
  
  Internet Systems Consortium DHCP Client V3.1.3
  
  Copyright 2004-2009 Internet Systems Consortium.
  
  All rights reserved.
  
  For info, please visit https://www.isc.org/software/dhcp/
  
   
   
  Listening on LPF/wlan0/48:5d:60:7c:9a:e6
  
  Sending on   LPF/wlan0/48:5d:60:7c:9a:e6
  
  Sending on   Socket/fallback
  
  trini@Zotac:~$ sudo ifup wlan0
  
  Internet Systems Consortium DHCP Client V3.1.3
  
  Copyright 2004-2009 Internet Systems Consortium.
  
  All rights reserved.
  
  For info, please visit https://www.isc.org/software/dhcp/
  
   
   
  Listening on LPF/wlan0/48:5d:60:7c:9a:e6
  
  Sending on   LPF/wlan0/48:5d:60:7c:9a:e6
  
  Sending on   Socket/fallback
  
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
  
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
  
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
  
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
  
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
  
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
  
  No DHCPOFFERS received.
  
  No working leases in persistent database - sleeping.
  
  trini@Zotac:~$ ^C
  
  
```

---

### Post by Uhura on 2011-08-07
Can anybody help with this please? I've now lost my network connection as well! Should I just reinstall Ubuntu?

ps. Network manager has disappeared from panel and can't get it back!

---

### Post by amjjawad on 2011-08-07
> **Uhura said:**
> Can anybody help with this please? I've now lost my network connection as well! Should I just reinstall Ubuntu?

ps. Network manager has disappeared from panel and can't get it back!

To restore Network Manager: [http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html](http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html)

To fix your issue, please follow this thread: [http://ubuntuforums.org/showthread.php?t=1643545](http://ubuntuforums.org/showthread.php?t=1643545)

If still nothing is working, please report back.

Thank you!

---

### Post by Uhura on 2011-08-07
Hi, thanks for replying. I tried method 1 and got the following error;

```
  trini@Zotac:~$ sudo edit /etc/NetworkManager/nm-system-settings.conf
    Warning: unknown mime-type for "/etc/NetworkManager/nm-system-settings.conf" -- using "application/octet-stream"
    Error: no "edit" mailcap rules found for type "application/octet-stream"
    [FONT=&quot]trini@Zotac:~$[/FONT]
```

I tried adding a notification area to the panel as in method 2 and all i got was an empty notification area, but still no network manager.

---

### Post by amjjawad on 2011-08-07
> **Uhura said:**
> Hi, thanks for replying. I tried method 1 and got the following error;

```
  trini@Zotac:~$ sudo edit /etc/NetworkManager/nm-system-settings.conf
    Warning: unknown mime-type for "/etc/NetworkManager/nm-system-settings.conf" -- using "application/octet-stream"
    Error: no "edit" mailcap rules found for type "application/octet-stream"
    [FONT=&quot]trini@Zotac:~$[/FONT]
```

I tried adding a notification area to the panel as in method 2 and all i got was an empty notification area, but still no network manager.

After adding the notification area, you need to add the NM-applet.
It should be inside the notification area. Or in another word, once you have a notification area, you can then add NM-Applet.

---

### Post by Uhura on 2011-08-07
> **amjjawad said:**
> After adding the notification area, you need to add the NM-applet.
It should be inside the notification area. Or in another word, once you have a notification area, you can then add NM-Applet.

I'm sorry, I don't know how to add the applet. When I added the notification area, all I got was a new line of three dots with a space next to it. I assume that's the notification area. I've tried left & right clicking that space and nothing happens. All I get are the options "remove from panel", "move" or "lock to panel". No sign of any applet. What should I be doing?

---

### Post by raydar on 2012-11-22
Thank you, thefasterblueone. The command in post #16 worked for me after an upgrade from 12.04 to 12.10 left me with this wifi-but-no-internet problem. 

I wish I understood the nature of what went wrong, but having it instantly work after issuing one command was a pleasure and a relief!

---

### Post by wildmanne39 on 2012-11-22
Old thread closed.

---

