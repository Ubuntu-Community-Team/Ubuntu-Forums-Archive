---
title: "RealTek Wireless Close, But No Cigar! Can't Connect to Router..."
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by skanxalot on 2007-10-08
I'm enjoying Feisty, but can't get my wlan0 to connect to my router.  I can see the router, and I see signal strength, but I cannot connect to get an IP.  I followed all the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), and I went through most of the troubleshooting at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide), but to no avail.  Could somebody please help me!?

---

### Post by Lambert on 2007-10-09
> **skanxalot said:**
> I'm enjoying Feisty, but can't get my wlan0 to connect to my router.  I can see the router, and I see signal strength, but I cannot connect to get an IP.  I followed all the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), and I went through most of the troubleshooting at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide), but to no avail.  Could somebody please help me!?

Open a terminal window and try this.

```

ifconfig

```

Anything but lo and wlan0 go ahead and take down. For example, if you see eth0 then run this command.

```

sudo ifdown eth0

```

After that run these commands

```

sudo ifdown wlan0

sudo ifup wlan0

```

Test to see if you have internet. If not then try this next command.

```

sudo dhclient wlan0

```

If this doesn't work, post out put of the following commands

```

sudo lshw -C network

dmesg | grep ndis

```

Also what kind of encryption are you using? To rule anything out, it's best to try and connect with encryption turned off first then troubleshoot from there. You can also try to set up a static ip and rule out dhcp problems.

---

### Post by skanxalot on 2007-10-09
> **Lambert said:**
> 

Test to see if you have internet. If not then try this next command.

```

sudo dhclient wlan0

```

If this doesn't work, post out put of the following commands

```

sudo lshw -C network

dmesg | grep ndis

```

Also what kind of encryption are you using? To rule anything out, it's best to try and connect with encryption turned off first then troubleshoot from there. You can also try to set up a static ip and rule out dhcp problems.

SUDO DHCLIENT RESULTS:
```

Listening on LPF/wlan0/00:c0:a8:f5:00:97
Sending on LPF/wlan0/00:c0:a8:f5:00:97
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No NDCPOFFERS received
No working leases in persistent database - sleeping

```

sudo lshw -C network Results:

```

*-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ec:0d:02
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d2000000-d2003fff ioport:2000-20ff irq:20
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:f5:99:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Realtek Semiconductor Corp.,07/ link=no multicast=yes wireless=IEEE 802.11g

```

dmesg | grep ndis Results:

```

[    25.600000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[    25.012000] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[   29.828000] usbcore: registered new interface driver ndiswrapper

```

Thanks so much for your response...I feel like this is close, and its frustrating that I can't get it the rest of the way.

---

### Post by Lambert on 2007-10-09
> **skanxalot said:**
> SUDO DHCLIENT RESULTS:
```

Listening on LPF/wlan0/00:c0:a8:f5:00:97
Sending on LPF/wlan0/00:c0:a8:f5:00:97
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No NDCPOFFERS received
No working leases in persistent database - sleeping

```

sudo lshw -C network Results:

```

*-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ec:0d:02
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d2000000-d2003fff ioport:2000-20ff irq:20
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:f5:99:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Realtek Semiconductor Corp.,07/ link=no multicast=yes wireless=IEEE 802.11g

```

dmesg | grep ndis Results:

```

[    25.600000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[    25.012000] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[   29.828000] usbcore: registered new interface driver ndiswrapper

```

Thanks so much for your response...I feel like this is close, and its frustrating that I can't get it the rest of the way.

After you run the sudo ifup wlan0, run iwconfig. Just want to see the second line where it says AP. It should say either not associated or have something like this xx:xx:xx:xx:xx

Also run lsmod and post output here.

Do you have encryption? If so which method are you using?

---

### Post by kevdog on 2007-10-09
Here try this:

