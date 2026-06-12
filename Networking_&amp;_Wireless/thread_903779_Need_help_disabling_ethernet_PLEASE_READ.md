---
title: "Need help disabling ethernet PLEASE READ"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by KOportal on 2008-08-28
Hi, I'm having trouble connecting to my wireless internet (which is my only way of internet access at this computer). I just discovered that the reason I cannot connect is because it assumes that I get my internet from ethernet.

I used the lshw -C network and it said I was using ethernet even though I want to use my wireless. Is there any way I can disable this? I currently have ndiswrapper and installed the driver for my wireless adapter, and everything else seems to be fine, but I don't know how to stop Ubuntu from looking for internet on my Realtek Ethernet port.

---

### Post by caljohnsmith on 2008-08-28
I think the simplest way to disable your ethernet interface is to just unplug the ethernet cable from your ethernet card. Then for sure Ubuntu will ignore it. But if for some reason you can't do that, then if your ethernet interface has been configured in /etc/network/interfaces, you could disable it with:
```
sudo ifdown eth0
```
Or replace "eth0" with your interface if it is different. Or you can try and disable eth0 with:
```
sudo ifconfig eth0 down
```
At least one of those commands ought to work. :)

---

### Post by KOportal on 2008-08-28
okay i'll try that, but i actually don't have any cable in it, it just for some reason picks up the card

---

### Post by caljohnsmith on 2008-08-28
> **KOportal said:**
> okay i'll try that, but i actually don't have any cable in it, it just for some reason picks up the card
I think you are misunderstanding the "sudo lshw -C network" output; that command lists all the network interfaces it finds, whether they are being used or not. It won't tell you which network interface card (NIC) is being used. Instead, use:
```
ifconfig
iwconfig
```

---

### Post by KOportal on 2008-08-28
i tried that out, for the second command you listed, i typed it in and it said nothing. for the first command it said that i haven't configured me eth0, even though i don't even want to configure it. I just want to set up my wireless and ndiswrapper says the hardware is plugged in, but i when i do the lsusb command, it doesn't show up. I've seen other people with this problem, but I've never seen a solution to this. i've used the guide on these forums, and I got to a point where i needed to use the lshw -C network command so my wireless could come up to see the problem, and that's when i realized its not even using wireless by default.

I'm really confused right now :(

oh and when i use i forget either if or iwconfig i get a message that says no wireless

---

### Post by caljohnsmith on 2008-08-28
OK, if you are understandably confused, let's start at the beginning: what is your wireless card chipset? And is your wireless interface a PCI card (inside your computer), or does it plug into a USB port (outside your computer)? Also you say you are using ndiswrapper--do you have the Windows wireless drivers for your wireless interface? Have you installed ndiswrapper?

---

### Post by KOportal on 2008-08-28
i have a trendnet tew-229ub 2.0
yes i have ndiswrapper installed and i also have the wireless driver that says the hardware for it is plugged in

its a usb adapter

---

### Post by caljohnsmith on 2008-08-28
OK, do you have the Windows drivers, namely the "sis162u.inf" file and a .sys file? Your Wireless adapter should have come with an install CD, and that should have those drivers.

---

### Post by KOportal on 2008-08-28
yes exactly what i used i got the inf file directly from the cd

and thats the exact name

---

### Post by caljohnsmith on 2008-08-28
Great, just make sure you use the Windows XP drivers and not the Vista ones, as most people have much better success using the XP drivers.

So have you actually installed the wireless drivers with ndiswrapper yet? In other words:
```
sudo ndiswrapper -i sis162u.inf
```
If so, if you do:
```
ndiswrapper -l
```
What exactly is the output? (Copy/paste it back here).

---

### Post by KOportal on 2008-08-28
okay hold on i have to boot up on ubuntu

i've done it before and i'm pretty sure that it comes up saying that its successfully installed.

---

### Post by KOportal on 2008-08-28
```
sis162u : driver installed
	device (0457:0162) present
```

---

### Post by caljohnsmith on 2008-08-29
OK, do:
```
sudo modprobe ndiswrapper
iwconfig
sudo iwlist wlan0 scan
```
Does the second command show interface wlan0? And does the third command list available wireless networks?

---

### Post by KOportal on 2008-08-29
okay the first one i typed in and nothing happened, it didn't have any errors, but nothing came up.

the second one had this:

```
lo no wireless extensions

eth0 no wireless extensions
```

the third one had this:

```
wlan0 doesn't support scanning
```

---

### Post by caljohnsmith on 2008-08-29
OK, first do this command:
```
gksudo gedit /etc/modules &
```
If you don't all ready have a line in that file with "ndiswrapper" on it, go ahead and add a line with "ndiswrapper" at the end of that file, save, and quit. Reboot, and then do:
```
lsmod | grep "ndiswrapper"
```
Does that return some line(s) with ndiswrapper? If so, do:
```
iwconfig
```
Does that show interface "wlan0"?

---

### Post by KOportal on 2008-08-29
this is what the second code gave me

```
ndiswrapper           243872  0 
usbcore               169904  7 usb_storage,libusual,usbhid,ndiswrapper,ehci_hcd,ohci_hcd
```

