---
title: "Errors trying to set up wifi for Atheros"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by tortis on 2008-01-11
I am a completely clueless new user, and I am trying to get my wireless to work using this tutorial:
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

First I tried the method using daily snapshots, and everything went smoothly until I entered
tar -zxvf madwifi<tab>
and it gave the error:
bash: syntax error near unexpected token `newline'

So, I tried the method that used Subversion. This is what happened:

faith@Paja-kun:~$ sudo apt-get install build-essential subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package subversion
faith@Paja-kun:~$ 

I am using a MacBook, running Ubuntu 7.10 as of yesterday, Is there anything else I can do? 
( My lack of computer knowledge is so immense, I don't even know where/how to begin learning. Please use small words and be patient. [-o< Thank you! )

output from lspci:
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

output from lsmod:
Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  2 
hci_usb                21020  2 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  7 hci_usb,rfcomm,l2cap
ppdev                  11272  0 
acpi_cpufreq           10632  0 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  2 
cpufreq_powersave       3072  0 
cpufreq_stats           8160  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     9608  0 
sbs                    21520  0 
button                 10400  0 
video                  21140  0 
ac                      7304  0 
battery                12424  0 
dock                   12264  0 
container               6400  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
joydev                 13440  0 
isight_usb             49924  0 
appleir                 8192  0 
snd_seq_dummy           5380  0 
compat_ioctl32         11136  1 isight_usb
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
videodev               31360  1 isight_usb
v4l1_compat            15364  2 isight_usb,videodev
v4l2_common            21888  3 isight_usb,compat_ioctl32,videodev
appletouch             12416  0 
xpad                   11400  0 
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
sky2                   52228  0 
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
intel_agp              30624  1 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
iTCO_wdt               13648  0 
iTCO_vendor_support     5636  1 iTCO_wdt
evdev                  13056  8 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  3 
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod
ata_generic             9988  0 
usbhid                 32576  0 
hid                    33408  1 usbhid
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ehci_hcd               40076  0 
ata_piix               20996  2 
libata                138928  2 ata_generic,ata_piix
scsi_mod              172856  5 sbp2,sg,sd_mod,sr_mod,libata
uhci_hcd               29600  0 
usbcore               161584  9 hci_usb,isight_usb,appleir,appletouch,xpad,usbhid,ehci_hcd,uhci_hcd
thermal                16528  0 
processor              36232  2 acpi_cpufreq,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

output from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Junglizer on 2008-01-11
Before you do the following run "lspci" in the command line and post the output in here. All we really need is the line that is about your network card, it should say "Atheros Communication" or something to that effect.

Here's the rundown on how I would get the madwifi drivers working, I believe they are in the package tree but I've never done it that way, and the following method should work regardless of the OS. This is compiling from source and installation/configuration is all done from the command line.

Download the current release of the madwifi drivers [http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz]("http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz"), thats the source.

Extract them and enter the newly created directory.
```

tar xvf madwifi-0.9.3.3.tar.gz
cd madwifi-0.9.3.3/

```
There should be a README or an INSTALL file, file which you can read using the less command.
```

less README

```
Pressing "q" quits from the less text viewer.
However, you can just do the following inside of the madwifi directory:
```

make clean
make
make install

```
The make process, the compile, takes about 5-10 minutes based on your system specs.
Once you've completed the 3 previous steps you can remove the directory, as all the contents have been installed in the proper locations on your system.
```

cd ..
rm -rf madwifi-0.9.3.3/

```
Using the drivers/utils:
You should now run
```

iwconfig

```
You will probably see a wifi0 device and an ath0 device. It may work right at this point, but I would recommend you start from scratch so you can see how to do this in the future.
```

wlanconfig ath0 destroy

```
This destroys the device association. We can recreate it using the following command, keep in mind that you may have to change this a bit for your system, but 9/10 times it will work just fine for most people:
```

wlanconfig ath0 create wlandev wifi0 wlanmode sta

```
We're creating an 'ath0' device to interface with the 'wifi0' kind of "front-end" if you will and we are putting it in 'sta' mode, which is the most common type. Specifically "client-server" or rather you connecting to an AP.

Now you'll want to find which AP's to connect to, so we scan for availble ones:
```

iwlist ath0 scan | more

```
Chances are pretty good taht you'll find your home AP in the list, we'll call it "homeAP" for the sake of this. So we associate with that AP.
```

iwconfig ath0 essid "homeAP"

```
Now we get a network address using DHCP.
```

dhclient ath0

```
Run ifconfig or iwconfig again to see that you correctly retrived an IP address.

You may have to edit /etc/resolv.conf based on your settings.
But that's the gist of it.

---

