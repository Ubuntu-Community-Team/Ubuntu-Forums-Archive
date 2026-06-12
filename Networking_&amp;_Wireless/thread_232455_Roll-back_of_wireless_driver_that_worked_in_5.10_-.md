---
title: "Roll-back of wireless driver that worked in 5.10 - HOW??"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by kvalis on 2006-08-08
I initially installed 5.10 and wireless worked straight after reboot.
After upgrading to 6.06, I - like many other despairing Ubuntu 6.06 users - lost our wireless connection.

iwconfig from 5.10:

> wlan0     IEEE 802.11b+/g+  ESSID:"Nytun"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:A5:03:64:04
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=46/100  Signal level=25/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwconfig from 6.06:

> wlan0     IEEE 802.11b+/g+  ESSID:"Nytun"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=50/100  Signal level=30/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I take it that Nickname constitutes the name of the driver used - and if so, are there any way to try loading the one that was working in 5.10 instead of the one listed in the 6.06 iwconfig.

How do we do that, or how can we keep the wireless settings from 5.10 when upgrading to 6.06. 

Can we manually set the Access-point

I am sure that many with me would like this looked into in the near future.

Don't think me ungrateful, because Ubuntu is a fantastic distribution, but we would all like everything that worked in earlier versions to work now.

Look forward to suggestions if this is possible.

