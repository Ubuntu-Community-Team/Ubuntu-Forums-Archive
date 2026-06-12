---
title: "WPA not working"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Duree on 2007-06-15
I have a thinkpad T30 that I recently installed Fiesty on and am trying to get WPA to work.  It works under XP, so I know the wlan adapter supports it, but in linux, it will only do WEP.  When I go to NetworkManager and connect to another... the encryption options only show WEP.  The adapter is an Intel and uses prism 2.5.  I'm rather new to wireless under linux so any help would be great!

Thanks!

---

### Post by spd106 on 2007-06-16
I believe that your card should be capable of WPA with Network Manager. However, as this doesn't seem to work for you, consider using wpa_supplicant throught the /etc/network/interfaces file. Directions to doing this can be found in the Howto: Wireless Security - WPA etc sticky. [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by ugm6hr on 2007-06-16
> **Duree said:**
> I have a thinkpad T30 that I recently installed Fiesty on and am trying to get WPA to work.  It works under XP, so I know the wlan adapter supports it, but in linux, it will only do WEP.  When I go to NetworkManager and connect to another... the encryption options only show WEP.  The adapter is an Intel and uses prism 2.5.  I'm rather new to wireless under linux so any help would be great!

Thanks!

Simple thing to try - but have you ticked the "Enable Roaming" option in Manual Settings?  Post a screenshot of your wifi options page if you don't understand what I mean.

---

