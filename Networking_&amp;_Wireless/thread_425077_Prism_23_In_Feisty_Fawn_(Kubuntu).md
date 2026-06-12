---
title: "Prism 2/3 In Feisty Fawn (Kubuntu)"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by ICE|8 on 2007-04-27
My original post - unanswered: [http://kubuntuforums.net/forums/index.php?topic=2738.0](http://kubuntuforums.net/forums/index.php?topic=2738.0)

I have two cards with no support in Kubuntu:
1) DLink DWL-650 P1  - Prism 3
2) ZoomAir 4100 (I think that' right) - Prism 2

The Zoomair hangs Feisty on boot, but is detected once booted and just doesn't do anything through KNetworkManager. The DWL is just plain missing in action. I have followed some posts here and in the Kubuntu forums for Feisty - with no luck from any of the instructions for either card.

I am trying to convert from openSuse. Too bloated and slow. Can anyone offer support so that I don't have to go back?  Back in the day I used to build pcmcia card support and install wlan-ng on RedHat. Now that hostap is (supposedly) built into the kernel, I thought that this would be seamless and that with all of the years that these cards have been around that this would be a no-brainer and seamless. 

If I can get some guidance, I'd be more than happy to post a solution.

Just as an added comment... It might be beneficial to post a howto for noobs/less experienced on the proper procedures for trying to get this stuff to work, with a listing of what to post to get the help they (we) need. 

Thanks...

---

### Post by chili555 on 2007-04-27
It is often the case that the modules, orinoco, hostap *and* prism2 load for these cards and fight for world domination instead of downloading mp3's, torrents and viral videos. You can verify this by doing:```
lsmod | grep prism2
```To get the other two to sit down and get to work, you need to fire prism2.```
sudo gedit /etc/modprobe.d/blacklist
```and add the following on its own new line:```
blacklist prism2_<whatever>
```Substitute the module you found from  *lsmod* without the .ko extension. It may be prism2_cs.

Post back and let the other Prism fans know.

---

### Post by dbott67 on 2007-04-27
Just to add what chili555 said, this [thread]("http://ubuntuforums.org/showthread.php?t=425032&page=2") has the same problem with the fix posted in #16.

-Dave

---

### Post by ICE|8 on 2007-04-28
Thanks for the posts.

Output of lshw -C:
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:b9:a9:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.15.101 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: Rate wireless Networking
       vendor: ZoomAir 11Mbps High
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:40:36:01:b0:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.4.9 multicast=yes wireless=IEEE 802.11b

Doing an lspci won't give us any information, as it is PCMCIA.

Added this to /etc/modprobe.d/blacklist:
# fixes fighting over the prism card(s)
blacklist prism2
blacklist prism2_cs
blacklist prism2_pci

Still not working. What other info is needed?

---

### Post by dbott67 on 2007-04-28
> **ICE|8 said:**
> Thanks for the posts.
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:40:36:01:b0:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes [COLOR=Red]driver=hostap[/COLOR] driverversion=0.4.4-kernel firmware=1.4.9 multicast=yes wireless=IEEE 802.11b

Doing an lspci won't give us any information, as it is PCMCIA.

Added this to /etc/modprobe.d/blacklist:
# fixes fighting over the prism card(s)
blacklist prism2
blacklist prism2_cs
blacklist prism2_pci

Still not working. What other info is needed?

Try adding the hostap* modules to the blacklist also:

```
blacklist prism2
blacklist prism2_pci
blacklist prism2_cs
[COLOR=Red]blacklist hostap_pci
blacklist hostap[/COLOR]
```

-Dave

---

### Post by chili555 on 2007-04-28
I don't actually believe blacklisting the hostap module is needed, or the fix. According to this:```
driver=3c59x duplex=full ip=192.168.15.101
```Your ethernet is connected and has an IP address. NetworkManager, installed by default in Feisty, will not initiate a connection with wireless if one is available with ethernet. Unplug the wire, reboot and see if your wireless doesn't spring to life.

---

### Post by ICE|8 on 2007-04-28
Dave and chilli555

I really appreciate all of the help.

I tried both of your tips. Even tried blacklisting orinoco and orinoco_cs. lshw -C network shows that it is loading the hostap driver in either case, oddly. And it still hangs when the wireless card is inserted during boot in both cases (I still have to insert after the system loads). In all three cases, there was no wireless.

In openSuse 10.2 I had similar problems. I blacklisted orinoco and orinoco_cs and KNetworkManager was off and going.

Hmmm...

---

### Post by dbott67 on 2007-04-28
I'm by no means an expert on this one, so please take my advice for what it's worth (i.e. nothing).  My advice is just some trial & error, really.

I was helping another poster that had a similar problem with the prism chipset and when I posted here, it was only using the answer I found in another thread.  Having said that, you may want to try blacklisting everything but the prism chipset (i.e. blacklist orinoco* & hostap*) and see what happens.

Another option would be to remove all items that you've added to your blacklist and post the output of lsmod.  From here, we may be able to see exactly which modules are loading for the wireless and systematically blacklist them:
```
dbott@feisty:~$ lsmod
Module                  Size  Used by
isofs                  36284  0
udf                    85252  0
smbfs                  66040  3
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
fglrx                 540004  11
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_ondemand        9228  0
cpufreq_powersave       2688  0
cpufreq_stats           7360  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0
cpufreq_conservative     8200  0
pcc_acpi               13184  0
dev_acpi               12292  0
tc1100_wmi              8068  0
sony_acpi               6284  0
ac                      6020  0
battery                10756  0
button                  8720  0
sbs                    15652  0
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
video                  16388  0
dock                   10268  0
container               5248  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
ipv6                  268704  14
lp                     12452  0
snd_emu10k1_synth       8192  0
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  4 snd_emu10k1_synth
snd_ac97_codec         98336  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
snd                    54020  18 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0
soundcore               8672  1 snd
emu10k1_gp              4736  0
gameport               16520  2 emu10k1_gp
intel_agp              25116  1
agpgart                35400  2 fglrx,intel_agp
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
af_packet              23816  2
tsdev                   8768  0
evdev                  11008  3
usbhid                 26592  0
hid                    27392  1 usbhid
ext3                  133128  2
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sd_mod                 23428  4
floppy                 59524  0
ehci_hcd               34188  0
ohci_hcd               22532  0
8139too                27648  0
mii                     6528  1 8139too
uhci_hcd               25360  0
usbcore               134280  5 usbhid,ehci_hcd,ohci_hcd,uhci_hcd
ata_piix               15492  3
ata_generic             9092  0
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

```-Dave

---

### Post by ICE|8 on 2007-04-28
Here's an lsmod with hostap the only thing not blacklisted. It looks like it is picked up to me. My network is WEP BTW. Do you think I should not use the KNetworkManager and try to manually configure? If so, do you have any ideas of what file(s).

Module                  Size  Used by
ipv6                  268704  8
arc4                    2944  2
ecb                     4480  2
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  0
hostap_cs              62740  3
hostap                113924  1 hostap_cs
ieee80211_crypt         7040  2 ieee80211_crypt_wep,hostap
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_ich           6288  0
speedstep_lib           6148  1 speedstep_ich
cpufreq_ondemand        9228  1
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
tc1100_wmi              8068  0
pcc_acpi               13184  0
dev_acpi               12292  0
sony_acpi               6284  0
container               5248  0
asus_acpi              17308  0
dock                   10268  0
ac                      6020  0
battery                10756  0
button                  8720  0
backlight               7040  1 asus_acpi
video                  16388  0
sbs                    15652  0
i2c_ec                  5888  1 sbs
sbp2                   23812  0
lp                     12452  0
fuse                   46612  0
joydev                 10816  0
pcmcia                 39212  1 hostap_cs
snd_intel8x0           34204  3
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
yenta_socket           27532  4
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  4 hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               22784  1 i2c_ec
serio_raw               7940  0
pcspkr                  4224  0
psmouse                38920  0
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
soundcore               8672  1 snd
intel_agp              25116  1
agpgart                35400  1 intel_agp
intel_rng               6528  0
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  6
evdev                  11008  4
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sd_mod                 23428  3
ata_generic             9092  0
usbhid                 26592  0
hid                    27392  1 usbhid
floppy                 59524  0
ata_piix               15492  2
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
3c59x                  46632  0
mii                     6528  1 3c59x
generic                 5124  0 [permanent]
uhci_hcd               25360  0
usbcore               134280  3 usbhid,uhci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

---

### Post by dbott67 on 2007-04-28
Just wrapping your post in 'code' tags to make it easier to read:
```

Module                  Size  Used by
ipv6                  268704  8
arc4                    2944  2
ecb                     4480  2
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  0
[COLOR=Red] hostap_cs[/COLOR]              62740  3
[COLOR=Red] hostap[/COLOR]                113924  1 [COLOR=Red]hostap_cs[/COLOR]
ieee80211_crypt         7040  2 ieee80211_crypt_wep,[COLOR=Red]hostap[/COLOR]
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_ich           6288  0
speedstep_lib           6148  1 speedstep_ich
cpufreq_ondemand        9228  1
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
tc1100_wmi              8068  0
pcc_acpi               13184  0
dev_acpi               12292  0
sony_acpi               6284  0
container               5248  0
asus_acpi              17308  0
dock                   10268  0
ac                      6020  0
battery                10756  0
button                  8720  0
backlight               7040  1 asus_acpi
video                  16388  0
sbs                    15652  0
i2c_ec                  5888  1 sbs
sbp2                   23812  0
lp                     12452  0
fuse                   46612  0
joydev                 10816  0
pcmcia                 39212  1 [COLOR=Red]hostap_cs[/COLOR]
snd_intel8x0           34204  3
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
yenta_socket           27532  4
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  4 [COLOR=Red]hostap_cs[/COLOR],pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               22784  1 i2c_ec
serio_raw               7940  0
pcspkr                  4224  0
psmouse                38920  0
snd 54020 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,sn d_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti mer,snd_seq_device
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
soundcore               8672  1 snd
intel_agp              25116  1
agpgart                35400  1 intel_agp
intel_rng               6528  0
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  6
evdev                  11008  4
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sd_mod                 23428  3
ata_generic             9092  0
usbhid                 26592  0
hid                    27392  1 usbhid
floppy                 59524  0
ata_piix               15492  2
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
3c59x                  46632  0
mii                     6528  1 3c59x
generic                 5124  0 [permanent]
uhci_hcd               25360  0
usbcore               134280  3 usbhid,uhci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability
```

---

### Post by ICE|8 on 2007-04-28
Don't know if this will be more clear...

ian@lycanthrope:~$ sudo lsmod | grep hostap
Password:
hostap_cs              62740  3
hostap                113924  1 hostap_cs
ieee80211_crypt         7040  2 ieee80211_crypt_wep,hostap
pcmcia                 39212  1 hostap_cs
pcmcia_core            40852  4 hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic

---

### Post by dbott67 on 2007-04-28
I would try blacklisting the [COLOR=Red]hostap[/COLOR] and [COLOR=Red]hostap_cs[/COLOR] modules, along with the [COLOR=Red]prism[/COLOR] ones.  Remove the [COLOR=Blue]orinoco[/COLOR] modules from the blacklist.

-Dave

---

### Post by ICE|8 on 2007-04-28
OK. Here's with prism2 and hostap blacklisted and Orinoco not...

```
ian@lycanthrope:~$ lsmod
Module                  Size  Used by
ipv6                  268704  8
arc4                    2944  2
ecb                     4480  2
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  0
orinoco_cs             16900  0
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
hostap_cs              62740  3
hostap                113924  1 hostap_cs
ieee80211_crypt         7040  2 ieee80211_crypt_wep,hostap
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_ich           6288  0
speedstep_lib           6148  1 speedstep_ich
cpufreq_ondemand        9228  1
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
tc1100_wmi              8068  0
pcc_acpi               13184  0
dev_acpi               12292  0
sony_acpi               6284  0
container               5248  0
asus_acpi              17308  0
dock                   10268  0
ac                      6020  0
battery                10756  0
button                  8720  0
backlight               7040  1 asus_acpi
video                  16388  0
sbs                    15652  0
i2c_ec                  5888  1 sbs
sbp2                   23812  0
lp                     12452  0
fuse                   46612  0
joydev                 10816  0
pcmcia                 39212  2 orinoco_cs,hostap_cs
snd_intel8x0           34204  1
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
serio_raw               7940  0
yenta_socket           27532  4
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  5 orinoco_cs,hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
i2c_core               22784  1 i2c_ec
psmouse                38920  0
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
intel_agp              25116  1
agpgart                35400  1 intel_agp
intel_rng               6528  0
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  8
evdev                  11008  4
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sd_mod                 23428  3
ata_generic             9092  0
usbhid                 26592  0
hid                    27392  1 usbhid
floppy                 59524  0
ata_piix               15492  2
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
3c59x                  46632  0
mii                     6528  1 3c59x
generic                 5124  0 [permanent]
uhci_hcd               25360  0
usbcore               134280  3 usbhid,uhci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability
```

---

### Post by chili555 on 2007-04-28
Although you blacklisted hostap, it's still loaded. Before you change anything, please let us see iwconfig. Thanks.

---

### Post by ICE|8 on 2007-04-28
Here goes:

```
ian@lycanthrope:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"ICE"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

eth1      IEEE 802.11b  ESSID:"ICE"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:74  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:4081   Missed beacon:0
```

---

### Post by chili555 on 2007-04-28
Assuming ICE is the ESSID of your router or access point, now let's see:```
sudo dhclient eth1
```If you are in the slightest doubt, confirm your ESSID with:```
sudo iwlist eth1 scan
```Scan may take a few tries. Thanks.

---

### Post by ICE|8 on 2007-04-28
Interesting:

```
ian@lycanthrope:~$ sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

[COLOR="Red"]wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801[/COLOR]
Listening on LPF/eth1/00:40:36:01:b0:63
Sending on   LPF/eth1/00:40:36:01:b0:63
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ian@lycanthrope:~$ sudo iwlist eth1 scan
eth1      No scan results
```

---

### Post by ICE|8 on 2007-04-28
Yeah, I'm stumpped, too. The last I used hostp (which I'd prefer to use), the wlan wasn't called wifi0, it was wlan0. It never showed me this today when it was the only module loaded. As I remember wifiX was reserved for Orinoco cards.

Are there any wireless config files worth showing?

---

### Post by ICE|8 on 2007-05-01
**This post could be related to an Ubuntu bug filed at**: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well, I followed all of the directions in the really great guide referred to via Launchpad.

Something is not working with encryption, me thinks, as the hostap driver is fully loaded. 

```
ian@lycanthrope:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"test"  Nickname:""
          Mode:Managed  Access Point: None   Bit Rate:2 Mb/s
          Sensitivity=1/3
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

eth1      IEEE 802.11b  ESSID:"test"  Nickname:""
          Mode:Managed  Access Point: None   Bit Rate:2 Mb/s
          Sensitivity=1/3
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0

ian@lycanthrope:~$ iwconfig wifi0 key A45AD7C087F7C567C7EB4956BD
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wifi0 ; Operation not permitted.
ian@lycanthrope:~$
```

Really odd.

---

