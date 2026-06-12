---
title: "[SOLVED] How to kill wireless completely"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by matjaz on 2008-09-25
Hi!

What i am trying to do in short is: I am trying to get the wireless on/of switch functionality in a script, because that switch does not work on my laptop.

I have a laptop, (fujitsu siemens v5505), that has a wireless card ( and bluetoooth ) inside.
It all works just fine, what i want to know is how can i completely disable the wireless card, so that i could for instance use my laptop on an aeroplane, where transmitting devices are prohibited.
The same question for the bluetooth.
( my wireless kill/toggle button on my laptop is not detected in ubuntu 8.04 and there does not seem to be a way to enable it according to laptop testing team).

What i would like to have in the end would be 4 scripts:
one for killing wifi card, another for enabeling it,
and two similar for bluetooth.

I would like to have a solution, that would not just kill the wireless temporarily ( so that for instance when i would reset the cpu, the wireless would work again ), but it would disable any transmittion through wifi antenna until i would for instance run the script that would enable it again.

I would appreciate any help or any directions.

Matjaz

---

### Post by HangMan101 on 2008-09-25
try rmmod your drivers should disable the card. and blacklist it to make sure it won't go on if you have to reboot

remove the blacklist and modprobe it back if you want it back on

and use a EMF testing device to look if it is a danger to a plane... 


BTW. no flight company would allow you to use a laptop/notebook in a plane because a laptop even with transmission units disabled has a EMF just as dangerous as a cellphone thats turned on  ](*,)

---

### Post by Muflon on 2008-09-25
I used my laptop on an Easyjet flight in July.  They only insisted that it be turned off for takeoff and landing.

Muflon

---

### Post by prshah on 2008-09-25
> **matjaz said:**
> 
What i am trying to do in short is: I am trying to get the wireless on/of switch functionality in a script, because that switch does not work on my laptop.

It's quite easy to turn off wireless; if your wireless card is eth1, give this command from a terminal (Applications-Accessories-Terminal)```
sudo iwconfig eth1 txpower off
```

To turn it back on ```
sudo iwconfig eth1 txpower on
``` (DUH!!)

Dunno for bluetooth; can you just modprobe -r the relevant module out?

---

### Post by matjaz on 2008-09-25
Hi,
Thank you for the suggetion.
The up/down of the wlan0 interface ( my wifi ) does shut it down, but when i restart the cpu, it starts as turned on, what is not what i would like.

I did some research and come up with:
[http://brainstorm.ubuntu.com/idea/9762/](http://brainstorm.ubuntu.com/idea/9762/)
[http://ubuntuforums.org/showthread.php?p=5848911](http://ubuntuforums.org/showthread.php?p=5848911)
and after doing what is described in:
[HTML]Ok, here are some hacks I do to create a bluetooth on/off option. First I removed Bluetooth service from Ubuntu Services (System->Administration->Services). So my bluetooth adapter will be turned off when I start up my computer.

Then I configured the Bluetooth applet to auto start with my session but to be only show in notification area when a bluetooth adpter is running.

Then I create a script named toogle_bt.sh with the content:

#!/bin/bash
if ps -A | grep -c bluetoothd-serv
then
gksudo /etc/init.d/bluetooth stop
else
gksudo /etc/init.d/bluetooth start
fi

give it permission to run and made a shortcut pointing to this script with a nice bluetooth icon and named Toogle Bluetooth.

Now I boot my pc, when I want to do some bluetooth transfers I click in the shortcut. It will activate my bluetooth, the icon will appear in notification area. When I'm done I run the shortcut again and bluetooth is turn off and the icon gone away.

Nice and simple. [/HTML]

i still can detect my cpu's bluettoth as turned on with my mobile phone.
( i unchecked the bluetooth services and ran the script ).
What the script does is just disable the icon ( i can't see the bluetooth icon on my desktop, but hciconfig gives:
hci0:	Type: USB
	BD Address: 00:1E:37:0E:6A:77 ACL MTU: 384:8 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:5571 acl:20 sco:0 events:168 errors:0
	TX bytes:2894 acl:20 sco:0 commands:119 errors:0

the following is the result of doing what is described in [http://ubuntuforums.org/showthread.php?t=120403&highlight=turn+bluetooth+radio](http://ubuntuforums.org/showthread.php?t=120403&highlight=turn+bluetooth+radio) :
```
matjaz@matjaz-laptop:~$ sudo /etc/init.d/bluez-utils stop
[sudo] password for matjaz: 
sudo: /etc/init.d/bluez-utils: command not found
matjaz@matjaz-laptop:~$ bluez-utils stop
bash: bluez-utils: command not found
matjaz@matjaz-laptop:~$ 
```

So i don't seem to have bluez-utils installed, although synaptic says i have.

I tried this stuff thinking there might be some similarities with killing wifi, but it didn't help even with bluetooth.

I will do some more research, and if i find something useful i will post it here.

[HTML]try rmmod your drivers should disable the card. and blacklist it to make sure it won't go on if you have to reboot

remove the blacklist and modprobe it back if you want it back on

and use a EMF testing device to look if it is a danger to a plane...

[/HTML]

I would like to try blacklisting the modules with modprobe, but i would need some info on which modules. How do i know which modules are for my wifi card? lsmod gives:
( ignore the ndiswrapper - the integrated card uses native drivers. ndiswrapper is for another wifi card i use when i am trying to kill the built-in one and i am looking for instructions to do so on the internet )
```
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
af_packet              23812  4 
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
binfmt_misc            12808  1 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
container               5632  0 
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
serio_raw               7940  0 
psmouse                40336  0 
ndiswrapper           192920  0 
pcspkr                  4224  0 
evdev                  13056  6 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
hci_usb                16540  2 
cfg80211               15112  1 iwlwifi_mac80211
bluetooth              61156  7 rfcomm,l2cap,hci_usb
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
battery                14212  0 
ac                      6916  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  19856  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi_acer                9644  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
iptable_nat             8324  0 
nf_nat                 20396  1 iptable_nat
nf_conntrack_ipv4      19080  2 iptable_nat
nf_conntrack           66752  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  0 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  2 iptable_nat,ip_tables
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
ata_piix               19588  0 
sd_mod                 30720  5 
pata_acpi               8320  0 
usb_storage            73664  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
libusual               19108  1 usb_storage
ata_generic             8324  0 
ahci                   28420  4 
libata                159344  4 ata_piix,pata_acpi,ata_generic,ahci
scsi_mod              151436  5 sr_mod,sg,sd_mod,usb_storage,libata
r8169                  32900  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  8 ndiswrapper,hci_usb,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```
 and if i right-click my network connection and click connection information i see iwl3945 as the driver.

So blacklisting iwl3945 would disable my wifi card or it would just make it run with another driver, which is less suitable for my device? ( I remember that in windows when you disable the display specific driver it then runs on another driver - perhaps vga driver or something else very old, i don't know exactly - the point is it is not disabled, just using diferent drivers )

How do i see which driver is used for my wifi card ( the clicking method makes me uncertain - i would like to have a terminal command )?

Thanks again for suggestions.

Matjaz

---

### Post by matjaz on 2008-10-11
Hi,

I have found a solution for killing wifi in ubuntu:
 [http://ubuntuforums.org/showthread.php?t=453380](http://ubuntuforums.org/showthread.php?t=453380)
( i have fujitsu siemens v5505 and it works for me )

I am still hoping to find a solution for killing bluetooth.

As far as killing wifi on an aeroplane is concerned, i think i will just have to do that from bios, when i will be using my laptop on an aeroplane

Thans again for all the suggestions.
Matjaz

---

