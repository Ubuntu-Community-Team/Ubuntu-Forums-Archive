---
title: "rtl8187L not rtl8187b driver issues"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2008-06-06
Much documentation exists for troubleshooting realtek's rtl8187B chipset, but I'm haven't found anything about the rtl8187L chipset. L and B have different sets of drivers available on the realtek site and the fixes i've read for rtl8187b don't work for rtl8187l. Also the rtl8187b driver is misread by linux as rtl8197 and this apparently is not a problem for rtl8187l.

My problem is with unstable wireless connections. I can connect, but drop connections frequently and don't maintain them for long. I'm using 32-bit Hardy now (after complete inoperability of wireless at 64bit) and the problem occurs regardless of AP. Some info, including a excerpt from my ridiculously long dmesg output:

```
matt@Ogodei:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"CafePasse"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:15:05:0F:E8:41   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=54/64  Signal level=9/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

#[NOTE: low signal level]

matt@Ogodei:~$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:d8:96:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.19 multicast=yes wireless=IEEE 802.11g

#[NOTE: no driver listed, suggesting an installation problem]

matt@Ogodei:~$ sudo pccardctl ident
[sudo] password for matt: 
Socket 0:
  no product info available

#I've read this means that the memory on the card cannot be read

matt@Ogodei:~$ lsmod

Module                  Size  Used by
sky2                   47492  0 
rtl8187                36096  0 
mac80211              165652  1 rtl8187
cfg80211               15112  1 mac80211
eeprom_93cx6            3200  1 rtl8187
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
video                  19856  0 
output                  4736  1 video
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
tifm_7xx1               8576  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                40336  0 
tifm_core              11012  1 tifm_7xx1
ac                      6916  0 
battery                14212  0 
i2c_piix4               9612  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
button                  9232  0 
ati_agp                 9996  0 
agpgart                34760  1 ati_agp
i2c_core               24832  1 i2c_piix4
soundcore               8800  1 snd
k8temp                  6656  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  7 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
ide_cd                 32544  0 
cdrom                  37408  1 ide_cd
ide_disk               17536  3 
pata_acpi               8320  0 
pata_atiixp             8960  0 
ata_generic             8324  0 
libata                159344  3 pata_acpi,pata_atiixp,ata_generic
scsi_mod              151436  2 sbp2,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ohci_hcd               25348  0 
ehci_hcd               37900  0 
atiixp                  5648  0 [permanent]
ide_core              113996  3 ide_cd,ide_disk,atiixp
usbcore               146028  4 rtl8187,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              36872  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 


#also, dmesg gives me the following
[   32.860465] phy0: hwaddr 00:c0:a8:d8:96:a1, rtl8187 V1 + rtl8225z2
[   32.860489] usbcore: registered new interface driver rtl8187
[   33.662825] cs: IO port probe 0x100-0x3af: clean.
...
[  302.421072] wlan0: Initial auth_alg=0
[  302.421082] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  302.552929] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  302.654557] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  302.754588] wlan0: authentication with AP 00:15:05:0f:e8:41 timed out
[  339.770941] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  344.030220] wlan0: Initial auth_alg=0
[  344.030228] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  344.031612] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transactio
n=2 status=0)
[  344.031621] wlan0: authenticated
[  344.031626] wlan0: associate with AP 00:15:05:0f:e8:41
[  344.032725] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 
aid=2)
[  344.032732] wlan0: associated
[  344.032738] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  344.032742] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41
)
[  344.034300] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  352.295272] wlan0: no IPv6 routers present
[  354.215916] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume ou
t of range
[  355.828536] wlan0: Initial auth_alg=0
[  355.828545] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  355.829601] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transactio
n=2 status=0)
[  355.829606] wlan0: authenticated
[  355.829610] wlan0: associate with AP 00:15:05:0f:e8:41
[  355.830529] wlan0: authentication frame received from 00:15:05:0f:e8:41, but 
not in authenticate state - ignored
[  355.831091] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=
0 aid=2)
[  355.831097] wlan0: associated
[  355.831103] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  355.831108] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41
)
[  355.863355] wlan0: Initial auth_alg=0
[  355.863365] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  355.962360] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  356.062283] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  356.162206] wlan0: authentication with AP 00:15:05:0f:e8:41 timed out
[  368.019459] wlan0: deauthenticate(reason=3)
[  400.785051] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  404.370774] wlan0: Initial auth_alg=0
[  404.370784] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  404.371764] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transactio
n=2 status=0)
[  404.371769] wlan0: authenticated
[  404.371772] wlan0: associate with AP 00:15:05:0f:e8:41
[  404.372699] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 
aid=2)
[  404.372705] wlan0: associated
[  404.372711] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  404.372716] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41
)
[  404.374167] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  412.203360] wlan0: no IPv6 routers present
[  421.265573] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume ou
t of range
[  422.946264] wlan0: Initial auth_alg=0
[  422.946271] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  423.044784] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  423.058045] wlan0: Initial auth_alg=0
[  423.058049] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  423.075498] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transactio
n=2 status=0)
[  423.075502] wlan0: authenticated
[  423.075506] wlan0: associate with AP 00:15:05:0f:e8:41
[  423.076617] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=
0 aid=2)
[  423.076620] wlan0: associated
[  423.076625] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  423.076628] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  430.258413] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  431.863070] wlan0: Initial auth_alg=0
[  431.863080] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  431.911589] wlan0: Initial auth_alg=0
[  431.911598] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  432.009683] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  432.109598] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  432.209525] wlan0: authentication with AP 00:15:05:0f:e8:41 timed out
[  440.248016] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  441.938383] wlan0: Initial auth_alg=0
[  441.938392] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  442.135642] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  442.149594] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  442.149601] wlan0: authenticated
[  442.149607] wlan0: associate with AP 00:15:05:0f:e8:41
[  442.150046] wlan0: Initial auth_alg=0
[  442.150051] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  442.152237] wlan0: association frame received from 00:15:05:0f:e8:41, but not in associ
ate state - ignored
[  442.152834] wlan0: association frame received from 00:15:05:0f:e8:41, but not in associ
ate state - ignored
[  442.153337] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  442.153344] wlan0: authenticated
[  442.153349] wlan0: associate with AP 00:15:05:0f:e8:41
[  442.161357] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  442.161364] wlan0: associated
[  442.161373] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  442.161377] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  442.162925] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  442.472935] wlan0: deauthenticate(reason=3)
[  445.795948] wlan0: Initial auth_alg=0
[  445.795957] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  445.896451] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  445.996368] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  446.098290] wlan0: authentication with AP 00:15:05:0f:e8:41 timed out
[  465.397971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  471.546104] wlan0: Initial auth_alg=0
[  471.546113] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  471.546931] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  471.546937] wlan0: authenticated
[  471.546942] wlan0: associate with AP 00:15:05:0f:e8:41
[  471.547925] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  471.547930] wlan0: associated
[  471.547937] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  471.547942] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  471.549408] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  479.140478] wlan0: no IPv6 routers present
[  493.874451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  498.855821] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  498.855828] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  649.077018] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  651.856084] wlan0: deauthenticate(reason=3)
[  654.749467] wlan0: Initial auth_alg=0
[  654.749474] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  654.750814] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  654.750818] wlan0: authenticated
[  654.750821] wlan0: associate with AP 00:15:05:0f:e8:41
[  654.751996] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  654.752000] wlan0: associated
[  654.752005] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  654.752008] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  654.753475] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  663.433067] wlan0: no IPv6 routers present
[  674.173630] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  675.860522] wlan0: Initial auth_alg=0
[  675.860529] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  675.960884] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  675.962945] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  675.962950] wlan0: authenticated
[  675.962953] wlan0: associate with AP 00:15:05:0f:e8:41
[  675.962965] wlan0: Initial auth_alg=0
[  675.962968] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  675.963686] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  675.963689] wlan0: authenticated
[  675.963692] wlan0: associate with AP 00:15:05:0f:e8:41
[  675.965186] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  675.965190] wlan0: associated
[  675.965195] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  675.965198] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  675.966780] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[  675.966788] wlan0: association frame received from 00:15:05:0f:e8:41, but not in associ
ate state - ignored
[  692.383303] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  694.124101] wlan0: Initial auth_alg=0
[  694.124110] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  694.222508] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  694.227747] wlan0: Initial auth_alg=0
[  694.227756] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  694.233497] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  694.233503] wlan0: authenticated
[  694.233508] wlan0: associate with AP 00:15:05:0f:e8:41
[  694.234427] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[  694.236293] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  694.236299] wlan0: associated
[  694.236306] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  694.236310] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  710.321288] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  712.087921] wlan0: Initial auth_alg=0
[  712.087929] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  712.188468] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  712.197757] wlan0: Initial auth_alg=0
[  712.197762] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  712.200761] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
-=0)
[  712.200766] wlan0: authenticated
[  712.200770] wlan0: associate with AP 00:15:05:0f:e8:41
[  712.201063] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[  712.202250] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  712.202256] wlan0: associated
[  712.202262] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  712.202267] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  799.206360] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  801.511140] wlan0: deauthenticate(reason=3)
[  804.207461] wlan0: Initial auth_alg=0
[  804.207470] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  804.208444] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  804.208450] wlan0: authenticated
[  804.208455] wlan0: associate with AP 00:15:05:0f:e8:41
[  804.209687] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  804.209693] wlan0: associated
[  804.209697] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  804.209707] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  804.211166] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  814.048930] wlan0: no IPv6 routers present
[  820.383854] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  822.162545] wlan0: Initial auth_alg=0
[  822.162554] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  822.261026] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  822.262216] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  822.262222] wlan0: authenticated
[  822.262225] wlan0: associate with AP 00:15:05:0f:e8:41
[  822.262336] wlan0: Initial auth_alg=0
[  822.262341] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  822.263281] wlan0: association frame received from 00:15:05:0f:e8:41, but not in associ
ate state - ignored
[  822.264023] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  822.264028] wlan0: authenticated
[  822.264032] wlan0: associate with AP 00:15:05:0f:e8:41
[  822.265152] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  822.265157] wlan0: associated
[  822.265164] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  822.265169] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  838.437725] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  840.363459] wlan0: Initial auth_alg=0
[  840.363468] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  840.564528] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  840.581883] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  840.581888] wlan0: authenticated
[  840.581894] wlan0: associate with AP 00:15:05:0f:e8:41
[  840.583317] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[  840.583325] wlan0: Initial auth_alg=0
[  840.583330] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  840.585759] wlan0: association frame received from 00:15:05:0f:e8:41, but not in associ
ate state - ignored
[  840.586376] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  840.586381] wlan0: authenticated
[  840.586384] wlan0: associate with AP 00:15:05:0f:e8:41
[  840.588753] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  840.588759] wlan0: associated
[  840.588765] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  840.588770] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  851.904931] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  853.708245] wlan0: deauthenticate(reason=3)
[  855.496139] wlan0: Initial auth_alg=0
[  855.496148] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  855.497120] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  855.497127] wlan0: authenticated
[  855.497131] wlan0: associate with AP 00:15:05:0f:e8:41
[  855.498487] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  855.498492] wlan0: associated
[  855.498499] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  855.498503] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  855.499981] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  865.125055] wlan0: no IPv6 routers present
[  889.341172] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  891.137871] wlan0: Initial auth_alg=0
[  891.137878] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  891.238382] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  891.255663] wlan0: Initial auth_alg=0
[  891.255668] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  891.256037] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  891.256041] wlan0: authenticated
[  891.256047] wlan0: associate with AP 00:15:05:0f:e8:41
[  891.256288] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[  891.257221] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in authenticate state - ignored
[  891.258595] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  891.258601] wlan0: associated
[  891.258607] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  891.258612] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[  912.415945] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[  914.144662] wlan0: Initial auth_alg=0
[  914.144671] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  914.243166] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  914.254428] wlan0: Initial auth_alg=0
[  914.254434] wlan0: authenticate with AP 00:15:05:0f:e8:41
[  914.257689] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[  914.257695] wlan0: authenticated
[  914.257700] wlan0: associate with AP 00:15:05:0f:e8:41
[  914.257990] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[  914.259053] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[  914.259058] wlan0: associated
[  914.259066] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[  914.259070] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[ 1005.871633] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[ 1007.482237] wlan0: Initial auth_alg=0
[ 1007.482246] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1007.483676] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[ 1007.483683] wlan0: authenticated
[ 1007.483687] wlan0: associate with AP 00:15:05:0f:e8:41
[ 1007.484859] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[ 1007.484864] wlan0: associated
[ 1007.484871] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[ 1007.484876] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[ 1007.539158] wlan0: Initial auth_alg=0
[ 1007.539165] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1007.638897] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1007.738821] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1007.840743] wlan0: authentication with AP 00:15:05:0f:e8:41 timed out
[ 1040.777999] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1043.449583] wlan0: deauthenticate(reason=3)
[ 1046.302558] wlan0: Initial auth_alg=0
[ 1046.302568] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1046.303417] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[ 1046.303423] wlan0: authenticated
[ 1046.303427] wlan0: associate with AP 00:15:05:0f:e8:41
[ 1046.304659] wlan0: RX AssocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[ 1046.304666] wlan0: associated
[ 1046.304672] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[ 1046.304677] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[ 1046.306129] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1054.958179] wlan0: no IPv6 routers present
[ 1061.022654] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[ 1062.715530] wlan0: Initial auth_alg=0
[ 1062.715538] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1062.813924] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1062.818929] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[ 1062.818933] wlan0: authenticated
[ 1062.818936] wlan0: associate with AP 00:15:05:0f:e8:41
[ 1062.827686] wlan0: Initial auth_alg=0
[ 1062.827696] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1062.828066] wlan0: association frame received from 00:15:05:0f:e8:41, but not in associ
ate state - ignored
[ 1062.829073] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[ 1062.829076] wlan0: authenticated
[ 1062.829080] wlan0: associate with AP 00:15:05:0f:e8:41
[ 1062.822607] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[ 1062.822613] wlan0: associated
[ 1062.822618] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[ 1062.822622] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[ 1079.014544] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[ 1080.753274] wlan0: Initial auth_alg=0
[ 1080.753283] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1080.851738] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1080.856993] wlan0: Initial auth_alg=0
[ 1080.856999] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1080.860369] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[ 1080.860375] wlan0: authenticated
[ 1080.860380] wlan0: associate with AP 00:15:05:0f:e8:41
[ 1080.861239] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[ 1080.862240] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[ 1080.862247] wlan0: associated
[ 1080.862253] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[ 1080.862257] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[ 1097.613795] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[ 1099.320542] wlan0: Initial auth_alg=0
[ 1099.320551] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1099.421048] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1099.435978] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[ 1099.435984] wlan0: authenticated
[ 1099.435987] wlan0: associate with AP 00:15:05:0f:e8:41
[ 1099.436286] wlan0: Initial auth_alg=0
[ 1099.436290] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1099.437477] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)
[ 1099.437483] wlan0: authenticated
[ 1099.437488] wlan0: associate with AP 00:15:05:0f:e8:41
[ 1099.437785] wlan0: RX ReassocResp from 00:15:05:0f:e8:41 (capab=0x461 status=0 aid=2)
[ 1099.437789] wlan0: associated
[ 1099.437796] wlan0: CTS protection enabled (BSSID=00:15:05:0f:e8:41)
[ 1099.437800] wlan0: switched to short barker preamble (BSSID=00:15:05:0f:e8:41)
[ 1099.439356] wlan0: authentication frame received from 00:15:05:0f:e8:41, but not in aut
henticate state - ignored
[ 1099.440588] wlan0: association frame received from 00:15:05:0f:e8:41, but not in associ
ate state - ignored
[ 1115.490778] wlan0: No ProbeResp from current AP 00:15:05:0f:e8:41 - assume out of range
[ 1117.176907] wlan0: Initial auth_alg=0
[ 1117.176915] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1117.275292] wlan0: authenticate with AP 00:15:05:0f:e8:41
[ 1117.282273] wlan0: RX authentication from 00:15:05:0f:e8:41 (alg=0 transaction=2 status
=0)

and so on, ad naseum...
```

