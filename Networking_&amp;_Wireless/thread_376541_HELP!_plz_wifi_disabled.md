---
title: "HELP! plz wifi disabled"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by dutch_master on 2007-03-05
I put Ubuntu (6.10) on my laptop HP ze4900 but I cant seem to get my wifi, Broadcom Corporation BCM4306, enabled (button on the side that disabled and enables), Ubuntu recognized my wireless card and i see it under "networking", I searched through the forums but I cant really understand what to do since im a complete n00b to anything linux and this is my first time messing around with this stuff. I did find type something in earlier that showed that it was disabled, I know you guys dont want to deal with us n00b's but I would really appreciate any help cause I cant figure it out, thank you soooo much!

---

### Post by n00b@linux on 2007-03-05
> **dutch_master said:**
> I know you guys dont want to deal with us n00b'sThat's not true. We were all n00bs at one time. We're here to help.\\:D/ 
 
Can you please post some details about your system? Namely, can you please open a terminal (Applications > Accessories > Terminal) and execute the following commands and copy and paste their output to this thread:```
lspci
``````
lsmod
``````
ifconfig
``````
iwconfig
```
 
Once you've done that, you could read this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28WifiDocs%2FDriver%29]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28WifiDocs%2FDriver%29") while you're waiting for another response.

---

### Post by dutch_master on 2007-03-05
when i type in ispci and ismod, i got a no command error but here's what you asked for (thnanks for the help)

pim@pim2:~$ Ispci
bash: Ispci: command not found
pim@pim2:~$ Ismod
bash: Ismod: command not found
pim@pim2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:5B:71:8A  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe5b:718a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:967341 (944.6 KiB)  TX bytes:221756 (216.5 KiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

pim@pim2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by n00b@linux on 2007-03-05
It's been a few months since I last used Ubuntu, so your 'no command' errors are indicative of a need to run those commands with root privileges. Sorry about that.
 
Try:```
sudo lspci
```and```
sudo lsmod
```Also, try running```
sudo ifconfig eth1 up
```then```
sudo iwlist eth1 scan
```and see if you can see your access point listed.

---

### Post by dutch_master on 2007-03-05
pim@pim2:~$ sudo ispci
sudo: ispci: command not found
pim@pim2:~$ sudo ismod
sudo: ismod: command not found
pim@pim2:~$ sudo ifconfig eth1 up
SIOCSIFFLAGS: No such file or directory
pim@pim2:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : No such device

i guess that doesnt help much, do i need to type something else in?

---

### Post by n00b@linux on 2007-03-05
lspci, not ispci (ie. a lower case 'L').  You probably don't need the sudo prefix as your errors are probably caused by using 'i' instead of 'l'.  Same goes for lsmod (use lower case 'L' and no sudo).
 
The error with 'sudo ifconfig eth1 up' suggests to me you haven't got the right kernel module installed.  lsmod should confirm this for us.

---

### Post by dutch_master on 2007-03-05
sorry, im retarded

pim@pim2:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
pim@pim2:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  8 
i915                   21632  2 
drm                    74644  3 i915
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  4 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
pcmcia                 40380  0 
8139cp                 24832  0 
bcm43xx               127252  0 
8139too                29056  0 
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7552  1 ieee80211
mii                     6912  2 8139cp,8139too
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                 11200  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
evdev                  11392  2 
tsdev                   9152  0 
hw_random               7320  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
psmouse                41352  0 
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
serio_raw               8452  0 
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capabili

---

### Post by n00b@linux on 2007-03-05
Okay, it's there:```
bcm43xx 127252 0
```Follow this thread: [URL="http://<a href="][http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
[/URL]It worked for 7/10 people.

---

### Post by dutch_master on 2007-03-05
thanks man, ill let you know how it worked out

---

### Post by dutch_master on 2007-03-05
DUDEEEEEE, your awesome, like super awesome, thank you sooooo much!

---

### Post by n00b@linux on 2007-03-06
I'm glad to hear you got it working.
Like I said originally, we're all here to help :)

---