iwconfig still came up with the same result :(

---

### Post by caljohnsmith on 2008-08-29
Is there anything about your computer or Ubuntu that might make it different from what most people would consider a "standard" install? Do you have Ubuntu on its own partition or are you using Wubi? Please give me as many details as you can about your set up, or anything else that you think could be possibly relevant.

How did you install ndiswrapper--did you install it through the repositories, or did you download the latest version and compile it yourself? Also post the output of the following:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by KOportal on 2008-08-29
I have a standard install, aka I downloaded and installed using Daemon Tools. I had trouble installing ndiswrapper with the .tar.gz and it kept coming up with errors when I tried to install it that way. So i used .deb files and used the terminal to install.
So I'm actually not 100% sure that my ndiswrapper is correct even though it seems to be working fine. I will post the results to that in a couple minutes.

---

### Post by KOportal on 2008-08-29
here it is

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:21:28:1c:f6", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

---

### Post by caljohnsmith on 2008-08-29
OK, please post the full output of:
```

uname -a
lsmod
dmesg | grep ndiswrapper
dmesg | grep wlan0
```
Also, you didn't mention yet, but are you using the Windows XP drivers or the Vista ones?

---

### Post by KOportal on 2008-08-29
oh i'm using xp. i currently own xp and the cd for my adapter came out before vista.

---

### Post by KOportal on 2008-08-29
Here is the results in order:

```
Linux kevin-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
```



```
Module                  Size  Used by
isofs                  39464  1 
nls_iso8859_1           6656  1 
nls_cp437               8320  1 
vfat                   16256  1 
udf                    91048  0 
fat                    60592  1 vfat
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  0 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
freq_table              6464  2 cpufreq_ondemand,cpufreq_stats
container               6656  0 
video                  23444  0 
output                  5632  1 video
dock                   12960  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
lp                     14916  0 
usb_storage            82496  1 
evdev                  14976  5 
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
libusual               23520  1 usb_storage
usbhid                 35296  0 
hid                    44992  1 usbhid
ndiswrapper           243872  0 
snd_intel8x0           40872  3 
snd_ac97_codec        123224  1 snd_intel8x0
ac97_bus                3840  1 snd_ac97_codec
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
serio_raw               9092  0 
psmouse                46236  0 
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
button                 10912  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4992  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
snd                    70856  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sis_agp                11652  1 
soundcore              10400  1 snd
snd_page_alloc         13200  2 snd_intel8x0,snd_pcm
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
loop                   21508  2 
sg                     41880  0 
sr_mod                 20132  1 
cdrom                  41512  1 sr_mod
sd_mod                 33280  4 
sata_sis               11396  0 
pata_sis               18820  3 sata_sis
ehci_hcd               41996  0 
ohci_hcd               27524  0 
8139too                31104  0 
8139cp                 27776  0 
mii                     7552  2 8139too,8139cp
pata_acpi               9856  0 
ata_generic             9988  0 
usbcore               169904  7 usb_storage,libusual,usbhid,ndiswrapper,ehci_hcd,ohci_hcd
libata                176432  4 sata_sis,pata_sis,pata_acpi,ata_generic
scsi_mod              178488  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                19744  0 
processor              41448  1 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  5 

```





```
[   43.133555] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   43.536520] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   43.536531] ndiswrapper (load_sys_files:210): couldn't prepare driver 'sis162u'
[   43.538176] ndiswrapper (load_wrap_driver:112): couldn't load driver sis162u; check system log for messages from 'loadndisdriver'
[   43.552699] usbcore: registered new interface driver ndiswrapper
```


and the fourth one came up with nothing

---

### Post by caljohnsmith on 2008-08-29
> **KOportal said:**
> 
```
[   43.133555] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[COLOR="Red"][   43.536520] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B[/COLOR]
[   43.536531] ndiswrapper (load_sys_files:210): couldn't prepare driver 'sis162u'
[   43.538176] ndiswrapper (load_wrap_driver:112): couldn't load driver sis162u; check system log for messages from 'loadndisdriver'
[   43.552699] usbcore: registered new interface driver ndiswrapper
```

So you are using a 64-bit version of Ubuntu? If you are, you need to use the 64-bit Windows wireless driver it looks like. If you don't have a 64-bit version, you may have to go with installing the 32-bit Hardy Ubuntu if you want your wireless to work. What brand is your computer and what processor does it use? Please post the output of:
```
sudo lshw -C cpu | grep width
```

---

### Post by KOportal on 2008-08-29
I have a Powerspec with an Intel Celron Processor, its about 3 years old, not very good stats at all. I will post the results in a couple minutes.

---

### Post by KOportal on 2008-08-29
it turns out to be 64 bit

so should i download the i386 version of ubuntu?

---

### Post by caljohnsmith on 2008-08-29
OK, like I mentioned, unless you have a 64-bit version of your Windows wireless driver, there's probably not much else you can do about your wireless problem except install the 32-bit Ubuntu.

---

### Post by KOportal on 2008-08-29
Alright, thanks a bunch I'm downloading it right now.

---

