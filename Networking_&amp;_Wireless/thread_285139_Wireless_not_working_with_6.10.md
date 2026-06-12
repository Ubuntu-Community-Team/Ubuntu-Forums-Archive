---
title: "Wireless not working with 6.10"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by englishmen on 2006-10-26
I done a clean install of ubuntu via a downloaded iso, however the network configuration failed which is strange because when i installed 6.06 it was successful(the second time, see below). My windows based laptop is on the my wireless network as we speak and its working fine.

Any suggestions how i can fix this?

P.S. My laptop network card is a intel pro/wireless 3945

Concerning "The second time" see [http://ubuntuforums.org/showthread.php?t=276595](http://ubuntuforums.org/showthread.php?t=276595), but i can assure you that the laptop switch is switched to on.

Thanks

---

### Post by Antman on 2006-10-26
My wireless failed too when I replaced 6.06 with Edgy Final. I have a IPW2200 card though. I'm working on the problem now.:rolleyes:

---

### Post by englishmen on 2006-10-26
At least its nothing i done :-), i did however reinstall 6.06 and again its working, strange. Even stranger is that as said i done a clean install of ubuntu from a iso i downloaded, however before i did that i was using the RC which worked fine.

---

### Post by nick122147 on 2006-10-26
I`m also struggling with getting the ipw3945 to work on my sony vaio. Please post solution if any of you finds out..

---

### Post by ebeyer on 2006-10-26
I too am unable to use the wifi card on my desktop after doing a clean install of 6.10.  It worked with no configuration at all on 6.06.

---

### Post by nick122147 on 2006-10-26
I`m a bit closer to the solution.. Install linux restricted modules, and the card will show up. I only have left to configure it.

---

### Post by englishmen on 2006-10-26
> restricted modules

Ooh me me, what are they and where can i get them?

Thanks

---

### Post by Antman on 2006-10-26
Ok, mine was a silly fix. Although I don't recall having to do it in 6.06.
Basically I had to disable my wireless card in the Network applet before NetworkManager picked it up. ;) 
Working like a charm now with WPA and all.
IPW2200 card.

Ant

---

### Post by nick122147 on 2006-10-26
it`s working!
you must enable the restricted repositories, then 
apt-get update
and then  search for 
linux-restricted-modules-generic

then I installed 
network-manager-gnome

started it manually by 
nm-applet 
in the therminal and it showed up and is working.

now things are starting to come together in edgy

---

### Post by rado_london on 2006-10-26
> **nick122147 said:**
> it`s working!
you must enable the restricted repositories, then 
apt-get update
and then  search for 
linux-restricted-modules-generic

then I installed 
network-manager-gnome

started it manually by 
nm-applet 
in the therminal and it showed up and is working.

now things are starting to come together in edgy

that didnt work for me. I use intel pro wireless 2200bg which should be out working of the box. Any updates on the way to fix that?
EDIT: It works but the nm-applet doesnt work. However I dont care about it so I am happy now:)

---

