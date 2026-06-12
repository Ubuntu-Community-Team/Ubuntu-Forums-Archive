---
title: "having trouble installing wireless driver"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by banned bandit on 2008-08-20
I have a Averatec 3250 laptop with the RT2500 wireless chipset using ubuntu 8.04LTS.  I am using these instructions to set wireless up:

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

every time i enter in the command:

sudo ndiswrapper -i Rt2500.inf

I get this error:

couldn't open Rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

No matter what path i put in i get that stupid error.

Any Idea's on how to fix this?

Cheers,

Roy

---

### Post by caljohnsmith on 2008-08-20
When you enter the command "sudo ndiswrapper -i Rt2500.inf", are you in the directory where that file exists? Otherwise you have to give the path to the driver, such as:
```
sudo ndiswrapper -i /path/Rt2500.inf
```
Also note that specifying the file is case-sensitive, so Rt2500.inf is not the same as rt2500.inf. And lastly, make sure the .sys file also exists in the same directory as the .inf file that you install with ndiswrapper.

---

### Post by banned bandit on 2008-08-20
tried what you said and no mater what path I put is still get the same error: 

```


home@linux-averatec:~$ ls
Desktop                                      Public
Documents                                    RT2500.CAT
Examples                                     Rt2500.INF
google-repo-setup.sh                         Rt2500.PNF
linux_signing_key.pub                        RT2500.SYS
Music                                        Templates
opera_9.20-20070409.6-shared-qt_en_i386.deb  Videos
Pictures                                     wine-doors_0.1-1_all.deb
home@linux-averatec:~$ sudo ndiswrapper -i /home/Rt2500.inf
[sudo] password for home: 
couldn't open /home/Rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
home@linux-averatec:~$ sudo ndiswrapper -i /Rt2500.inf
couldn't open /Rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.



```

---

### Post by caljohnsmith on 2008-08-20
> **banned bandit said:**
> 
```


home@linux-averatec:~$ ls
Desktop                                      Public
Documents                                    RT2500.CAT
Examples                                     Rt2500.INF
google-repo-setup.sh                         Rt2500.PNF
linux_signing_key.pub                        RT2500.SYS
Music                                        Templates
opera_9.20-20070409.6-shared-qt_en_i386.deb  Videos
Pictures                                     wine-doors_0.1-1_all.deb
home@linux-averatec:~$ sudo ndiswrapper -i /home/Rt2500.inf
[sudo] password for home: 
couldn't open /home/Rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
home@linux-averatec:~$ sudo ndiswrapper -i /Rt2500.inf
couldn't open /Rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

```
That shows your wireless driver is in your home directory. Just do the following:
```
cd ~
sudo ndiswrapper -i Rt2500.INF
```

---

### Post by banned bandit on 2008-08-20
that worked, however my wireless card still doesn't work.  Doesn't even show up in the wifi manager.  My guess is that it was the wrong driver.  I guess I will have to do some more digging...sigh....

---

### Post by caljohnsmith on 2008-08-20
Did you follow the rest of that guide you originally linked to? If you haven't, here is what you need to do:
```
sudo modprobe ndiswrapper
echo -e "blacklist rt2500\nblacklist rt2500pci" | sudo tee -a /etc/modprobe.d/blacklist 
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

---

### Post by banned bandit on 2008-08-20
ya i followed all those instructions....still no go :(

---

### Post by caljohnsmith on 2008-08-20
OK, how about rebooting, open a terminal and do:
```
ndiswrapper -l
sudo modprobe ndiswrapper
iwconfig
sudo iwlist scan
```
Please post the output of all those commands.

---

### Post by banned bandit on 2008-08-20
ok i did the commands as you asked and here are the results (note: right now I have an old linksys PCMCIA WIFI B card plugged in right now):

```

home@linux-averatec:~$ ndiswrapper -l
rt2500 : driver installed
	device (1814:0201) present (alternate driver: rt2500pci)
home@linux-averatec:~$ sudo modprobe ndiswrapper
[sudo] password for home: 
home@linux-averatec:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b  ESSID:"WL-HDD"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:D4:5E:AE:20   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/92  Signal level=-11 dBm  Noise level=-142 dBm
          Rx invalid nwid:0  Rx invalid crypt:200  Rx invalid frag:0
          Tx excessive retries:113  Invalid misc:0   Missed beacon:0

home@linux-averatec:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:D4:5E:AE:20
                    ESSID:"WL-HDD"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/100  Signal level=-63 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000c234605065
          Cell 02 - Address: 00:1D:7E:20:E5:E3
                    ESSID:"dd-wrt_vap"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level=-68 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000017a0da7d6a

eth1      Scan completed :
          Cell 01 - Address: 00:13:D4:5E:AE:20
                    ESSID:"WL-HDD"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Signal level:52/153  Noise level:14/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s


