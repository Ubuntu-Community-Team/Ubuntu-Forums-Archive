---
title: "intrepid: nework isn't working after wake up from suspend"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by unsen on 2008-11-02
this is for WIRED connection!

after resuming from suspend-mode my connection to the router is broken. 

ip addr show doesn't have a inet IP for the eth-port which is connected to the router.

after booting it looks like:
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:1b:fc:a1:1c:c7 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:1b:fc:a1:15:3d brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.104/24 brd 192.168.2.255 scope global eth1
    inet6 fe80::21b:fcff:fea1:153d/64 scope link
       valid_lft forever preferred_lft forever
4: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN
    link/ether 32:60:8a:19:73:a4 brd ff:ff:ff:ff:ff:ff

```

after wakeup from S3 at 3:eth1 the inet entry is missing. inet6 is still there!
anyways, there's no connection to the router or internet possible anymore.

i already tried a /etc/init.d/networking restart
or dhclient eth1

but dhclient didnt get an answer and the ip was set to 169.somewhat

its a ASUS M2N SLI deluxe 590 nvidia Chipset (two GBit LAN)

---

### Post by wbell12 on 2008-11-04
I was having the same problem; it seems there's something broken when reloading the network driver module "forcedeth" after a suspend. Found these two bug reports on launchpad ([[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+bug/280981[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/280981") and [[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283462[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283462")) and this other post on the forums ([[COLOR="Blue"]http://www.backports.ubuntuforums.org/showthread.php?t=137633[/COLOR]]("http://www.backports.ubuntuforums.org/showthread.php?t=137633")) that gave me the idea to manually unload and reload the driver.

$***sudo modprobe -r forcedeth; sudo modprobe forcedeth***

After this, NetworkManger acts nice again :grin: and connects to the ethernet.  I'm still trying to find an automatic way of doing this (adding it to the blacklist in acpi-support doesn't seem to help) but it's alot better than a restart.

Hope this helps.

---

### Post by unsen on 2008-11-04
> $sudo modprobe -r forcedeth; sudo modprobe forcedeth

thx, but that didn't help. i was able to unload and reload forcedeth. but i didnt get a new IP that way.

again, i have only a IPv6 on eth0 this time (i already changed the LAN interface from eth1 to eth0 and back):

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
7: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:1b:fc:a1:1c:c7 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::21b:fcff:fea1:1cc7/64 scope link
       valid_lft forever preferred_lft forever
```

dhclient eth1 (cable connected to the other port this time):
```
Internet Systems Consortium DHCP Client V3.1.1                     
Copyright 2004-2008 Internet Systems Consortium.                   
All rights reserved.                                               
For info, please visit http://www.isc.org/sw/dhcp/                 

Listening on LPF/eth1/00:1b:fc:a1:15:3d
Sending on   LPF/eth1/00:1b:fc:a1:15:3d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

lsmod:
```
Module                  Size  Used by                          
af_packet              25728  4                                
ipv6                  263972  21                               
binfmt_misc            16904  1                                
bridge                 56980  0                                
stp                    10628  1 bridge                         
bnep                   20480  2                                
sco                    18308  2                                
rfcomm                 44432  0                                
l2cap                  30464  6 bnep,rfcomm                    
bluetooth              61924  6 bnep,sco,rfcomm,l2cap          
ppdev                  15620  0                                
powernow_k8            22148  1                                
cpufreq_conservative    14600  0                               
cpufreq_stats          13188  0                                
cpufreq_ondemand       14988  1                                
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0                                           
cpufreq_powersave       9856  0                                           
video                  25104  0                                           
output                 11008  1 video                                     
sbs                    19464  0                                           
pci_slot               12552  0                                           
sbshc                  13440  1 sbs                                       
container              11520  0                                           
wmi                    14504  0                                           
battery                18436  0                                           
iptable_filter         10752  0                                           
ip_tables              19600  1 iptable_filter                            
x_tables               22916  1 ip_tables                                 
dm_crypt               21124  0                                           
crypto_blkcipher       25476  1 dm_crypt                                  
dm_mod                 63432  1 dm_crypt                                  
ac                     12292  0                                           
lp                     17156  0                                           
nvidia               6900560  38                                          
agpgart                42184  1 nvidia                                    
serio_raw              13444  0                                           
psmouse                45200  0                                           
pcspkr                 10624  0                                           
k8temp                 12416  0                                           
joydev                 18368  0                                           
evdev                  17696  8                                           
shpchp                 37908  0                                           
pci_hotplug            35236  1 shpchp                                    
snd_hda_intel         381488  1                                           
snd_ens1371            30880  1                                           
parport_pc             39204  1                                           
gameport               19468  1 snd_ens1371                               
snd_seq_dummy          10884  0                                           
parport                42604  3 ppdev,lp,parport_pc                       
snd_ac97_codec        111652  1 snd_ens1371                               
snd_seq_oss            38528  0                                           
snd_seq_midi           14336  0                                           
ac97_bus                9856  1 snd_ac97_codec                            
snd_rawmidi            29824  2 snd_ens1371,snd_seq_midi                  
snd_pcm_oss            46848  0                                           
snd_mixer_oss          22784  1 snd_pcm_oss                               
snd_pcm                83204  4 snd_hda_intel,snd_ens1371,snd_ac97_codec,snd_pcm_oss
cfi_cmdset_0002        30720  1                                                     
cfi_util               11392  1 cfi_cmdset_0002                                     
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi                            
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq                                          
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
jedec_probe            19968  0                                                           
snd                    63268  15 snd_hda_intel,snd_ens1371,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device                            
cfi_probe              13568  0                                                                 
soundcore              15328  1 snd                                                             
i2c_nforce2            14468  0                                                                 
button                 14224  0                                                                 
gen_probe              11264  2 jedec_probe,cfi_probe                                           
ck804xrom              13060  0                                                                 
mtd                    23560  3 cfi_cmdset_0002,ck804xrom                                       
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm                                           
i2c_core               31892  2 nvidia,i2c_nforce2                                              
chipreg                11012  3 jedec_probe,cfi_probe,ck804xrom                                 
map_funcs               9984  1 ck804xrom                                                       
ext3                  133256  1
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0
cdrom                  43168  1 sr_mod
sd_mod                 42264  6
crc_t10dif              9984  1 sd_mod
pata_amd               18692  0
sata_nv                30600  4
sg                     39732  0
usbhid                 35840  0
hid                    50560  1 usbhid
ata_generic            12932  0
pata_jmicron           11136  0
ahci                   37132  0
ohci1394               37936  0
pata_acpi              12160  0
ieee1394               96324  1 ohci1394
libata                177312  6 pata_amd,sata_nv,ata_generic,pata_jmicron,ahci,pata_acpi
forcedeth              61328  0
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0
ohci_hcd               31888  0
usbcore               148848  4 usbhid,ehci_hcd,ohci_hcd
thermal                23708  0
processor              42156  2 powernow_k8,thermal
fan                    12548  0
fuse                   60828  3
vesafb                 13828  1
fbcon                  47648  72
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
maybe someone has an idea, which module could cause trouble..