Kvalis
:-({|=

---

### Post by Dr. Nick on 2006-08-08
wow, ive never had this problem but have seen it mentioned a lot lately.

The kernel controls the drivers, what I would do is run "lsmod" and save the output to a file in 6.06. that will also tell you what drivers are loaded.

How did you update to 6.06? If you did a online update then you most likely still have the 5.10 kernel installed. At the boot screen choose a older kernel ver and see if wireless works, if so run lsmod in that kernel and compare the 2.

Also from 6.06 run 

locate acx

from a terminal, that should show most of the acx drivers avaible. Modprobe will load them.

---

### Post by kvalis on 2006-08-09
Here is the lmod's:

6.06:

> tore@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
i915                   20608  1
drm                    73236  2 i915
ppdev                   9220  0
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
ipv6                  265728  6
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
lp                     11844  0
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
8139cp                 22528  0
tsdev                   8000  0
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
analog                 12320  0
pcspkr                  2180  0
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
floppy                 62148  0
serio_raw               7300  0
gameport               15496  1 analog
psmouse                36100  0
8139too                26880  0
rtc                    13492  0
mii                     5888  2 8139cp,8139too
acx                   101132  0
i2c_i810                5252  0
i2c_algo_bit            9608  1 i2c_i810
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_core               21904  2 i2c_acpi_ec,i2c_algo_bit
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  4 acx,ehci_hcd,uhci_hcd
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

5.10:

> tore@ubuntu:~$ lsmod
Module                  Size  Used by
i915                   17920  1
drm                    58004  2 i915
ppdev                   9092  0
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
snd_mpu401              6344  0
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
analog                 10528  0
gameport               14472  1 analog
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
acx_pci               122752  0
firmware_class          9472  1 acx_pci
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  0
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  3 ppdev,parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  3 ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  682
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

Locate acx in 6.06:

> tore@ubuntu:~$ locate acx
/lib/firmware/2.6.15-26-386/acx
/lib/firmware/2.6.15-26-386/acx/0.4.11.4
/lib/firmware/2.6.15-26-386/acx/0.4.11.4/tiacx111c16
/lib/firmware/2.6.15-26-386/acx/1.2.0.30
/lib/firmware/2.6.15-26-386/acx/1.2.0.30/tiacx111
/lib/firmware/2.6.15-26-386/acx/1.2.0.30/tiacx111c16
/lib/firmware/2.6.15-26-386/acx/1.2.0.30/tiacx111c17
/lib/firmware/2.6.15-26-386/acx/1.2.0.30/tiacx111r16
/lib/firmware/2.6.15-26-386/acx/1.2.0.30/tiacx111r17
/lib/firmware/2.6.15-26-386/acx/1.2.1.34
/lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111
/lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111c16
/lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111c17
/lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111r16
/lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111r17
/lib/firmware/2.6.15-26-386/acx/default
/lib/firmware/2.6.15-26-386/acx/default/tiacx100usb
/lib/firmware/2.6.15-26-386/acx/default/tiacx100
/lib/firmware/2.6.15-26-386/acx/default/tiacx100r0D
/lib/firmware/2.6.15-26-386/acx/default/tiacx100r11
/lib/firmware/2.6.15-26-386/acx/default/tiacx100r15
/lib/firmware/2.6.15-26-386/acx/default/tiacx111c16
/lib/firmware/2.6.15-26-386/acx/default/tiacx111c17
/lib/firmware/2.6.15-26-386/acx/default/tiacx111c19
/lib/firmware/2.6.15-26-386/acx/0.4.11.9
/lib/firmware/2.6.15-26-386/acx/0.4.11.9/tiacx111
/lib/firmware/2.6.15-26-386/acx/0.4.11.9/tiacx111c16
/lib/firmware/2.6.15-26-386/acx/0.4.11.9/tiacx111r16
/lib/firmware/2.6.15-26-386/acx/1.0.7
/lib/firmware/2.6.15-26-386/acx/1.0.7/tiacx100usb
/lib/firmware/2.6.15-26-386/acx/1.7.0
/lib/firmware/2.6.15-26-386/acx/1.7.0/tiacx100
/lib/firmware/2.6.15-26-386/acx/1.7.0/tiacx100r11
/lib/firmware/2.6.15-26-386/acx/1.7.0/tiacx100r0D
/lib/firmware/2.6.15-26-386/acx/1.9.8.b
/lib/firmware/2.6.15-26-386/acx/1.9.8.b/tiacx100
/lib/firmware/2.6.15-26-386/acx/1.9.8.b/tiacx100r11
/lib/firmware/2.6.15-26-386/acx/1.9.8.b/tiacx100r15
/lib/firmware/2.6.15-26-386/acx/1.9.8.b/tiacx100r0D
/lib/firmware/2.6.15-26-386/acx/0.1.0.11
/lib/firmware/2.6.15-26-386/acx/0.1.0.11/tiacx111c16
/lib/firmware/2.6.15-26-386/acx/2.3.1.31
/lib/firmware/2.6.15-26-386/acx/2.3.1.31/tiacx111c16
/lib/firmware/2.6.15-26-386/acx/2.3.1.31/tiacx111c17
/lib/firmware/2.6.15-26-386/acx/2.3.1.31/tiacx111c19
/lib/firmware/2.6.15-26-386/acx/1.0.9
/lib/firmware/2.6.15-26-386/acx/1.0.9/tiacx100usb
/lib/firmware/2.6.15-26-386/acx/readme.txt
/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/acx
/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/acx/acx_pci.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/acx
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/acx/acx_pci.ko
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/acx
/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/acx/acx.ko

The driver or Nickname from 5.10 under iwconfig is:

> acx100 v0.2.0pre8

Can I extract this driver from the 5.10 CD??


Kvalis

---

### Post by Dr. Nick on 2006-08-09
nope, you cant really extract the driver from 5.10. drivers are specific to each kernel version and since 5.10 and 6.06 have different kernels they are not interchangable, most of the times though the same drivers should be in both

It looks like 6.06 is just loading the wrong driver/or none at all, try this in 6.06 and see what happes

sudo modprobe -r acx
sudo modporbe acx_pci

---

### Post by kvalis on 2006-08-09
Thanks Dr.Nick - tried that, the results you can see underneath

> tore@ubuntu:~$ sudo modprobe -r acx
Password:

tore@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

tore@ubuntu:~$ sudo modprobe acx_pci
FATAL: Module acx_pci not found.
tore@ubuntu:

Very frustrating. I have my eth0, so getting on the net is no problem, but
I was hoping to have this machine elsewhere in the house where it is not practical to have cables all over the place.

Any ideas?

Thanks a lot for all your suggestions so far.

Kvalis

---

### Post by Dr. Nick on 2006-08-09
sorry, no other ideas at the moment and I have to go to work now, Ill see if I notice anything later though

---

### Post by Dr. Nick on 2006-08-09
similar threaad about the acx cards not working below, do you know specific cards model number? It may help to search by it. It appears to be a firmware problem according to a few other posts

[http://ubuntuforums.org/showthread.php?t=208408&highlight=acx_pci](http://ubuntuforums.org/showthread.php?t=208408&highlight=acx_pci)

---

### Post by kvalis on 2006-08-10
Dr.Nick - thank you - we are a step closer
Added the line about firmware on the acx, so now I have got an Access Point.
Just need an IP now

Here is what I have now:

> tore@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:A5:03:64:04
                    ESSID:"Nytun"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level=28/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s

Would it help me if I downloaded **wifi-radar?**

Thanks again 
Kvalis

---

### Post by kvalis on 2006-08-10
Downoaded and installed wifi-radar.

Ran it, selected my network, w-r informed me that network did not have a profile and if I wanted to create one - I clicked yes, saved profile without adding any changes, and there was my IP address.

I am very pleased, I was just about to return to 5.10.
What wfif-radar does,that Ubuntu does not, I do not know, but I am OK now.

Thanks for all help.

Kvalis:D

---

### Post by Dr. Nick on 2006-08-10
glad you got it, I wouldnt have known lol. I have never had to deal with firmware for any of my cards.

---

