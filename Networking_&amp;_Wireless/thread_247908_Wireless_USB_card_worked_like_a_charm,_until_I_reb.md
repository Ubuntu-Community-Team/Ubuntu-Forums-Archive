---
title: "Wireless USB card worked like a charm, until I rebooted..."
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by emilsall on 2006-08-31
Hi everybody, I'm new both on this forum and to linux, so I apologize for any dumb questions that might lay ahead!

I have a Dell TrueMobile 1180 wireless USB card, and this morning I got it to work with just a few easy commands, following this guide;
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

At first I had a problem, so I looked in /var/log/syslog and found this:
```
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file package_description.xml is ignored 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file PCANDIS3.VXD is ignored 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file PCANDIS4.SYS is ignored 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file PCANDIS5.SYS is ignored 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file PCARmDrv.exe is ignored 
...(many lines like these)...
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file PRISMIOC.dll is ignored 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file PRISMIOC.vxd is ignored 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(324): file PRISMR16.DLL is ignored 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(328): too many .sys files for driver netdelus 
Aug 31 09:48:41 holger loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver netdelus
```

I realized that I had to remove the unnecessary windows-files I had copied to /etc/ndiswrapper/netdelus and did so, leaving only the .inf and .sys. Then I ran:
```
sudo depmod -a
sudo modprobe ndiswrapper
```

Hallelujah! wlan0 popped up in System > Administration > Networking and I could configure the wireless connection and disable the wired connection and prepare myself to live happily ever after. I just wanted to make sure that the settings would stick even after a reboot. Of course, they did not.

Since then I've been running in circles trying to get back to where I was, aargh! I've even put all those windows files back just to be able to recreate the loadndisdriver messages in syslog, but nothing shows up at all when I run depmod and modprobe. What am I doin wrong? 

The driver and hardware is aknowledged by ndiswrapper:
```
emil@holger:~$ ndiswrapper -l
Installed ndis drivers:
netdelus                driver present, hardware present
```

But not by iwconfig:
```
emil@holger:~$ iwconfig
lo        no wireless extensions.
sit0      no wireless extensions.
eth0      no wireless extensions.
wlan0     no wireless extensions.
```

Any tips or hints are extremely appreciated! I feel like I'm forgetting something obvious, there must be a simple step to get wlan0 to show up in iwconfig and Networking again!? Please save me!

---

### Post by spd106 on 2006-08-31
You don't say whether you ran **ndiswrapper -m** which allows ndiswrapper to loaded on startup. Check the **/etc/modules** file, to be sure.

Do you see the ndiswrapper module loaded in **dmesg** or **lsmod**?

---

### Post by emilsall on 2006-08-31
Thank you very much for replying!

I did run ndiswrapper -m, and heres my /etc/modules:
```
emil@holger:~$ more /etc/modules
lp
mousedev
psmouse
ndiswrapper

```

No errors in dmesg
```
emil@holger:~$ dmesg | grep ndis
[   73.431229] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   73.517549] usbcore: registered new driver ndiswrapper

```

Here's all my modules, perhaps I should disable some of them? 
```
emil@holger:~$ lsmod
Module                  Size  Used by
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
apm                    22768  1
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
dm_mod                 63256  1
md_mod                 76052  0
ndiswrapper           189876  0
lp                     12356  0
rsrc_nonstatic         14624  0
pcmcia_core            45272  1 rsrc_nonstatic
af_packet              24520  2
snd_es1938             23844  0
gameport               16776  2 snd_es1938
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  2 snd_es1938,snd_pcm_oss
snd_page_alloc         11304  1 snd_pcm
snd_opl3_lib           11648  1 snd_es1938
snd_timer              26884  2 snd_pcm,snd_opl3_lib
snd_hwdep               9952  1 snd_opl3_lib
snd_mpu401_uart         8640  1 snd_es1938
snd_rawmidi            26848  1 snd_mpu401_uart
snd_seq_device          9228  2 snd_opl3_lib,snd_rawmidi
parport_pc             37988  1
parport                39400  2 lp,parport_pc
snd                    60004  10 snd_es1938,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10784  1 snd
tsdev                   8032  0
floppy                 64676  0
pcspkr                  2244  0
i2c_voodoo3             5156  0
i2c_algo_bit            9800  1 i2c_voodoo3
intel_agp              24700  1
agpgart                36784  1 intel_agp
psmouse                40004  0
serio_raw               7748  0
8139cp                 24032  0
8139too                29056  0
mii                     6176  2 8139cp,8139too
i2c_piix4               9168  0
i2c_core               22848  2 i2c_algo_bit,i2c_piix4
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
evdev                  10176  1
ipv6                  286976  36
ext3                  148104  1
jbd                    65876  1 ext3
ide_generic             1504  0
uhci_hcd               35408  0
usbcore               139076  3 ndiswrapper,uhci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  3
piix                   11652  1
generic                 5124  0
processor              26888  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  71
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

---