```

---

### Post by caljohnsmith on 2008-08-21
It looks like Ubuntu is using the "rt2500pci" driver instead of ndiswrapper, so I don't think you went through the step that was supposed to blacklist that driver. Try the following:
```
grep -i rt2500pci /etc/modprobe.d/blacklist
```
If the above command doesn't return "blacklist rt2500pci", then you need to blacklist your rt2500pci module:
```
gksudo gedit /etc/modprobe.d/blacklist &
```
Add the line "blacklist rt2500pci" at the end of that file, save, and reboot. After rebooting do:
```
ndiswrapper -l
lsmod | grep 2500
```
And post the output.

---

### Post by Ayuthia on 2008-08-21
> **caljohnsmith said:**
> It looks like Ubuntu is using the "rt2500pci" driver instead of ndiswrapper, so I don't think you went through the step that was supposed to blacklist that driver. Try the following:
```
grep -i rt2500pci /etc/modprobe.d/blacklist
```
If the above command doesn't return "blacklist rt2500pci", then you need to blacklist your rt2500pci module:
```
gksudo gedit /etc/modprobe.d/blacklist &
```
Add the line "blacklist rt2500pci" at the end of that file, save, and reboot. After rebooting do:
```
ndiswrapper -l
lsmod | grep 2500
```
And post the output.

If it does show up with 'blacklist rt2500pci' can you post the results of the following:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
dmesg|grep ndiswrapper
lshw -C network
```
This will remove the ndiswrapper module and then reload it.  The dmesg command will let us see if any messages come up for ndiswrapper and the last command will let us see what your card is trying to use.

---

### Post by banned bandit on 2008-08-21
> **caljohnsmith said:**
> It looks like Ubuntu is using the "rt2500pci" driver instead of ndiswrapper, so I don't think you went through the step that was supposed to blacklist that driver. Try the following:
```
grep -i rt2500pci /etc/modprobe.d/blacklist
```
If the above command doesn't return "blacklist rt2500pci", then you need to blacklist your rt2500pci module:
```
gksudo gedit /etc/modprobe.d/blacklist &
```
Add the line "blacklist rt2500pci" at the end of that file, save, and reboot. After rebooting do:
```
ndiswrapper -l
lsmod | grep 2500
```
And post the output.

OK i did what you said.  I had rt2500 blacklisted, so i changed it to rt2500pci to be backlisted.  Wireless card still doesn't work.  Here is the output from the commands you asked me to run:

```

home@linux-averatec:~$ ndiswrapper -l
rt2500 : driver installed
	device (1814:0201) present (alternate driver: rt2500pci)
home@linux-averatec:~$ lsmod | grep 2500
home@linux-averatec:~$ 


```

---

### Post by banned bandit on 2008-08-21
> **Ayuthia said:**
> If it does show up with 'blacklist rt2500pci' can you post the results of the following:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
dmesg|grep ndiswrapper
lshw -C network
```
This will remove the ndiswrapper module and then reload it.  The dmesg command will let us see if any messages come up for ndiswrapper and the last command will let us see what your card is trying to use.

I did those commands and here is the output:

```

home@linux-averatec:~$ sudo modprobe -r ndiswrapper
[sudo] password for home: 
home@linux-averatec:~$ sudo modprobe ndiswrapper
home@linux-averatec:~$ dmesg|grep ndiswrapper
[   44.704441] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   44.796057] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/17/2005, 3.00.04.0000) loaded
[   44.799895] ndiswrapper: using IRQ 11
[   45.012662] usbcore: registered new interface driver ndiswrapper
[  638.268023] ndiswrapper: device wlan0 removed
[  638.268175] usbcore: deregistering interface driver ndiswrapper
[  662.659966] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  662.844405] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/17/2005, 3.00.04.0000) loaded
[  662.848724] ndiswrapper: using IRQ 11
[  663.064814] usbcore: registered new interface driver ndiswrapper
home@linux-averatec:~$ lsshw -c network
bash: lsshw: command not found
home@linux-averatec:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


```

---

### Post by Ayuthia on 2008-08-21
> **banned bandit said:**
> I did those commands and here is the output:

```

home@linux-averatec:~$ sudo modprobe -r ndiswrapper
[sudo] password for home: 
home@linux-averatec:~$ sudo modprobe ndiswrapper
home@linux-averatec:~$ dmesg|grep ndiswrapper
[   44.704441] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   44.796057] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/17/2005, 3.00.04.0000) loaded
[   44.799895] ndiswrapper: using IRQ 11
[   45.012662] usbcore: registered new interface driver ndiswrapper
[  638.268023] ndiswrapper: device wlan0 removed
[  638.268175] usbcore: deregistering interface driver ndiswrapper
[  662.659966] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  662.844405] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/17/2005, 3.00.04.0000) loaded
[  662.848724] ndiswrapper: using IRQ 11
[  663.064814] usbcore: registered new interface driver ndiswrapper
home@linux-averatec:~$ lsshw -c network
bash: lsshw: command not found
home@linux-averatec:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


