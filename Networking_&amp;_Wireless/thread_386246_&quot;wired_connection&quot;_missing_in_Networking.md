---
title: "&quot;wired connection&quot; missing in Networking Admin Screen"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by jensporup on 2007-03-16
I have a brand new completely vanilla install of Ubuntu Dapper. I have connected the box through an ethernet cable to the switch/router/thingamabob/whatever that connects the house to the internet (whatever it is, it has four ports.)

This is a dual boot machine. The internet connection worked out of the box in Windows, no password needed, no configuration asked for.

The connection does not work in Ubuntu. Worse, I found this help page:

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

which looks as though I ought to be seeing a "Wired Connection" option in the Networking Screen. It isn't there. Instead I see a Wireless Connection option (which won't work because it's a Belkin card and I can't get ndiswrapper to play nice, but that's another story.)

ifconfig lists only the loopback interface. I'm guessing the wireless is eth0, but ifup eth1 just gives me a bunch of error messages.

How do I get my internet connection working?

Thanks,
me

---

### Post by Floppyjoe on 2007-03-16
Your problem looks like one that will be very difficult to solve. Can you post your /etc/network/interfaces file by going to the terminal and entering the following:
```
sudo gedit /etc/network/interfaces
```
copy and paste the text of that file into your post. Also enter the following:
```
sudo lshw
```
and post the part that has a prefix of the following:
>  *-network

This may enable someone to figure out what is wrong.

---

### Post by jensporup on 2007-03-16
OK, /etc/network/interfaces says:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhc

```

the relevant output of lshw is:

```

 *-network DISABLED
             description: Wireless interface
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: a
             bus info: pci@01:0a.0
             logical name: eth0
             version: 02
             serial: 00:11:50:9c:f6:6e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26 -386 link=no multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:dfffc000-dfffdfff irq:50

```

oh crap. does this mean that annoying belkin wireless card is also my ethernet controller???

---

### Post by Floppyjoe on 2007-03-16
> **jensporup said:**
> OK, /etc/network/interfaces says:

the relevant output of lshw is:

```

 *-network DISABLED
             description: Wireless interface
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: a
             bus info: pci@01:0a.0
             logical name: eth0
             version: 02
             serial: 00:11:50:9c:f6:6e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26 -386 link=no multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:dfffc000-dfffdfff irq:50

```

Looks like your wireless card listed here has a broadcom 4318 chipset. I have a link in my signature that shows how to get one of them working. Of course that probably won't help you if you don't have a wireless access point. It doesn't look like Ubuntu recognizes your wired ethernet card.

---

### Post by jensporup on 2007-03-16
Well I gots good news and bad news.

The good news is that your ndiswrapper how-to (the best I've come across) means I finally have the wireless card working under Ubuntu.

The bad news is that I still don't have wired access, nor does "Wired Connection" appear in the list of interfaces.

Can you refer me to a source of information to help get the ethernet card working?

---

### Post by Floppyjoe on 2007-03-16
> **jensporup said:**
> Well I gots good news and bad news.

The good news is that your ndiswrapper how-to (the best I've come across) means I finally have the wireless card working under Ubuntu.

The bad news is that I still don't have wired access, nor does "Wired Connection" appear in the list of interfaces.

Can you refer me to a source of information to help get the ethernet card working?
Unfortunately I am not very knowledgeable about this type of problem. I can't find anything that will probably help you very much with the wired connection problem. I did find this link:
[https://wiki.ubuntu.com/CommonProblemsNetwork?](https://wiki.ubuntu.com/CommonProblemsNetwork?)

maybe someone more knowlegeable will read this thread and be able to point you in the right direction.

---

### Post by dbott67 on 2007-03-17
Can you post the output of the following commands:
```
dbott@thedrake:~$ **sudo lspci**
Password:
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
0000:02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
[COLOR=Red]0000:02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)[/COLOR]
0000:02:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:0d.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:0d.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)

```and lsmod:

```
dbott@thedrake:~$ lsmod
Module                  Size  Used by
smbfs                  66552  3
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
fglrx                 388908  8
speedstep_lib           4484  0
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
vfat                   13440  0
fat                    53020  1 vfat
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
lp                     11844  0
tsdev                   8000  0
rtc                    13492  0
usbhid                 39904  0
floppy                 62148  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
[COLOR=Red]8139too                26880  0[/COLOR]
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
[COLOR=Red]mii                     5888  1 8139too[/COLOR]
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_intel8x0           33692  1
snd_emu10k1           117284  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         93216  2 snd_intel8x0,snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
psmouse                36100  0
snd_pcm_oss            53664  0
serio_raw               7300  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
emu10k1_gp              3840  0
gameport               15496  2 emu10k1_gp
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
snd                    55268  18 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_intel8x0,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
snd_page_alloc         10632  3 snd_intel8x0,snd_emu10k1,snd_pcm
soundcore              10208  1 snd
intel_agp              22940  1
agpgart                34888  2 fglrx,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  1
ext3                  135944  2
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
ohci_hcd               21892  0
usbcore               130820  5 usbhid,ehci_hcd,uhci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
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

```The parts in red are specific to my computer; your mileage will most likely vary, but we'll be able to determine what the card & module should be.

Another help might be if you can boot into windows and check the device manager for the make & model of the wired NIC and post it here.

Thanks,
Dave

---

