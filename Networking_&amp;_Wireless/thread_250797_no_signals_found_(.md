---
title: "no signals found :("
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by Saoirse on 2006-09-04
hello everybody!
i have just installed ubuntu. internet works only with the cable(i just had to set the ip adresses). with the wireless i had a problem with windows as well, the card in the laptop couldnt find any signal, and i put an usb adapter instead of the card and it worked.however now, with ubuntu, even the adapter doesn't find any signals.
god save ubuntu, is really cool!
saoirse!
(i read the wiki thing but doesn t seem to give any good suggestion to my prob)

---

### Post by lupine_nickt on 2006-09-04
Are you scanning as root? i.e. iwlist <interface> scan

interface could be wlan0, eth1, rausb0... iwconfig will tell you which.

If that doesn't help, could you post the output of the terminal commands lsusb, lsmod, iwconfig and ifconfig. Also the contents of your /etc/network/interfaces file :)

xF,

...Nick

---

### Post by kamilczauz on 2006-09-04
yes ive been having the same problem... i just put a mini pci wireless card in my laptop and i am having lots of troubles finding an access point when there are atleast 3 around me.

here are my outputs, please help

```
kamil@kamil-laptop:~$ sudo iwlist ath0 scan
ath0      Failed to read scan data : Resource temporarily unavailable

kamil@kamil-laptop:~$ lsmod
Module                  Size  Used by
sg                     37920  0 
scsi_mod              139496  1 sg
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
nvram                   9224  1 
uinput                  9088  1 
ppdev                   9220  0 
savage                 35584  1 
drm                    73236  2 savage
speedstep_ich           5260  0 
speedstep_lib           4484  1 speedstep_ich
cpufreq_userspace       4696  1 
cpufreq_stats           5636  0 
freq_table              4740  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
video                  16260  0 
tc1100_wmi              6916  0 
sony_acpi               5644  0 
pcc_acpi               12416  0 
ibm_acpi               26112  0 
hotkey                 11556  0 
dev_acpi               11140  0 
container               4608  0 
button                  6672  0 
acpi_sbs               19980  0 
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
ipv6                  265728  6 
dm_mod                 58936  1 
af_packet              22920  8 
md_mod                 72532  0 
lp                     11844  0 
pcmcia                 40508  0 
e100                   40580  0 
mii                     5888  1 e100
ath_pci                80540  0 
ath_rate_sample        17160  1 ath_pci
wlan                  144924  3 ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
yenta_socket           28428  2 
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
hw_random               5652  0 
tsdev                   8000  0 
parport_pc             35780  1 
irtty_sir               8576  0 
sir_dev                19628  1 irtty_sir
nsc_ircc               23948  0 
parport                36296  3 ppdev,lp,parport_pc
irda                  187068  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               2304  1 irda
intel_agp              22940  1 
agpgart                34888  2 drm,intel_agp
floppy                 62148  0 
rtc                    13492  0 
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
snd_intel8x0           33692  1 
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
pcspkr                  2180  0 
psmouse                36100  0 
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
serio_raw               7300  0 
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
evdev                   9856  2 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
uhci_hcd               33680  0 
usbcore               130692  2 uhci_hcd
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
kamil@kamil-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.427 GHz  Access Point: FF:00:FF:00:FF:00   
          Bit Rate=11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

kamil@kamil-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:78:77:58:78  
          inet6 addr: fe80::214:78ff:fe77:5878/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:d8ac0000-d8ad0000 

eth0      Link encap:Ethernet  HWaddr 00:02:8A:36:44:FE  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:8aff:fe36:44fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:932565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:602055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2665 txqueuelen:1000 
          RX bytes:1235829639 (1.1 GiB)  TX bytes:50540277 (48.1 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2520 (2.4 KiB)  TX bytes:2520 (2.4 KiB)

kamil@kamil-laptop:~$ 

```

---

### Post by johnmc811 on 2006-09-04
[COLOR="black"]When I installed Ubuntu, last night, I used the wireless option to install the rest of Ubuntu, but I made sure that my SSID was broadcasting.  I usually have it turned off, but It enabled Ubuntu to find my wireless router.
Good Luck,
johnmc811[/COLOR]

---

### Post by lupine_nickt on 2006-09-04
OK, you're running an Atheros card and it's loaded and working perfectly... except this "temporarily unavailable" business.

Of course, you didn't check the error message with Google, and so completely missed the "I'm Feeling Lucky" solution [here](http://madwifi.org/wiki/UserDocs/Troubleshooting#WhenIruntrytoscanIget:ath0:Failedtoreadscandata:Resourcetemporarilyunavailable.HowdoIfixit) ;)

I think that the version of wireless-tools included in Ubuntu is the right one. If not, google for it and build the newer version. It's more likely to be the hardware switch, though...

xF,

...Nick

---

### Post by kamilczauz on 2006-09-04
yes i wish the solution was that simple...

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ih=015&item=250019925135&rd=1&sspagename=STRK%3AMEWN%3AIT&rd=1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ih=015&item=250019925135&rd=1&sspagename=STRK%3AMEWN%3AIT&rd=1)

