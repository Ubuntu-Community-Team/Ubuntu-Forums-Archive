---
title: "Help, Can't connect or see my wireless network!"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Darconix on 2007-04-21
Ok i have just started using ubunut 2 weeks ago and i have to say I LOVE IT! :) 
I started with Ubuntu 6.10 and my wireless was fine and manualy connected fairly easily
but when i upgraded to Ubuntu 7.04 Feisty Fawn i can't see any wireless networks
i have a belkin 54g USB wireless adapter. What concerns me is that there is 2 wireless networks
wlan0 and wmaster0
i tried manual configuring it but no luck
does enyone know whats wrong? :confused:

---

### Post by Austin_KW on 2007-04-21
Which version of the belkin is it

In a terminal get the ID with "lsusb"

---

### Post by Darconix on 2007-04-22
Bus 002 Device 003: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
that is what i get, along with my other hardware

---

### Post by Darconix on 2007-04-22
hello? o.o

---

### Post by Austin_KW on 2007-04-22
The versions I have are 2000 & 3000 so not sure if I can be much help. I think v1000 is the prism chipset.  What drivers are running, post the output from "lsmod" and " lshw -C net"

Also I think that feisty has a new network-manager. I know that this conflicts with the the later versions of the belkin but these are a different chipset. However it may be worth uninstalling the network-manager and manually configuring or configuring via the /etc/network/interfaces file. You can always re-install if it does not help.

---

### Post by Darconix on 2007-04-22
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
sg                     36252  0 
sd_mod                 23428  2 
usb_storage            72256  1 
libusual               17936  1 usb_storage
isofs                  36284  1 
udf                    85252  0 
ipv6                  268704  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
powernow_k8            16064  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
af_packet              23816  2 
lp                     12452  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
rc80211_simple          6400  1 
rt2570                186432  0 
prism54usb             16896  0 
prism54common          12288  1 prism54usb
snd_intel8x0           34204  3 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
analog                 12832  0 
rt73usb                33536  0 
rt2x00lib              11904  1 rt73usb
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
mac80211              175364  5 rc80211_simple,prism54usb,prism54common,rt73usb,rt2x00lib
gameport               16520  1 analog
nvidia               6837140  32 
cfg80211               22920  1 mac80211
psmouse                38920  0 
snd_mpu401              9256  0 
snd_mpu401_uart         9472  1 snd_mpu401
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
agpgart                35400  1 nvidia
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
crc_itu_t               3072  1 rt73usb
serio_raw               7940  0 
k8temp                  6656  0 
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_nforce2             6784  0 
i2c_core               22784  3 i2c_ec,nvidia,i2c_nforce2
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
usbhid                 26592  0 
hid                    27392  1 usbhid
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
sata_nv                20868  0 
ata_generic             9092  0 
libata                125720  2 sata_nv,ata_generic
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
amd74xx                15260  0 [permanent]
forcedeth              46728  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  9 usb_storage,libusual,rt2570,prism54usb,rt73usb,usbhid,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

for lsmod

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:8b:02:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

for lshw -C net
i tried doin it from the interfaces file b4 but no luck either
and i tired reinstalling it also hmmm

---

### Post by Austin_KW on 2007-04-22
There is a bunch of drivers here that I did not expect to see loaded:
rt2570 186432 0  <- this is the driver for version 2000
rt73usb 33536 0  < this is a driver for version 3000 

prism54usb 16896 0 <- I THINK this is the dirver for your V1000, but I am not sure it is working


Try blacklisting rt2570 & rt73usb by adding them to the driver blacklist

gksudo gedit /etc/modprobe.d/blacklist
and add to the file:
  blacklist rt2570
  blacklist rt73usb

Save and reboot,

---

### Post by lrmulli on 2007-04-22
Just wanna say thanks guys as this has just helped me get back online.

I had the same problem as above, 

So I did what Austin_KW suggested

but that failed so I changed it slightly because i was pretty sure that my device was not a priism54usb

This is my device : -

Bus 003 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

So this is what I did

gksudo gedit /etc/modprobe.d/blacklist
and add to the file:
blacklist prism54usb
blacklist rt73usb

Save and reboot,

And then the connection worked,

Now only one last thing to solve im sure its trivial but can anybody tell me with the current setup is there anyway i can the usb dongle to connect at boot?

Because currently, im booting then typing sudo ifup rausb0


????

---

### Post by Austin_KW on 2007-04-22
Edit your /etc/network/interfaces so rausb0 comes up automatically

#For Wep With dhcp
auto rausb0
iface rausb0 inet dhcp
    pre-up ifconfig rausb0 up
    pre-up iwconfig rausb0 essid YourNetworkNameHere
    pre-up iwconfig rausb0 key YourWepKeyHere 



#Or for WPA-PSK with dhcp
auto rausb0
iface rausb0 inet dhcp
    pre-up ifconfig rausb0 up
    pre-up iwconfig rausb0 mode managed
    pre-up iwconfig rausb0 essid YourNetworkNameHere
    pre-up iwpriv rausb0 set EncrypType=TKIP
    pre-up iwpriv rausb0 set AuthMode=WPAPSK
    pre-up iwconfig rausb0 essid YourNetworkNameHere
    pre-up iwpriv rausb0 set  WPAPSK="YourPreSharredKeyHere"
    pre-up iwconfig rausb0 essid YourNetworkNameHere

---

### Post by Austin_KW on 2007-04-22
There should be a small sticker on the usb dongle, what version does it show. It is possible that belkin have not been updating the IDs which would explain why all the drivers are loading.

---

### Post by Darconix on 2007-04-23
> **lrmulli said:**
> Just wanna say thanks guys as this has just helped me get back online.

I had the same problem as above, 

So I did what Austin_KW suggested

but that failed so I changed it slightly because i was pretty sure that my device was not a priism54usb

This is my device : -

Bus 003 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

So this is what I did

gksudo gedit /etc/modprobe.d/blacklist
and add to the file:
blacklist prism54usb
blacklist rt73usb

Save and reboot,

And then the connection worked,

Now only one last thing to solve im sure its trivial but can anybody tell me with the current setup is there anyway i can the usb dongle to connect at boot?

Because currently, im booting then typing sudo ifup rausb0


????

thank you sooooo much you guys! im back on internet. without that long cord coming from my downstairs living room all the way upstairs to my pc :lolflag: 
thankyou Austin_KW very much!

---

### Post by Darconix on 2007-05-15
> **Darconix said:**
> thank you sooooo much you guys! im back on internet. without that long cord coming from my downstairs living room all the way upstairs to my pc :lolflag: 
thankyou Austin_KW very much!

sorry guys but due to my HDD blowing a pin i had to buy a new on and reinstall ubuntu
OK now im having the same trouble but when i tried doing all the things i did last time it still didnt work :mad: :mad: :mad: :mad: 
i configed everything but it still not seeing the outside world:confused:

---

