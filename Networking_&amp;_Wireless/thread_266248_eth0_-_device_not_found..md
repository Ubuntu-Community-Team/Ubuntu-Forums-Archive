---
title: "eth0 - device not found."
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-09-27
i can't seem to get my pcmcia wired ethernet adapter to get recognized in ubuntu.  i know i could get it to work if i had gui access to network manager because that's how everyone else can make it work.  but i'm restricted to cli only (it's a really old computer, what can i say?).

my ethernet (network everywhere np100 pcmcia card) adapter works in ubuntu by blacklisting pcnet_cs, which i have done.

my card is attached to eth0 by the kernel:
```
[17179702.056000] pcmcia: registering new device pcmcia0.0
[17179703.112000] eth0: Asix AX88190: io 0x300, irq 3, hw_addr 00:00:00:00:00:00
```
pcmcia recognizes the card:
```
$cardctl ident
Socket 0:
  product info: "Network Everywhere", "Fast Ethernet 10/100 PC Card", "3.0", "AX88190"
  manfid: 0x0149, 0xc1ab
  function: 6 (network)
```
i've edited my interfaces to include eth0:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet dhcp
        wireless-mode managed
        wireless-essid myessid

auto eth0
iface eth0 inet dhcp
```
i know for a fact that the correct module is loaded for my card:
```
$ lsmod | grep pcmcia
pcmcia                 40508  1 axnet_cs
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
```
axnet drives this card on other boxes just fine.

but when i try to activate the card by restarting network or with ifup, i get the following:
```
$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
```

previously (breezy) i would have corrected this by adding "eth0=eth0" in /etc/network/run/ifstate, but ifstate does not appear in the dapper release.

what does the network configuration gui do that i can't via command line?

this card does work in other computers, and it does work with the above configuration on my other machines.  also, it has worked under breezy on this same computer.

it's something i've overlooked, or something simple i'm missing ... anyone have any ideas?

---

### Post by dmizer on 2006-09-28
gotta do a little bump here.  still haven't solved this one.

---

### Post by dannyboy79 on 2006-09-29
if it's a really old comp, why don't you try a really lightweight window manager. I am running xubuntu dapper drake on my Pentium MMX 266 mhz with 128 mb ram. you would do, sudo aptitude install xubuntu-desktop I think? also i have read that icewm is small also. my pcmcia card is ath0 not eth0 but  I did notice that your dmesg log or is that your dmesg log. if not, what does dmesg say?

---

### Post by dmizer on 2006-10-01
> **dannyboy79 said:**
> if it's a really old comp, why don't you try a really lightweight window manager. I am running xubuntu dapper drake on my Pentium MMX 266 mhz with 128 mb ram. you would do, sudo aptitude install xubuntu-desktop I think? also i have read that icewm is small also. my pcmcia card is ath0 not eth0 but  I did notice that your dmesg log or is that your dmesg log. if not, what does dmesg say?
thanks for the reply.

xubuntu would be way too heavy for this low ram pre-pentium computer.  i have icewm on one of my other pc's.  i could use it, but it doesn't have a network manager client either, so i'd be stuck with the same problem anyway.

besides, since this computer is just going to be a tnc for a ham station, a window manager would be something of a waste.

also, as i indicated in my first post, my pcmcia wired network adapter is without doubt eth0.

---

### Post by dmizer on 2006-10-14
a full ps aux and lsmod follows:
```
$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   1568   532 ?        S    20:08   0:02 init [2]      
root         2  0.0  0.0      0     0 ?        SN   20:08   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    20:08   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   20:08   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   20:08   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   20:08   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   20:08   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   20:08   0:00 [kacpid]
root       125  0.0  0.0      0     0 ?        S    20:08   0:00 [pdflush]
root       126  0.0  0.0      0     0 ?        S    20:08   0:00 [pdflush]
root       128  0.0  0.0      0     0 ?        S<   20:08   0:00 [aio/0]
root       127  0.0  0.0      0     0 ?        S    20:08   0:00 [kswapd0]
root       715  0.0  0.0      0     0 ?        S<   20:08   0:00 [kseriod]
root      1696  0.0  0.0      0     0 ?        S<   20:08   0:00 [kacpid-work-0]
root      1697  0.0  0.0      0     0 ?        S<   20:08   0:00 [kacpid-work-1]
root      1698  0.0  0.0      0     0 ?        S<   20:08   0:00 [kacpid-work-2]
root      1779  0.0  0.0      0     0 ?        S<   20:08   0:00 [khubd]
root      1851  0.0  0.0      0     0 ?        S    20:08   0:00 [kjournald]
root      2096  0.0  0.2   2108   524 ?        S<s  20:08   0:00 /sbin/udevd --d
root      2847  0.0  0.0      0     0 ?        S    20:08   0:00 [shpchpd_event]
root      2874  0.0  0.0      0     0 ?        S    20:08   0:00 [pccardd]
root      2876  0.0  0.0      0     0 ?        S    20:08   0:00 [pccardd]
root      2887  0.0  0.0      0     0 ?        S<   20:08   0:00 [kgameportd]
root      3829  0.0  0.0      0     0 ?        SN   20:09   0:00 [ktoshkeyd]
root      3844  0.0  0.6   2548  1596 ?        Ss   20:09   0:00 /usr/sbin/acpid
syslog    3932  0.0  0.2   1764   656 ?        Ss   20:09   0:00 /sbin/syslogd -
root      3955  0.0  0.1   1676   492 ?        Ss   20:09   0:00 /bin/dd bs 1 if
klog      3957  0.0  0.5   2400  1324 ?        Ss   20:09   0:00 /sbin/klogd -P
hplip     3983  0.0  0.3  12872   920 ?        Ssl  20:09   0:00 /usr/sbin/hpiod
hplip     3986  0.0  1.8   9412  4668 ?        S    20:09   0:00 python /usr/sbi
cupsys    4030  0.0  0.6   4192  1668 ?        Ss   20:09   0:00 /usr/sbin/cupsd
104       4059  0.0  0.3   2192   792 ?        Ss   20:09   0:00 /usr/bin/dbus-d
110       4072  0.0  2.0   6724  5308 ?        Ss   20:09   0:01 /usr/sbin/hald
root      4073  0.0  0.3   2720   976 ?        S    20:09   0:00 hald-runner
110       4078  0.0  0.3   2004   860 ?        S    20:09   0:00 /usr/lib/hal/ha
110       4128  0.0  0.3   2000   788 ?        S    20:09   0:00 /usr/lib/hal/ha
110       4139  0.0  0.3   2008   816 ?        S    20:09   0:01 /usr/lib/hal/ha
110       4140  0.0  0.3   2008   816 ?        S    20:09   0:00 /usr/lib/hal/ha
root      4149  0.0  0.1   2200   408 ?        Ss   20:09   0:00 /usr/sbin/fnfxd
root      4179  0.0  0.5   2636  1312 ?        S    20:09   0:00 /bin/sh /usr/bi
mysql     4243  0.0  6.6 126428 17076 ?        Sl   20:09   0:00 /usr/sbin/mysql
root      4244  0.0  0.1   1552   504 ?        S    20:09   0:00 logger -p daemo
root      4385  0.0  0.1   1628   300 ?        Ss   20:09   0:00 /sbin/mdadm -F
daemon    4411  0.0  0.1   1800   396 ?        Ss   20:09   0:00 /usr/sbin/atd
root      4421  0.0  0.3   2116   832 ?        Ss   20:09   0:00 /usr/sbin/cron
root      4457  0.0  2.3  19868  6056 ?        Ss   20:09   0:00 /usr/sbin/apach
www-data  4505  0.0  1.3  19868  3368 ?        S    20:09   0:00 /usr/sbin/apach
www-data  4506  0.0  1.3  19868  3368 ?        S    20:09   0:00 /usr/sbin/apach
www-data  4507  0.0  1.3  19868  3368 ?        S    20:09   0:00 /usr/sbin/apach
www-data  4508  0.0  1.3  19868  3368 ?        S    20:09   0:00 /usr/sbin/apach
www-data  4509  0.0  1.3  19868  3368 ?        S    20:09   0:00 /usr/sbin/apach
root      4513  0.0  0.3   5268   864 ?        S    20:09   0:00 /usr/bin/wdm
root      4514  0.0  0.3   5268   912 ?        S    20:09   0:00 /usr/bin/wdm
root      4533  0.0  0.1   1564   496 tty1     Ss+  20:09   0:00 /sbin/getty 384
root      4536  0.0  0.1   1564   496 tty2     Ss+  20:09   0:00 /sbin/getty 384
root      4537  0.0  0.1   1560   492 tty3     Ss+  20:09   0:00 /sbin/getty 384
root      4538  0.0  0.1   1564   496 tty4     Ss+  20:09   0:00 /sbin/getty 384
root      4539  0.0  0.1   1564   492 tty5     Ss+  20:09   0:00 /sbin/getty 384
root      4540  0.0  0.1   1564   496 tty6     Ss+  20:09   0:00 /sbin/getty 384
root      4549  0.0  3.8  16428  9864 tty7     Ss+  20:09   0:02 /usr/bin/X11/X
root      4552  0.0  0.5   5900  1500 ?        S    20:09   0:00 -:0         
dmizer    4595  0.0  0.4   4748  1044 ?        S    20:09   0:00 x-session-manag
dmizer    4630  0.0  0.2   4332   684 ?        Ss   20:09   0:00 /usr/bin/ssh-ag
dmizer    4633  0.0  0.2   2712   640 ?        S    20:09   0:00 /usr/bin/dbus-l
dmizer    4635  0.0  0.1   2076   424 ?        Ss   20:09   0:00 dbus-daemon --f
dmizer    4636  0.0  0.6   4804  1560 ?        SNs  20:09   0:00 icewmbg
dmizer    4637  0.0  1.4   7924  3824 ?        Ss   20:09   0:00 icewm
dmizer    4638  0.0  0.7   6136  1868 ?        Ss   20:09   0:00 icewmtray
dmizer    4642  0.0  0.6   9712  1700 ?        Ss   20:09   0:00 /usr/lib/scim-1
dmizer    4644  0.0  2.9  14552  7556 ?        S    20:09   0:01 rox --pinboard=
dmizer    4647  0.0  0.3   4928  1004 ?        Ss   20:09   0:00 /usr/lib/scim-1
dmizer    4648  0.0  1.6  21896  4280 ?        Ssl  20:09   0:00 /usr/lib/scim-1
dmizer    4650  0.0  0.6   6628  1788 ?        Ss   20:09   0:00 /usr/lib/scim-1
dmizer    4651  0.0  1.1   9036  3012 ?        Ss   20:09   0:00 xterm -class UX
dmizer    4663  0.0  1.2   5576  3240 pts/0    Ss   20:09   0:00 bash
dmizer    4890  0.0  0.3   2392  1008 pts/0    R+   23:45   0:00 ps aux

