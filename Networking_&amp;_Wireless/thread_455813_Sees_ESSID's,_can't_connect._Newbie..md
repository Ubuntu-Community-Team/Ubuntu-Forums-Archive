---
title: "Sees ESSID's, can't connect. Newbie."
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Alex74447 on 2007-05-27
I have a wua-1340 usb adapter. When I plug it into Feisty, it recognizes the stick and I am able to see different access points. But I can't seem to log on to mine. I'm a newbie to linux, as well as networking, so any help would be appreciated. I have tried connecting with both WEP on and off, but I can't seem to get it. Is there anything that I have to do first before it can be enabled? Thanks in advance.

---

### Post by Ateo on 2007-05-27
Are you putting in the clear text password that you set in your AP? If so, I *believe* the gnome network manager requires the longer, encrypted from of the password. I might be wrong, but try that...

HTH

---

### Post by Alex74447 on 2007-05-27
After I posted that, I took the WEP off for a few minutes to see if it would connect, but alas, it did not.

So basically, I have a USB adapter (WUA-1340) that can find connections but is not able to connect, and I'm not sure how I would go about doing this other than trying to install ndiswrapper or something similar.

---

### Post by odiseo77 on 2007-05-27
I'm not sure about this card, but if ubuntu recognizes it and you can see different AP's, then maybe is something wrong between your ubuntu connection settings and your router settings?? I have a Edimax wireless card (rt2500 chipset) and I have set my router to assign IP's to my home pc's automaticaly by DHCP. Have you tried it?? Also, after you've set your router to assign IP's by DHCP you should go to 'System>Administration>Network' then select your network card on the dialog box, click on 'properties', type in your ESSID name, your wep key (note that you must specify whether it's ascii or hexadecimal) and then on the same dialog box, select 'DHCP'.

Hope this can be helpful.

Regards.

---

### Post by Alex74447 on 2007-05-27
DHCP was enabled already, so I tried manually entering the information like you said for both the wmaster0 and the wlan0 and i enabled both of them but that didn't work. Also I tried it in roaming mode and it wouldn't connect either.

Also I have a USB adapter so its an rt73.

I just assumed it would work since I think rt73 is installed w/ feisty and also since it can find APs.

Also if anything needs to be changed on my wireless settings ([http://i36.photobucket.com/albums/e44/Alex74447/meow.jpg](http://i36.photobucket.com/albums/e44/Alex74447/meow.jpg)) maybe there is a problem w/ the settings.

Also when I do iwconfig, it says that I am connected to my ssid (alex) and it also displays my mac address, but the signal strength is stuck at 0 even though the adapter is in the same place as it was when i had windows on and it worked fine.

---

### Post by odiseo77 on 2007-05-27
ok, it's usefull to know that you have a rt73 based card. I searched on google and on the serialmonkey forum and I found [this thread]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3638") that can be usefull. I had similar issues with my rt2500 card on openSuSE 10.2 and the solution was to uninstall the driver that came with SuSE, install the kernel sources, get the rt2500 driver from rt2x00.serialmonkey.com and compile it/install it. So you should start by blacklisting the rt73 module they say in the forum I linked to, get the [rt73usb driver]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz") and the ubuntu kernel sources. After you've installed the kernel sources, compile/install the rt73usb driver and reconfigure your network again.

Regards.

---

### Post by Alex74447 on 2007-05-27
Alright, thanks very much! Though I'm not completely sure how to go about doing all of that, I think I can figure it out with enough research. At least now I have an outline for what to do.

---

### Post by odiseo77 on 2007-05-27
Hi, I'll try to explain myself better and step by step. Let's start by blacklisting the wrong modules as they say in the serialmonkey forum. To do this, we need the output of the ***lsmod*** command on your ubuntu machine (it shows you which modules are currently loaded into the kernel); open the terminal and type:

```
lsmod
```

Then copy the results here :)

EDIT: We don't need to blacklist the rt73 module as I said in my previous post but probably the rt25usb and rt2570 modules, my bad; but we need to know exactly which modules are loaded in the kernel.

---

### Post by Alex74447 on 2007-05-27
Whoah, thanks a ton! Here's the output of lsmod:

```
alex@alex-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
r128                   40832  2 
drm                    81044  3 r128
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
ac                      6020  0 
video                  16388  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
button                  8720  0 
af_packet              23816  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
rc80211_simple          6400  1 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt73usb                33536  0 
rt2x00lib              11904  1 rt73usb
mac80211              175364  3 rc80211_simple,rt73usb,rt2x00lib
cfg80211               22920  1 mac80211
usbhid                 26592  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
crc_itu_t               3072  1 rt73usb
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
hid                    27392  1 usbhid
psmouse                38920  0 
serio_raw               7940  0 
pcspkr                  4224  0 
intel_agp              25116  1 
agpgart                35400  2 drm,intel_agp
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_generic             9092  0 
floppy                 59524  0 
uhci_hcd               25360  0 
usbcore               134280  4 rt73usb,usbhid,uhci_hcd
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
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

From what I gather it doesn't look like rt73usb module is being used, but the rt2x00lib module is being used by the rt73usb. Strange.

---

### Post by TotallyConfused on 2007-05-27
I have exactly the same problem. I bought an Edimax wireless USB dongle that uses the rt73 chipset. I just tried out Linux a month ago and I love it but the wireless issue is a big bummer. I hope I can sort the problem out. Then, I say say bye to Microsoft. :p

---

### Post by odiseo77 on 2007-05-27
@ Alex74447: Well, there's something that puzzles me: according to the serialmonkey forum, the rt25usb and rt2570 modules should appear when you execute lsmod but they don't (these are the modules that would cause the problem); so my guess is that maybe there's something wrong with the rt73 driver that comes with ubuntu.

So, let's try to install the rt73 driver manually. First, make sure you have the kernel headers installed:

```
dpkg -l linux-headers
```

(I think the linux-headers package is installed by default with the standard ubuntu installation, but it's better to check for it first, anyway)

Then download the [rt73 driver]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz") to your personal directory (your /home/username directory), open a terminal and type the following commands:

```
tar -zxvf rt73-cvs-daily.tar.gz
cd rt73-cvs-2007052714/Module #you should type here the appropriate directory name of the uncompressed driver
make
sudo make install

```

Reboot your machine and configure your network again. Hope it works.
Let us know how it goes :)

@ TotallyConfused: Since you're using a rt73 based card, the previous steps should work for you too :)

Regards.

---

### Post by Alex74447 on 2007-05-27
Nevermind, I found this thread:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
And followed the instructions step-by-step, except I didn't aptitude the build-essential but used the Ubuntu CD to get 'em.
Now internet works perfectly.

Still, thanks for all your help and your putting in time to help me! 

What you said initially, to blacklist the rt73usb and install the rt73 modules was basically what I did. But reading what you said made me realize that that post was basically doing exactly what you told me. 

Thanks!

---

### Post by odiseo77 on 2007-05-27
Good!! Glad you got it working :D

Regards.

---