### Post by kevdog on 2007-06-16
WPA in Ubuntu is frankly a pain in the a$$.  What works for some, doesnt work for others.  Here is the simplest easiest version that worked for me (and a few other people whom Ive helped): [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Give it a shot.  You will know if it works for you in about 2 minutes.

---

### Post by jingba on 2007-06-18
kevdog,
I would be one of those people it hasn't worked for.  Of course, I haven't gone through all the threads yet...  I have a D-Link DWL-G122 B1.  I read through a bunch of threads before I could find one that actually enabled it.  It's a response by Floppyjoe in this thread: [http://ubuntuforums.org/showthread.php?t=398643&highlight=dwl-g122+b1]("http://ubuntuforums.org/showthread.php?t=398643&highlight=dwl-g122+b1").  Of course, it seems I always have to type in ```
sudo modprobe rt2500usb
``` for it to enable.  (Any quick way around that?)

I followed the thread you posted, but it doesn't seem to allow WPA for me.  Now, what I've been trying is to enable the D-Link wireless using the modprobe command, then left-clicking on the network icon in the top-right of the desktop and trying to select my network.  When I do that it gives me the following error:

> Error connecting to wireless network

The requested wireless network requires security capabilities unsupported by your hardware.

Now, I am apparently missing something.  Any ideas what that something might be?  Maybe my SSID is not configured correctly?  (Not sure how to do that, but I've been seeing other people mention it in some of their feedback on the page you listed.)   Am I missing some software or drivers?

I know it might be something rather simple, but this is literally my 5th or 6th day using ubuntu...

Thanks for all the assistant I have seen you give in the forums!

[COLOR="Blue"]This is added later:  when I select the option to connect to other wireless networks, I do not have a WPA option under wireless security.  I have WEP 128-bit passphrase, WEP 64/128-bit Hex, and WEP 64/128-bi ASCII.

I am using network-manager-gnome.  Should I be using something like kwlan?[/COLOR]

---

### Post by unisol on 2007-06-18
hey kevdog, i tried your way and feisty froze up on me. rt61 wireless,WRT54G wireless router on main pc.

---

### Post by Sailorcancer on 2007-06-18
Yeah, having the SAME problem.

---

### Post by kevdog on 2007-06-19
Sorry if the WPA trick didnt work.  Do you all have wpasupplicant package installed??

---

### Post by jingba on 2007-06-19
kevdog,
I typed in the apt-get commanod listed on the site.  It basiacally said that I had all of the package installed.  Looking in the synaptic package manager, it shows that it is installed.  Is there some other way to tell if all of the wpasupplicant package is installed?

---

### Post by Austin_KW on 2007-06-19
the ralink drivers do not support the wpa suppliciant so you cannot configure it for WPA using network manager. you need to configure wpa using the iwpriv interface (usually done in the /etc/network/interfaces)

For a pci rt2500 the following works;
auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid MyNetSSID"
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid MyNetSSID
    pre-up iwpriv ra0 set  WPAPSK="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
    pre-up iwconfig ra0 essid MyNetSSID

try adding this to your /etc/network/interfaces; replace ra0 with your interface name (rausb0?)


To get the rt2500usb driver to auto load try adding it to /etc/modules

---

### Post by unisol on 2007-06-19
hey Austin_KW, do you have to disable ra0  before you add these lines?

---

### Post by Austin_KW on 2007-06-19
Should not have to. this file is read when the interface is brought up. You may have to restart the interface after making the change
sudo ifdown ra0 && sudo ifup ra0  

After that it should init on boot and you only need to restart the interface if it loses connection.

---

### Post by jingba on 2007-06-19
> **Austin_KW said:**
> 
For a pci rt2500 the following works;
auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid MyNetSSID"
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid MyNetSSID
    pre-up iwpriv ra0 set  WPAPSK="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
    pre-up iwconfig ra0 essid MyNetSSID

try adding this to your /etc/network/interfaces; replace ra0 with your interface name (rausb0?)
To get the rt2500usb driver to auto load try adding it to /etc/modules

I tried this, but ubuntu would not start.  Actually, it would get to the login screen.  After I entered my usrname and pword, it would go to the background screen (minus the ubuntu splash) and hang.  After a few moments, an empty  white box would appear in the top left of the screen.  The system would stay that way.  The HD indicator would not flash.

I assume that is not usual?  I replaced ra0 with rausb0. Any thoughts on this?

---

### Post by Austin_KW on 2007-06-19
Should not cause a hang,
Possible driver conflict, what is the output of the following commands
lsusb
lsmod

also "ifconfig -a"

---

### Post by jingba on 2007-06-19
Here is that information:

From lsusb:
```
Bus 003 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 011: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

From lsmod:
```
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
ipv6                  268960  14 
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dock                   10268  0 
video                  16388  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
button                  8720  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
ndiswrapper           194608  0 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
joydev                 10816  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
usbhid                 26592  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
hid                    27392  1 usbhid
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
sis_agp                 9604  1 
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
serio_raw               7940  0 
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  1 sis_agp
i2c_sis96x              6532  0 
i2c_core               22656  2 i2c_ec,i2c_sis96x
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
pata_sis               14732  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  2 sbp2,libata
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
sis900                 24704  0 
mii                     6528  1 sis900
sis5513                14856  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

From ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:50:EB:04:6D:06  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:ebff:fe04:6d06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:723604 (706.6 KiB)  TX bytes:187336 (182.9 KiB)
          Interrupt:5 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4596 (4.4 KiB)  TX bytes:4596 (4.4 KiB)


```

All of that code is without using:
```
sudo modprobe rt2500usb
```

**Here is the code when I enable rt2500usb:**

From lsusb:
```
Bus 003 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 011: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```


From lsmod:
```
Module                  Size  Used by
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
rc80211_simple          6400  1 
rt2500usb              29696  0 
rt2x00lib              11904  1 rt2500usb
mac80211              175364  3 rc80211_simple,rt2500usb,rt2x00lib
cfg80211               22920  1 mac80211
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
ipv6                  268960  14 
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dock                   10268  0 
video                  16388  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
button                  8720  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
ndiswrapper           194608  0 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
joydev                 10816  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
usbhid                 26592  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
hid                    27392  1 usbhid
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
sis_agp                 9604  1 
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
serio_raw               7940  0 
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  1 sis_agp
i2c_sis96x              6532  0 
i2c_core               22656  2 i2c_ec,i2c_sis96x
af_packet              23816  6 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
pata_sis               14732  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  2 sbp2,libata
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 rt2500usb,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
sis900                 24704  0 
mii                     6528  1 sis900
sis5513                14856  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

From ifconf -a:
```
eth0      Link encap:Ethernet  HWaddr 00:50:EB:04:6D:06  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:ebff:fe04:6d06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1453570 (1.3 MiB)  TX bytes:211127 (206.1 KiB)
          Interrupt:5 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4596 (4.4 KiB)  TX bytes:4596 (4.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:93:2A:7C  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:5827 (5.6 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:13:46:93:2A:7C  
          inet addr:169.254.5.109  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-13-46-93-2A-7C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

When I tried the code that you provided earlier, rt2500usb was not enabled bacause I rebooted right after modifying the file.  The first list of data is probably what the system is seeing on boot.

Thanks for all the help with this.

---

### Post by Austin_KW on 2007-06-19
A couple of things, 
Seems to be two network drivers for the usb adapter (after you modprobe), rt2500usb and ndiswrapper for the windows driver
usbcore               134280  6 **rt2500usb,ndiswrapper**,usbhid,ehci_hcd,uhci_hcd

rt2500usb seems to bring up wlan0 (not rausb0)

I think that rt2500usb is a newer beta driver from serialmonkey.com, I dont think these drivers work, (not sure but the rt2500pci does not so I am guessing here). Either way the newer driver uses the supliciant for WPA noy iwpriv, but I dont think it works.

I need to look up "2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]" . I think it might be a rt2571 chipset but not sure.
EDIT; I meant rt2570

---

### Post by Austin_KW on 2007-06-19
I suggest that you try the older 'legacy driver from serialmonkey

download it with 
wget [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) 

#remove the current drivers 
sudo modprobe -r rt2500usb
sudo modprobe -r ndiswrapper

#blacklist them to stop from reloading
sudo bash -c "echo \"blacklist rt2500usb\" >>/etc/modprobe.d/blacklist"   
sudo bash -c "echo \"blacklist ndiswrapper\" >>/etc/modprobe.d/blacklist"   

#expand the downloaded archive
tar -xvzf  rt2570-cvs-daily.tar.gz 

# build & install the driver
cd rt2570*/Module
make
sudo make install

then reboot, then check ifconfig -a, I think the rt2570 driver uses rausb0 but they have changed some to wlan0. The config in the interfaces should work

---