### Post by mexlinux on 2006-10-26
> **nick122147 said:**
> it`s working!
you must enable the restricted repositories, then 
apt-get update
and then  search for 
linux-restricted-modules-generic

But If netowrk is not working,... how is one going to retrive the restricted modules????

---

### Post by Antman on 2006-10-26
> **mexlinux said:**
> But If netowrk is not working,... how is one going to retrive the restricted modules????

Don't have a hardwire connection??

---

### Post by acegolfer on 2006-10-26
I also had problems with WG511 v2 (China) connecting to my WPA network after a clean install of 6.10. I finally got it to work. The key was to use ndiswrapper 1.8 version. The rest was basically the same as configuring in Dapper. BTW, I'm using network-manager. One strange thing is in Dapper, I had to comment wlan0 in /etc/network/interfaces. But in Edgy, I had to comment it out (enabled).

Now the bad news. While booting, it takes a while during wireless card setup. But eventually it boots up and I'm right in to entering the key ring for the network manager. I upgraded to Edgy for speedy booting. But ironically, it's now way slower.

---

### Post by BroncoInCalifornia on 2006-10-27
I had trouble with an old orinoco gold card when I ran the 6.10 rc live. iwconfig gave the message 'no wireless extensions' for all interfaces. 

It turns out it erroneously loaded a prism2 module along with needed orinoco and hermes modules.  When I unloaded the modules and then reloaded orinoco_plx then everything worked.  Then I installed and everything worked!


I wonder if some of you who are having trouble could try lsmod in a terminal and post the results.  I would like to see if other people also had trouble with extra wireless kernel modules getting in the way.

---

### Post by FastZ on 2006-10-27
Here's my lsmod print out.

I hava Dell Inspiron 9300 with the built-in wireless card which for some reason isnt working for me after freshly installing Edgy.

```
matt@matt-laptop:~$ lsmod
Module                  Size  Used by
isofs                  38076  0 
udf                    89348  0 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  2 
drm                    74644  3 radeon
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
nls_utf8                3200  1 
ntfs                  112116  1 
nls_iso8859_1           5248  2 
nls_cp437               6912  2 
vfat                   14720  2 
fat                    56348  1 vfat
af_packet              24584  4 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
pcmcia                 40380  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
ipw2200               115652  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
ieee80211              35272  1 ipw2200
joydev                 11200  0 
ieee80211_crypt         7552  1 ieee80211
b44                    26764  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
tsdev                   9152  0 
usbhid                 45152  0 
sdhci                  20108  0 
mmc_core               32392  1 sdhci
mii                     6912  1 b44
sg                     37404  0 
pcspkr                  4352  0 
psmouse                41352  0 
serio_raw               8452  0 
evdev                  11392  2 
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
sd_mod                 22656  6 
generic                 5764  0 
ata_piix               11780  5 
ahci                   20228  0 
libata                 74892  2 ata_piix,ahci
scsi_mod              144648  6 sbp2,sg,sr_mod,sd_mod,ahci,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

No point in having a laptop when you aint got a working wireless connection.  It worked when I had Dapper on here.  

Downloaded and installed the Network Manager Applet but I dont think that was what I needed.  Everything works AFAIK except for my wireless.  ](*,)

---

### Post by BroncoInCalifornia on 2006-10-27
Does that Dell Inspiron 9300 have an Intel Wireless?  Perhaps lspci will tell.

---

### Post by serlex on 2006-10-27
hmm my 2200Gb worked out of the box

---

### Post by Nycto on 2006-10-27
I'm having the same problem. I just finished upgrading to 6.10 from 6.06 and my network connection went out. Everything else is working fine. 

I've got an old Belkin F5D6001 in my box. When I go to System -> Administration -> Networking, it lists both my nic and my on-board as wlan0 and eth0, but they are both labeled "wired connection."

The rub of it is, it would be a pain in the butt to hard wire the computer to a router. There is a reason I threw a wireless card in there.

