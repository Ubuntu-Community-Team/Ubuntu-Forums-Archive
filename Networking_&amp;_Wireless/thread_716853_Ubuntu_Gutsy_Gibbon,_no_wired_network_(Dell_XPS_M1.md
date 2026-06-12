---
title: "Ubuntu Gutsy Gibbon, no wired network (Dell XPS M1530)"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by Max Kolombia on 2008-03-06
Hello all. I am running Gutsy (first time ubuntu user) on a Dell XPS M1530 machine. 

Unfortunately I cannot establish any *wired* network connection. Wireless doesn't work either, but I am letting this aside for the moment. 

My ethernet card seems to be configured fine, however, I cannot have any access to the network (I cannot even ping any IP). The LED light at the cable connection is not flashing (no activity transmiting or receiving) only the light which shines when the cable is connected (When the network cable is connected dmesg | grep eth gives "sky2 eth0: Link is up at 10 Mbps, half duplex, flow control none", while when it is removed it says "sky2 eth0: Link is down."). I am "using" a university network with a static IP (no DHCP). 

Here is some basic information that may be useful to you:

>ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:15:C5:86:37:80  
          inet addr:195.134.93.33  Bcast:195.134.93.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1938 (1.8 KB)  TX bytes:1938 (1.8 KB)

```


>iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```


>lshw -C network  
```
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:15:c5:86:37:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=195.XXX.XX.XX latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
```

>/etc/hosts

```
127.0.0.1 localhost mylaptop
127.0.1.1 mylaptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

>lscpi
```
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

>/etc/network/interfaces

```

auto lo
iface lo inet loopback

iface eth0 inet static
address 195.XXX.XXX.XX
netmask 255.255.255.0
gateway 195.XXX.XX.X

```

I don't display my ip, etc. but all parameters are correct. I checked /etc/resolv.conf but it displays the correct nameserver so there is no problem there. All parameters of the connection seem well set. I have also tried blacklisting or setting off ipv6 with no effect. Others claimed that booting with the noapic option solved similar problems but it didn't work out with me.

Could it be a BIOS problem (my laptop came with A06)? Any missing modules? 

>lsmod
```
Module                  Size  Used by
usbhid                 29536  0 
hid                    28928  1 usbhid
hci_usb                18332  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  7 hci_usb,rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
button                  8976  0 
container               5504  0 
video                  18060  0 
ac                      6148  0 
sbs                    19592  0 
battery                11012  0 
dock                   10656  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
uvcvideo               48644  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
sr_mod                 17828  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cdrom                  37536  1 sr_mod
compat_ioctl32          2304  1 uvcvideo
snd_timer              24324  2 snd_pcm,snd_seq
sdhci                  18828  0 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               26112  0 
mmc_core               28420  1 sdhci
psmouse                39952  0 
sky2                   46852  0 
serio_raw               8068  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
intel_agp              25620  0 
agpgart                35016  1 intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  6 
ata_piix               17540  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ahci                   23300  5 
ata_generic             8452  0 
libata                125168  3 ata_piix,ahci,ata_generic
scsi_mod              147084  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  6 usbhid,hci_usb,uvcvideo,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

Perhaps a firewall issue? (i do not see any options to configure firewall). Is there any known issue with Marvell's ethernet controller or sky2 driver?

I have spent many hours looking into this problem without any luck so I am now pretty much desperate for any help or suggestions from you.

Thanks

---

### Post by dca on 2008-03-06
Do you dual-boot w/ WinXP by any chance?

---

### Post by Max Kolombia on 2008-03-06
Yeah I forgot to mention, but not with XP. I have Vista installed on another partition.

edit: I have read a suggestion about enabling the Wake-on-Lan option in XP but there is no such option in Vista...

---

### Post by dca on 2008-03-06
Don't know if this is relative:
 
[http://suseforums.net/index.php?showtopic=18920](http://suseforums.net/index.php?showtopic=18920)
[http://www.mepislovers.org/forums/showthread.php?t=14227](http://www.mepislovers.org/forums/showthread.php?t=14227)
[http://www.mepis.org/node/13549](http://www.mepis.org/node/13549)
..different distro but Marvell chipset
  
 
First one says using 'acpi=off' solved his issue.
Second one says using 'update-pciids' command as root at CLI or installing sk2 driver(s) worked.
Third one suggests just using ndiswrapper for network cards (wireless & wired).
 
...I iwsh I was more help but the only time I've seen this happen wasn't w/ Marvell ethernet card, it was with another one and it was caused from some kind of power-save on shutdown setting in WinXP for the ethernet card(s)...

---

### Post by Max Kolombia on 2008-03-06
> **dca said:**
> Don't know if this is relative:
 
[http://suseforums.net/index.php?showtopic=18920](http://suseforums.net/index.php?showtopic=18920)
[http://www.mepislovers.org/forums/showthread.php?t=14227](http://www.mepislovers.org/forums/showthread.php?t=14227)
[http://www.mepis.org/node/13549](http://www.mepis.org/node/13549)
..different distro but Marvell chipset
  
 
First one says using 'acpi=off' solved his issue.
Second one says using 'update-pciids' command as root at CLI or installing sk2 driver(s) worked.
Third one suggests just using ndiswrapper for network cards (wireless & wired).
 
...I iwsh I was more help but the only time I've seen this happen wasn't w/ Marvell ethernet card, it was with another one and it was caused from some kind of power-save on shutdown setting in WinXP for the ethernet card(s)...

Thanks for the reply. Well, my ethernet is fully recognized so updating pciids does not seem very useful. It is also very strange to me why an "acpi=off" option would do any difference... It seems that my wireless is now working ok (i played with so many things but i think moving to iwl3945 from ipw3945 did the trick for me). Perhaps there is something wrong with the sky2 driver for my device so I will try to switch to the Syskonnect driver and see if it helps. Meanwhile if anyone has the same problem (should be common for some dell users) please post your experience.

---

### Post by Max Kolombia on 2008-03-07
UPDATE:

So it turned out that using the sk98lin driver solved the problem. I assume that sky2 version used is very buggy or does not like my ethernet... 

For anyone who might have the same problem, I downloaded the drivers that I found in Marvell's site:
[http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36](http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36)

---

### Post by vidueirof on 2008-03-28
I have the same problem. Can you guide me to the solution please. I've download the path/driver. I have ubuntu 7.10 and a dell inspiron 1525 with the marvell yucon net card.
thanks

---

### Post by Max Kolombia on 2008-03-28
> **vidueirof said:**
> I have the same problem. Can you guide me to the solution please. I've download the path/driver. I have ubuntu 7.10 and a dell inspiron 1525 with the marvell yucon net card.
thanks

Hi. Untar the file you downloaded and you go through the detailed README file. They provide a script which installs the driver in an almost straightforward way which guides you through the process. Let me know if you have any specific problem. I remember that first I had to change the shell type (i modified the first line of install.sh) and get the kernel source in /usr/src/linux (ubuntu uses a different path by default but you can simply create a symbolic link). 

Good luck.
M

---

### Post by vidueirof on 2008-03-28
Thanks I worked out! I've just modify the .sh an make de link to headers
Thanks!

---

