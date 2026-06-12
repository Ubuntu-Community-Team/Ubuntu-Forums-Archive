---
title: "Another wireless issue"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by eagletistic on 2008-04-06
First off I see the numerous threads for wireless issues.  I have been trying for some time to get this to work.  I have failed with Ubuntu and now I am trying Kubuntu dapper.

I followed a particular how to on another site(I will post a link if allowed).  It looked simple to follow.  Basically downloaded windows driver for my wireless BCM43XX.  Extrated on a thumb drive and copied it to my home folder.  Using Adept went into manage rep. and made all dep and dep-src enabled and fetched the updates.

Used ndisgtk since I read it has ndiswrapper. Changed gksudo to kdesu in command on Windows Wireless Drivers.  Installed the windows driver.  It populated in Windows Wireless Drivers.  

Next is were I may haves screwed up.  I tried to blacklist the bcm43xx driver and added a blacklist bcm43xx  when i typed sudo kate /etc/modprobe.d/blacklist. The line is present but not sure if it does it's purpose?

When I go into Wireless Assistant it says that no wireless device found.

This is what I get when I type sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:07:03:96
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe07:396/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7851754 (7.4 MiB)  TX bytes:501880 (490.1 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I would think ndiswrapper is not working?

I believe I am savy on the computer but must admit this is something new to me.  To make atters worse I am post DOS so command lines are new to me.  I would love to get the wireless to work.  This is the only frustrating thing for me when it comes to Linux.  I heard my particular wireless card can be a hassel.

Any help would be great.

Thanks

---

### Post by spd106 on 2008-04-06
Blacklisting bcm43xx is a good step (if you don't want it automatically loaded), but you also need to ensure that ndiswrapper is being loaded instead. This is usually done by adding it to the /etc/modules file. So check that ndiswrapper is listed in there.

You can see which driver is being used by your network cards with this command
```
sudo lshw -class network
```

and you can see a list of all the driver modules already loaded with
```
lsmod
```

---

### Post by eagletistic on 2008-04-06
This is what I get under those commands
sudo lshw -class network

-network:0
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:07:03:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.49 duplex=full ip=192.168.1.4 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faff0000-faffffff irq:11
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:fafee000-fafeffff irq:11

lsmod

Module                  Size  Used by
radeon                116000  1
drm                    73236  2 radeon
rfcomm                 40216  0
l2cap                  26372  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ndiswrapper           177364  0
ipv6                  266112  6
dm_mod                 59192  1
af_packet              22920  2
md_mod                 72532  0
lp                     11844  0
pcmcia                 40508  0
joydev                 10048  0
tg3                   102788  0
yenta_socket           28428  4
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
tsdev                   8000  0
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
rtc                    13492  0
serio_raw               7300  0
psmouse                36100  0
pcspkr                  2180  0
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
sr_mod                 16932  0
sg                     37920  0
sd_mod                 19984  1
evdev                   9856  2
usb_storage            74304  1
scsi_mod              139496  4 sr_mod,sg,sd_mod,usb_storage
ext3                  135944  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  5 ndiswrapper,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

Looks like network1 is unclaimed?  I do not know what that means

Any help is appreciated

---

### Post by pseudo-random on 2008-04-06
Can you tell us more about your wireless network and also give the result of ```
iwconfig
```

---

### Post by spd106 on 2008-04-06
[QUOTE=eagletistic]Looks like network1 is unclaimed? I do not know what that means
[/QUOTE]

It means ndiswrapper hasn't picked it up.

Can you please post the output of these commands too:
```
ndiswrapper -v
```
```
ndiswrapper -l
```

---

### Post by tonyh703 on 2008-04-06
I am also having the same problem. I am able to connect if I use a physical wire, but it seems that my wireless card is not being seen. I am using the beta of Hardy, and apparently they left the device manager out of this one. Help option tells me go to  System-->Preferences-->Hardware Information. There is no Hardware info on mine. I also use the Broadcom wireless card, when I type in ndiswrapper - l i get the following....     bsmwl5 : driver installed   Device (14E4 : 4311) present ( alternate driver : bcm43xx)

---

### Post by eagletistic on 2008-04-06
Wireless uses WEP and is encrypted but haven' t got to that point yet.

iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ndiswrapper -v
utils version: 1.7
driver version:        1.8

Is this and older version?

ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

Looks like I have the right Windows driver.  Dell D600 bcm4309 True Mobile 1400

This may be a stupid question but the laptop has a funtion F2 button that will disable wireless in Windows.  There is no wifi light on a D600 so see if it is on or off.  Does this also affect Linux or is that a software feature in windows?  I have tried the funtion f2 to see if it turns on or off but I see no difference.

Am I right is assuming ndiswrapper wraps the windows driver so the driver works in linux?  It seems I am missing something with ndiswrapper.  At this point I am wondering if the card works. I would think it does with the info I see with ndiswrapper -l.  The laptop has been idle.  The connections are secure.  I'm about to put in a windows OS to see if it picks it up.  

Unless someone sees my mistake?

Hardwire ethernet is working.  I am using the laptop as we speak.

---

### Post by eagletistic on 2008-04-07
Bump

Does anyone have any other suggestions with the info I gave?

---

