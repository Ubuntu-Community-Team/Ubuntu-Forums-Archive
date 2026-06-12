---
title: "Wired Internet Connection not working"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by unca.paka on 2008-08-03
Hello all,
I've installed Hardy, and everything went ok, till about 5 day in, my wired internet connection stopped working(Qwest DSL w/2WIRE 2701HG-D router).

I'm dual-booting, and the net connection works fine w/XP.

After searching for a while, I came across some posts([http://ubuntuforums.org/showthread.php?t=812528&highlight=wired+network+connection+dropping](http://ubuntuforums.org/showthread.php?t=812528&highlight=wired+network+connection+dropping)) that suggested I install WicD, disable IPv6, and use the OpenDNS servers.

After doing all that, the connection worked fine for 12-14hrs. Until today, when it dropped again.

Using WicD, I can disconnect/reconnect and get an ip address, but all internet connectivity continues to not work. Changing the external apps that WicD uses had no effect, and eth0 is not configurable.

My room-mate got back from vacation today, and is connecting through the router wirelessly, not sure if that has anything to do with the problem, just an observation.

Any ideas/suggestions?

---

### Post by montgoss on 2008-08-03
Try the following commands:
```
sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by unca.paka on 2008-08-03
And it worked, posting this in Ubuntu right now. Thanks so much.

Any ideas on what could cause a problem like this?

---

### Post by montgoss on 2008-08-03
That's just a band-aid.  I'm betting you'll have the exact same problems after rebooting.  I don't have a permanent fix.  I'm still looking hoping someone can help me with a fix that lasts more than one session.  But at least this makes debugging easier since you can get to the forums on the troubled PC.

---

### Post by unca.paka on 2008-08-04
So here it is. Back from a night on the town, to find I have no net connection in hardy(again...)

Restart the machine, and connection is back for about 20min.
Reset the nic, try to get something out of DHCP, and nothing.

Heres some output, in case anyone is interested.
**DHCP INFO**
> 
moff@EVA-01:~$ sudo dhclient -r eth0
[sudo] password for moff: 
There is already a pid file /var/run/dhclient.pid with pid 6130
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:66:1d:15:37
Sending on   LPF/eth0/00:19:66:1d:15:37
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67

moff@EVA-01:~$ sudo ifconfig eth0 down
moff@EVA-01:~$ sudo ifconfig eth0 up
moff@EVA-01:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:19:66:1d:15:37
Sending on   LPF/eth0/00:19:66:1d:15:37
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

**LSHW**
> 
moff@EVA-01:~$ sudo lshw -C network *-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: 01
serial: 00:19:66:1d:15:37
size: 1GB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=yes 
module=r8169 multicast=yes port=twisted pair speed=1GB/s

**LSMOD**
> 
moff@EVA-01:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc            12808  1 
af_packet              23812  4 
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
ac                      6916  0 
lp                     12324  0 
snd_hda_intel         344728  3 
snd_hwdep              10500  1 snd_hda_intel
snd_pcm_oss            42144  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
usblp                  15872  0 
snd_mixer_oss          17920  1 snd_pcm_oss
nvidia               7105956  28 
i2c_core               24832  1 nvidia
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
psmouse                40336  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irtty_sir               9728  0 


snd                    56996  17 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sir_dev                17412  1 irtty_sir
button                  9232  0 
intel_agp              25492  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
irda                  203068  2 irtty_sir,sir_dev
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
evdev                  13056  3 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
crc_ccitt               3072  1 irda
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  5 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
ata_piix               19588  3 
floppy                 59588  0 
ata_generic             8324  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
r8169                  32900  0 
usbcore               146028  4 usblp,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 


Sorry for the wall o` text, but as far as I can tell, everything is on the up & up. Please, tell me if I'm wrong.

And again, thanks for all the help.

---

### Post by montgoss on 2008-08-04
To me, that looks like a problem with your router.  It's not offering you an IP address.  Does it work with other computers?  Reboot your router and try again.

---

### Post by unca.paka on 2008-08-04
Yeah, the router is serving up IP's to 3 machines, 2 XP, and 1 Vista. Just seems to be dropping the connection when I boot into linux. Tried resetting my router, and again, works for about an hour tops.

[B]After some playing around, it looks like it is my router causing the problem. Connection works fine after rebooting the machine, then drops 5-10min later. Rebooting the router still has no effect. 

Checked the router settings, and everything seems alright(DHCP enabled, and working on windows machines). Firewall settings seem fine(nothing getting blocked that shouldn't be).

Strange thing is, everything worked fine for about a week, then one day, poof, connection gone.[/B]

**UPDATE:**
After some checking, I threw the OpenDNS servers into my routers config, and everything seems to be working. I can renew IP's, and have been connected for an hour now. Lets see if it keeps tickin'

---

### Post by unca.paka on 2008-08-05
Alright, after having a working internet connection for about 4hrs, it decided to drop again. I've scoured the web looking for any solution I could find, and pretty much came up practically empty.

A few suggestions I could find were install some new drivers for my on-board nic(no help) turn off wake-on lan settings(not even close) reset my router settings to default(nope) completely disable IPv6(worth a try) and nothing has worked so far.

The laughable part of it is, all the windows machines never got even a hickup in connectivity while this was going on...

So me thinks its time to try a fresh ubuntu install. Gonna save it for the morning, so any suggestions would still be helpful at this point.

---

### Post by NTolerance on 2008-08-06
> **unca.paka said:**
> Alright, after having a working internet connection for about 4hrs, it decided to drop again. I've scoured the web looking for any solution I could find, and pretty much came up practically empty.

A few suggestions I could find were install some new drivers for my on-board nic(no help) turn off wake-on lan settings(not even close) reset my router settings to default(nope) completely disable IPv6(worth a try) and nothing has worked so far.

The laughable part of it is, all the windows machines never got even a hickup in connectivity while this was going on...

So me thinks its time to try a fresh ubuntu install. Gonna save it for the morning, so any suggestions would still be helpful at this point.

Hopefully you haven't started to reformat because I had the same issue as you and found a fix in a new DEB driver posted at the bottom of this Launchpad report:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212497](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212497)

I have the same PCI-E gigabit ethernet adapter and had the same problem.  The adapter is available but won't get an IP.  The only issue with the DEB driver is that kernel updates might break it.  I've yet to find out if that's going to happen or not.

---

### Post by unca.paka on 2008-08-06
Thanks for the info, I'll give it a try when i get home from work. From the sounds of it, it just might work.

---

### Post by unca.paka on 2008-08-10
Sorry it took so long, family emergency a few hundred miles away...

Anyway, it works. After installing the 8168 drivers, everything is just peachy. Thanks for the help.

---

### Post by Joor on 2008-08-10
Got the same problem , no internet in 8.0.4
Where can do I download the R8168 driver and how do I install ?

---

### Post by NTolerance on 2008-08-11
> **Joor said:**
> Got the same problem , no internet in 8.0.4
Where can do I download the R8168 driver and how do I install ?

[http://ubuntuforums.org/showpost.php?p=5535638&postcount=9](http://ubuntuforums.org/showpost.php?p=5535638&postcount=9)

Download and double click the DEB file.

---

### Post by Joor on 2008-08-12
After installing the R8168 driver and reboot , there is still no connection to the internet.
I wonder if its fine just to use 7.10 until 8.10 is available ?

---