[http://ubuntuforums.org/showthread.php?t=571194](http://ubuntuforums.org/showthread.php?t=571194)

---

### Post by skanxalot on 2007-10-09
Yes, it says "Not Associated"

Here is lsmod output:

```

Module                  Size  Used by
ndiswrapper           194608  0 
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
i915                   24448  2 
drm                    81044  3 i915
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
sbs                    15652  0 
ac                      6020  0 
asus_acpi              17308  0 
dock                   10268  0 
button                  8720  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
backlight               7040  1 asus_acpi
video                  16388  0 
battery                10756  0 
container               5248  0 
af_packet              23816  0 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
pcmcia                 39212  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
sky2                   43528  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
psmouse                38920  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              10240  0 
tifm_core               9856  1 tifm_7xx1
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              25116  1 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
agpgart                35400  3 drm,intel_agp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  3 
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
ata_piix               15492  0 
ata_generic             9092  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ahci                   22020  2 
libata                125720  3 ata_piix,ata_generic,ahci
scsi_mod              142348  5 sbp2,sd_mod,sg,sr_mod,libata
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 ndiswrapper,ehci_hcd,uhci_hcd
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

I think encryption is WEP.  I can't turn it off at the moment, but I'm fairly confident that's right. I know the access key, and can logon with other windows laptops successfully.

---

### Post by Lambert on 2007-10-09
It appears to be in your encryption. You can try this.

```

sudo iwconfig wlan0 essid ____ key restricted _____ mode managed

sudo dhclient wlan0

```it that doesn't work then 

```

sudo iwconfig wlan0 essid _____ key open _____ mode managed

sudo dhclient wlan0

```If you are using an ascii password you can enter the command like this.

```

sudo iwconfig wlan0 essid ____ key restricted s:____ mode managed

sudo dhclient wlan0

```I would also suggest looking at other graphical network tools like wicd.

And you didn't sound confident about it being wep. If the router uses wpa then there are more steps to entering information correctly so you can connect to the router. If you run:

sudo iwlist wlan0 scan

it might give you information on the encryption.

---

### Post by skanxalot on 2007-10-09
```

sudo iwconfig wlan0 essid ____ key restricted _____ mode managed

sudo dhclient wlan0

```

Result: No DHCPOFFERS received.

```

sudo iwconfig wlan0 essid _____ key open _____ mode managed

sudo dhclient wlan0

```

Result: No DHCPOFFERS received.

```

sudo iwconfig wlan0 essid ____ key restricted s:____ mode managed

sudo dhclient wlan0

```

Result: Invalid argument.  ??

> 
And you didn't sound confident about it being wep. If the router uses wpa then there are more steps to entering information correctly so you can connect to the router. If you run:

sudo iwlist wlan0 scan

it might give you information on the encryption.

It shows the network and says "Encryption key: on", but no details about the encryption.

---

### Post by skanxalot on 2007-10-09
OK, here are my router details:

Authentication: Open System
WEP: enabled
Encryption: 64bit
Key Type: HEX

---

### Post by skanxalot on 2007-10-11
I'm using Wicd, but I'm afraid there's still no IP address. Again, I can see all available wireless networks, but never connect.  What is left to try?  I received the linux drivers from a Realtek support email, but I don't know how to undo everything I've done so far and start over with the linux drivers instead of Win / NDISwrapper.

---

### Post by kevdog on 2007-10-11
Turn WEP off in the router and see if you can connect to an unencrypted network/

---

### Post by skanxalot on 2007-10-11
Yeah, I did that a while ago. No dice.

---

### Post by skanxalot on 2007-10-11
Working!  I built the linux drivers received from Realtek, and it's working now!  For anyone who needs them, I've uploaded the package I used. I followed the readme.txt instructions.  Here: [http://www.tysonkirksey.com/rtl8187B_linux_24](http://www.tysonkirksey.com/rtl8187B_linux_24)[1].6.1024.0822.2007.tar.gz

---