and maybe i have a general ACPI problem with my mainboard (ASUS M2N32 SLI deluxe)
after resume from S3 the nvidia graphics-driver isn't able to control the fanspeed on the graphics-board anymore (staying constantly at 80%). i've had this issue with hardy already and had to use a script with nvclock to control the fanspeed again. in intrepid there's no change.. but now additionally the network isnt working after resume from S3.. f*** ;)

---

### Post by ponkarthik on 2008-11-08
Hi,

  I had similar problem with nvidia chipset. My wired connection used the 'forcedeth' module as well.

I have everything - restarting /etc/init.d/networking, /etc/init.d/NetworkManager , reloading forcedeth. None worked.

**The good news is removing forcedeth**

```
sudo modprobe -r forcedeth
```
 before suspending and reloading it after suspend 
```
sudo modprobe forcedeth
```
works very well.


In order to automatically unload 'forcedeth' and load at suspend I did the following. But it does not seem to work.

I added 'forcedeth' to /etc/default/acpi-support
```

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="forcedeth"

``` 
and added acpi-support to methods of suspending in the same file.
```
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils acpi-support"
```
Can anyone please help to automatically unload and load a module on suspend and resume ?

---

### Post by unsen on 2008-11-08
meanwhile i've solved the problem using pm-utils only:

lshw is listing the hardware and the according modulenames. in my case forcedeth is the driver controlling my LAN-port.

next you can have a look at /var/log/pm-suspend.log what went wrong while going to sleepmode or at resume. 
in /usr/lib/pm-utils you can see some configurable settings for hilbernate/sleepmode. dont change here, use a conf-file in /etc/pm/config.d instead: 00sleep_module.

in my case i was adding a line:

SUSPEND_MODULES="forcedeth"

..and my NetworkManager now is able to restore the network-connection after a sleep/resume

infact, this option is doing an auto modprobe -r before sleep and a modprobe on resume, as i've read. besides, pm-utils seems to replace the old ACPI-Support and is extended by HAL support.

if someone knows more, please report :)

---

### Post by m4cph1sto on 2008-11-08
I have this same problem, on Ubuntu Intrepid 64-bit fresh install, with my nvidia 680i motherboard.  The problem did not occur on Hardy.  Anyway, unsen's solution fixed it.

---

### Post by Moz Holmes on 2008-11-21
Hey thanks unsen, that worked like a charm. 

I also added the line in /etc/pm/config.d 00sleep_module but in my particular situation I added 

SUSPEND_MODULES="sis900" 

as that is the driver that is being used for my card. 

If anyone's interested I'm using Mythbuntu Intrepid release and my network card is an SiS integrated wired ethernet. 

Cheers!

---

