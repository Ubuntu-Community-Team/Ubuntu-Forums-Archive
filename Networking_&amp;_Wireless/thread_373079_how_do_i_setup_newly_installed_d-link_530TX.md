---
title: "how do i setup newly installed d-link 530TX?"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by jonqrandom on 2007-02-28
in order to get this box sharing the internet, i've installed a d-link 530TX network card alongside the realtek already in it.  ubuntu didn't notice the new addition, so i tried searching the forum, i've added the via-rhine module to /etc/modules, i've addded eth1 to /etc/network/interfaces (but don't know the file so have probably gone wrong), and nothing has changed, other than the device manager can see the network card now.  woo :/

anyways, here's a bunch of output ;)  please help, i'm in deep caca if i can't get internet sharing going :(

lspci says:
```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
            ######## this is the d-link 530TX ^^^^^ ########
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 01)
```

lsmod says:
```
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
nfsd                  194176  9
exportfs                5376  1 nfsd
lockd                  55848  2 nfsd
sunrpc                125124  12 nfsd,lockd
ipt_limit               2432  8
iptable_mangle          2816  0
ipt_LOG                 6400  8
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  1
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  6
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
apm                    19308  1
ipv6                  217408  10
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_cs46xx             78664  1
gameport               14472  2 snd_cs46xx
snd_rawmidi            22816  1 snd_cs46xx
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_cs46xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_cs46xx,snd_pcm
i2c_piix4               8336  0
i2c_core               19728  1 i2c_piix4
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
processor              23100  0
via_rhine              20356  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  3 via_rhine,8139too,8139cp
uhci_hcd               28048  0
usbcore               104316  2 uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  660
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

ifconfig says nothing about eth1.  humbug!


my /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
piix
ide-core
ide-cd
ide-disk
ide-generic
via_rhine

```

my /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        network 192.168.0.0
        broadcast 192.168.0.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 194.168.4.100 194.168.8.100

iface eth1 inet dhcp
        network 192.168.0.0
        broadcast 192.168.0.255
        # dns-* options are implemented by the resolvconf package, if installed

auto eth0
auto eth1

```



any more info you need, please ask :)

---

