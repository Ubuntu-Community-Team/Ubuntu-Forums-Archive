---
title: "Goodnight wireless!"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by jwalker on 2007-04-01
Hi

Really hoping someone can help here:

I run Kbuntu on my laptop, after installing the ndiswrapper and knetwork manager I was happily wirelessing away, until...

One night I was researching into WEP security and packet sniffing, I didn't download or install anything (that I can remember), and the next morning I went to fire up the wireless and all of a sudden it can't see any networks.

I have tried a few things but to tell you the truth I am really mystified. I should able to see at least two networks, but I see nothing. 

Is there anything I can check, I'm sure the card is still there and the drivers are ok, but I cannot for the life of me see anything? 

Frustrating, I honestly don't know what happened :-( I hope some one can help!

Thanks!

Chris

---

### Post by jwalker on 2007-04-02
bump

:-( I sure hope someone can help me, this is the soft of weird stuff Linux throws at you and you end up backing your stuff up and reinstalling the whole OS because you don't know any better. 

If any body could suggest some procedures for troubleshooting this issue I would be extremely grateful. Thanks!

---

### Post by Floppyjoe on 2007-04-02
My laptop has buttons for the wifi on the front of it and if I am not careful when moving it around I sometimes deactivate my wireless because of that.

Your problem may not be that simple but who knows.

---

### Post by jwalker on 2007-04-02
Cheers mate

Sadly its a Dell, they don't have any buttons for turning the wireless on and off (like the HPs do). 

It is honestly the damnedest thing, one night fine, next day completely screwed. (Well, not completely, the hardware is still recognized by the OS, it's simply not transmitting or whateverthehell. 

I even went through my terminal command history but I really do not think I installed or downloaded any software to cause this issue. 

Are there any tests I can conduct. I don't know much by way of command line action when it comes to wireless, ifup/down, networking restart etc, that's about it...

---

### Post by Floppyjoe on 2007-04-02
For packet sniffing does the card have to be set into a different mode then usual?
Maybe it is still in the promiscuous mode and needs to be switched back to normal mode?
Unfortunately I don't know much about that.

---

### Post by dmizer on 2007-04-02
well, if it was working before ... we can likely make it work again.  let's get some useful information.

post the output of:
```
lspci
```
```
lsmod
```
```
ndiswrapper -l
```
```
ifconfig
```
```
iwconfig
```
and the contents of the file /etc/network/interfaces

---

### Post by jwalker on 2007-04-03
Nice! That's the spirit! I like the sound of that promiscuous mode thing, would make sense. Below are the outputs of the commands as requested, I am pretty n00b but they seem ok to me:

**lspci:**

> 
0:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)


**lsmod:**

> 
Module                  Size  Used by
nls_utf8                3200  1
nls_cp437               6912  1
vfat                   14720  1
fat                    56348  1 vfat
ipv6                  272288  8
vmnet                  41900  15
vmmon                 118380  5
binfmt_misc            13448  1
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  3
drm                    74644  4 radeon
speedstep_centrino      9760  1
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sony_acpi               6412  0
sbs                    16804  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0
dock                    8716  0
dev_acpi               12292  0
container               5632  0
button                  7952  0
battery                11652  0
asus_acpi              17688  0
ac                      6788  0
sg                     37404  0
sd_mod                 22656  2
af_packet              24584  4
ndiswrapper           208656  0
lp                     12964  0
snd_intel8x0           34844  1
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 40380  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
usb_storage            75072  1
scsi_mod              144648  3 sg,sd_mod,usb_storage
snd_seq_midi            9984  0
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           28812  4
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
tg3                   107652  0
joydev                 11200  0
tsdev                   9152  0
libusual               17040  1 usb_storage
usbhid                 45152  0
evdev                  11392  2
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                41352  0
parport_pc             37796  1
parport                39496  2 lp,parport_pc
pcspkr                  4352  0
intel_agp              26012  1
agpgart                34888  2 drm,intel_agp
serio_raw               8452  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  142728  1
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  7 ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0
ide_cd                 33696  1
cdrom                  38944  1 ide_cd
ide_disk               18560  3
piix                   11780  1
generic                 6276  0
thermal                15624  0
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability


**ndiswrapper -l:**

> 
Installed drivers:
bcmwl5          driver installed, hardware present


**ifconfig:**
> eth0      Link encap:Ethernet  HWaddr 00:0D:56:DF:AF:8F
          inet addr:129.223.99.92  Bcast:129.223.99.127  Mask:255.255.255.192
          inet6 addr: fe80::20d:56ff:fedf:af8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27847385 (26.5 MiB)  TX bytes:13281106 (12.6 MiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.252.1  Bcast:172.16.252.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.106.1  Bcast:192.168.106.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:71:F2:0E
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:fafee000-faff0000


**iwconfig:**
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.


**contents of the file /etc/network/interfaces**

> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Looking forward to hearing back and getting my awesome Ubuntu system going (lost a co-worker to Vista today). I'm gonna go look into this promiscuous mode business. 

Cheers!

---

### Post by dmizer on 2007-04-03
okay ... lets blacklist two modules:

edit /etc/modprobe.d/blacklist
```
gksudo gedit /etc/modprobe.d/blacklist
```
scroll all the way to the end and add these two lines:
```
blacklist ipv6
blacklist uhci_hcd
```
save the file, reboot, and see if you can get online with your wireless.

---

### Post by jwalker on 2007-04-03
Shiku-shiku! (:_;)

That's a negative good buddy. For the record, my /etc/modprobe.d/blacklist looks like this:

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
#module below does not work with Broadcom 4318 wireless cards
blacklist bcm43xx

blacklist ipv6
blacklist uhci_hcd


My promiscuous mode research hasn't turned up much, I am considering reinstalled the ndiswrapper...

---

### Post by sabi on 2007-04-03
> **jwalker said:**
> Hi

Really hoping someone can help here:

I run Kbuntu on my laptop, after installing the ndiswrapper and knetwork manager I was happily wirelessing away, until...

One night I was researching into WEP security and packet sniffing, I didn't download or install anything (that I can remember), and the next morning I went to fire up the wireless and all of a sudden it can't see any networks.

I have tried a few things but to tell you the truth I am really mystified. I should able to see at least two networks, but I see nothing. 

Is there anything I can check, I'm sure the card is still there and the drivers are ok, but I cannot for the life of me see anything? 

Frustrating, I honestly don't know what happened :-( I hope some one can help!

Thanks!

Chris

Did you perhaps perform a system update between when it was working and not?

Do you have an ethernet wired connection active?

Try the following command:

```
sudo modprobe ndiswrapper
```

Sabi...

---

### Post by dmizer on 2007-04-03
sabi:

if you look at the output of lsmod above, you can see that the ndiswrapper module is loaded and functioning for the card, so "sudo modprobe ndiswrapper" is not needed.

jwalker:

are you using feisty?  are you trying to connect to an encrypted network?

if not, try this:
```
sudo ifdown eth0&&sudo ifdown wlan0&&sudo ifup wlan0
```

---

### Post by jwalker on 2007-04-04
> **sabi said:**
> Did you perhaps perform a system update between when it was working and not?

Do you have an ethernet wired connection active?

Try the following command:

```
sudo modprobe ndiswrapper
```

Sabi...

Hi

No, one of the reasons I like kubuntu so much is because it doesn't constantly get in my face about updates. So, no, no updates are part of the picture. 

Your suggestion gives no results at the command prompt. No feedback whatsoever. Anything else?

Two other things I might mention, knetworkmanager seems fine, and if I manually connect to my Access Point by entering it SSID, it makes some progress but eventually falls over (gives up).

---

### Post by jwalker on 2007-04-04
> **dmizer said:**
> sabi:

if you look at the output of lsmod above, you can see that the ndiswrapper module is loaded and functioning for the card, so "sudo modprobe ndiswrapper" is not needed.

jwalker:

are you using feisty?  are you trying to connect to an encrypted network?

if not, try this:
```
sudo ifdown eth0&&sudo ifdown wlan0&&sudo ifup wlan0
```

I'm running Edgy, the network is WAP secured but that's it. When I try your suggested command (similar to my fave 'networking restart') it goes through the motions, then DHCPDISCOVERs on wlan0 to 255.255.255.255 on port 67 with various intervals, then gives up, No DHCPOFFERS recieved. Sorry can't post the out put as I'm using another computer. 
 

I figure as long as it can't see networks that are there, connecting ain't its issue, making it aware of its surrounding is. 

The only thing I was playing with was xmame and mamory, things that have nothing to do with wireless. 

Is there a command to reinitialize the ndiswrapper, perhaps reset some settings that may have been tampered with?

Thanks

Chris

---

### Post by hoopsta1423 on 2007-04-04
this is the same problem i have, only i have the broadcom 4318, i am able to scan with iwlist but cannot for the life of me connect to any network, encrypted or not. I have tried everything to no avail.

you may want to try using bcmwl5a.inf with ndiswrapper, that might make a difference

---

### Post by dmizer on 2007-04-04
let's add a few options to interfaces.  we'll have to edit it again:
```
gksudo gedit /etc/network/interfaces
```

for this section:
```
auto wlan0
iface wlan0 inet dhcp
```

add both your essid and your wep key like so:
```
auto wlan0
iface wlan0 inet dhcp
    wireless-essid YOUR_ESSID
    key XXXX-XXXX-XXXX-XXXX
```
where "XXXX-XXXX-XXXX-XXXX" is your wep key in hex format.  sorry, no passphrase support for this method.

---