```
```
$ lsmod
Module                  Size  Used by
acx                   101132  0 
axnet_cs               19460  1 
savage                 35584  1 
drm                    73236  2 savage
ipv6                  265728  13 
ppdev                   9220  0 
speedstep_lib           4484  0 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
video                  16260  0 
toshiba_acpi           10940  0 
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
af_packet              22920  2 
dm_mod                 58936  1 
md_mod                 72532  0 
fuse                   38412  0 
lp                     11844  0 
tsdev                   8000  0 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0 
pcmcia                 40508  1 axnet_cs
i2c_piix4               9104  0 
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
rtc                    13492  0 
psmouse                36100  0 
pcspkr                  2180  0 
snd_ymfpci             61248  0 
serio_raw               7300  0 
gameport               15496  1 snd_ymfpci
snd_ac97_codec         93216  1 snd_ymfpci
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10624  1 snd_ymfpci
snd_timer              25220  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd_page_alloc         10632  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         7808  1 snd_ymfpci
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd                    55268  11 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer
_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_se
q_device
soundcore              10208  1 snd
donauboe               17152  0 
yenta_socket           28428  5 
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              22940  1 
agpgart                34888  2 drm,intel_agp
irda                  187068  1 donauboe
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
crc_ccitt               2304  2 donauboe,irda
evdev                   9856  1 
ext3                  135816  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
uhci_hcd               33808  0 
usbcore               130820  3 acx,uhci_hcd
ide_cd                 33028  0 
cdrom                  38560  1 ide_cd
ide_disk               17664  3 
piix                   11012  1 
generic                 5124  0 
thermal                13576  0 
processor              23360  1 thermal
fan                     4868  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  71 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
```

---

### Post by dmizer on 2006-11-06
would you believe ... i finally solved this one.

just added an entry in interfaces for eth1, and off she went.  it still shows up everywhere as eth0, but as long as i'm online, i'm happy so ... i guess that's that.  really have no idea why it would be that it would show up everywhere as eth0, but work as eth1 though.

---

### Post by dmizer on 2007-08-06
okay ... this has become a huge problem.

the adapter seems to wander on reboots frequently.  one time it will be eth1, another it will be eth0 or eth2 or even eth3.

for a computer with a single network adapter, this was no problem.  i just made several entries in /etc/network/interfaces and all was well.

but now i'd like to use this machine as a server for a subnet sandbox for hosting diskless clients.  with the wandering network adapter, it's impossible for me to have a working configuration from one boot to the next.

any ideas on how i can make that network adapter stay put?

---

