---
title: "Wireless network does not like Ubuntu only windows."
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Nem1976 on 2008-07-07
Good morning all. 

I just started working with a new company this last week and I have run into an issue with my Ubuntu Laptop. I can't connect to the wireless network.  The Access points are Cisco and the DHCP is a program call firstspot.

I can connect to the wireless via Windows Vista which I have on the laptop as well(via dualboot).

If I try to connect using Wicd Manager I just get obtaining IP address.  It goes for about 1 min then just stops trying.  I talked to the System admin and he mentioned that he has also had issues with Mac's connecting to the wireless network as well.  

With out taking or changing the wireless network is there something I can test or try to see where the problem is located.

I'm starting to think that the gateway server that is handing out dhcp is causing the issue but I wanted to be sure.

Thanks for any help.

---

### Post by blazercist on 2008-07-07
you need to provide alot more information

in order to diagnose the problem you need to provide the output of these commands in terminal

```

sudo ifconfig

```
```

lsmod

```

depending on whether the wireless adapter in PCI or USB either: 
```

lspci

```

or

```

lsusb

```
Also, you need to give us information about the security scheme in place on this network... is it WEP WPA etc...

---

### Post by Nem1976 on 2008-07-07
Sorry for not providing enough info I'm still not awake and still green when it comes to linux.

Current security is none anyone can connect to the wireless network but if you try to browse the web you are taken to a login page were you need to provide a username and password.


```
sudo ifconfig


eth0      Link encap:Ethernet  HWaddr 00:16:d4:af:b2:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96228 (93.9 KB)  TX bytes:96228 (93.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:69:b8:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10662 (10.4 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:19:d2:69:b8:96  
          inet addr:169.254.8.199  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-69-B8-96-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


```

lsmod

Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
af_packet              23812  4 
binfmt_misc            12808  1 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ipv6                  267780  16 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
pcmcia                 40876  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
snd_seq_dummy           4868  0 
battery                14212  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
ac                      6916  0 
snd_rawmidi            25760  1 snd_seq_midi
psmouse                40336  0 
sdhci                  19076  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mmc_core               51460  1 sdhci
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
evdev                  13056  8 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi_acer                9644  1 acer_acpi
intel_agp              25492  1 
pcspkr                  4224  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  3 drm,intel_agp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
pata_acpi               8320  0 
ata_piix               19588  2 
b44                    28432  0 
ata_generic             8324  0 
ssb                    34308  1 b44
mii                     6400  1 b44
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  3 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

```

lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)


```

---

### Post by blazercist on 2008-07-07
It appears you have the same wireless chipset as me and your system is detecting the adapter correctly and the driver seems to be functioning properly....Why are you using Wicd?  Why not just network-manager?  I use network manager and it works just fine.

---

### Post by Nem1976 on 2008-07-07
If I remember right I installed it to be able to see wireless networks with a hidden ssid.  Every other network I can connect to it's just this specific network I'm having issues.  I'm starting to think it's the Firstspot server causing the issue.

---

### Post by blazercist on 2008-07-07
could be, I had a problem with my home network once and I just set my router to factory defaults and the problem went away, maybe its the configuration on the AP thats causing the problem.

---

### Post by Nem1976 on 2008-07-07
I'm starting to think that it's either the access points or the gateware server.  Leaning more towards the gateway server(firstspot) since I'm running Cisco Access points.

---

### Post by The incredible bulk on 2008-07-07
First let me say sorry for your issues.

Second, I have a very large amount of wireless experience. From cisco to Mikrotik and about everything in between. I guess that said let's start on your issue.

Now as I understand the wireless link association process:
[LIST=1]
[*]Connect to the access point in question (usually identified by bssid)
[*]exchange security information so that the client and ap can find a common token
[*]agree on said protocol, and then the client hands the ap it's security information
[*]AP authenticates and allows a REGISTRATION.
[*]Network traffic is passed (including dhcp information)
[/LIST]

If there's a breakdown at ANY step, you don't get good MOJO.

Now all that said (sorry for being windy) I would simply check my logs on the AP for an ASSOCIATION as cisco likes to call it... Mikrotik it's a registration.. but you get the idea. Simply check to see if the AP even is letting you in the door (you'd be looking for your the MAC address of your wireless card.)

Then look at the logs on your DHCP server, and see if your MAC shows up there. In my experience it's usually the cisco AP being a bit OVER ZEALOUS with it's security.

Hope this helps

---