And, brought direct to you through the power of thumb drives, here is my lsmod output:
```
Module                  Size  Used by
nls_utf8                2304  1 
nls_cp437               6016  1 
vfat                   13440  1 
fat                    54556  1 vfat
usb_storage            73408  1 
libusual               15632  1 usb_storage
binfmt_misc            11784  1 
ipv6                  257632  17 
via                    46688  2 
drm                    72468  3 via
powernow_k8            10888  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  1 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
af_packet              21768  4 
dm_mod                 60088  3 
md_mod                 78740  0 
sr_mod                 17060  0 
sbp2                   23304  0 
lp                     11972  0 
snd_seq_dummy           4100  0 
snd_seq_oss            34304  0 
snd_seq_midi            9088  0 
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                   8256  0 
sg                     35356  0 
snd_via82xx            28696  1 
gameport               15368  1 snd_via82xx
snd_ac97_codec         96672  1 snd_via82xx
snd_ac97_bus            2432  1 snd_ac97_codec
usbhid                 42464  0 
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
pcspkr                  3072  0 
via_rhine              23940  0 
snd_pcm                80520  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  2 snd_seq,snd_pcm
snd_page_alloc         10504  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8704  1 snd_via82xx
hostap_pci             56720  0 
hostap                119300  1 hostap_pci
i2c_viapro              8980  0 
evdev                  10496  1 
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
snd_rawmidi            25600  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8972  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
floppy                 60676  0 
ieee80211_crypt         6016  1 hostap
mii                     6016  1 via_rhine
psmouse                40072  0 
serio_raw               7300  0 
rtc                    12596  0 
i2c_core               22288  2 i2c_ec,i2c_viapro
orinoco_pci             7168  0 
orinoco                41748  1 orinoco_pci
hermes                  8576  2 orinoco_pci,orinoco
prism2_pci             72960  0 
amd64_agp              12228  1 
agpgart                33456  2 drm,amd64_agp
snd                    55428  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9952  1 snd
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
ext3                  138632  1 
jbd                    55700  1 ext3
ehci_hcd               32520  0 
uhci_hcd               23176  0 
usbcore               130304  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ohci1394               35248  0 
ieee1394              302904  2 sbp2,ohci1394
ide_generic             1536  0 
ide_cd                 32416  0 
cdrom                  37792  2 sr_mod,ide_cd
via82cxxx               9604  0 [permanent]
sd_mod                 21648  5 
generic                 4868  0 
sata_via                9604  4 
libata                 73228  1 sata_via
scsi_mod              141320  6 usb_storage,sr_mod,sbp2,sg,sd_mod,libata
thermal                14600  0 
processor              26028  2 powernow_k8,thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability
```

I'm relatively new to linux, so any help you can offer would be great.

---

### Post by englishmen on 2006-10-27
As i said i reinstalled 6.06 and i have just got ubuntu to update me via auto update, for someone reason its now working, strange but hay its working.

---

### Post by englishmen on 2006-10-27
As i said i reinstalled 6.06 and i have just got ubuntu to update me via auto update, for someone reason its now working, strange but hay its working.

---

### Post by FastZ on 2006-10-27
> **BroncoInCalifornia said:**
> Does that Dell Inspiron 9300 have an Intel Wireless?  Perhaps lspci will tell.

Here's what lspci pulls up for me on the laptop, (which I have hardwired to the switch at the moment).

```

matt@matt-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```It's showing my PRO/Wireless 2200BG built-in WLAN card there and it's also showing up under the System > Administration > Networking as being an option to turn on and off.  The wireless connection there in the Networking configuration window is enabled as is the hardwired connection for my ethernet NIC.

Would I need to install the IPW2200 drivers like I had to do back when I was running Fedora Core 5?  I remember having to do that then because my wireless NIC wasnt even showing up in the network configuration.  But this time it actually shows up, it just doesnt work, even though it's enabled and my SSID and WAP password information is inputted in the configuration.

---

### Post by FastZ on 2006-10-27
Ok, I just installed the IPW2200 firmware on here and then disabled and reenabled the wireless card in System > Administration > Networking and then ran ifconfig from a terminal session and this is what I got as an output.

```
matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXXX::XXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1721296 (1.6 MiB)  TX bytes:236140 (230.6 KiB)
          Interrupt:209 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xe000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6100 (5.9 KiB)  TX bytes:6100 (5.9 KiB)

```

Why does my eth01 interface have link encapsulation as ethernet when it's supposed to be wireless?

---

### Post by mexlinux on 2006-10-28
> **Antman said:**
> Don't have a hardwire connection??
Not at home, we share a wireless, router is at neightbourgs place.

BUT, I'm posting this from kubuntu live CD, and wireless is working....
I'm confused....!
It's me supposed not to connect from installation, but I'm doing it from live cd...

---

