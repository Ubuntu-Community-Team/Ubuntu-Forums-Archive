---
title: "Wireless failed in 8.04 (Worked for a while)"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by smashwolf on 2008-09-17
I was running 8.04 on my lenovo ThinkPad T61 flawlessly for several months, and several OS updates., and wireless "Just worked" 

Then I ran an update a couple weeks ago, and now the wireless device does not show up in the GUI.  I checked, and I can see the hardware is present.  I just cannot see it in iwconfig.  

I usually use this machine docked, and don;t even think of wireless till I need it.  unfortunately, I did not realize my wireless was dead until I was in an airport and tried to use it.

Below is a listing of what I see in lspci, dmesg, etc.  Can someone tell me what went wrong, and how I might correct this?  I tried booting older versions of the kernel, and that did not help ether.  I'm hoping it's something simple.

Please look at this below and let me know if there is a quick fix.

-------

root@lappywolf:/dev# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:16:b1:f4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=10.33.27.19 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
root@lappywolf:/dev# 

lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

dmesg lines pertainign to radio:
[   39.849294] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   39.849297] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   39.849482] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   39.982464] iwl4965: Radio disabled by HW RF Kill switch


And lastly, lsmod:
root@lappywolf:/dev# lsmod
Module                  Size  Used by
ipv6                  267780  12 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
nfsd                  228848  13 
lockd                  67720  2 nfsd
nfs_acl                 4608  1 nfsd
auth_rpcgss            43424  1 nfsd
sunrpc                185500  9 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                6016  1 nfsd
uinput                 10240  1 
ppdev                  10372  0 
autofs4                23044  3 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
bay                     6912  0 
dock                   11280  1 bay
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  1 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
snd_hda_intel         344728  5 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
joydev                 13120  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
pcmcia                 40876  0 
iwl4965               105844  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
iwlwifi_mac80211      219108  1 iwl4965
nvidia               7825536  36 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
yenta_socket           27276  1 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               15112  1 iwlwifi_mac80211
psmouse                40336  0 
rsrc_nonstatic         13696  1 yenta_socket
i2c_core               24832  1 nvidia
video                  19856  0 
output                  4736  1 video
serio_raw               7940  0 
ac                      6916  0 
snd_timer              24836  3 snd_pcm,snd_seq
battery                14212  0 
thinkpad_acpi          51836  0 
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
wmi_acer                9644  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvram                   9992  2 thinkpad_acpi
intel_agp              25492  0 
snd                    56996  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
agpgart                34760  2 nvidia,intel_agp
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  9 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
pcspkr                  4224  0 
ext3                  136712  5 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  7 
ata_piix               19588  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_generic             8324  0 
ahci                   28420  6 
pata_acpi               8320  0 
libata                159344  4 ata_piix,ata_generic,ahci,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
e1000                 126016  0 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
root@lappywolf:/dev#

---

### Post by pytheas22 on 2008-09-17
> dmesg lines pertainign to radio:
[ 39.849294] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[ 39.849297] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[ 39.849482] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[ 39.982464] iwl4965: **Radio disabled by HW RF Kill switch**

That's the problem (and thanks for providing so much useful information in your first post!).  The card won't work till the radio is enabled.  If there's a button on your computer or a key combination (e.g. function+F2) that you have to press to turn the wireless on, try toggling it, then waiting a few seconds to see if you can see networks by typing:
```

sudo iwlist scan
```

It's also possible that this is a bug with the driver, so if you really can't get the radio to turn on, we can look at other things.  In that case, please post the output of:
```

modinfo iwl4965
```

so we know which version of the driver you're using.

---

### Post by smashwolf on 2008-09-17
I did not find any button on the keyboard.  However that does not mean lenovo doesn;t have something in a hidden key combo, or a BIOS setting, so I will look for opetions to enable/disable the radio.

In the mean time:

root@lappywolf:/dev# modinfo iwl4965
filename:       /lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.0
description:    Intel(R) Wireless WiFi Link 4965AGN driver for Linux
srcversion:     BFF70BD669F5E9D76F2C9C1
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlwifi_mac80211
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
root@lappywolf:/dev#

---

### Post by smashwolf on 2008-09-18
[QUOTE=pytheas22;5808915]That's the problem (and thanks for providing so much useful information in your first post!).  The card won't work till the radio is enabled.  If there's a button on your computer or a key combination (e.g. function+F2) that you have to press to turn the wireless on, try toggling it, then waiting a few seconds to see if you can see networks by typing:
[CODE]

Ther eis a key combo (FN+F5) that toggles bluetooth and WiFi, or none, and I thought it was that, but I was wrong.  There  is a separate "wireless kill switch" on the edge of the laptop that is not labeled well.  I had to boot into Windows to see if Wireless worked there, and the software in Windows brought up an actual animated graphic showing the switch, and what it looked like, and then I was able to find it.  

It's all good now.

---

### Post by poorbadger on 2008-11-21
Thank goodness for the archives!

I've been battling the same problem for the past 24 hrs. Everything was telling me I had a WiFi card, drivers were loaded, it just wasn't enabled.

Here's [an image]("http://www.notebookreview.com/assets/18346.jpg") showing the switch on the left side of the front edge of the machine for future reference.

Up and running again and it feels good :)

> **smashwolf said:**
> 
There is a key combo (FN+F5) that toggles bluetooth and WiFi, or none, and I thought it was that, but I was wrong.  There  is a separate "wireless kill switch" on the edge of the laptop that is not labeled well.  I had to boot into Windows to see if Wireless worked there, and the software in Windows brought up an actual animated graphic showing the switch, and what it looked like, and then I was able to find it.  

It's all good now.

---

