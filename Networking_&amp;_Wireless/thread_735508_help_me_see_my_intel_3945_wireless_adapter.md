---
title: "help me see my intel 3945 wireless adapter"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by extendedping on 2008-03-25
hi all, I just installed ubuntu 7.10 on a hp dv2050 laptop. I did a graphical install and just hit next.  I should first mention that my I got a bad dhcp address (from a subnet that could not reach the internet) so I did not get all the packages during install. after the install completed went into /etc/apt/sources.list and uncommented all the lines below the lines reading "commented out by installer because it failed to verify". I then fixed my ip address and got all the ubdates. now when I run lspci I see  lspci | grep 3945
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

but I from iwconfig I see only lo and eth0 no wireless extensions and only lo and eth0 from ifconfig.  so the actual device is seen as far as I can tell but there is no wireless device that I can configure.  I did read several threads and it seems that normally this abb 3945 just works out of the box...so...short of doing a new install which I really don't want to do .... any suggestions? thanks.

---

### Post by extendedping on 2008-03-25
also the device does show up in the restricted drivers menu (whatever that is) and has a check next to "in use".

---

### Post by which_chick on 2008-03-25
iwconfig only shows the interfaces that are currently up.  If your wireless isn't up yet, then it won't show up in iwconfig.  ("up" here means "installed" and not "connected and doing internet")

The fact that it shows up in lspci means that your linux can *see* the wireless card.  That's a great start towards getting it working.

Could  you please show the output of 

```
ifconfig -a
```

This will show *all* network interfaces, including ones that are currently *down*.  I'd like to see if your system even has the wireless in the existing interfaces.

Also, please paste the screen that you get from typing

```
cat /etc/network/interfaces
```

Thanks!

---

### Post by extendedping on 2008-03-25
brad@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D3:04:36:5A  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe04:365a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112636754 (107.4 MB)  TX bytes:3678165 (3.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1170 (1.1 KB)  TX bytes:1170 (1.1 KB)

brad@ubuntu:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.21
netmask 255.255.255.0
gateway 192.168.1.11

auto eth0

---

### Post by which_chick on 2008-03-25
Okay.  It's not got the wireless as-a-wireless-card anywhere in there. 

Let's try the stuff in the Wireless Troubleshooting:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Step 1:  Check for the device using 

```
lshw
```

(It shows up for you in lspci, but I didn't see where you tried lshw.  Try lshw -- I think it will work, but we're going by the steps, here.)

Step 2:  Device drivers.

Your card should be supported out of the box, but we'll check anyway.  Look at your lshw output for something that lists the card, in the pile of information after the card.  We're hoping it has the driver you are using.  Mine looks like this:

```
 *-network
                description: Wireless interface
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:1e:4c:29:eb:af
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes **driver=bcm43xx driverversion=2.6.22-14-generic **ip=192.168.254.2 latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

Yours will  probably look different, but the line we are interested in is bolded in mine.  I think this will be OK in yours, too, because the driver says "in use" in your Network manager.  However, I could be wrong.

Next, check that the driver (if there is one.  If there isn't one, post that and we'll look at it there.) gets loaded to talk to your kernel.

type 

```
lsmod
```

to see if the driver is loaded.  It should show up with the same name (if any) that you got under lshw.

Your iwconfig command though (the next step) fails miserably.

The directions say > ... run the command iwconfig. If you see out put like in the example in the command section then the driver is at least identifying the device as a wireless device to the kernel.

Your iwconfig output doesn't list the device at all, so the problem is pretty low-level.

---

### Post by extendedping on 2008-03-25
hmm not looking good is it? 

brad@ubuntu:~$ lshw | grep -i 3945
WARNING: you should run this program as super-user.
                product: PRO/Wireless 3945ABG Network Connection
                configuration: driver=ipw3945 latency=0 module=ipw3945
brad@ubuntu:~$ lshw | grep -i eth
WARNING: you should run this program as super-user.
                description: Ethernet interface
                logical name: eth0
                capabilities: bus_master cap_list ethernet physical
brad@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

brad@ubuntu:~$ lsmod
Module                  Size  Used by
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  2 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
dock                   10656  0 
button                  8976  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               48644  0 
sdhci                  18828  0 
ipw3945               119840  1 
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
mmc_core               28420  1 sdhci
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               8068  0 
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
ipv6                  273892  10 
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
sd_mod                 30336  3 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
e100                   37644  0 
mii                     6528  1 e100
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
brad@ubuntu:~$

---

### Post by which_chick on 2008-03-25
Okay.  It shows up in lshw, so that part is good.  Step 1, check.

Step 2:  check the drivers.  Your system *says* it is using the ipw3945 drivers.  From what I can find online, these are the drivers you should be using.

Step 3: check to see that the drivers are loaded (the lsmod command)
You have the drivers showing up as loaded.  

The next thing it says to do is to type the iwconfig (which we know doesn't turn up the wireless).

I'm starting to think this is a driver problem.  Where did you get the drivers and have you tried re-getting/reloading them?  (Like fresh ones, in case they got garbled or something during your install.)

---

### Post by extendedping on 2008-03-26
I just did the install using the entire disk ... and I reinstalled within the last hour fixing the original dhcp issuse so the install was smooth. so I have no idea why it doesn't work. I guess I could try getting the drivers off the internet but I was hoping to avoid that situation...in fact I am trying ubuntu because I got so tired of fedora flaking with wireless.  I just don't understand why the device seems to be there and for others it works but I can't see a eth1 or whatever the wireless is supposed to be called.

---

### Post by extendedping on 2008-03-26
is there any way to setup the interface manually? or if the driver shows as loaded with lsmod but I see no interface I'm...well you know what...

---

### Post by chili555 on 2008-03-26
Do you by any chance have the ethernet cable attached at the same time that you are trying to configure your wireless?> eth0 Link encap:Ethernet HWaddr 00:163:04:36:5A
inet addr:192.168.1.21 Bcast:192.168.1.255 Mask:255.255.255.0Network Manager will not activate wireless if ethernet is available.> Network Manager aims for Network Connectivity which "Just Works". The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.From [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Please detach the wire, reboot and run *iwconfig* and see if your wireless magically appears.

---

### Post by extendedping on 2008-03-26
> **chili555 said:**
> Do you by any chance have the ethernet cable attached at the same time that you are trying to configure your wireless?Network Manager will not activate wireless if ethernet is available.From [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Please detach the wire, reboot and run *iwconfig* and see if your wireless magically appears.

thanks no magic unfortunately...I would understand if I did not have the driver loaded and said to be active in the restricted devices.  the unplugged ethernet and reboot did not wield any results from the iwconfig.  :( 

does it matter that I did the install from within the graphical live cd? should I be doing a text install?

---

### Post by chili555 on 2008-03-27
> does it matter that I did the install from within the graphical live cd? should I be doing a text install?It doesn't matter at all.

I am a bit concerned that the 3945 doesn't have a logical name, ideally eth1. Could we please see:```
sudo lshw -C network
```You can skip the data associated with your ethernet interface. Thanks.

---

