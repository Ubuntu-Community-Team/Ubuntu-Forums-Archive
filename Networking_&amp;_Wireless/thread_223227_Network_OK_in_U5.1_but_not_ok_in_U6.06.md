---
title: "Network OK in U5.1 but not ok in U6.06"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by ltolledo on 2006-07-26
Greetings and Salutations!

I need help in connecting to the network using U6.06LTS. I cannot ping  the server thus cant connect to the internet and other PCs. However re-installing to U5.1, I am able to connect to the network and  connect to the internet (am using U5.1 now).

The hardware used for both installations are exactly the same, so why is it that with U5.1 I can connect ant not with U6.06?

My network card spec: Davicom DM9102 AF
(21x4x DEC-Tulip compatible 10/100 Ethernet)

Other harware specs:
Processor : Intel Pentium III 500
MB  : i440BX series MB
RAM : 384MB SDRAM
HDD : SG 10GB 5400RPM
VGA : 86c368 (Trio 3D/2X)

Hope you guys can help me out so I can upgrade all my U5.1 to U6.06.


Live long and prosper!

---

### Post by rattlerviper on 2006-07-26
Hang in there, somone will come by soon who know the answer.  Are you trying to upgrade or a fresh install?

---

### Post by ltolledo on 2006-07-26
Fresh intall, they say fresh is best.

---

### Post by philippe_carlo on 2006-07-26
Need more info:
 - What module do you need?
 - do you use dhcp or static ip?

What does this give you:
```

sudo lsmod
sudo ifconfig
sudo cat /etc/network/interfaces

```

---

### Post by ltolledo on 2006-07-26
Ok, I switched to U6.06 to get the info requested, and went back to U5.1 to post this reply:

results of lsmod:

Module                  Size  Used by
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
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
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
af_packet              22920  0
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
snd_ymfpci             60864  1
gameport               15496  1 snd_ymfpci
snd_ac97_codec         92704  1 snd_ymfpci
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10624  1 snd_ymfpci
snd_timer              25220  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd_page_alloc         10632  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         7808  1 snd_ymfpci
tsdev                   8000  0
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
floppy                 62148  0
snd                    55268  13 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
psmouse                36228  0
soundcore              10208  1 snd
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
serio_raw               7300  0
pcspkr                  2180  0
i2c_piix4               9104  0
dmfe                   21532  0
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
intel_agp              22940  1
agpgart                34888  1 intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
tulip                  51872  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               129668  2 uhci_hcd
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
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

result of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:08:A1:8B:8E:7E
          inet addr:192.168.100.168  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe8b:8e7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21159 (20.6 KiB)  TX bytes:2484 (2.4 KiB)
          Interrupt:11 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1780 (1.7 KiB)  TX bytes:1780 (1.7 KiB)

result of cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.100.168
netmask 255.255.255.0
gateway 192.168.100.254

auto eth1
iface eth1 inet static
address 192.168.100.169
netmask 255.255.255.0
gateway 192.168.100.254

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

