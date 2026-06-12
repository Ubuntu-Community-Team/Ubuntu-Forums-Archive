---
title: "Can see wireless server, can't connect"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by wfb on 2006-12-15
Using 6.06 Dapper Drake -- only downloaded last week so bang up to date.

Have an old Toshiba Satellite Pro -- though the model number is irrelevant.

Wireless card is D-link DWL G650plus.

Can't easily cut and past output from iwconfig etc because the notebook won't connect to the net and I'm working from another machine.

Basically, the card appears to be running normally, but it doesn't make the connection to the router.

Connection properties tells me the signal strength is 85% -- which is about right. But it also says I'm disconnected. I've disabled all security on the router so there's no WEP to negotiate. 

iwconfig tells me the access point is not associated. My router can see the notebook. The DHCP settings give me the notebook's ip as 10.1.12 and there's also a MAC address.

So the notebook and the router can 'see' each other, but they can't make the connection. This should be easy from here, right?

---

### Post by tturrisi on 2006-12-16
post results of:
~# lsmod

---

### Post by wfb on 2006-12-16
Here goes:

bill@bill-laptop:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  1
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
apm                    21228  1
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
nls_iso8859_1           4224  1
nls_cp437               5888  2
vfat                   13440  2
fat                    53020  1 vfat
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
tsdev                   8000  0
acx                   101132  0
pcmcia                 40508  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_es1968             30848  1
pcspkr                  2180  0
gameport               15496  1 snd_es1968
snd_ac97_codec         93088  1 snd_es1968
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
rtc                    13492  0
floppy                 62148  0
serio_raw               7300  0
snd_pcm                89864  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  2 snd_es1968,snd_pcm
snd_mpu401_uart         7808  1 snd_es1968
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
psmouse                36100  0
donauboe               17152  0
snd                    55268  11 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer _oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
irda                  187068  1 donauboe
crc_ccitt               2304  2 donauboe,irda
soundcore              10208  1 snd
i2c_piix4               9104  0
i2c_core               21904  1 i2c_piix4
yenta_socket           28428  3
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                   9856  1
sg                     37920  0
sd_mod                 19984  2
usb_storage            74176  2
scsi_mod              139496  3 sg,sd_mod,usb_storage
ext3                  135688  2
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  4 acx,usb_storage,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  5
piix                   11012  1
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

---

### Post by spd106 on 2006-12-16
Try this thread [http://www.ubuntuforums.org/showthread.php?t=295992](http://www.ubuntuforums.org/showthread.php?t=295992)

---