```

The commands in the Terminal are case sensitive.  You need to have the capital C in lshw -C network.  The dmesg info looks ok.

---

### Post by caljohnsmith on 2008-08-21
In linux, commands are case-sensitive, so the command Ayuthia gave should use a capital "C":
```
sudo lshw -C network
```
Also, according to ndiswrapper, that rt2500pci module still seems to be getting in the way, yet lsmod doesn't show that module is loaded. Just to make sure it doesn't get loaded, try doing the following:
```
cd /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2x00/
sudo mv rt2500pci.ko rt2500pci.ko.backup

```
Reboot, and post the output of:
```
ndiswrapper -l
lsmod
lshw -C network
iwconfig
```

---

### Post by banned bandit on 2008-08-21
ok, i did what you said and ran those commands after the reboot, here is the result:

```

home@linux-averatec:~$ ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
home@linux-averatec:~$ lsmod
Module                  Size  Used by
binfmt_misc            12808  1 
via                    43648  2 
drm                    82452  3 via
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k7             9000  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
freq_table              5536  3 powernow_k7,cpufreq_ondemand,cpufreq_stats
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
ipv6                  267780  8 
af_packet              23812  8 
ndiswrapper           192920  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
hostap_cs              62868  0 
hostap                110724  1 hostap_cs
ieee80211_crypt         7040  1 hostap
orinoco_cs             16396  1 
orinoco                42772  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
joydev                 13120  0 
pcmcia                 40876  2 hostap_cs,orinoco_cs
ac                      6916  0 
battery                14212  0 
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
serio_raw               7940  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
via_ircc               27796  0 
ac97_bus                3072  1 snd_ac97_codec
irda                  203068  1 via_ircc
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
crc_ccitt               3072  1 irda
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                78596  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
i2c_viapro              9876  0 
evdev                  13056  7 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via_agp                11136  1 
snd_timer              24836  2 snd_seq,snd_pcm
i2c_core               24832  1 i2c_viapro
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
yenta_socket           27276  3 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  5 hostap_cs,orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd                    56996  19 snd_via82xx,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq,snd_pcm,snd_seq_device,snd_timer
agpgart                34760  2 drm,via_agp
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore               8800  1 snd
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
pata_via               13316  3 
via_rhine              26632  0 
mii                     6400  1 via_rhine
libata                159344  3 ata_generic,pata_acpi,pata_via
ehci_hcd               37900  0 
uhci_hcd               27024  0 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  3 powernow_k7,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 
home@linux-averatec:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 01
       serial: 00:11:09:0b:a0:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.52+Ralink Technology, Inc.,06/ latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:24:d3:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:06:25:16:c6:ad
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.4 ip=192.168.1.101 multicast=yes wireless=IEEE 802.11b
home@linux-averatec:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"WL-HDD"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:D4:5E:AE:20   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/92  Signal level=-37 dBm  Noise level=-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:560  Rx invalid frag:0
          Tx excessive retries:107  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:"WL-HDD"  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by caljohnsmith on 2008-08-21
Looks like your ndiswrapper may be happy now, so now try:
```
ndiswrapper -l   [COLOR="Blue"][that's a lower-case L, not a one][/COLOR]
sudo iwlist wlan0 scan
```
Also, do you have another wireless card or wireless USB adapter? Because lshw seems to think so.

---

### Post by banned bandit on 2008-08-21
ok did those commands and here is the result:

```

ome@linux-averatec:~$ ndiswrapper -l
rt2500 : driver installed
	device (1814:0201) present (alternate driver: rt2500pci)
home@linux-averatec:~$ sudo iwlist wlan0 scan
[sudo] password for home: 
wlan0     Scan completed :
          Cell 01 - Address: 00:13:D4:5E:AE:20
                    ESSID:"WL-HDD"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1D:7E:20:E5:E3
                    ESSID:"dd-wrt_vap"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

The onboard wireless card is still not recognized in the GUI network manager though.  I am going to reboot and remove my PCMCIA linksys wireless B card to see if that helps.

---

### Post by banned bandit on 2008-08-21
well I rebooted and the network manager still doesn't pick up the onboard WIFI

---

### Post by caljohnsmith on 2008-08-21
> **banned bandit said:**
> well I rebooted and the network manager still doesn't pick up the onboard WIFI
Well, your card is picking up wireless networks OK now, so what do you mean exactly that network manager doesn't pick up your wireless card? When you open network manager, click the unlock button and type your password, does it show "Wireless connection" that you can click on, and hit "properties"? You could provide a screen shot to make it clear what you are seeing.

---

### Post by banned bandit on 2008-08-21
ok, i can manualy configure the wifi card to connect to my wireless net work but when its in roaming mode it doesn't give the list of wireless networks or the back icon in the upper right corner next to the sound icon in the tray bar.

---

### Post by caljohnsmith on 2008-08-21
Roaming mode means that Ubuntu will try to connect to whichever open network it can find. So if you want to connect to a specific network like you do, you have to take your wireless card out of roaming mode in network manager.

---

### Post by banned bandit on 2008-08-22
ITS WORKING.

I had to remove the wireless B card then, goto add/remove programs and re-install the networkmanager.  Now roaming mode works with the onboard WIFI.

Big thanks to all you folks that helped me out.  Going to bed now LOL

---

