---
title: "Wireless Broadcom (BCM4318 (Rev 02)) not working on AMD 64"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by renrats on 2008-05-01
Please help me figure this out! I am a complete noob to Linux, (this is my first distro) and am having serious issues with wireless. I know it's not a hardware issue, because my wireless works under Windows XP. I've tried a few of the solutions I've seen around, but none ave seemed to work. As I am a noob, there is a pretty good chance I just screwed it up. If someone would sort of lead me, it would be greatly appreciated

---

### Post by Ayuthia on 2008-05-01
From what I can tell, you should be able to use the b43 driver.  This is the Linux native driver.  If you want to use this, you will need to install b43-fwcutter from Synaptic or type in the terminal:
```
sudo aptitude install b43-fwcutter
```
It will ask you if you want it to get the firmware for you.  If you want this, you need to make sure that you have a working internet connection. If you don't, it will get stuck.

Hope that helps.

---

### Post by renrats on 2008-05-01
Thanks for the info. Two things, I've heard that ndiswrapper is better/allows for greater connection speed. And along the way I know that I blacklisted b43-fwcutter trying to utilize ndiswrapper. So if they are the same, how does one "unblacklist" something, or I need help with the ndiswrapper method.

---

### Post by agim on 2008-05-01
[http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

---

### Post by Ayuthia on 2008-05-01
There are mixed responses between whether one is better than the other.  I have tried out both and I have not found any speed differences between the two.  The best way is to try them out.  If you want to try out the b43 driver, you will need to edit /etc/modprobe.d/blacklist and look for:
```
b43
ssb
```
replace it with:
```
#b43
#ssb
ndiswrapper
```
You will also have to go to /etc/modules and remove the word ndiswrapper and add the word b43.

Depending on how far you have gotten with the ndiswrapper route, you will also have to remove the modprobe removal/additions that might have been done in /etc/rc.local or update /etc/init.d/wirelessfix.sh to show the following:
```
#modprobe -r b44
#modprobe -r b43
#modprobe -r b43legacy
#modprobe -r ssb
#modprobe -r ndiswrapper
#modprobe ndiswrapper
#modprobe b44
```

If you have already started going the ndiswrapper route, I would go ahead and try it out because the steps to back out ndiswrapper will be able as difficult as setting it up.

---

### Post by renrats on 2008-05-01
Thanks for the advice. I'll go the ndiswrapper route then. Either way, I'm still having trouble. I've followed the instructions to a tee, and successfully as welllm except that I still have no wireless. I have no idea where I've gone wrong.

---

### Post by Ayuthia on 2008-05-02
Can you post the info for the following:
```
lspci -nn
lshw -C network
ndiswrapper -v
ndiswrapper -l
```
The lspci -nn is mainly for me.  I just want to know if your laptop needs the b44 driver.  The lshw will provide us information about your network cards and which driver they are trying to use.  The ndiswrapper -v will let us know what version of ndiswrapper you are using and the ndiswrapper -l will let us know what ndiswrapper is trying to use.  

Are you also using the bcmwl5 driver from your XP?  Also which set of instructions are you using for installing ndiswrapper?

---

### Post by renrats on 2008-05-02
The output is as follows:

lspci -nn: lspci -nn: 01:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

lshw -C network: WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wlan0
       version: 02
       serial: 00:1b:fc:8f:5e:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.51+Broadcom,10/12/2006, 4.100. latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

ndiswrapper -v: utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
version:        1.51
vermagic:       2.6.24-16-generic SMP mod_unload 

ndiswrapper -l: utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
version:        1.51
vermagic:       2.6.24-16-generic SMP mod_unload 
renrats@renrats:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
--------------------------------------------------------------------------

As for the driver type in Xp, I'll have to get back to you on that one. I'm using wired Internet in Ubuntu right now. I think that these are the only two I tried:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

---

### Post by Ayuthia on 2008-05-02
Ok.  That looks fine.  Can you do me a favor and post your lsmod info?  It will list all the loaded modules.  You might as well post your ifconfig and iwconfig info too, please.

EDIT:
By the way, the XP drivers might not work on yours.  I forgot that you are using 64-bit.

---

### Post by renrats on 2008-05-02
Here it is. Thanks for your help.

lsmod: Module                  Size  Used by
nls_iso8859_1           6656  1 
nls_cp437               8320  1 
vfat                   16256  1 
fat                    60592  1 vfat
ipv6                  311720  10 
af_packet              27272  2 
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
b44                    33168  0 
ssb                    37252  1 b44
mii                     7552  1 b44
ndiswrapper           244544  0 
ppdev                  11400  0 
cpufreq_ondemand       11152  0 
cpufreq_stats           8416  0 
cpufreq_userspace       6180  0 
cpufreq_powersave       3200  0 
freq_table              6464  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    10632  0 
video                  23444  0 
output                  5632  1 video
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
arc4                    3456  0 
ecb                     5248  0 
blkcipher               9476  1 ecb
snd_hda_intel         440408  5 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               9092  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                46236  0 
snd                    70856  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               8858052  34 
button                 10912  0 
i2c_nforce2             8704  0 
dcdbas                 11312  0 
soundcore              10400  1 snd
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
k8temp                  7680  0 
evdev                  14976  3 
i2c_core               28544  2 nvidia,i2c_nforce2
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  4 
usb_storage            82496  3 
usbhid                 35168  0 
hid                    44992  1 usbhid
libusual               23520  1 usb_storage
sata_nv                31624  0 
ata_generic             9988  0 
pata_acpi               9856  0 
pata_amd               16772  0 
floppy                 69096  0 
forcedeth              55564  0 
libata                176304  4 sata_nv,ata_generic,pata_acpi,pata_amd
scsi_mod              178488  5 sg,sr_mod,sd_mod,usb_storage,libata
ehci_hcd               41996  0 
ohci_hcd               27524  0 
usbcore               169904  7 ndiswrapper,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  1 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

ifconfig: eth0      Link encap:Ethernet  HWaddr 00:1a:a0:56:c5:c0  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe56:c5c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:242902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:190820277 (181.9 MB)  TX bytes:157754636 (150.4 MB)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88300 (86.2 KB)  TX bytes:88300 (86.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:8f:5e:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fdefe000-fdf00000 

iwconfig: lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by renrats on 2008-05-06
Ok, update, I decided that it was a good idea to reinstall Ubuntu and to try all over again. And it worked, sort of. I used b43-fwcutter, and now the light shows on my wireless card, however I am still having trouble connecting to the internet. Does anyone have any idea whats going on?

---

### Post by Ayuthia on 2008-05-06
Are you using encryption?  If so, you might try turning it off and see if you can connect.  If not, can you post your ifconfig, iwconfig, and iwlist scan info?

---

### Post by renrats on 2008-05-06
I'm not using encryption.

ifconfig: eth0      Link encap:Ethernet  HWaddr 00:1a:a0:56:c5:c0  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe56:c5c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1071123 (1.0 MB)  TX bytes:192094 (187.5 KB)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95500 (93.2 KB)  TX bytes:95500 (93.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:8f:5e:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-8F-5E-48-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig: eth0      Link encap:Ethernet  HWaddr 00:1a:a0:56:c5:c0  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe56:c5c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1071123 (1.0 MB)  TX bytes:192094 (187.5 KB)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95500 (93.2 KB)  TX bytes:95500 (93.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:8f:5e:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-8F-5E-48-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwlist scan: eth0      Link encap:Ethernet  HWaddr 00:1a:a0:56:c5:c0  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe56:c5c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1071123 (1.0 MB)  TX bytes:192094 (187.5 KB)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95500 (93.2 KB)  TX bytes:95500 (93.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:8f:5e:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-8F-5E-48-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Ayuthia on 2008-05-06
I think that you posted your ifconfig information three times instead of the iwconfig and iwlist.  This is a silly question, but did you try to connect with the wired connection unplugged?

Can you also check your lshw -C network and make sure that the configuration shows:
configuration: driver=b43-pci-bridge latency=0 module=ssb

---

### Post by renrats on 2008-05-06
Yep, you're right, I did post my ifconfig info three times. I'm used to Windows, and was using Ctrl-C instead of Shift-Ctrl-C to copy. I'll repost the correct info, and add the lshw info as well:

 ifconfig: eth0      Link encap:Ethernet  HWaddr 00:1a:a0:56:c5:c0  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe56:c5c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1071123 (1.0 MB)  TX bytes:192094 (187.5 KB)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95500 (93.2 KB)  TX bytes:95500 (93.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:8f:5e:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-8F-5E-48-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig: lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:46:10:5F   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan: lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:46:10:5F
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level=-52 dBm  Noise level=-47 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001318479c286

And here is the line from lshw: configuration: driver=b43-pci-bridge latency=32 module=ssb. It all matchs up, except for the latency bit.

---

### Post by Ayuthia on 2008-05-07
Everything looks fine in that portion.  We need to check our modules to make sure that there are no active modules that will conflict with the b43 module:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```
You might even try changing the channel on your router just in case it is getting interference from that channel.

By the way, sorry about not responding earlier to your ndiswrapper post. I forgot to subscribe to the thread. From your last ndiswrapper post, you were close.  It looked like your b44 driver triggered the ssb module which would have caused the conflict with ndiswrapper.  All we needed to do was remove the b44, ssb, and ndiswrapper modules and then load ndiswrapper first then b44.  But that is now another story.

---

### Post by renrats on 2008-05-07
D'oh. Oh well, as long as I get wireless...

lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper:
b43                   126760  0 
rfkill                 10128  3 rfkill_input,b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43
ssb                    37252  1 b43

---

### Post by Ayuthia on 2008-05-07
Everything looks like it is configured correctly.  The driver is loaded, bcm43xx is not conflicting, there is no ndiswrapper, and you are able to see access points.

We can try to do it manually from the Terminal.  By the way, if you did not know, Terminal can't use control-c because it will break out of the current thing that it is executing.  That is why copy is control-shift-c.

Let's try:
```
sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0
```

Are you able to change the channel on your router?

---

### Post by renrats on 2008-05-07
I haven't changed the channel on the router, because right now it's very late here. So I'll post teh output from the commands, and then attack this again tomorrow.

sudo dhclient wlan0:
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:fc:8f:5e:48
Sending on   LPF/wlan0/00:1b:fc:8f:5e:48
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

