---
title: "New Ubuntu install, no internet"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by pozer69 on 2008-10-13
brand new linux user and i cant connect to the internet, I have no idea what im doing but after some searching i ran these tests:

joseph@joseph-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:462476 (462.4 KB)  TX bytes:462476 (462.4 KB)


joseph@joseph-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:462476 (462.4 KB)  TX bytes:462476 (462.4 KB)

pan0      Link encap:Ethernet  HWaddr 9e:2a:33:19:99:60  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

joseph@joseph-desktop:~$ lsmod
Module                  Size  Used by
isofs                  40100  1 
udf                    88356  0 
crc_itu_t              10112  1 udf
ipv6                  263972  14 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  4 
l2cap                  30464  16 bnep,rfcomm
bluetooth              61924  5 bnep,rfcomm,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_ondemand       14988  4 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
sbs                    19464  0 
wmi                    14504  0 
container              11520  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_mixer_oss          22784  1 snd_pcm_oss
snd_hwdep              15236  1 snd_usb_audio
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss,snd_usb_audio
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29952  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
uvcvideo               62728  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
snd                    63140  19 snd_hda_intel,snd_pcm_oss,snd_usb_audio,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                45200  0 
usblp                  20480  0 
v4l1_compat            22404  2 uvcvideo,videodev
iTCO_wdt               18596  0 
soundcore              15328  1 snd
iTCO_vendor_support    11652  1 iTCO_wdt
serio_raw              13444  0 
shpchp                 37908  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
evdev                  17696  12 
intel_agp              33724  1 
pci_hotplug            35236  1 shpchp
button                 14224  0 
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81600  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
libusual               26772  1 usb_storage
pata_jmicron           11136  2 
sg                     39732  0 
pata_acpi              12160  0 
sd_mod                 42264  3 
sr_mod                 22212  1 
crc_t10dif              9984  1 sd_mod
cdrom                  43168  1 sr_mod
ata_generic            12932  0 
ohci1394               37936  0 
ata_piix               24580  0 
sata_via               15492  1 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  5 pata_jmicron,pata_acpi,ata_generic,ata_piix,sata_via
scsi_mod              155212  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
dock                   16656  1 libata
ehci_hcd               43148  0 
uhci_hcd               30736  0 
usbcore               148848  10 snd_usb_audio,snd_usb_lib,uvcvideo,usblp,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              43052  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10752  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
uvesafb                34788  0 
cn                     15776  1 uvesafb
fuse                   60828  3 
compcache              13004  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14220  1 compcache

joseph@joseph-desktop:~$ sudo mii-tool
[sudo] password for joseph: 
no MII interfaces found

joseph@joseph-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

joseph@joseph-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


Please help me

---

### Post by pozer69 on 2008-10-13
Device - wired ethernet Intel 82566DC built in to mobo

---

### Post by Iowan on 2008-10-13
Results of **lspci**? I'd ask about contents of **/etc/network/interfaces**, but I've a feeling your "card" isn't recognized. [This]("http://hardware4linux.info/component/17379/") site suggests the e1000 or e1000e drivers.
[Another]("http://ubuntuforums.org/showthread.php?t=551720") one I found.
I also learned that Intrepid has some serious issues with the [e1000e]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555") driver.

---

### Post by groverblue on 2008-10-22
I'm having the same problem.  I followed the install method listed in Iowan's post, but the result is the same as pozer69's.

I downloaded this version (e1000-8.0.6.tar.gz):
[http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=983&DwnldID=9180&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=983&DwnldID=9180&lang=eng)

I added e1000 to /etc/modules and ran 'update-initramfs -u'

lsmod lists e1000, and i even tried running rmmod before modprobe.

Here is some output:

```

user@PCID075:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...    eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
```

```
user@PCID075:~$ sudo lshw -numeric
pcid075                   
    description: Desktop Computer
    product: Vostro 200
    vendor: Dell Inc.
  *-core
     *-pci
        *-network UNCLAIMED
             description: Ethernet controller
             product: 82562V-2 10/100 Network Connection [8086:10C0]
             vendor: Intel Corporation [8086]
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:c9:37:17:da:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
user@PCID075:~$ sudo lspci -nn
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
```

---

### Post by groverblue on 2008-10-22
I just found this page, but it looks like it's an issue with the kernel supplied driver, and not the one from Intel:

[http://www.notebookforums.com/thread221499.html](http://www.notebookforums.com/thread221499.html)

I still can't figure this out.  Going to contact Intel.  If I get any information from them I will post it.

btw, ifconfig -a gives me this (isn't pan0 a IPv6 device?):

```
user@PCID075:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:174616 (174.6 KB)  TX bytes:174616 (174.6 KB)

pan0      Link encap:Ethernet  HWaddr 3e:bc:7b:12:8b:3a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by groverblue on 2008-10-22
Ok, Dell and Intel would not offer any support.

Instead, I decided to try a previous version of the driver, specifically 7.6.15.5. 

It worked.

You can get previous version here:
[http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835](http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835)

So, it looks like there is a problem with 8.0.6.

BTW, I'm running with kernel version 2.6.27-4-generic, from an install of 8.10 beta 64-bit (The official name is "64-bit PC (AMD64) desktop CD").

I hope this helps someone else out there.

---

