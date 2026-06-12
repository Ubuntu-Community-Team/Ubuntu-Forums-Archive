---
title: "wlan0 configured but doesnt work! PLease HELP!!"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by hayim on 2006-07-30
HI!

Ive just spent the whole day fighting with the wireless. Im running Dapper, on an Acer laptop.

Upon install, Ubuntu recognised the Inprocomm IPN 2220 wireless card on board (centrino..), but had no drivers. I downloaded the driver, neti2220, ran the ndiswrapper GUI from System -> Admin. -> Windows wireless drivers (or something) and installed the .inf. OK.

THEN, network-admin (Sys>Admin>Networking) shows three interfaces. Loopback, eth0 and wlan0. Great. So i do activate, then configure, and nothing. Nothing happens. What is *supposed* to happen?

wireless settings: a WinXP machine acts as the gateway, using windows ICS. The thing has 192.168.0.1 IP and runs its own DHCP. 

Is the gnome network thing supposed to detect networks? it does nothing.

Finally, i went back to console. Iwconfig shows that wlan0 has wireless extensions, and the stats there look like its disconnected. The *only* command that actually changes anything is iwconfig mode <mode>. Nothing else seems to change when i check again with iwconfig (not ESSID, not channel, not key not nothing). When i do a iwlist wlan0 scan it gives 'no results', but there are like 4 networks in range of the computer.

DOES anyone have any idea whats going on? I can only think that the card isnt installed properly, that its not on or something. Network Manager shows it as wlan0, lets me activate and configure it etc, but nothing actually happens.

Hope someone out there reads all this, thanks so much, i dont wanna run back to XP.. again. (fell on the wireless obstacle last year on mandrake 10...)

Thanks!

---

### Post by Zaff on 2006-07-30
Hey I have the exact same problem with a belkin F5D7000. I installed the driver through ndiswrapper but it won't even turn itself on. If you get an answer tell about it please.

---

### Post by hayim on 2006-08-01
OK, here's the latest:

the card seems to bbe set up. It appears in the devices, it appears in the netword-admin app list, i can 'activate' and i can 'configure'.

When i do iwconfig the card shows up. When i load ndiswrapper and the check dmesg everything seems fine - the card has a mac address and a process thingie, and a config file..?

Only it DOESNT WORK.

network-manager-gnome doesnt see a wireless interface. iwlist wlan0 scan returns no results.

What could be going wrong? Could the radio be off? How do i turn it on? Can anyone help? 

Thanks. *really trying to get this migration working..*

PS - in XP, i can configure properties of the wireless NIC through the device driver - i can configure its MAC, its IP, its SSID and stuff. If i do this in windows, will it carry over when i boot Ubuntu? Would this obviate the need to set the card up in Ubuntu?? Thx.

---

### Post by stupidkid on 2006-08-01
When you load ndiswrapper, you must remove the native Linux drivers. Can you post your lsmod and iwconfig?

---

### Post by Grog140 on 2006-08-04
I have the same problem and I get this when I do that:

```
Module                  Size  Used by
ipv6                  286976  22
binfmt_misc            13064  1
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ppdev                   9668  0
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
speedstep_ich           6188  0
speedstep_lib           4580  1 speedstep_ich
cpufreq_userspace       6496  2
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
af_packet              24520  2
dm_mod                 63256  1
md_mod                 76052  0
ndiswrapper           189876  0
pcmcia                 41948  0
joydev                 10432  0
b44                    27980  0
mii                     6176  1 b44
yenta_socket           30124  1
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
nvidia               4552660  20
i2c_core               22848  2 i2c_acpi_ec,nvidia
hw_random               5716  0
pcspkr                  2244  0
snd_intel8x0           35772  2
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
shpchp                 49504  0
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
pci_hotplug            30788  1 shpchp
psmouse                40004  0
serio_raw               7748  0
intel_agp              24700  1
agpgart                36784  2 nvidia,intel_agp
sr_mod                 17988  0
sg                     40160  0
evdev                  10176  2
tsdev                   8032  0
sd_mod                 20448  1
usbhid                 42752  0
usb_storage            79584  1
scsi_mod              145960  4 sr_mod,sg,sd_mod,usb_storage
ext3                  148104  1
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  1 ohci1394
ehci_hcd               36104  0
uhci_hcd               35408  0
usbcore               139076  6 ndiswrapper,usbhid,usb_storage,ehci_hcd,uhci_hcdide_cd                 35780  0
ide_disk               19136  2
cdrom                  41408  2 sr_mod,ide_cd
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

And

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by hayim on 2006-08-04
actually, i got the thing working old-school styles using the terminal commands. The card works fine, im posting here wirelessly, but the GUI interfaces dont work - the network-admin app and the network-maanager-gnome app doesnt do a damned thing.

maybe it's ubuntu's way of gently getting us to learn the command line..

---