that is the wifi card that i bought, i have already tried intalling a new version of wireless tools to no avail.  Still have the same problem.  I dont see any switch on the mini pci card, but you can have a look at the card from the link above.

thanks, please help some more

thanks again
kamil

---

### Post by lupine_nickt on 2006-09-04
Maybe try [this](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)?

---

### Post by kamilczauz on 2006-09-04
> **lupine_nickt said:**
> Maybe try [this](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)?

yup,,, thats exactly what i did... and now i dont get the error, but i also dont get any access points listed, as when i use windows... i get aleast 3 access points

```

kamil@kamil-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


```

```
kamil@kamil-laptop:~$ dmesg|grep 'ath'
[17179593.952000] ath_hal: module license 'Proprietary' taints kernel.
[17179593.952000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179594.136000] ath_rate_sample: 1.2 (0.9.2)
[17179594.156000] ath_pci: 0.9.4.5 (0.9.2)
[17179608.588000] ath0: no IPv6 routers present
[17179717.300000] ath0: no IPv6 routers present

```

```
kamil@kamil-laptop:~$ iwlist ath0 scan
ath0      No scan results
kamil@kamil-laptop:~$ iwlist ath0 ap
ath0      No Peers/Access-Point in range

kamil@kamil-laptop:~$ iwlist ath0 scanning
ath0      No scan results

```

```
kamil@kamil-laptop:~$ wlanconfig ath0 list ap
kamil@kamil-laptop:~$ sudo wlanconfig ath0 list ap
kamil@kamil-laptop:~$ sudo wlanconfig ath0 list scan
kamil@kamil-laptop:~$ sudo wlanconfig ath0 list sta
kamil@kamil-laptop:~$ sudo wlanconfig ath0 list freq
Channel   1 : 2412  Mhz 11g          Channel   8 : 2447  Mhz 11g          
Channel   2 : 2417  Mhz 11g          Channel   9 : 2452  Mhz 11g          
Channel   3 : 2422  Mhz 11g          Channel  10 : 2457  Mhz 11g          
Channel   4 : 2427  Mhz 11g          Channel  11 : 2462  Mhz 11g          
Channel   5 : 2432  Mhz 11g          Channel  12 : 2467  Mhz 11g          
Channel   6 : 2437  Mhz 11g Dynamic  Channel  13 : 2472  Mhz 11g          
Channel   7 : 2442  Mhz 11g          
kamil@kamil-laptop:~$ sudo wlanconfig ath0 list chan
Channel   1 : 2412  Mhz 11g          Channel   8 : 2447  Mhz 11g          
Channel   2 : 2417  Mhz 11g          Channel   9 : 2452  Mhz 11g          
Channel   3 : 2422  Mhz 11g          Channel  10 : 2457  Mhz 11g          
Channel   4 : 2427  Mhz 11g          Channel  11 : 2462  Mhz 11g          
Channel   5 : 2432  Mhz 11g          Channel  12 : 2467  Mhz 11g          
Channel   6 : 2437  Mhz 11g Dynamic  Channel  13 : 2472  Mhz 11g          
Channel   7 : 2442  Mhz 11g          
kamil@kamil-laptop:~$ sudo wlanconfig ath0 list caps
ath0=7782e00f<WEP,TKIP,AES,AES_CCM,TXPMGT,SHSLOT,SHPREAMBLE,TKIPMIC,WPA1,WPA2,BURST,WME>
kamil@kamil-laptop:~$ sudo wlanconfig ath0 list active
Channel   1 : 2412  Mhz 11g          Channel   8 : 2447  Mhz 11g          
Channel   2 : 2417  Mhz 11g          Channel   9 : 2452  Mhz 11g          
Channel   3 : 2422  Mhz 11g          Channel  10 : 2457  Mhz 11g          
Channel   4 : 2427  Mhz 11g          Channel  11 : 2462  Mhz 11g          
Channel   5 : 2432  Mhz 11g          Channel  12 : 2467  Mhz 11g          
Channel   6 : 2437  Mhz 11g Dynamic  Channel  13 : 2472  Mhz 11g          
Channel   7 : 2442  Mhz 11g          
kamil@kamil-laptop:~$ 

```




So, now i dont get an error, yet i still have no AP :(

thanks again and please help,

Kamil

---

