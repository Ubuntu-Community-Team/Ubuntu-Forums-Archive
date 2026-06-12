---
title: "Dell Wireless 1470 causing me lots of trouble"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by spudgunner on 2008-03-30
First off, I have an Inspiron 1300 with a Dell 1470 Dual-Band Mini-PCI wireless card in it...

So I've repeatedly uninstalled and reinstalled Ubuntu, trying different things to get things to work. I've followed different sets of instructions presented in this thread:

[http://ubuntuforums.org/showthread.php?t=284584](http://ubuntuforums.org/showthread.php?t=284584)

and this thread:

[http://ubuntuforums.org/showthread.php?t=211283](http://ubuntuforums.org/showthread.php?t=211283)

And nothing I've done has got it to work. It doesn't even show up as a network device, none of the outputs are what either of these two threads say they should be... so I'm gonna start from scratch, fresh copy of Ubuntu and ndiswrapper (any my driver), willing to accept any instructions, even try repeat instructions from these two threads and post the output and answer questions about my system.

What it really comes down to is, this wireless issue is basically the only thing preventing me from using Ubuntu as an OS for good (instead of crappy Windows).

Come one and all, please help me, I really really need...
(and if you actually have a Dell Inspiron 1300 with working wireless, that'd be super awesome).

Thanks people,
Josh

---

### Post by dmizer on 2008-03-31
just to be sure, let's find out what chipset you're using (looks like it's probably broadcom).  please post the output of:
```
lspci
```

a bit more information about your current settings:
```
sudo ifconfig$$iwconfig
```

---

### Post by spudgunner on 2008-03-31
As a side note [may be a stupid question]... how do you get the boxes around your code in yours posts... would make me outputs  to your questions a bit easier to read

---

### Post by spudgunner on 2008-03-31
Here's my outputs to the commands you wanted (the ifconfig$$iwconfig didn't want to work for some reason, so I just did them separately... I hope the output is the same)

```
joshua@joshua-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

joshua@joshua-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:aa:ba:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100184 (97.8 KB)  TX bytes:100184 (97.8 KB)

joshua@joshua-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And don't worry about the fancy code boxes, I figured it out... ahaha I feel kinda stupid for that one... but anywho, onto figuring stuff out

---

### Post by dmizer on 2008-03-31
okay ... try the output of:
```
sudo iwlist wlan0 scan
```

are you using any kind of encryption like wep or wpa?

---

### Post by spudgunner on 2008-03-31
Here's what it gave me:

```
joshua@joshua-laptop:~$ sudo iwlist wlan0 scan

[sudo] password for joshua: 

wlan0     Interface doesn't support scanning : Network is down
```

I'm usually on a network that uses WPA Personal, but now I'm at my school, which doesn't use encryption like that (they use Cisco Systems to authenticate on a server) - I'm currently plugged into a hardwire at school.

Note: I just unplugged the hardline and tried it, same thing.

---

### Post by dmizer on 2008-04-01
okay ... let's see what's currently driving your card:

```
lsmod
```

and for good measure, let's see if you have ndiswrapper configured correctly:
```
ndiswrapper -l
```

---

### Post by spudgunner on 2008-04-01
So apparently I forgot to install ndiswrapper... thats my bad... sorry if this screws with your analysis a bit. Here's what happened:

```
joshua@joshua-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  267780  8 
i915                   32128  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5504  0 
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   118176  0 
rfkill                  8592  11 rfkill_input,b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_hda_intel         344088  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
video                  20112  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
evdev                  13056  16 
dcdbas                  9504  0 
serio_raw               7940  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
psmouse                40336  0 
snd_rawmidi            25760  1 snd_seq_midi
button                  9232  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
battery                14212  0 
ac                      6916  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
loop                   18948  2 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  2 
pata_acpi               8320  0 
b44                    28432  0 
ata_piix               19588  1 
ata_generic             8324  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ssb                    32772  2 b43,b44
mii                     6400  1 b44
ehci_hcd               37516  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
joshua@joshua-laptop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
```

---

### Post by dmizer on 2008-04-01
well, in your first post you included links to two tutorials, both of which make use of ndiswrapper.  so if you don't have it installed, you should take a look at the howto again.

specifically these instructions listed in the [second link](http://ubuntuforums.org/showpost.php?p=1725395&postcount=3):
> add 'blacklist bcm43xx' to /etc/modprobe.d/blacklist
This is because it was using the broad com 43xx driver and it was not working for my card.

I then installed ndiswrapper,
apt-get install ndiswrapper-utils

Next I downloaded the windows driver from dell.
unziped the exe and installed the driver with this command
'ndiswrapper -i bcmwl5.inf'

checked that it was installed properly.
ndiswrapper -l

which should display the following if correctly installed.
Installed drivers:
bcmwl5 driver installed, hardware present

then I ran ndiswrapper -m

I rebooted so it was using the correct driver.
The card should show up as wlan0 if it worked correctly.

for more verbose directions, try this: [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by spudgunner on 2008-04-01
No, you don't understand... I went through them with ndiswrapper installed... after failing multiple times, I reinstalled Ubuntu so everything would be clean and I can get help with it.

Sorry for the confusion.

---

### Post by dmizer on 2008-04-01
no worries about the confusion.

try the howto i linked above.  if you run into trouble with it, post and i'll try to give you a hand.  either way, you definitely need ndiswrapper for this card.

---

### Post by spudgunner on 2008-04-03
Now I have some new problems... with the command to get ndiswrapper, this is what I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils
```

which always happened anyways, so the other times I downloaded it from the Add/Remove programs menu (using a wired connection at school), however, when I try to download it, I get error 111: Connection refused

I'm gonna trying... possibly uninstall/reinstall Ubuntu again try it... I'll keep you posted.
In the meantime, if you have any ideas of how to work around my getting ndiswrapper problem, let me know.

---

### Post by dmizer on 2008-04-03
what version of ubuntu are you using?

no need to keep reinstalling.  that's the windows way of fixing things.

---

### Post by spudgunner on 2008-04-06
I installed it using those instructions, although I haven't tested it yet... I will test it later tonight.
In the meantime, here is the output to all that:

```
joshua@joshua-laptop:~$ ndiswrapper -i /host/home/joshua/R115321/DRIVER/bcmwl5.inf

couldn't create /etc/ndiswrapper/bcmwl5: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.

joshua@joshua-laptop:~$ sudo ndiswrapper -i /home/joshua/R115321/DRIVER/bcmwl5.inf

[sudo] password for joshua: 

installing bcmwl5 ...

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

joshua@joshua-laptop:~$ ndiswrapper -l

bcmwl5 : driver installed

	device (14E4:4319) present (alternate driver: bcm43xx)

joshua@joshua-laptop:~$ ndiswrapper -m

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

sh: cannot create /etc/modprobe.d/ndiswrapper: Permission denied

couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 882.

joshua@joshua-laptop:~$ sudo ndiswrapper -m

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...



************************************************************************

*

* The update-modules command is deprecated and should not be used!

*

************************************************************************]
```

I had already re-installed it before I got the message, sorry.
I am using Hardy Heron... and although I'm sure I read somewhere around here not the post about Hardy problems, this problem has persisted with each and every release of Ubuntu. After learning a little programming in school and with summer coming up (being a good time to get things working) I figured I might as well get it all done now.
And FYI: bcm43xx is already blacklisted in this release, so I didn't need to do that step.

Give me a few hours and I'll let you know on the status of connecting to the wireless.

---

### Post by spudgunner on 2008-04-06
So I've finally got to test out the wireless...another fail... here's the outputs to a bunch of commands you requested earlier, with ndiswrapper and the driver installed:

```
joshua@joshua-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:aa:ba:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79200 (77.3 KB)  TX bytes:79200 (77.3 KB)

joshua@joshua-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joshua@joshua-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

joshua@joshua-laptop:~$ lsmod
Module                  Size  Used by
af_packet              23812  0 
ipv6                  267780  8 
usbhid                 31872  0 
hid                    38784  1 usbhid
i915                   32128  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5504  0 
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   118176  0 
rfkill                  8592  57 rfkill_input,b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_hda_intel         344088  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
video                  20112  0 
output                  4736  1 video
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               7940  0 
button                  9232  0 
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
dcdbas                  9504  0 
soundcore               8800  1 snd
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  29 
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
loop                   18948  2 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  2 
pata_acpi               8320  0 
b44                    28432  0 
ata_piix               19588  1 
ata_generic             8324  0 
ssb                    32772  2 b43,b44
mii                     6400  1 b44
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37516  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
joshua@joshua-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4319) present (alternate driver: bcm43xx)

```

I'd also like to note that upon shutting down, this message keeps popping up (and it was damn hard to get, I had to record it with my roomie's digital camera and watch it over and over again 'till I found the place to pause it):

```
[357.004792] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[357.004888] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download correct firmware (version 4).
```

I'm hoping this will give you a little more information figure out what's going on.

Again, thanks for your willingness to help.

---

### Post by dmizer on 2008-04-06
for future reference, all messages appearing in startup and shutdown (as well as many others) can be viewed at your leisure in /var/log

please post the output of:
```
cat /etc/modprobe.d/blacklist | grep bcm43xx
```

because it looks like the bcm43xx driver is loading anyway, and ndiswrapper is not driving your card yet.

also post the output of
```
cat /etc/modules
```

---

### Post by spudgunner on 2008-04-07
Thanks for that tip... now I feel stupid for having laboured so hard hahaha... oh well.
Here's the outputs you wanted:

```
joshua@joshua-laptop:~$ cat /etc/modprobe.d/blacklist | grep bcm43xx
blacklist bcm43xx
joshua@joshua-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```

---

### Post by dmizer on 2008-04-07
well, lets add some more modules to the blacklist:

add these lines:
```
blacklist b43
blacklist rfkill_input
blacklist mac80211
```
to /etc/modprobe.d/blacklist

then edit (with sudo) /etc/modules and add the line:
```
ndiswrapper
```

reboot and see if you have any luck with wireless then.

---

### Post by spudgunner on 2008-04-07
It seems to have gotten worse (although the status of ndiswrapper is still the same)...

```
joshua@joshua-laptop:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

joshua@joshua-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

joshua@joshua-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4319) present (alternate driver: bcm43xx)
```

wlan0 seems to have disappeared, it doesn't show up with network manager anymore... unless this was supposed to happen.

To be fair, there aren't any messages complaining about it on the shutdown anymore either.

And its still not picking up my network

---

### Post by dmizer on 2008-04-07
try the output from this command:
```
lsmod | grep ndiswrapper
```

if nothing is returned try this:
```
sudo modprobe -v ndiswrapper
```

---

### Post by spudgunner on 2008-04-07
The first code returned something, so I didn't bother with the second, like you said (unless I mistook what you said). Here's the output:

```
joshua@joshua-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
```

I hope it helps

---

### Post by dmizer on 2008-04-07
okay ... let's take a look at what you have now.

1) we know that the driver is loaded correctly in to ndiswrapper
2) we know that ndiswrapper is loaded into the modules list (it wasn't before).

let's take one more look at **lsmod** to see if there are any other modules potentially interfering with the card's function.  also take a look at the output of: **ifconfig**

---

### Post by spudgunner on 2008-04-07
Man, you are one smart cookie... I have no idea what 99.9% of this stuff is anymore hahaha...

Here's the output you wanted:

```
joshua@joshua-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  267780  8 
i915                   32128  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         344088  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
serio_raw               7940  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
video                  20112  0 
output                  4736  1 video
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  7 
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
loop                   18948  2 
sg                     36880  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  2 
pata_acpi               8320  0 
b44                    28432  0 
ata_piix               19588  1 
ata_generic             8324  0 
ssb                    32772  1 b44
mii                     6400  1 b44
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37516  0 
uhci_hcd               27024  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
joshua@joshua-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:aa:ba:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:220800 (215.6 KB)  TX bytes:220800 (215.6 KB)
```

---

### Post by kevdog on 2008-04-07
Why dont you check dmesg to see if any errors occurred when loading the ndiswrapper module into the kernel.

---

### Post by spudgunner on 2008-04-07
Will do... tomorrow though... I'm tired.

I looked at your Ndiswrapper Help page, seems pretty solid... although I'm gonna stick to following dmizer for now... but if he gets stuck, I'll start over with your Ndiswrapper help.

---

### Post by kevdog on 2008-04-07
dmizer taught me a lot of things too!:)

---

### Post by spudgunner on 2008-04-08
Here's the output to the dmesg:

```
Script started on Tue 08 Apr 2008 11:16:26 AM NDT
joshua@joshua-laptop:~$ dmesg

[    0.000000] Linux version 2.6.24-12-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu4)) #1 SMP Wed Mar 12 23:01:54 UTC 2008 (Ubuntu 2.6.24-12.22-generic)

[    0.000000] BIOS-provided physical RAM map:

[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)

[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)

[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7d3800 (usable)

[    0.000000]  BIOS-e820: 000000001f7d3800 - 0000000020000000 (reserved)

[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)

[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)

[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)

[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)

[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)

[    0.000000] 0MB HIGHMEM available.

[    0.000000] 503MB LOWMEM available.

[    0.000000] Entering add_active_range(0, 0, 128979) 0 entries of 256 used

[    0.000000] Zone PFN ranges:

[    0.000000]   DMA             0 ->     4096

[    0.000000]   Normal       4096 ->   128979

[    0.000000]   HighMem    128979 ->   128979

[    0.000000] Movable zone start PFN for each node

[    0.000000] early_node_map[1] active PFN ranges

[    0.000000]     0:        0 ->   128979

[    0.000000] On node 0 totalpages: 128979

[    0.000000]   DMA zone: 32 pages used for memmap

[    0.000000]   DMA zone: 0 pages reserved

[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

[    0.000000]   Normal zone: 975 pages used for memmap

[    0.000000]   Normal zone: 123908 pages, LIFO batch:31

[    0.000000]   HighMem zone: 0 pages used for memmap

[    0.000000]   Movable zone: 0 pages used for memmap

[    0.000000] DMI 2.3 present.

[    0.000000] ACPI: RSDP signature @ 0xC00FC970 checksum 0

[    0.000000] ACPI: RSDP 000FC970, 0014 (r0 DELL  )

[    0.000000] ACPI: RSDT 1F7D4425, 0038 (r1 DELL    D05     27D60318 ASL        61)

[    0.000000] ACPI: FACP 1F7D4C00, 0074 (r1 DELL    D05     27D60318 ASL        61)

[    0.000000] ACPI: DSDT 1F7D5800, 324F (r1 INT430 SYSFexxx     1001 MSFT  100000E)

[    0.000000] ACPI: FACS 1F7E4000, 0040

[    0.000000] ACPI: APIC 1F7D5400, 0068 (r1 DELL    D05     27D60318 ASL        47)

[    0.000000] ACPI: MCFG 1F7D53C0, 003E (r16 DELL    D05     27D60318 ASL        61)

[    0.000000] ACPI: SSDT 1F7D4658, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)

[    0.000000] ACPI: SSDT 1F7D445D, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)

[    0.000000] ACPI: PM-Timer IO Port: 0x1008

[    0.000000] ACPI: Local APIC address 0xfee00000

[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

[    0.000000] Processor #0 6:13 APIC version 20

[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])

[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])

[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

[    0.000000] ACPI: IRQ0 used by override.

[    0.000000] ACPI: IRQ2 used by override.

[    0.000000] ACPI: IRQ9 used by override.

[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs

[    0.000000] Using ACPI (MADT) for SMP configuration information

[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)

[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000

[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000

[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127972

[    0.000000] Kernel command line: root=UUID=6830DD9430DD6A18 loop=/ubuntu/disks/root.disk ro quiet splash

[    0.000000] mapped APIC to ffffb000 (fee00000)

[    0.000000] mapped IOAPIC to ffffa000 (fec00000)

[    0.000000] Enabling fast FPU save and restore... done.

[    0.000000] Enabling unmasked SIMD FPU exception support... done.

[    0.000000] Initializing CPU#0

[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)

[    0.000000] Detected 1496.317 MHz processor.

[   20.063067] Console: colour VGA+ 80x25

[   20.063072] console [tty0] enabled

[   20.063286] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)

[   20.063547] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)

[   20.076643] Memory: 498964k/515916k available (2164k kernel code, 16256k reserved, 1007k data, 364k init, 0k highmem)

[   20.076652] virtual kernel memory layout:

[   20.076653]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)

[   20.076655]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

[   20.076656]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)

[   20.076658]     lowmem  : 0xc0000000 - 0xdf7d3000   ( 503 MB)

[   20.076659]       .init : 0xc041f000 - 0xc047a000   ( 364 kB)

[   20.076660]       .data : 0xc031d1bd - 0xc0418dc4   (1007 kB)

[   20.076662]       .text : 0xc0100000 - 0xc031d1bd   (2164 kB)

[   20.076666] Checking if this processor honours the WP bit even in supervisor mode... Ok.

[   20.076707] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1

[   20.156697] Calibrating delay using timer specific routine.. 2996.10 BogoMIPS (lpj=5992201)

[   20.156726] Security Framework initialized

[   20.156736] SELinux:  Disabled at boot.

[   20.156753] AppArmor: AppArmor initialized

[   20.156757] Failure registering capabilities with primary security module.

[   20.156766] Mount-cache hash table entries: 512

[   20.156913] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000 00000000

[   20.156927] CPU: L1 I cache: 32K, L1 D cache: 32K

[   20.156930] CPU: L2 cache: 1024K

[   20.156933] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000000 00000000 00000000 00000000

[   20.156943] Compat vDSO mapped to ffffe000.

[   20.156956] Checking 'hlt' instruction... OK.

[   20.173126] SMP alternatives: switching to UP code

[   20.175274] Freeing SMP alternatives: 11k freed

[   20.175396] Early unpacking initramfs... done

[   20.602764] ACPI: Core revision 20070126

[   20.602830] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

[   20.605330] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08

[   20.605358] Total of 1 processors activated (2996.10 BogoMIPS).

[   20.605553] ENABLING IO-APIC IRQs

[   20.605751] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

[   20.752479] Brought up 1 CPUs

[   20.752509] CPU0 attaching sched-domain:

[   20.752512]  domain 0: span 01

[   20.752514]   groups: 01

[   20.752699] net_namespace: 64 bytes

[   20.752710] Booting paravirtualized kernel on bare hardware

[   20.753252] Time:  9:42:00  Date: 04/08/08

[   20.753309] NET: Registered protocol family 16

[   20.753529] EISA bus registered

[   20.753558] ACPI: bus type pci registered

[   20.784494] PCI: PCI BIOS revision 2.10 entry at 0xfba7e, last bus=13

[   20.784497] PCI: Using configuration type 1

[   20.784501] Setting up standard PCI resources

[   20.789936] ACPI: EC: Look up EC in DSDT

[   20.793456] ACPI: Interpreter enabled

[   20.793460] ACPI: (supports S0 S3 S4 S5)

[   20.793475] ACPI: Using IOAPIC for interrupt routing

[   20.806371] ACPI: PCI Root Bridge [PCI0] (0000:00)

[   20.807137] Force enabled HPET at base address 0xfed00000

[   20.807144] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO

[   20.807149] PCI quirk: region 1080-10bf claimed by ICH6 GPIO

[   20.807624] PCI: Transparent bridge - 0000:00:1e.0

[   20.807662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[   20.808179] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]

[   20.808371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]

[   20.808531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]

[   20.815871] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)

[   20.815988] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10

[   20.816102] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)

[   20.816215] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)

[   20.816314] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   20.816424] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   20.816529] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   20.816667] Linux Plug and Play Support v0.97 (c) Adam Belay

[   20.816705] pnp: PnP ACPI init

[   20.816713] ACPI: bus type pnp registered

[   20.831792] pnpacpi: exceeded the max number of mem resources: 12

[   20.845315] pnp: PnP ACPI: found 11 devices

[   20.845317] ACPI: ACPI bus type pnp unregistered

[   20.845321] PnPBIOS: Disabled by ACPI PNP

[   20.845559] PCI: Using ACPI for IRQ routing

[   20.845562] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

[   20.888374] NET: Registered protocol family 8

[   20.888376] NET: Registered protocol family 20

[   20.888561] hpet clockevent registered

[   20.888568] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0

[   20.888573] hpet0: 3 64-bit timers, 14318180 Hz

[   20.889622] AppArmor: AppArmor Filesystem Enabled

[   20.892366] Time: tsc clocksource has been installed.

[   20.900402] system 00:00: iomem range 0x0-0x9fbff could not be reserved

[   20.900406] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved

[   20.900409] system 00:00: iomem range 0xc0000-0xcffff could not be reserved

[   20.900413] system 00:00: iomem range 0xe0000-0xfffff could not be reserved

[   20.900416] system 00:00: iomem range 0x100000-0x1f7d37ff could not be reserved

[   20.900420] system 00:00: iomem range 0x1f7d3800-0x1f7fffff could not be reserved

[   20.900423] system 00:00: iomem range 0x1f800000-0x1fffffff could not be reserved

[   20.900427] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved

[   20.900431] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved

[   20.900434] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved

[   20.900438] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved

[   20.900441] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved

[   20.900449] system 00:02: ioport range 0x4d0-0x4d1 has been reserved

[   20.900452] system 00:02: ioport range 0x1000-0x1005 has been reserved

[   20.900455] system 00:02: ioport range 0x1008-0x100f has been reserved

[   20.900462] system 00:03: ioport range 0xf400-0xf4fe has been reserved

[   20.900465] system 00:03: ioport range 0x1006-0x1007 has been reserved

[   20.900468] system 00:03: ioport range 0x100a-0x1059 could not be reserved

[   20.900472] system 00:03: ioport range 0x1060-0x107f has been reserved

[   20.900475] system 00:03: ioport range 0x1080-0x10bf has been reserved

[   20.900478] system 00:03: ioport range 0x10c0-0x10df has been reserved

[   20.900481] system 00:03: ioport range 0x10e0-0x10ff has been reserved

[   20.900490] system 00:08: ioport range 0x900-0x90f has been reserved

[   20.900493] system 00:08: ioport range 0x910-0x91f has been reserved

[   20.900496] system 00:08: ioport range 0x920-0x92f has been reserved

[   20.900499] system 00:08: ioport range 0x930-0x93f has been reserved

[   20.900502] system 00:08: ioport range 0x940-0x97f has been reserved

[   20.930937] PCI: Bridge: 0000:00:1c.0

[   20.930939]   IO window: disabled.

[   20.930945]   MEM window: disabled.

[   20.930950]   PREFETCH window: disabled.

[   20.930956] PCI: Bridge: 0000:00:1c.3

[   20.930960]   IO window: d000-dfff

[   20.930966]   MEM window: dfc00000-dfdfffff

[   20.930971]   PREFETCH window: d0000000-d01fffff

[   20.930977] PCI: Bridge: 0000:00:1e.0

[   20.930979]   IO window: disabled.

[   20.930985]   MEM window: dfb00000-dfbfffff

[   20.930990]   PREFETCH window: disabled.

[   20.931025] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16

[   20.931033] PCI: Setting latency timer of device 0000:00:1c.0 to 64

[   20.931059] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17

[   20.931065] PCI: Setting latency timer of device 0000:00:1c.3 to 64

[   20.931079] PCI: Setting latency timer of device 0000:00:1e.0 to 64

[   20.931092] NET: Registered protocol family 2

[   20.968403] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)

[   20.968619] TCP established hash table entries: 16384 (order: 5, 131072 bytes)

[   20.968733] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)

[   20.968851] TCP: Hash tables configured (established 16384 bind 16384)

[   20.968854] TCP reno registered

[   20.980466] checking if image is initramfs... it is

[   21.392135] Switched to high resolution mode on CPU 0

[   21.818621] Freeing initrd memory: 7698k freed

[   21.819336] audit: initializing netlink socket (disabled)

[   21.819355] audit(1207647720.636:1): initialized

[   21.821725] VFS: Disk quotas dquot_6.5.1

[   21.821819] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[   21.821995] io scheduler noop registered

[   21.821998] io scheduler anticipatory registered

[   21.822001] io scheduler deadline registered

[   21.822014] io scheduler cfq registered (default)

[   21.822028] Boot video device is 0000:00:02.0

[   21.822245] PCI: Setting latency timer of device 0000:00:1c.0 to 64

[   21.822302] assign_interrupt_mode Found MSI capability

[   21.822353] Allocate Port Service[0000:00:1c.0:pcie00]

[   21.822396] Allocate Port Service[0000:00:1c.0:pcie02]

[   21.822502] PCI: Setting latency timer of device 0000:00:1c.3 to 64

[   21.822558] assign_interrupt_mode Found MSI capability

[   21.822604] Allocate Port Service[0000:00:1c.3:pcie00]

[   21.822640] Allocate Port Service[0000:00:1c.3:pcie02]

[   21.822925] isapnp: Scanning for PnP cards...

[   22.177073] isapnp: No Plug & Play device found

[   22.209420] Real Time Clock Driver v1.12ac

[   22.209548] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

[   22.210870] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

[   22.210952] input: Macintosh mouse button emulation as /devices/virtual/input/input0

[   22.211066] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

[   22.211216] i8042.c: Warning: Keylock active.

[   22.212609] serio: i8042 KBD port at 0x60,0x64 irq 1

[   22.212615] serio: i8042 AUX port at 0x60,0x64 irq 12

[   22.219737] mice: PS/2 mouse device common for all mice

[   22.219867] EISA: Probing bus 0 at eisa.0

[   22.219876] Cannot allocate resource for EISA slot 1

[   22.219911] EISA: Detected 0 cards.

[   22.219915] cpuidle: using governor ladder

[   22.219917] cpuidle: using governor menu

[   22.220037] NET: Registered protocol family 1

[   22.220070] Using IPI No-Shortcut mode

[   22.220108] registered taskstats version 1

[   22.220223]   Magic number: 4:225:727

[   22.220367] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[   22.220369] EDD information not available.

[   22.220586] Freeing unused kernel memory: 364k freed

[   22.222354] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1

[   23.459989] fuse init (API version 7.9)

[   23.478671] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])

[   23.478678] ACPI: Processor [CPU0] (supports 8 throttling states)

[   23.478693] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]

[   23.483635] ACPI: Thermal Zone [THM] (34 C)

[   24.162590] usbcore: registered new interface driver usbfs

[   24.162619] usbcore: registered new interface driver hub

[   24.174570] usbcore: registered new device driver usb

[   24.182553] USB Universal Host Controller Interface driver v3.0

[   24.182631] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16

[   24.182645] PCI: Setting latency timer of device 0000:00:1d.0 to 64

[   24.182650] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[   24.183064] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

[   24.183102] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80

[   24.183262] usb usb1: configuration #1 chosen from 1 choice

[   24.183288] hub 1-0:1.0: USB hub found

[   24.183295] hub 1-0:1.0: 2 ports detected

[   24.286584] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18

[   24.286601] PCI: Setting latency timer of device 0000:00:1d.1 to 64

[   24.286607] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[   24.286634] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

[   24.286668] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60

[   24.286791] usb usb2: configuration #1 chosen from 1 choice

[   24.286818] hub 2-0:1.0: USB hub found

[   24.286824] hub 2-0:1.0: 2 ports detected

[   24.310703] SCSI subsystem initialized

[   24.372600] libata version 3.00 loaded.

[   24.390515] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19

[   24.390531] PCI: Setting latency timer of device 0000:00:1d.2 to 64

[   24.390536] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[   24.390573] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

[   24.390608] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40

[   24.390737] usb usb3: configuration #1 chosen from 1 choice

[   24.390763] hub 3-0:1.0: USB hub found

[   24.390769] hub 3-0:1.0: 2 ports detected

[   24.494450] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17

[   24.494466] PCI: Setting latency timer of device 0000:00:1d.3 to 64

[   24.494472] uhci_hcd 0000:00:1d.3: UHCI Host Controller

[   24.494499] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4

[   24.494536] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20

[   24.494663] usb usb4: configuration #1 chosen from 1 choice

[   24.494689] hub 4-0:1.0: USB hub found

[   24.494695] hub 4-0:1.0: 2 ports detected

[   24.598542] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16

[   24.598561] PCI: Setting latency timer of device 0000:00:1d.7 to 64

[   24.598565] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[   24.598597] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5

[   24.602504] ehci_hcd 0000:00:1d.7: debug port 1

[   24.602511] PCI: cache line size of 32 is not supported by device 0000:00:1d.7

[   24.602524] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000

[   24.618264] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[   24.618401] usb usb5: configuration #1 chosen from 1 choice

[   24.618429] hub 5-0:1.0: USB hub found

[   24.618437] hub 5-0:1.0: 8 ports detected

[   24.722531] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 18

[   24.765539] ssb: SPROM revision 2 detected.

[   24.782256] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0

[   24.786663] ata_piix 0000:00:1f.1: version 2.12

[   24.786685] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16

[   24.786727] PCI: Setting latency timer of device 0000:00:1f.1 to 64

[   24.789195] scsi0 : ata_piix

[   24.790354] scsi1 : ata_piix

[   24.791021] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14

[   24.791025] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15

[   25.134601] ata1.00: ATA-6: WDC WD800VE-75HDT1, 11.07D11, max UDMA/100

[   25.134606] ata1.00: 156301488 sectors, multi 8: LBA 

[   25.134637] ata1.01: ATAPI: PHILIPS DVD+/-RW SDVD8820, AD15, max UDMA/33

[   25.142515] ata1.00: configured for UDMA/100

[   25.314318] ata1.01: configured for UDMA/33

[   25.314370] ata2: port disabled. ignoring.

[   25.314525] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800VE-75HD 11.0 PQ: 0 ANSI: 5

[   25.315211] scsi 0:0:1:0: CD-ROM            PHILIPS  DVD+-RW SDVD8820 AD15 PQ: 0 ANSI: 5

[   25.317968] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 19

[   25.361125] ssb: SPROM revision 16 detected.

[   25.377889] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0

[   25.377917] b44.c:v2.0

[   25.385845] Clocksource tsc unstable (delta = -21554729322 ns)

[   25.389817] Time: hpet clocksource has been installed.

[   25.390306] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:aa:ba:a7

[   25.402007] Driver 'sd' needs updating - please use bus_type methods

[   25.402107] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[   25.402122] sd 0:0:0:0: [sda] Write Protect is off

[   25.402125] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   25.402144] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   25.402200] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[   25.402211] sd 0:0:0:0: [sda] Write Protect is off

[   25.402214] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   25.402231] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   25.402235]  sda:<4>Driver 'sr' needs updating - please use bus_type methods

[   25.446331]  sda1 sda2

[   25.446426] sd 0:0:0:0: [sda] Attached SCSI disk

[   25.453475] sd 0:0:0:0: Attached scsi generic sg0 type 0

[   25.453498] sr 0:0:1:0: Attached scsi generic sg1 type 5

[   25.471183] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray

[   25.471189] Uniform CD-ROM driver Revision: 3.20

[   25.471251] sr 0:0:1:0: Attached scsi CD-ROM sr0

[   25.671669] loop: module loaded

[   25.692732] kjournald starting.  Commit interval 5 seconds

[   25.692750] EXT3-fs: mounted filesystem with ordered data mode.

[   29.203329] input: PC Speaker as /devices/platform/pcspkr/input/input2

[   29.790917] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   29.838918] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   29.921082] intel_rng: FWH not detected

[   29.961894] Linux agpgart interface v0.102

[   30.016400] agpgart: Detected an Intel 915GM Chipset.

[   30.016737] agpgart: Detected 7932K stolen memory.

[   30.035842] agpgart: AGP aperture is 256M @ 0xc0000000

[   30.059491] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x200000

[   30.148327] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input3

[   30.234725] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)

[   30.378554] iTCO_vendor_support: vendor-support=0

[   30.438516] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)

[   30.438625] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)

[   30.438662] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

[   30.722812] ACPI: AC Adapter [AC] (on-line)

[   31.162300] ACPI: Battery Slot [BAT0] (battery present)

[   31.162403] input: Lid Switch as /devices/virtual/input/input4

[   31.174395] ACPI: Lid Switch [LID]

[   31.174453] input: Power Button (CM) as /devices/virtual/input/input5

[   31.202097] ACPI: Power Button (CM) [PBTN]

[   31.202171] input: Sleep Button (CM) as /devices/virtual/input/input6

[   31.234060] ACPI: Sleep Button (CM) [SBTN]

[   31.820648] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16

[   31.820680] PCI: Setting latency timer of device 0000:00:1b.0 to 64

[   32.366479] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7

[   32.393427] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

[   32.393616] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8

[   32.417389] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)

[   34.769252] lp: driver loaded but no devices found

[   34.853829] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)

[   34.950931] usbcore: registered new interface driver ndiswrapper

[   35.093707] EXT3 FS on loop0, internal journal

[   39.574112] Adding 390616k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:390616k

[   39.674370] ip_tables: (C) 2000-2006 Netfilter Core Team

[   39.970025] No dock devices found.

[   40.888703] apm: BIOS not found.

[   40.939994] ppdev: user-space parallel port driver

[   41.938030] Bluetooth: Core ver 2.11

[   41.938927] NET: Registered protocol family 31

[   41.938932] Bluetooth: HCI device and connection manager initialized

[   41.938937] Bluetooth: HCI socket layer initialized

[   41.976552] Bluetooth: L2CAP ver 2.9

[   41.976557] Bluetooth: L2CAP socket layer initialized

[   42.080330] Bluetooth: RFCOMM socket layer initialized

[   42.080825] Bluetooth: RFCOMM TTY layer initialized

[   42.080829] Bluetooth: RFCOMM ver 1.8

[   42.655855] b44: eth0: Link is up at 100 Mbps, full duplex.

[   42.655862] b44: eth0: Flow control is off for TX and off for RX.

[   44.444219] NET: Registered protocol family 17

[   44.575149] [drm] Initialized drm 1.1.0 20060810

[   44.579095] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16

[   44.579106] PCI: Setting latency timer of device 0000:00:02.0 to 64

[   44.579194] [drm] Initialized i915 1.6.0 20060119 on minor 0

[   46.534832] NET: Registered protocol family 10

[   46.535516] lo: Disabled Privacy Extensions

[   50.460858] eth0: no IPv6 routers present
```

The ndiswrapper thing is there like it says on your help page

---

### Post by dmizer on 2008-04-08
still got a native driver in there messing things up.

add:
```
blacklist b44
```
to /etc/modprobe.d/blacklist

without rebooting, try unloading ndiswrapper, and the b44 module:
```
sudo modprobe -r ndiswrapper
sudo modprobe -r b44
```

then try readding the ndiswrapper module to see if we can get  a clean start and make your card finally show up:
```
sudo modprobe ndiswrapper
```

check networking to see if you have a wlan0

[COLOR="DimGray"]edit:
why do i feel like i'm playing bingo? ;)[/COLOR]

---

### Post by spudgunner on 2008-04-08
So funny story (and by funny I mean super-annoying):

I did what you said dmizer, I had wlan0 and wireless networks detected, but my eth0 disappeared... I had been doing some updates at the same time (which I probably shouldn't have) but I had to restart my comptuer... but I did, wlan0 was gone again and eth0 was returned, but didn't want to connect.

---

### Post by dmizer on 2008-04-08
try this:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

may sound silly, but do you have any usb devices connected to your computer?  if so, try rebooting without the usb devices attached, and see if your wlan0 comes up automatically then.

---

### Post by dmizer on 2008-04-08
just realized ... 

you'll have to remove the b44 module from the blacklist, as that's the module driving your wired network card.

---

### Post by spudgunner on 2008-04-08
Turns out I'm an idiot with the updates... but yeah, the whole eth0 disappearing before restarting is still valid... I will try removing b44 from the blacklist and let you know

One other thing... I removed b44 from modprobe earlier:

```
sudo modprobe -r b44
```

I don't have to add it back in or anything, only un-blacklist it?

---

### Post by dmizer on 2008-04-08
> **spudgunner said:**
> One other thing... I removed b44 from modprobe earlier:

```
sudo modprobe -r b44
```

I don't have to add it back in or anything, only un-blacklist it?

un-blacklisting it will allow the module to load on reboot.  it will also allow the module to load with:
```
sudo modprobe b44
```

edit:
past midnight and i have to be at work early tomorrow.  gonna call it quits for tonight.  i'll pick it up again sometime tomorrow afternoon if i have time.  still have tricks up my sleeve though, so do not despair.

---

### Post by spudgunner on 2008-04-08
OK, so I think I have everything working fine... only problem is everytime I restart, wlan0 has disappeared again, but by blacklisting b44, removing ndiswrapper and b44, restarting ndiswrapper, un-blacklisting b44 and then restarting it, I get both ports working (but I haven't tested it out on and encrypted wireless network yet) - It's basicallythe last set of instructions you gave me, each time I boot.

It appears to me (and I don't think I have a good idea of what's going on anyway) that b44 is loading before ndiswrapper and screwing it up, because when I turn it off and get ndiswrapper going first, and then b44, everything works. But that's just what I think, I have a good chance of being wrong.

So.... how would I fix this problem, to get them do to whatever in the right order?

---

### Post by spudgunner on 2008-04-08
Another kind-of off topic question... would doing this stuff also work with Kubuntu?

---

### Post by dmizer on 2008-04-08
you shouldn't need to blacklist the b44 module.  i'm still not positive that the b44 is the problem.

let's try blacklisting the usb modules (for testing purposes).  the reason for this is that ndiswrapper loads as a usb module and sometimes there can be conflicts.  so let's eliminate that as a possibility.

make sure that all usb devices are disconnected, and blacklist both usb modules:
blacklist ehci_hcd
blacklist uhci_hcd

reboot and see if that helps.  if it doesn't help, remove them both from the black list, and we'll try something else.

> **spudgunner said:**
> Another kind-of off topic question... would doing this stuff also work with Kubuntu?

anything done via the command line will work in all of the ubuntu distributions (ubuntu, kubuntu, and xubuntu).  the only difference between these is the graphical manager.  everything underneath the graphical manager (cli) is identical.

---

### Post by spudgunner on 2008-04-09
Blacklisting ehci_hcd and uhci_hcd didn't work.

I did find out that I don't have to blacklist b44 every time, I only have to follow this sequence

```
sudo modprobe -r ndiswrapper
sudo modprobe -r b44
sudo modprobe ndiswrapper
sudo modprobe
```

I don't even know if I have to do the -r in that order, but I have to do restart them in that particular order or it won't work, and I only get eth0 (and not wlan0)

---

### Post by dmizer on 2008-04-09
so blacklisting usb did nothing ...

okay, this is probably a bug.

edit /etc/rc.local (with sudo) and add those lines before "exit 0" like so:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r ndiswrapper
modprobe -r b44
modprobe ndiswrapper
modprobe b44
exit 0
```

this is a work around, and not a permanent fix.  the b44 module seems to be interfering with both the native wireless module as well as ndiswrapper, though i don't have the knowledge to tell you how to figure out more than that.  if you feel up to it, you should file a bug report.

---

### Post by spudgunner on 2008-04-09
Will do... I knew there had to be some kind of work around... and I will go about doing a bug report... but I don't know how to format it or anything... if you could let me know how I'd appreciate it.

Thanks for all your help with this... I really, really appreciate it. Now I've overcome the last hurdle in escaping Windows! I definately owe you one hahaha.

Keep up the good work!

---

### Post by dmizer on 2008-04-09
thanks, but let me know if the workaround works for ya. :)

here's some good information on how to go about filing a bug: [http://www.ubuntu.com/community/ReportProblem](http://www.ubuntu.com/community/ReportProblem)

it should be filed against the native b44 module.

---

### Post by spudgunner on 2008-04-09
It worked... thank you again for all your help... I'd be so lost otherwise haha.

Anyways, off to submitting that report now.

---

### Post by spudgunner on 2008-04-12
Do you have any idea of how to get my modem working? It's a Conexant HDA D110 MDC V.92 Modem.

---

### Post by dmizer on 2008-04-13
> **spudgunner said:**
> Do you have any idea of how to get my modem working? It's a Conexant HDA D110 MDC V.92 Modem.

nope, but there's a sticky post at the top of the "networking & wireless" forum called "Setting up your dialup modem (aka winmodem)" ... i suggest starting there.

---

