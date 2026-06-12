---
title: "Wireless Final Yard"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by ibc on 2006-12-27
I'm trying to set up Ubuntu for a friend that would like to try a Linux distro.  Aside from a couple of issues (e.g removing 'dri' from xorg.conf; downloading and extracting the wireless adapter firmware; etc...) the Ubuntu install has gone pretty cleanly.

But now I'm running up against something that I'm not sure is a problem w/ the distro, the adapter, or my configuration.  Everything looks like it should work, but I just cannot successfully ping the gateway.

I've got a Linksys WPC54G adapter (v.3), in a Fujitsu-Siemens AMILO-A laptop.  The adapter shows up both in iwconfig/ifconfig.  I've set its IP to a static 192.168.1.24.  

Thanks in advance to anyone who can help me out.

Excruciating detail begins here:


[iwconfig]
```
eth1      IEEE 802.11b/g  ESSID:"IANSLAN"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:10:42:FB:AC   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level=-51 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:11  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
*****************************
[ifconfig]
```
eth1      Link encap:Ethernet  HWaddr 00:14:BF:E6:CC:3C  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fee6:cc3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:81 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2005 (1.9 KiB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5220 (5.0 KiB)  TX bytes:5220 (5.0 KiB)

```
*****************************
[iwlist eth1 scan]
```
eth1      Scan completed :
          Cell 01 - Address: 00:13:10:42:FB:AC
                    ESSID:"IANSLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-50 dBm  
                    Extra: Last beacon: 144ms ago

```
*****************************
[uname -a]
```
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

```*****************************
[lsmod]
```
[FONT="Fixedsys"]Module                  Size  Used by
nls_utf8                3200  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
powernow_k7             8872  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k7,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
sg                     37404  0 
sd_mod                 22656  2 
sbp2                   24584  0 
lp                     12964  0 
arc4                    3200  2 
ieee80211_crypt_wep     6528  1 
bcm43xx               127252  0 
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
joydev                 11200  0 
tsdev                   9152  0 
usb_storage            75072  1 
scsi_mod              144648  4 sg,sd_mod,sbp2,usb_storage
libusual               17040  1 usb_storage
pcmcia                 40380  0 
snd_ali5451            25356  1 
snd_ac97_codec         97696  1 snd_ali5451
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
evdev                  11392  1 
serio_raw               8452  0 
pcspkr                  4352  0 
snd_pcm                84612  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
8139cp                 24832  0 
8139too                29056  0 
mii                     6912  2 8139cp,8139too
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ati_agp                10636  1 
agpgart                34888  1 ati_agp
i2c_ali1535             7940  0 
snd                    58372  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  1 snd_pcm
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
psmouse                41352  0 
floppy                 63044  0 
i2c_ali15x3             8708  0 
i2c_core               23424  3 i2c_ec,i2c_ali1535,i2c_ali15x3
yenta_socket           28812  3 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ohci_hcd               22532  0 
usbcore               134912  4 usb_storage,libusual,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
generic                 5764  0 
alim15x3               13324  0 [permanent]
thermal                15624  0 
processor              31560  2 powernow_k7,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability[/FONT]

```

---

### Post by ibc on 2006-12-27
SUCCESS!  Before you dump the native BCM4318 drivers in favor of NDISWRAPPER, you may want to try this.  It worked for me:

I finally got my infamous Linksys-G card working.  Everything appeared to be configured properly (as perlsmod, iwconfig, ifconfig, dmesg etc...) on my Fujitsu-Siemens w/ a BCM4318 v.02.  But I couldn't get it to actually ping the gateway to save my life.

[If you've already "blacklisted" the bcm43xx drivers, remove them from the blacklist (/etc/modules.d/blacklist).  Then remove ndiswrapper from the list of modules to load at boot (/etc/modules)]

So I installed network-manager-gnome, network-manager, and wpasupplicant via "System" -> "Administration" -> "Synaptic Package Manager" (using the install CD).

Then I cleared out the old interfaces config data w/:

```
sudo vi /etc/network/interfaces
```

Commenting out everything other than &#8220;lo&#8221; entries, and saving the file.

Then I created a file ```
/etc/default/wpasupplicant
```, adding a single entry "ENABLED=0" and saved the file

```
sudo touch /etc/default/wpasupplicant
```

Reboot your system or use the following command

```
sudo /etc/init.d/dbus restart
```

Once, that was restarted, I could click on the NetworkManager icon in the "system tray" (right next to the date, and speaker volume icon) and choose a SSID from the drop-down.

epilogue: For some reason, the bottom line was that my interface config (/etc/network/interfaces) as generated by "System -> Administration -> Networking" wasn't getting the job done, and when I installed NetworkManager, the "weird" format was preventing NetworkManager from detecting anything as well.  Heckuva job, Brownie!

---

