---
title: "BCM4310 Wireless Card Issues"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by robrown on 2008-06-15
I've followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

And also here (even tho it's not the same card, it's similiar):

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

And I'm no closer to being able to log onto my wireless network.  I can see the SSID but I can't connect after I enter my WPA password.  When I enter lshw -C network my wireless says module=wl, not module=ndiswrapper...

After posting about it in [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) Ayuthia gave me some pointers:

```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo depmod -ae
sudo modprobe wl
sudo ifconfig wlan0 up
sudo iwlist scan
```

And that didn't work either.  I'm running kernel 2.6.24.18-generic.  When I run the first line of code I get an error:  FATAL Module ssb is in use.

Please help, I'm so close, I know it!

---

### Post by Ayuthia on 2008-06-15
> **robrown said:**
> I've followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

And also here (even tho it's not the same card, it's similiar):

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

And I'm no closer to being able to log onto my wireless network.  I can see the SSID but I can't connect after I enter my WPA password.  When I enter lshw -C network my wireless says module=wl, not module=ndiswrapper...

After posting about it in [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) Ayuthia gave me some pointers:

```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo depmod -ae
sudo modprobe wl
sudo ifconfig wlan0 up
sudo iwlist scan
```

And that didn't work either.  I'm running kernel 2.6.24.18-generic.  When I run the first line of code I get an error:  FATAL Module ssb is in use.

Please help, I'm so close, I know it!

It sounds like you have another module that is using ssb.  Can you post the results of:
```
lsmod |grep ssb
lshw -C network
```
The first command will help us see what is using the ssb module.  The second command it to help confirm that we really need ssb or not.  From what I understand at this point is that b43 and the b44 drivers are currently using the ssb module.

---

### Post by robrown on 2008-06-15
> **Ayuthia said:**
> It sounds like you have another module that is using ssb.  Can you post the results of:
```
lsmod |grep ssb
lshw -C network
```
The first command will help us see what is using the ssb module.  The second command it to help confirm that we really need ssb or not.  From what I understand at this point is that b43 and the b44 drivers are currently using the ssb module.

Sure:

First command
```
ssb                    32260  1 b44
```

The second command shows some different info than it did before I installed the linux-restricted-modules:
```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: XXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

---

### Post by Ayuthia on 2008-06-15
> **robrown said:**
> Sure:

First command
```
ssb                    32260  1 b44
```

The second command shows some different info than it did before I installed the linux-restricted-modules:
```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: XXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

It looks like the b44 came from the guide because it does not look like you need it.  Try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo depmod -ae
sudo modprobe wl
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwlist scan
```

You might want to turn of encryption for now too so that we can make sure that it works first.

---

### Post by robrown on 2008-06-15
> **Ayuthia said:**
> It looks like the b44 came from the guide because it does not look like you need it.  Try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo depmod -ae
sudo modprobe wl
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwlist scan
```

You might want to turn of encryption for now too so that we can make sure that it works first.

Hey man, I'm so sorry, I forgot that I unchecked the box in System>Administration>Hardware Drivers, so that's why my lshw -C network looks different:

[code]
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:50:ab:4f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: XXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
[/code

Also, I was able to run every command until I got to 'sudo ifconfig wlan0 up' and I got 'wlan0: ERROR while getting interface flags: No such device'

This was after I checked the box mentioned above...no reboot...

---

### Post by Ayuthia on 2008-06-15
> **robrown said:**
> Hey man, I'm so sorry, I forgot that I unchecked the box in System>Administration>Hardware Drivers, so that's why my lshw -C network looks different:

```

  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: XXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
[/code

Also, I was able to run every command until I got to 'sudo ifconfig wlan0 up' and I got 'wlan0: ERROR while getting interface flags: No such device'

This was after I checked the box mentioned above...no reboot...

Ok.  Your logical name is eth1 instead of wlan0.  Please do the following:
[CODE]sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo depmod -ae
sudo modprobe wl
sudo ifconfig eth1 up
sudo dhclient -r eth1
sudo iwlist scan
```

---

### Post by robrown on 2008-06-16
I just read in one of those previous threads that someone tried Wicd and it worked.  Only problem is I can't connect with any encryption at all.  Tried WEP and WPA, I can only connect with it disabled.  Linksys router, wrtg54g, I just upgraded the firmware, same result.

---

### Post by Ayuthia on 2008-06-16
> **robrown said:**
> I just read in one of those previous threads that someone tried Wicd and it worked.  Only problem is I can't connect with any encryption at all.  Tried WEP and WPA, I can only connect with it disabled.  Linksys router, wrtg54g, I just upgraded the firmware, same result.
Is this with the ndiswrapper or the wl option?

Can you also post your lsmod info?

---

### Post by robrown on 2008-06-18
> **Ayuthia said:**
> Is this with the ndiswrapper or the wl option?

Can you also post your lsmod info?

This is using Wicd Manager.  I disabled the encryption and I can connect.  So I had the idea of filtering my wireless access by mac addy, set that up, and I can't connect.  Weird.  Also, now when I suspend my ubuntu, I get an error when I open the screen:

[504.311241] drm_sysfs_suspend
[1.607097] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp . 26).

While I was typing that my screen went blank and then the mouse showed up, so I touched the trackpad and it came out of suspend, so I don't know what that was all about.

lsmod:

Module                  Size  Used by
ipv6                  267780  10 
i915                   32512  2 
drm                    82580  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
vboxdrv                61360  1 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
sbshc                   7680  1 sbs
af_packet              23812  6 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
ieee80211_crypt_tkip    11648  0 
hci_usb                16540  2 
uvcvideo               58116  0 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
wl                   1062272  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
snd_hda_intel         344728  9 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
sky2                   47492  0 
snd_pcm                78596  4 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
video                  19856  0 
output                  4736  1 video
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
ricoh_mmc               4352  0 
sdhci                  19076  0 
serio_raw               7940  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_pcm,snd_seq
mmc_core               51460  1 sdhci
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi_acer                9644  0 
snd                    56996  25 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
battery                14212  0 
iTCO_wdt               13092  0 
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
ac                      6916  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
evdev                  13056  8 
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_piix               19588  3 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 ndiswrapper,hci_usb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3

---

### Post by Ayuthia on 2008-06-19
> **robrown said:**
> This is using Wicd Manager.  I disabled the encryption and I can connect.  So I had the idea of filtering my wireless access by mac addy, set that up, and I can't connect.  Weird.  Also, now when I suspend my ubuntu, I get an error when I open the screen:

[504.311241] drm_sysfs_suspend
[1.607097] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp . 26).

While I was typing that my screen went blank and then the mouse showed up, so I touched the trackpad and it came out of suspend, so I don't know what that was all about.

lsmod:

Module                  Size  Used by
wl                   1062272  0 
ndiswrapper,hci_usb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
I am not for sure if it has something to do with ndiswrapper or not.  I am seeing that the ndiswrapper module is there along with wl.  That could be causing the problem.  You might check lshw -C network to see which module it is trying to use.

---

### Post by robrown on 2008-06-19
It's using the wl driver still...  module=wl

---

### Post by Ayuthia on 2008-06-19
> **robrown said:**
> It's using the wl driver still...  module=wl

I don't know too much encryption.  I just know that people have been having issues with encryption lately and I cannot tell if it is a bug with the various network managers or something else.  You might try to see if you can do it manually via the thread in the stickies:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