Help!

---

### Post by Tlingit on 2008-07-19
Hey i found you have to remove mac90211 module (rebuild you kernel with out it)
and build the kernel with the ieee80211.
use the custom driver form aircrack-ng if you find anyway removing the mac from the kernel before compilation i would appreciate a heads up

---

### Post by scholzilla on 2008-07-20
Thanks, but I gave up on this chipset and bought a linksys usb card.

---

### Post by afeasfaerw23231233 on 2009-03-14
I have exactly the same problem but I don't want to buy an external dongle. ```

dmesg:
wlan0: No ProbeResp from current AP 00:19:5b:df:63:da - assume out of range 
```
and at the same time the log of router said 
```

Router:
Sat Mar 14 02:08:34 2009 Disassociated:  00-22-43-74-7B-05 because idle 300 seconds

```

I google around and knows this not the problem from realtek 8187b/l only, many people with other wireless chipsets also suffer from this problem. Would anyone please help me? I am really tired with the wireless problem in UBUNTU. 
Thanks!

---

### Post by scholzilla on 2009-03-15
i've convinced myself at least that there is no hope for this chipset. I'm afraid an external dongle is likely your only hope.

---

### Post by afeasfaerw23231233 on 2009-03-15
I am now trying to remove ndiswrapper and get back the native driver to see if instability issue still occurs. I don't want to plug an usb dongle on it. It will stick out and I am afraid it will be detached by careless. My notebook doesn't have a pcimia slot.

---

### Post by afeasfaerw23231233 on 2009-03-21
My problem seems solved

[http://ubuntuforums.org/showthread.php?p=6932570#post6932570](http://ubuntuforums.org/showthread.php?p=6932570#post6932570)

---

