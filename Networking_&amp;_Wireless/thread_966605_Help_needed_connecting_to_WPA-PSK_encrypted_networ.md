---
title: "Help needed connecting to WPA-PSK encrypted network"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by arcster on 2008-11-01
I'm a Linux newbie trying to connect to my home wireless network. My laptop is a Compaq Armada with a Lucent PC card and Oronoco drivers installed. I'm running Xubuntu 8.04. I connected to an open WiFi network this morning, so the card doesn't seem to be the issue.

When I look at /etc/network/interfaces, I see
# the loopback network interface
auto lo
iface lo inet loopback
# The primary network interface

... and nothing else

If I click on the network icon in the taskbar at the top, I see my network ssid. If I click it, I get a dialog box "Passphrase Required by Wireless Network" However, the security options are a few WEP choices (ASCII, HEX, or Passphrase) or LEAP. There is no WPA option

If I go into Application > System > Nework, I see my network ssid, and I enter my password and set dhcp, but no luck

I found some advice at <http://tillamookrage.blogspot.com/2007/11/getting-wpa-psk-wireless-working-in.html> to make sure the wpa_supplicant is installed. I also modified the wpa_supplicant.conf file as the author advised.

I'm lost. Any help would be appreciated.

Thanks,
arcster

---

### Post by itakeupspace on 2008-11-02
I won't claim to be any good at this, but since I'm fighting my own wireless battle right now, I might as well see if I can help.  There isn't much listed in your /etc/network/interfaces file because that's the old way of configuring networks.  NetworkManager does the same job, differently and more dynamically...when it works correctly.

If NetworkManager doesn't list WPA as an option, it's because your drivers aren't telling NM that they support it.  This means either your current drivers don't support WPA , or the card doesn't support WPA.

I looked for info on the Lucent cards, and it looks like that could mean any number of different models and/or chipsets (way to go marketing dept...[sigh]).  Lets figure out exactly what you have first.  Run this and post the output:
```
sudo lshw -C network
```

Edit to add:  For good measure, post this too:
```
lsmod
```

---

### Post by arcster on 2008-11-03
> **itakeupspace said:**
> 

Thanks for the interest, itakeupspace. I should tell you I've done a couple things since my post. I switched my router's security from WPA to WEP. So now I can connect. (I would prefer to go back to WPA if possible). Also, I installed wicd. Here's the output you requested
```
sudo lshw -C network
```
  *-network               
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network:0
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:9f:d3:d1:57:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: eth0
       serial: 00:02:2d:2b:12:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 7.28 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11b




Edit to add:  For good measure, post this too:
```
lsmod
```
```

Module                  Size  Used by
orinoco_cs             21516  1 
orinoco                48020  1 orinoco_cs
hermes                 14976  2 orinoco_cs,orinoco
usbhid                 35840  0 
hid                    50560  1 usbhid
ipv6                  263972  8 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_ondemand       14988  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
af_packet              25728  4 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
loop                   23180  0 
joydev                 18368  0 
pcmcia                 43052  1 orinoco_cs
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
radio_maestro          14720  0 
videodev               41344  1 radio_maestro
v4l1_compat            22404  1 videodev
snd_es1968             34208  2 
gameport               19468  1 snd_es1968
snd_ac97_codec        111652  1 snd_es1968
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
evdev                  17696  8 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_es1968,snd_pcm
snd_mpu401_uart        15360  1 snd_es1968
psmouse                45200  0 
serio_raw              13444  0 
snd_seq_dummy          10884  0 
container              11520  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
battery                18436  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                     12292  0 
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              16144  0 
pcspkr                 10624  0 
intel_agp              33724  1 
yenta_socket           31756  4 
shpchp                 37908  0 
soundcore              15328  1 snd
i2c_core               31892  1 i2c_piix4
rsrc_nonstatic         19072  1 yenta_socket
agpgart                42184  1 intel_agp
pci_hotplug            35236  1 shpchp
pcmcia_core            43412  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ata_piix               24580  2 
uhci_hcd               30736  0 
libata                177312  3 pata_acpi,ata_generic,ata_piix
usbcore               148848  3 usbhid,uhci_hcd
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 

```
Any thoughts?
Thanks,
arcster

---

### Post by itakeupspace on 2008-11-04
It looks like this thread ([http://ubuntuforums.org/showthread.php?t=304217](http://ubuntuforums.org/showthread.php?t=304217)) and this post ([http://ubuntuforums.org/showthread.php?t=304217#4](http://ubuntuforums.org/showthread.php?t=304217#4)) in particular hold the definitive solution to your problem.  Long story short, the driver Ubuntu shipped doesn't support WPA, so either be happy with WEP or jump through the hoops those guys came up with.

Hope this helps.

---

