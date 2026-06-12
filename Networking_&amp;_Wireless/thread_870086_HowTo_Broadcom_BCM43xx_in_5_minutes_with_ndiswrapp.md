---
title: "HowTo: Broadcom BCM43xx in 5 minutes with ndiswrapper/WPA for fresh installs"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2008-07-25
[SIZE="3"][B]Note: I'm continuing the thread that has been made read-only in the archives:
"[HowTo: Broadcom 4311 in 5 minutes with ndiswrapper/WPA for fresh Feisty installs]("http://ubuntuforums.org/showthread.php?t=475963")"[/B][/SIZE]

Edit: Since I originally posted this I've also added support for other devices, so it now supports the BCM4306, BCM4310, BCM4311, BCM4312, BCM4318, and BCM4328
Edit 2: Update (Oct 2007): Gutsy Gibbon (*Ubuntu 7.10) has native support (via the restricted driver manager) that actually works, so this guide isn't strictly necessary for Gutsy. However, Gutsy's native support isn't capable of quite the same bandwidth as this ndiswrapper solution. Further, it doesn't seem to work for everyone. Fortunately, this guide also appears to be compatible with Gutsy.
Edit 3: Update (Apr 26 2008): This howto works with Hardy Heron (*Ubuntu 8.04) for many users. I've added some Hardy-specific commands that workaround an outstanding (ssb) module loading bug. Note, this howto still doesn't work for some Hardy users, for reasons we haven't fully hashed out yet, but almost certainly related to the ssb issue. Hardy users, please refrain from voting until this is worked out, but feel free to make thread posts.

I created a quick howto for myself, since I've had to install this card a few times. This howto works well for fresh installs of Feisty (and Gutsy, and Hardy), and requires no compiled packages. (This means simple apt-get installs only for most people, but there are ndiswrapper compilation instructions for those who need it.)
[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"]
BCM43xx HowTo.[/URL]

This should take less than 5 minutes.

Please report your results here or on the wiki. Others benefit from detailed feedback, so you get bonus points if you provide all of the following:

HARDY Users, Before Following the Wiki: (I need this to try to develop a module-reloading script, since Hardy users ideally should use a custom module reloader for their particular hardware.)

    * Modules and Dependencies: lsmod


All Users, After Following the Wiki
[LIST]
[*]Machine Brand and Model
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
[*]Wireless Chipset: lspci -n | grep '14e4:43'
[*]Ubuntu Version: lsb_release -d
[*]Kernel / Architecture: uname -mr
[*]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper
[*]Which version of Step 2 you used **(If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)**
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
[/LIST]

Good luck,
Jamie
Last edited by Jamie Jackson; May 6th, 2008 at 11:34 PM. Reason: hardy update

---

### Post by Jamie Jackson on 2008-07-25
> **Rastus said:**
> the driver still shows "wl". Isn't it supposed to show ndiswrapper instead? Should I unclick "enabled" in the Administration > Hardware Drivers dialog for the "wl" driver?

I await further instructions Captain Jackson.


BTW, even though we haven't got my unit working yet, this is the easiest and best maintained resource for this issue on the net that I have found. I feel sure that the problem lies mainly in my linux N00b status and I really appreciate you taking the time to assist.
R

Ahoy, matey!

Sure, you can try disabling it, then, I guess do:
```

sudo modprobe -d ndiswrapper
sudo modprobe ndiswrapper
```

And if that doesn't work, post the output of "lsmod" and "lshw -C network".

Arrrrhh,
Cap'n Jackson
P.S. Right, "wl" is not what you want to see in the lshw -C network. It should look more like:
```
 configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes 
```
P.S.S. Hands off me booty!

---

### Post by PinkFloyd102489 on 2008-07-25
It would be great if I could get bcm43 to install on my 4328 instead of ndiswrapper. I really want monitor and promiscuous mode, but ndiswrapper doesnt support it.

---

### Post by Rastus on 2008-07-25
I am back yet again.

First let me say that the captain reference was more like "oh Captain, My captain" and I was standing on my desk when I typed it but I do like the pirate touch.  Arrrrhhhh.

OK, 
Since I am using a new machine, I decided to reinstall ubuntu and start over from step 1.

I listed lsmod and lshw -C network before I did anything.  It looked like this> 
administrator@laptop4:~$ lsmod 
Module                  Size  Used by 
ipv6                  267780  10 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm 
bluetooth              61156  4 rfcomm,l2cap 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand 
cpufreq_userspace       5284  0 
sbs                    15112  0 
sbshc                   7680  1 sbs 
dock                   11280  0 
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter 
x_tables               16132  1 ip_tables 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp 
joydev                 13120  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm 
snd_hwdep              10500  1 snd_hda_intel 
snd_seq_dummy           4868  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod 
snd_seq_oss            35584  0 
serio_raw               7940  0 
ieee80211_crypt_tkip    11648  0 
snd_seq_midi            9376  0 
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl 
sky2                   47492  0 
snd_rawmidi            25760  1 snd_seq_midi 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              24836  2 snd_pcm,snd_seq 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
sdhci                  19076  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci 
video                  19856  0 
output                  4736  1 video 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
wmi_acer                9644  0 
intel_agp              25492  1 
battery                14212  0 
button                  9232  0 
ata_generic             8324  0 
ac                      6916  0 
soundcore               8800  1 snd 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt 
agpgart                34760  3 drm,intel_agp 
evdev                  13056  7 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp 
dcdbas                  9504  0 
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  1 
jbd                    48404  1 ext3 
mbcache                 9600  1 ext3 
ata_piix               19588  1 
sg                     36880  0 
sd_mod                 30720  3 
pata_acpi               8320  0 
ahci                   28420  2 
libata                159344  4 ata_generic,ata_piix,pata_acpi,ahci 
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata 
ieee1394               93752  2 sbp2,ohci1394 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal 
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon 
font                    9472  1 fbcon 
bitblit                 6784  1 fbcon 
softcursor              3072  1 bitblit 
fuse                   50708  3 
administrator@laptop4:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: 88E8040 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 12 
       serial: 00:21:9b:cd:08:21 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.100.127 latency=0 module=sky2 multicast=yes 
  *-network 
       description: Wireless interface 
       product: BCM4310 USB Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:1f:e1:5d:bb:c8 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11 
administrator@laptop4:~$ 

I went through the guide carefully using 2e drivers.
when I got done, I ran lshw -C network and lsmod again and they looked like this:> 
administrator@laptop4:~/bcm43xx$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: 88E8040 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 12 
       serial: 00:21:9b:cd:08:21 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.100.127 latency=0 module=sky2 multicast=yes 
  *-network 
       description: Wireless interface 
       product: BCM4310 USB Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:1f:e1:5d:bb:c8 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11 
administrator@laptop4:~/bcm43xx$ lsmod 
Module                  Size  Used by 
ndiswrapper           192920  0 
ipv6                  267780  10 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm 
bluetooth              61156  4 rfcomm,l2cap 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand 
cpufreq_userspace       5284  0 
sbs                    15112  0 
sbshc                   7680  1 sbs 
dock                   11280  0 
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter 
x_tables               16132  1 ip_tables 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp 
joydev                 13120  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm 
snd_hwdep              10500  1 snd_hda_intel 
snd_seq_dummy           4868  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod 
snd_seq_oss            35584  0 
serio_raw               7940  0 
ieee80211_crypt_tkip    11648  0 
snd_seq_midi            9376  0 
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl 
sky2                   47492  0 
snd_rawmidi            25760  1 snd_seq_midi 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              24836  2 snd_pcm,snd_seq 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
sdhci                  19076  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci 
video                  19856  0 
output                  4736  1 video 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
wmi_acer                9644  0 
intel_agp              25492  1 
battery                14212  0 
button                  9232  0 
ata_generic             8324  0 
ac                      6916  0 
soundcore               8800  1 snd 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt 
agpgart                34760  3 drm,intel_agp 
evdev                  13056  7 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp 
dcdbas                  9504  0 
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  1 
jbd                    48404  1 ext3 
mbcache                 9600  1 ext3 
ata_piix               19588  0 
sg                     36880  0 
sd_mod                 30720  3 
pata_acpi               8320  0 
ahci                   28420  2 
libata                159344  4 ata_generic,ata_piix,pata_acpi,ahci 
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata 
ieee1394               93752  2 sbp2,ohci1394 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal 
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon 
font                    9472  1 fbcon 
bitblit                 6784  1 fbcon 
softcursor              3072  1 bitblit 
fuse                   50708  3 
administrator@laptop4:~/bcm43xx$ 


I noted that the 'wl'driver was still listed so I tried to use the > sudo modprobe -d ndiswrapper but it said that -d was an invalid argument.

So I went to the System > Administration > Hardware drivers and unchecked the "wl" driver and rebooted.

Now I have > administrator@laptop4:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:cd:08:21
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:5d:bb:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
administrator@laptop4:~$ 


But I have the same symptoms, I can see the network and it still will not connect with my WEP key.
Suggestions?

PS I am sure that you have nice booty but I'm not that kind of guy.;)

---

### Post by Frem on 2008-07-25
The stripped down driver bundle for my card (Broadcom Corporation BCM4310 USB Controller (rev 01)) *did not work*; ndiswrapper it didn't detect the hardware after loading it. The driver in the massive ~86mb-ish exe file from Dell did, though. (I've got a Vostro 1510).

Other than that, though? Golden. Thank you very much, good sir!

---

### Post by Hasmarth on 2008-07-26
I'm having trouble with the wiki. I have a dell inspiron 5100, with a Broadcom BCM 4306 rev 02. I followed the first couple steps on the wiki, but when i get to step 3, in lshw -C network, the module=ssb. So i tried to do the temporary bugfix, but whenever i try to use a command with b43 or b43 legacy, it says it doesn't exist in /proc/modules. Does anyone know the cause of this error?

Much obliged, Hasmarth

---

### Post by pippo_jedi on 2008-07-26
Hello
now, I followed your wiki several times redoing it and trying everything

now network manager sees the wi-fi networks but isn't capable to connect to them...

I installed wlassistant and it doesn't see anything... 

I don't know what to do... help!

I think I did step 2a last time...

```
$ lspci | grep Broadcom
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
$ lspci -n | grep '14e4:43'
03:03.0 0280: 14e4:4318 (rev 02)
$ lsb_release -d
Description:	Ubuntu 8.04.1
$ uname -mr
2.6.24-19-generic x86_64

$lshw -C network
*-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: wlan0
       version: 02
       serial: 00:15:f2:57:20:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

---

### Post by Ayuthia on 2008-07-26
> **Hasmarth said:**
> I'm having trouble with the wiki. I have a dell inspiron 5100, with a Broadcom BCM 4306 rev 02. I followed the first couple steps on the wiki, but when i get to step 3, in lshw -C network, the module=ssb. So i tried to do the temporary bugfix, but whenever i try to use a command with b43 or b43 legacy, it says it doesn't exist in /proc/modules. Does anyone know the cause of this error?

Much obliged, Hasmarth
It just means that the driver is not currently loaded.  b43legacy is one word though.  I just wanted to point that out because the 4306 rev 02 is sometimes a b43legacy module intsead of the b43.

So, if you see that it does not exist, then it is ok because the module has been removed (or was never loaded) so it will not cause any conflicts.

---

### Post by Hasmarth on 2008-07-27
Ok so i odn't need it at all? cause if a search my files for b43/b43legacy, i cant find them. Would the problem be fixed if i moved them or should i just not worry about them?

---

### Post by mootpoint on 2008-07-27
Hasmarth,

Just execute the commands in 0.3, and if it says "Not found," ignore it and keep going. You'll be fine.

m00t

---

### Post by mootpoint on 2008-07-27
Testimonial:

Laptop: Compaq F572US
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
0280: 14e4:4311 (rev 02)
Ubuntu 8.04.1
2.6.24-16-generic i686

I'm not using any kernel flags at bootup (irqpoll, etc.)

Used 0.3 version of the Hardy bugfix. Everything went flawlessly. Thanks!

m00t

---

### Post by Hasmarth on 2008-07-27
> **mootpoint said:**
> Hasmarth,

Just execute the commands in 0.3, and if it says "Not found," ignore it and keep going. You'll be fine.

m00t
Sorry i don't understand excuting in 0.3, ubuntu is a totally new concept to me. Care to shed a bit of light?

---

### Post by Ayuthia on 2008-07-27
> **Hasmarth said:**
> Sorry i don't understand excuting in 0.3, ubuntu is a totally new concept to me. Care to shed a bit of light?

Modifying /etc/modprobe.d/ndiswrapper

Version 0.3

```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```
The Version 0.3 command is like a script that runs whenever ndiswrapper is being loaded.  What it will do is automatically remove the b43, b44, b43legacy, and ssb modules (the native Broadcom Linux modules for wireless (b43* modules) and wired ethernet cards (b44) then load the ndiswrapper modules, and then reload the b44 module so that the wired card will work (if you have a Broadcom wired ethernet card).

This is similar to the Trying It Temporarily section, but is the automated version.

As for the b43/b43legacy concern, you don't need to worry about it beause the Version 0.3 command will take care of it if they do exist.

---

### Post by Hasmarth on 2008-07-27
Oh i see what you meant by 0.3. I'll try it a little later and get backt o you guys. If the bug fix works, should i go back to step 3 and try that?

---

### Post by Ayuthia on 2008-07-27
> **Hasmarth said:**
> Oh i see what you meant by 0.3. I'll try it a little later and get backt o you guys. If the bug fix works, should i go back to step 3 and try that?
If you have already done these steps:
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```
you will not need to do step 3 again.  The steps in this post loads the Windows driver to ndiswrapper and creates the alias information in /etc/modprobe.d/ndiswrapper (lets ndiswrapper know to use wlan0).  It also resets all the configurations done to /etc/network/interfaces.  If this part is not done, ndiswrapper will not work.

---

### Post by Hasmarth on 2008-07-27
ok i tried 0.3 but module is still ssb in lshw -C network. I don't think i did those commands Ayuthia. I'm a little cnfused about what to do next. Any ideas?

---

### Post by Ayuthia on 2008-07-27
> **Hasmarth said:**
> ok i tried 0.3 but module is still ssb in lshw -C network. I don't think i did those commands Ayuthia. I'm a little cnfused about what to do next. Any ideas?

Let's go back and check if the driver is installed:
```
ndiswrapper -l
```
If it shows that the device/hardware is present and that bcmwl5 is the driver, then you have done those commands.  If it is not there, then you should do those steps.  There is a good chance that the ndiswrapper -m step will return an error, but that is ok.  That command verifies that only alias commands are in there.  It does not expect us to add the 0.3 steps in there.

---

### Post by Hasmarth on 2008-07-27
k it says bcml5 : invalid driver
im gonna go ahead and try those commands
okkk... looks like along with ndiswrapper -m, the first two commands came back with errors

---

### Post by bilbobagins on 2008-07-27
Hi,followed all steps,but when i check network connection after setting wep key etc i get this message wlan0:avahi.This has plagued me since Gusty can anyone tell me how to get this avahi thing to go!!!!!!!
        Bilbo :confused:

---

### Post by Ayuthia on 2008-07-27
> **Hasmarth said:**
> k it says bcml5 : invalid driver
im gonna go ahead and try those commands
okkk... looks like along with ndiswrapper -m, the first two commands came back with errors
The invalid driver message means that it does not like the driver.  You will want to remove the driver:
```
sudo ndiswrapper -e bcmwl5
```
and try again.  Just make sure that you are in the same directory as the bcmwl5.inf file and the bcmwl5.sys (32-bit) or bcmwl564.sys (64-bit) file.  To load the file again:
```
sudo modprobe -i bcmwl5.inf
ndiswrapper -l
```

---

### Post by Hasmarth on 2008-07-27
what do you mean by the same directory? i have the folder on my desktop but thats it. it has bcmwl5.inf, bcmwl5.sys, and lsbcmnds.cat

should they be some where else?

---

### Post by Ayuthia on 2008-07-27
> **Hasmarth said:**
> what do you mean by the same directory? i have the folder on my desktop but thats it. it has bcmwl5.inf, bcmwl5.sys, and lsbcmnds.cat

should they be some where else?
No.  It is fine there.  Just make sure you are in the desktop when you run the ndiswrapper -i command:
```
cd ~/Desktop
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```
I added the ndiswrapper -e command in there in case you have not removed the current driver.

---

### Post by bilbobagins on 2008-07-27
jonathan@jonathan-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wlan0
       version: 02
       serial: 00:11:50:ed:34:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
jonathan@jonathan-desktop:~$ 
THis is what is seen using the above command.BUT when I use network manager to st mt ESSID and password,all I keep getting is  wlan0:avahi
I use the applet found in "add to panel" also when I go back into network manager my password is scrambled.any ideas for a solution please.:confused:Bilbo
 UPDATE..jonathan@jonathan-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk a89308d08c05ad9f2c580dde5b51832c3d35670c2774c431cf272b96724372dd
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid BTHomeHub-ED74

auto wlan0
jonathan@jonathan-desktop:~$

---

### Post by Hasmarth on 2008-07-27
other commands are all good, except for ndiswrapper -l, it says bcml5 : invalid driver

---

### Post by bilbobagins on 2008-07-27
Just to say THANK YOU for the instructions.finally installed my broadcom 4318 by building NDISWRAPPER from source.
but still had problems with AVAHI. This was solved by installing Wicd as per their website  put in wep code added to startup list  rebooted and its all good . thanks again .a very happy bilbo  :popcorn::KS

---

### Post by Ayuthia on 2008-07-27
> **Hasmarth said:**
> other commands are all good, except for ndiswrapper -l, it says bcml5 : invalid driver

Does it say bcml5 instead of bcmwl5?  If so, remove that driver by:
```
sudo modprobe -r bcml5
```

Otherwise, are you using the driver in step 2f?

---

### Post by Hasmarth on 2008-07-27
that was a typo, sorry
Yeah i'm using the drivers from step 2f

---

### Post by Ayuthia on 2008-07-27
> **Hasmarth said:**
> that was a typo, sorry
Yeah i'm using the drivers from step 2f
You might try going to this link:
[http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&osl=EN&catid=5&impid=-1&servicetag=&SystemID=INS_PNT_P4_5100&hidos=WW1&hidlang=en&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&osl=EN&catid=5&impid=-1&servicetag=&SystemID=INS_PNT_P4_5100&hidos=WW1&hidlang=en&TabIndex=)

It is from the Dell site for the Inspiron 5100.  I am guessing that you will need the Dell-Driver from the wireless wlan section.  Hope that helps.

---

### Post by heiko_s on 2008-07-27
Just used your instructions with Hardy 8.04 and it works (using the Hardy bug procedure). Here the details:

$lsmod

Module                  Size  Used by
ipv6                  267780  8 
af_packet              23812  4 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
acpi_cpufreq           10796  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
pcmcia                 40876  0 
joydev                 13120  0 
b43                   144420  0 
rfkill                  8592  1 b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43
hci_usb                16540  2 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
yenta_socket           27276  4 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ndiswrapper           192920  0 
video                  19856  0 
output                  4736  1 video
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  6 
dcdbas                  9504  0 
snd_seq_dummy           4868  0 
serio_raw               7940  0 
battery                14212  0 
button                  9232  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
ac                      6916  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 34452  0 
intel_agp              25492  1 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
ata_piix               19588  3 
ata_generic             8324  0 
pata_acpi               8320  0 
tg3                   116228  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 hci_usb,ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  3 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


* Machine Brand and Model
  Dell Latitude D600

* Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
  02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
  02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

* Wireless Chipset: lspci -n | grep '14e4:43'
  02:03.0 0280: 14e4:4320 (rev 03)

* Ubuntu Version: lsb_release -d
  Description:	Ubuntu 8.04.1

* Kernel / Architecture: uname -mr
  2.6.24-19-generic i686

* Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
  -

* Whether or not you had to compile NDISWrapper
  No compile needed

* Which version of Step 2 you used
  I took the driver referred to on:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210373]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210373")
  (see near bottom), driver page is:
[http://www.wireless-driver.com/download/broadcom/Broadcom-4306-driver-download.htm]("http://www.wireless-driver.com/download/broadcom/Broadcom-4306-driver-download.htm")

* If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
yes !

Thanks for the great job - wish I had found this earlier!

---

### Post by Disastorm on 2008-07-28
Hi just fresh installed Hardy but when I try to apt-get ndiswrapper, it cant find it.

*nm i had to update the aptitude.

*thx i got it working.  No errors at all, although I had to use the Hardy workaround. (also used 2a)
I litteraly installed Hardy, and the first thing I did was this guide.  With the workaround, and the "make it permanent" it works fine, and i restarted my laptop and it still works.

---

### Post by Rastus on 2008-07-28
SUCCESS!

Dell Inspiron 1525

* Wireless Brand and Model  0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


* Wireless Chipset: 0b:00.0 0280: 14e4:4315 (rev 01)


Description:	Ubuntu 8.04.1


Kernel / Architecture: 2.6.24-19-generic i686


No boot options
Did Not have to recompile ndiswrapper
Used 2e but tried it with the small version of the package and had no success.  Downloaded the larger package from Dell and it worked.

No Hardy Bug Fix.

Thanks Captain Jackson.:)
:popcorn:

---

### Post by Jamie Jackson on 2008-07-28
> **Rastus said:**
> 
But I have the same symptoms, I can see the network and it still will not connect with my WEP key.
Suggestions?

PS I am sure that you have nice booty but I'm not that kind of guy.;)

I'm curious to know if it works if you turn off WEP on your AP. Could you try that and report back?

UPDATE: Just saw your new post. Would you please provide a link to the big driver file package you downloaded?

---

### Post by Jamie Jackson on 2008-07-28
> **Frem said:**
> The stripped down driver bundle for my card (Broadcom Corporation BCM4310 USB Controller (rev 01)) *did not work*; ndiswrapper it didn't detect the hardware after loading it. The driver in the massive ~86mb-ish exe file from Dell did, though. (I've got a Vostro 1510).

Other than that, though? Golden. Thank you very much, good sir!

Thanks, Frem. Please provide a link to the Dell download?

---

### Post by Jamie Jackson on 2008-07-28
I don't know why I'm getting so much extra help on this thread as compared to my old one, but thanks a lot to the folks who are giving support to others.

:popcorn:

---

### Post by BlackholeZ on 2008-07-28
I'm trying this procedure on my HP Pavilion dv8000 on a pretty fresh install of Hardy, but I've had no luck. 

My chipset is: 06:02.0 0280: 14e4:4319 (rev 02)

I tried step 2a going off the "other bcm43xx" suggestion. After going through the whole process, and using the "lshw -C network" command, I don't have any "module" specifying ssb or ndiswrapper. 
here is what it shows.

```
 *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:2c:71:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

I tried the temporary hardy fix, it now shows the module=ndiswrapper, but I still don't have any available wireless APs.
Here is the hardy fix and the network readout after:

```
dan@dan-laptop:~$ sudo rmmod b43
dan@dan-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod ssb
dan@dan-laptop:~$ sudo rmmod ndiswrapper
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo modprobe ssb
dan@dan-laptop:~$ sudo modprobe b44
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:2c:71:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

Anything I missed? Or should have done differently? I'm pretty capable with computers, but I'm new to linux. Any help will be greatly appreciated, if I need to post more info, let me know.
-Dan

---

### Post by henrich.born on 2008-07-28
The BCM94311MCG-device still doesn't work, even after installing the driver with ndiswrapper. For testing I installed another driver for an usb device (tew-424UB) and it works very well.

Here the recommended data

> root@mms-mobile:~# # HP Compaq 6720s
root@mms-mobile:~# 
root@mms-mobile:~# lspci | grep Broadcom
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
root@mms-mobile:~# 
root@mms-mobile:~# 
root@mms-mobile:~# lspci -n | grep '14e4:43'
10:00.0 0280: 14e4:4311 (rev 02)
root@mms-mobile:~# lsb_release -d
Description:	Ubuntu 8.04.1
root@mms-mobile:~# 
root@mms-mobile:~# uname -mr
2.6.24-19-generic i686

After all steps of the HowTo (1, 2a and 3) I didn't see any available wireless access point under "Wireless Networks".

Result of lshw
> root@mms-mobile:/# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:4b:89:ff:11
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-2 ip=192.168.1.42 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:bf:62:02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:03:1b:57:a3:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

With the tew-424ub-device (above "eth1") a wirless-lan-connection can be established without any problems.

> 
root@mms-mobile:/# ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:1a:4b:89:ff:11  
          inet Adresse:192.168.1.42  Bcast:255.255.255.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21a:4bff:fe89:ff11/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:265587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204729 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:100 
          RX bytes:161914370 (154.4 MB)  TX bytes:45631684 (43.5 MB)
          Basisadresse:0x4020 Speicher:e4600000-e4620000 

eth1      Link encap:Ethernet  Hardware Adresse 00:03:1b:57:a3:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:3696 (3.6 KB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:7364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7364 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:275233 (268.7 KB)  TX bytes:275233 (268.7 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:1a:73:bf:62:02  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Speicher:e4000000-e4004000 

> root@mms-mobile:/# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b/g  ESSID:"67042640"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:CC:DC:4A:6C   
          Bit Rate=24 Mb/s   
          Encryption key:off
          Link Quality=99/100  Signal level=53/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


What's going wrong? Could it be possible, that the bcm-interface is not powered on?

It would be great, if someone would be able to help me, because im really new in Linux and Ubuntu.

Thx :)

---

### Post by vanix on 2008-08-05
[COLOR="Blue"]*On my other lap...*[/COLOR]


    * Machine Brand and Model **[COLOR="Blue"]HP PAVILLION ZX5000[/COLOR]**
    * Wireless Brand and Model [COLOR="Blue"]**02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**[/COLOR]

    * Wireless Chipset: [COLOR="Blue"]**02:02.0 0280: 14e4:4320 (rev 03)**[/COLOR]
    * Ubuntu Version: 	[COLOR="Blue"]**Ubuntu 8.04.1**[/COLOR]
    * Kernel / Architecture: [COLOR="Blue"]**2.6.24-19-generic i686**[/COLOR]
    * Any extra boot options you might be using **NONE**
    * Whether or not you had to compile NDISWrapper [COLOR="Blue"]**WITHOUT COMPILE**[/COLOR]
    * Which version of Step 2 you used (If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.) [COLOR="Blue"]**USED ONE I HAD**[/COLOR]
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not [COLOR="Blue"]**VER 0.3**[/COLOR]

[COLOR="Blue"]*In my case, i couldn't make it work, the ssb and b43 were always loaded when modprobin' ndiswrapper despite they were blacklisted... 'till i found this little detail...  the fix???*[/COLOR]

```
[COLOR="Blue"]**sudo gedit /etc/initramfs-tools/initramfs.conf **[/COLOR]

```
[COLOR="Blue"]*and change*[/COLOR]

```
**DEVICE=eth0 **
```
*[COLOR="Blue"]to look like[/COLOR]*
```
**DEVICE=lo**
```

*[COLOR="Blue"]save, then [/COLOR]*

```
**[COLOR="Blue"]sudo update-initramfs -u [/COLOR]**

```
*[COLOR="Blue"]then restart and voila!... b43 has gone...[/COLOR]*
:lolflag:
[COLOR="Blue"]*Salud!os*[/COLOR]

---

### Post by Ayuthia on 2008-08-05
> **vanix said:**
> 
```
**[COLOR="Blue"]sudo update-initramfs -u [/COLOR]**

```

I think that this command is the magic one.  It appears to update the blacklisting.  I had to use it recently on one of my installs.  However, I have not pinpointed why it makes it work yet though.

---

### Post by Peter0Pan on 2008-08-06
> **Jamie Jackson said:**
> [SIZE="3"][B]Note: I'm continuing the thread that has been made read-only in the archives:
"[HowTo: Broadcom 4311 in 5 minutes with ndiswrapper/WPA for fresh Feisty installs]("http://ubuntuforums.org/showthread.php?t=475963")"[/B][/SIZE]

Edit: Since I originally posted this I've also added support for other devices, so it now supports the BCM4306, BCM4310, BCM4311, BCM4312, BCM4318, and BCM4328
Edit 2: Update (Oct 2007): Gutsy Gibbon (*Ubuntu 7.10) has native support (via the restricted driver manager) that actually works, so this guide isn't strictly necessary for Gutsy. However, Gutsy's native support isn't capable of quite the same bandwidth as this ndiswrapper solution. Further, it doesn't seem to work for everyone. Fortunately, this guide also appears to be compatible with Gutsy.
Edit 3: Update (Apr 26 2008): This howto works with Hardy Heron (*Ubuntu 8.04) for many users. I've added some Hardy-specific commands that workaround an outstanding (ssb) module loading bug. Note, this howto still doesn't work for some Hardy users, for reasons we haven't fully hashed out yet, but almost certainly related to the ssb issue. Hardy users, please refrain from voting until this is worked out, but feel free to make thread posts.

I created a quick howto for myself, since I've had to install this card a few times. This howto works well for fresh installs of Feisty (and Gutsy, and Hardy), and requires no compiled packages. (This means simple apt-get installs only for most people, but there are ndiswrapper compilation instructions for those who need it.)
[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"]
BCM43xx HowTo.[/URL]

This should take less than 5 minutes.

Please report your results here or on the wiki. Others benefit from detailed feedback, so you get bonus points if you provide all of the following:

HARDY Users, Before Following the Wiki: (I need this to try to develop a module-reloading script, since Hardy users ideally should use a custom module reloader for their particular hardware.)

    * Modules and Dependencies: lsmod


All Users, After Following the Wiki
[LIST]
[*]Machine Brand and Model
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
[*]Wireless Chipset: lspci -n | grep '14e4:43'
[*]Ubuntu Version: lsb_release -d
[*]Kernel / Architecture: uname -mr
[*]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper
[*]Which version of Step 2 you used **(If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)**
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
[/LIST]

Good luck,
Jamie
Last edited by Jamie Jackson; May 6th, 2008 at 11:34 PM. Reason: hardy update

Hi Jamie,

Incredible work for fresh install. And it works perfect till I reboot the system. As soon as I reboot the system, the network manager doesn't show any wireless option at all. The lspci | grep Broadcom return nothing. iconfig returns - no wireless connections (for both lo & eth0). Worst: A fresh install after that doesn't solve the problem, if it does then again a reboot messes it up. Though wired works each time. Can you please help? :(

The last thing I tried was the tutorial at:
[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

I am positing the results of the commands:

```

maya@Maya-Laptop:~$ lspci | grep Broadcom
maya@Maya-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

maya@Maya-Laptop:~$ 

```

Answers to your questions:
[List]
[*]Machine Brand and Model
HP dv6361eu
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
Broadcom 4312 (rev 01)
[*]Wireless Chipset: lspci -n | grep '14e4:43'
14e4:43
[*]Ubuntu Version: lsb_release -d
8.04.01
[*]Kernel / Architecture: uname -mr
2.6.24-19-generic i686
[*]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
None
[*]Whether or not you had to compile NDISWrapper
Yes
[*]Which version of Step 2 you used.
Step 2b
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
Yes
[/list]

---

### Post by Ayuthia on 2008-08-06
> **Peter0Pan said:**
> Hi Jamie,

Incredible work for fresh install. And it works perfect till I reboot the system. As soon as I reboot the system, the network manager doesn't show any wireless option at all. The lspci | grep Broadcom return nothing. iconfig returns - no wireless connections (for both lo & eth0). Worst: A fresh install after that doesn't solve the problem, if it does then again a reboot messes it up. Though wired works each time. Can you please help? :(

The last thing I tried was the tutorial at:
[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

I am positing the results of the commands:

```

maya@Maya-Laptop:~$ lspci | grep Broadcom
maya@Maya-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

maya@Maya-Laptop:~$ 

```

Answers to your questions:
[List]
[*]Machine Brand and Model
HP dv6361eu
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
Broadcom 4312 (rev 01)
[*]Wireless Chipset: lspci -n | grep '14e4:43'
14e4:43
[*]Ubuntu Version: lsb_release -d
8.04.01
[*]Kernel / Architecture: uname -mr
2.6.24-19-generic i686
[*]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
None
[*]Whether or not you had to compile NDISWrapper
Yes
[*]Which version of Step 2 you used.
Step 2b
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
Yes
[/list]
By any chance are you dual-booting?  If so, can you try and see if you can connect on the other operating system?  I know that some HP laptops have been running into problems where the motherboard overheats and causes problems with the wireless.  My laptop had that problem and had to get serviced.  From what I have known, if your wireless card was shown in lspci and then it disappears, it usually is a hardware problem.

---

### Post by Jamie Jackson on 2008-08-06
> **BlackholeZ said:**
> I'm trying this procedure on my HP Pavilion dv8000 on a pretty fresh install of Hardy, but I've had no luck. 

My chipset is: 06:02.0 0280: 14e4:4319 (rev 02)

I tried step 2a going off the "other bcm43xx" suggestion. After going through the whole process, and using the "lshw -C network" command, I don't have any "module" specifying ssb or ndiswrapper. 
here is what it shows.
 *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:2c:71:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I tried the temporary hardy fix, it now shows the module=ndiswrapper, but I still don't have any available wireless APs.
Here is the hardy fix and the network readout after:

dan@dan-laptop:~$ sudo rmmod b43
dan@dan-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod ssb
dan@dan-laptop:~$ sudo rmmod ndiswrapper
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo modprobe ssb
dan@dan-laptop:~$ sudo modprobe b44
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:2c:71:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes

Anything I missed? Or should have done differently? I'm pretty capable with computers, but I'm new to linux. Any help will be greatly appreciated, if I need to post more info, let me know.
-Dan

Please post the output of "lsmod"

---

### Post by Jamie Jackson on 2008-08-06
> **Peter0Pan said:**
> Hi Jamie,

Incredible work for fresh install. And it works perfect till I reboot the system. As soon as I reboot the system, the network manager doesn't show any wireless option at all. The lspci | grep Broadcom return nothing. iconfig returns - no wireless connections (for both lo & eth0). Worst: A fresh install after that doesn't solve the problem, if it does then again a reboot messes it up. Though wired works each time. Can you please help? :(

The last thing I tried was the tutorial at:
[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

I am positing the results of the commands:

```

maya@Maya-Laptop:~$ lspci | grep Broadcom
maya@Maya-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

maya@Maya-Laptop:~$ 

```

Answers to your questions:
[List]
[*]Machine Brand and Model
HP dv6361eu
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
Broadcom 4312 (rev 01)
[*]Wireless Chipset: lspci -n | grep '14e4:43'
14e4:43
[*]Ubuntu Version: lsb_release -d
8.04.01
[*]Kernel / Architecture: uname -mr
2.6.24-19-generic i686
[*]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
None
[*]Whether or not you had to compile NDISWrapper
Yes
[*]Which version of Step 2 you used.
Step 2b
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
Yes
[/list]

Okay, so "trying it temporarily" worked, but the permanent fix did not?

Please "sudo gedit /etc/modprobe.d/ndiswrapper" and comment out the line after "#Hardy ssb/ndiswrapper workaround, added..."

Then, reboot (you won't have wireless, so don't expect it), and post the output of "lsmod" I want to give you a custom string to put in /etc/modprove.d/ndiswrapper, based on what you post.

---

### Post by Jamie Jackson on 2008-08-06
> **BlackholeZ said:**
> I'm trying this procedure on my HP Pavilion dv8000 on a pretty fresh install of Hardy, but I've had no luck. 

My chipset is: 06:02.0 0280: 14e4:4319 (rev 02)

I tried step 2a going off the "other bcm43xx" suggestion. After going through the whole process, and using the "lshw -C network" command, I don't have any "module" specifying ssb or ndiswrapper. 
here is what it shows.
 *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:2c:71:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I tried the temporary hardy fix, it now shows the module=ndiswrapper, but I still don't have any available wireless APs.
Here is the hardy fix and the network readout after:

dan@dan-laptop:~$ sudo rmmod b43
dan@dan-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod ssb
dan@dan-laptop:~$ sudo rmmod ndiswrapper
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo modprobe ssb
dan@dan-laptop:~$ sudo modprobe b44
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:2c:71:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes

Anything I missed? Or should have done differently? I'm pretty capable with computers, but I'm new to linux. Any help will be greatly appreciated, if I need to post more info, let me know.
-Dan

Try the XP drivers from the [HP site]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=500449") (this link assumes dv8000 and not dv8000t).

It's confusing that they list two wireless drivers on the site, but try the first (most recent) one first: 
Broadcom Wireless LAN Driver 05-2006 6.00 A Version: 4.12M

See [this]("http://ubuntuforums.org/showpost.php?p=3767216&postcount=273") for trying a new driver.

If you get it working, please report back exactly which driver download link you used, so I can incorporate this chipset/driver into the wiki.

---

### Post by Jamie Jackson on 2008-08-06
> **vanix said:**
> 

```
**[COLOR="Blue"]sudo update-initramfs -u [/COLOR]**

```
*[COLOR="Blue"]then restart and voila!... b43 has gone...[/COLOR]*
:lolflag:
[COLOR="Blue"]*Salud!os*[/COLOR]

Can anyone give me some info on why this works, and a gauge for it's "hackiness?"

---

### Post by MrPickle12481632 on 2008-08-07
First off, after using the commands in v0.3, it didn't carry through past the install. I also seem to be unable to add ndiswrapper to the modules anymore, due to the line of code "--ingnore-install".

One thing I'm seeing, when I run ndiswrapper -l, it shows the driver of my wireless card:

> bcmwl5 : driver installed
        device (14e4:4324) present (alternate driver:ssb)


Is there any way to simply remove that alternate?

---

### Post by Ayuthia on 2008-08-07
> **MrPickle12481632 said:**
> First off, after using the commands in v0.3, it didn't carry through past the install. I also seem to be unable to add ndiswrapper to the modules anymore, due to the line of code "--ingnore-install".

One thing I'm seeing, when I run ndiswrapper -l, it shows the driver of my wireless card:



Is there any way to simply remove that alternate?

The alternate driver message usually does not go away but it should cause no problems.  The main concern is that it does not get loaded before ndiswrapper.  Some people will need to have ssb because their wired ethernet card is also from Broadcom and uses the b44 driver.  The b43 (wireless) and b44(wired) need to have ssb.  However, ssb does interfere with ndiswrapper because it will grab the wireless before ndiswrapper can.  That is why ssb needs to be loaded after ndiswrapper.

As for --ingnore-install, did you type it incorrectly so it is not loading ndiswrapper?  If so, you can update the file:
```
gksu gedit /etc/modprobe.d/ndiswrapper
```

---

### Post by Peter0Pan on 2008-08-07
> **Jamie Jackson said:**
> Okay, so "trying it temporarily" worked, but the permanent fix did not?

Please "sudo gedit /etc/modprobe.d/ndiswrapper" and comment out the line after "#Hardy ssb/ndiswrapper workaround, added..."

Then, reboot (you won't have wireless, so don't expect it), and post the output of "lsmod" I want to give you a custom string to put in /etc/modprove.d/ndiswrapper, based on what you post.

> **Ayuthia said:**
> By any chance are you dual-booting?  If so, can you try and see if you can connect on the other operating system?  I know that some HP laptops have been running into problems where the motherboard overheats and causes problems with the wireless.  My laptop had that problem and had to get serviced.  From what I have known, if your wireless card was shown in lspci and then it disappears, it usually is a hardware problem.

Hi Ayuthia,
Well no dual boot just Ubuntu.
But what I tried was to remove Ubuntu, install XP to see if Wireless works and it did. I am back on Ubuntu now and the card is not detected on fresh install. 
Overheating problem - Yes I had that but not due to wireless card but cause of the graphics card. The issue was solved by HP 5 months ago, now there is no over heating whatsoever.


Hi Jamie,
Yes temporary worked (had to apply Hardy fix). Followed the permanent steps, enjoyed wireless for sometime and restart - kaboom: no wireless internet, no wireless option in network manager, no wireless interfaces detected. Just wired. Did a fresh install just now and still no luck for wireless. Can't even follow your tutorial :(

The following code is in a fresh install (no configuration changes done)
Also attached is the system log in case that helps for diagnosis. 

lspci result:
```

maya@Maya-Laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
maya@Maya-Laptop:~$

```

lspci | grep Broadcom result:
```

maya@Maya-Laptop:~$ lspci | grep Broadcom
maya@Maya-Laptop:~$

```


iwlist scan result
```

maya@Maya-Laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
maya@Maya-Laptop:~$

```

iwconfig result
```

maya@Maya-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
maya@Maya-Laptop:~$

```

lshw -C network result
```

maya@Maya-Laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
maya@Maya-Laptop:~$       

```

lsmod result:
```

maya@Maya-Laptop:~$ lsmod
Module                  Size  Used by
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
uvcvideo               58116  0 
evdev                  13056  8 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
hci_usb                16540  2 
sdhci                  19076  0 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 
agpgart                34760  0 
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
serio_raw               7940  0 
snd_seq_midi            9376  0 
psmouse                40336  0 
snd_rawmidi            25760  1 snd_seq_midi
wmi_acer                9644  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
button                  9232  0 
i2c_nforce2             7680  0 
k8temp                  6656  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  1 i2c_nforce2
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sd_mod                 30720  3 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sata_nv                27528  2 
pata_amd               14212  0 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
ehci_hcd               37900  0 
forcedeth              51980  0 
libata                159344  4 sata_nv,pata_amd,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sd_mod,sg,sr_mod,libata
ohci_hcd               25348  0 
usbcore               146028  6 uvcvideo,hci_usb,usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  4 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
maya@Maya-Laptop:~$

```

---

### Post by MrPickle12481632 on 2008-08-07
Actually, strange as this sounds, I removed the entire init code from the ndiswrapper file, reinstalled ndiswrapper, and went through the steps to get the temp fix in.

After that, I installed about 90-something updates that had been released since that point in time, and now it works perfectly:KS! Did someone release a fix in the past few days?

---

### Post by Jamie Jackson on 2008-08-07
> **Peter0Pan said:**
> Hi Ayuthia,
Well no dual boot just Ubuntu.
But what I tried was to remove Ubuntu, install XP to see if Wireless works and it did. I am back on Ubuntu now and the card is not detected on fresh install. 
Overheating problem - Yes I had that but not due to wireless card but cause of the graphics card. The issue was solved by HP 5 months ago, now there is no over heating whatsoever.


Hi Jamie,
Yes temporary worked (had to apply Hardy fix). Followed the permanent steps, enjoyed wireless for sometime and restart - kaboom: no wireless internet, no wireless option in network manager, no wireless interfaces detected. Just wired. Did a fresh install just now and still no luck for wireless. Can't even follow your tutorial :(

The following code is in a fresh install (no configuration changes done)
Also attached is the system log in case that helps for diagnosis. 

lspci result:
```

maya@Maya-Laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
maya@Maya-Laptop:~$

```

lspci | grep Broadcom result:
```

maya@Maya-Laptop:~$ lspci | grep Broadcom
maya@Maya-Laptop:~$

```


iwlist scan result
```

maya@Maya-Laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
maya@Maya-Laptop:~$

```

iwconfig result
```

maya@Maya-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
maya@Maya-Laptop:~$

```

lshw -C network result
```

maya@Maya-Laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
maya@Maya-Laptop:~$       

```

lsmod result:
```

maya@Maya-Laptop:~$ lsmod
Module                  Size  Used by
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
uvcvideo               58116  0 
evdev                  13056  8 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
hci_usb                16540  2 
sdhci                  19076  0 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 
agpgart                34760  0 
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
serio_raw               7940  0 
snd_seq_midi            9376  0 
psmouse                40336  0 
snd_rawmidi            25760  1 snd_seq_midi
wmi_acer                9644  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
button                  9232  0 
i2c_nforce2             7680  0 
k8temp                  6656  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  1 i2c_nforce2
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sd_mod                 30720  3 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sata_nv                27528  2 
pata_amd               14212  0 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
ehci_hcd               37900  0 
forcedeth              51980  0 
libata                159344  4 sata_nv,pata_amd,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sd_mod,sg,sr_mod,libata
ohci_hcd               25348  0 
usbcore               146028  6 uvcvideo,hci_usb,usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  4 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
maya@Maya-Laptop:~$

```

Bah! What happened to the device? "lspci | grep Broadcom" should show *something*. Until it does, I don't know what the heck to do.

Update: Here's a shot in the dark, and hopefully I'm wrong. Some cards get an automatic firmware update in Windows that borks them in Linux (this part, I know). This would seem to fit the clues you've provided. I'm probably wrong that this is what's happened to you, though.

---

### Post by Jamie Jackson on 2008-08-07
> **MrPickle12481632 said:**
> Actually, strange as this sounds, I removed the entire init code from the ndiswrapper file, reinstalled ndiswrapper, and went through the steps to get the temp fix in.

After that, I installed about 90-something updates that had been released since that point in time, and now it works perfectly:KS! Did someone release a fix in the past few days?

It seems to be a moving target. Wait another week, and they'll do something to break it again. ;-)

---

### Post by pippo_jedi on 2008-08-08
> **pippo_jedi said:**
> Hello
now, I followed your wiki several times redoing it and trying everything

now network manager sees the wi-fi networks but isn't capable to connect to them...

I installed wlassistant and it doesn't see anything... 

I don't know what to do... help!

I think I did step 2a last time...

```
$ lspci | grep Broadcom
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
$ lspci -n | grep '14e4:43'
03:03.0 0280: 14e4:4318 (rev 02)
$ lsb_release -d
Description:	Ubuntu 8.04.1
$ uname -mr
2.6.24-19-generic x86_64

$lshw -C network
*-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: wlan0
       version: 02
       serial: 00:15:f2:57:20:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

hello, I want to tell I've found a way to make it work.
the problem is that the acpi shipped with hardy isn't working good and the is bug open on it(or so I understood).
now I have my fn+f2 configured and it 'wake up' the wlan card, so wicd can make it work.
thank you.
if you have the same notebook (asus a7d) and have problems feel free to contact me

---

### Post by BlackholeZ on 2008-08-11
> **Jamie Jackson said:**
> Please post the output of "lsmod"

> **Jamie Jackson said:**
> Try the XP drivers from the [HP site]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=500449") (this link assumes dv8000 and not dv8000t).

It's confusing that they list two wireless drivers on the site, but try the first (most recent) one first: 
Broadcom Wireless LAN Driver 05-2006 6.00 A Version: 4.12M

See [this]("http://ubuntuforums.org/showpost.php?p=3767216&postcount=273") for trying a new driver.

If you get it working, please report back exactly which driver download link you used, so I can incorporate this chipset/driver into the wiki.

Sorry, I've been away from the internet for a bit. I will try the suggested drivers, and once I get it working, I will definitely let you know what worked. Here is my lsmod:

```
dan@dan-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
ipv6                  267780  8 
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5504  0 
ppdev                  10372  0 
powernow_k8            16704  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
sg                     36880  0 
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_atiixp_modem       17544  5 
snd_atiixp             21388  3 
snd_ac97_codec        101028  2 snd_atiixp_modem,snd_atiixp
ac97_bus                3072  1 snd_ac97_codec
b43                   144420  0 
sd_mod                 30720  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
snd_pcm                78596  6 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
cfg80211               15112  1 mac80211
fglrx                1555468  20 
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
battery                14212  0 
snd_rawmidi            25760  1 snd_seq_midi
ac                      6916  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
tifm_7xx1               8576  0 
sdhci                  19076  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                40336  0 
tifm_core              11012  1 tifm_7xx1
mmc_core               51460  1 sdhci
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi_acer                9644  0 
button                  9232  0 
snd                    56996  26 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
i2c_piix4               9612  0 
ati_agp                 9996  0 
snd_page_alloc         11400  3 snd_atiixp_modem,snd_atiixp,snd_pcm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  1 i2c_piix4
agpgart                34760  2 fglrx,ati_agp
k8temp                  6656  0 
evdev                  13056  8 
pcspkr                  4224  0 
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
ide_cd                 32544  0 
cdrom                  37408  1 ide_cd
ide_disk               17536  5 
pata_acpi               8320  0 
pata_atiixp             8960  0 
8139cp                 24704  0 
ata_generic             8324  0 
libata                159344  3 pata_acpi,pata_atiixp,ata_generic
usb_storage            73664  1 
scsi_mod              151436  5 sbp2,sg,sd_mod,libata,usb_storage
libusual               19108  1 usb_storage
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ssb                    34308  1 b43
atiixp                  5648  0 [permanent]
ide_core              113996  3 ide_cd,ide_disk,atiixp
ehci_hcd               37900  0 
ohci_hcd               25348  0 
usbcore               146028  6 ndiswrapper,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  3 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```

Thanks for the help,
Dan

---

### Post by BlackholeZ on 2008-08-11
Tried the latest driver you suggested, restarted, still no wireless. lshw -C network did not show any "module=ndiswrapper" or "module=ssb." so I did the temp hardy fix. Now it shows ""module=ndiswrapper" but I still don't have any available APs. Should I try the older drivers? I will probably do that after lunch.
Here is the readout from everything i did.

```
dan@dan-laptop:~$ sudo modprobe -r ndiswrapper
[sudo] password for dan: 
dan@dan-laptop:~$ sudo modprobe -r ndiswrapper
dan@dan-laptop:~$ sudo ndiswrapper -r bcmwl5
dan@dan-laptop:~$ wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
--11:25:49--  [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe'
Resolving ftp.hp.com... 15.201.49.21, 15.192.45.138
Connecting to ftp.hp.com|15.201.49.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.
Length: 4,318,656 (4.1M) (unauthoritative)

100%[====================================>] 4,318,656    141.31K/s    ETA 00:00

11:26:21 (137.92 KB/s) - `sp33008.exe' saved [4318656]

dan@dan-laptop:~$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
dan@dan-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
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
dan@dan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4319) present (alternate driver: bcm43xx)
dan@dan-laptop:~$ sudo depmod -a
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
dan@dan-laptop:~$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

dan@dan-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

dan@dan-laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
dan@dan-laptop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:2c:71:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
dan@dan-laptop:~$ 
```

RESTARTED

```
dan@dan-laptop:~$ sudo rmmod b43
[sudo] password for dan: 
dan@dan-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod b43legacy #this step added Apr 27 2008
ERROR: Module b43legacy does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod ssb
dan@dan-laptop:~$ sudo rmmod ndiswrapper
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo modprobe ssb
dan@dan-laptop:~$ sudo modprobe b44 #this step added May 1 2008
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:2c:71:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
dan@dan-laptop:~$
```

---

### Post by mpm on 2008-08-11
Thanks, worked like a charm!

Compaq presario f700
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
03:00.0 0280: 14e4:4311 (rev 02)
Hardy 8.04
2.6.24-19-generic x86_64
no extra boot options
no compiling necessary
step 2a used 
used the hardy workaround (yet module=ssb was listed in the first section)
output of lshw -C network only one section after workaround (included below)

 *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:c5:db:e4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.1.107 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


users should be careful with -l in command line, as it often appears to be the number one (1)

worked well when other fwcutter fixes only allowed access to a few wireless routers

---

### Post by Ayuthia on 2008-08-11
> **BlackholeZ said:**
> Tried the latest driver you suggested, restarted, still no wireless. lshw -C network did not show any "module=ndiswrapper" or "module=ssb." so I did the temp hardy fix. Now it shows ""module=ndiswrapper" but I still don't have any available APs. Should I try the older drivers? I will probably do that after lunch.
Here is the readout from everything i did. I don't know how to code the fancy scrollable text boxes, so if my long posts annoy people, maybe you could fill me in. 


dan@dan-laptop:~$ sudo modprobe -r ndiswrapper
[sudo] password for dan: 
dan@dan-laptop:~$ sudo modprobe -r ndiswrapper
dan@dan-laptop:~$ sudo ndiswrapper -r bcmwl5
dan@dan-laptop:~$ wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
--11:25:49--  [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe'
Resolving ftp.hp.com... 15.201.49.21, 15.192.45.138
Connecting to ftp.hp.com|15.201.49.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.
Length: 4,318,656 (4.1M) (unauthoritative)

100%[====================================>] 4,318,656    141.31K/s    ETA 00:00

11:26:21 (137.92 KB/s) - `sp33008.exe' saved [4318656]

dan@dan-laptop:~$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
dan@dan-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
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
dan@dan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4319) present (alternate driver: bcm43xx)
dan@dan-laptop:~$ sudo depmod -a
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
dan@dan-laptop:~$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

dan@dan-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

dan@dan-laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
dan@dan-laptop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:2c:71:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
dan@dan-laptop:~$ 

RESTARTED

dan@dan-laptop:~$ sudo rmmod b43
[sudo] password for dan: 
dan@dan-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod b43legacy #this step added Apr 27 2008
ERROR: Module b43legacy does not exist in /proc/modules
dan@dan-laptop:~$ sudo rmmod ssb
dan@dan-laptop:~$ sudo rmmod ndiswrapper
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo modprobe ssb
dan@dan-laptop:~$ sudo modprobe b44 #this step added May 1 2008
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:2c:71:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
dan@dan-laptop:~$

Can you post the results of:
```
lspci -nnm
uname -a
```
I want to see the subvendor information for your card, kernel version, and 32/64-bit version you are using.  You have a 4311 rev 02 card, but it shows a 4319 chipset so I would like to see if the subvendor matches up with the windows driver you downloaded.

---

### Post by BlackholeZ on 2008-08-12
> **Ayuthia said:**
> Can you post the results of:
```
lspci -nnm
uname -a
```
I want to see the subvendor information for your card, kernel version, and 32/64-bit version you are using.  You have a 4311 rev 02 card, but it shows a 4319 chipset so I would like to see if the subvendor matches up with the windows driver you downloaded.

Here:

```
dan@dan-laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS480 Host Bridge [5950]" -r01 "Hewlett-Packard Company [103c]" "Unknown device [309b]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a3f]" "" ""
00:04.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a36]" "" ""
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]" -p10 "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]" -p10 "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]" -p20 "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "IXP SB400 SMBus Controller [4372]" -r11 "Hewlett-Packard Company [103c]" "Unknown device [309b]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "IXP SB400 IDE Controller [4376]" -p8a "Hewlett-Packard Company [103c]" "Unknown device [309b]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-ISA Bridge [4377]" "" ""
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-PCI Bridge [4371]" -p01 "" ""
00:14.5 "Multimedia audio controller [0401]" "ATI Technologies Inc [1002]" "IXP SB400 AC'97 Audio Controller [4370]" -r02 "Hewlett-Packard Company [103c]" "Unknown device [309b]"
00:14.6 "Modem [0703]" "ATI Technologies Inc [1002]" "SB400 AC'97 Modem Controller [4378]" -r02 "Hewlett-Packard Company [103c]" "Unknown device [309b]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon XPRESS 200M 5955 (PCIE) [5955]" "Hewlett-Packard Company [103c]" "Unknown device [309b]"
06:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [4319]" -r02 "Hewlett-Packard Company [103c]" "Broadcom 802.11a/b/g WLAN [1358]"
06:04.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCIxx21/x515 Cardbus Controller [8031]" "Hewlett-Packard Company [103c]" "Unknown device [309b]"
06:04.2 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "OHCI Compliant IEEE 1394 Host Controller [8032]" -p10 "Hewlett-Packard Company [103c]" "Unknown device [309b]"
06:04.3 "Mass storage controller [0180]" "Texas Instruments [104c]" "PCIxx21 Integrated FlashMedia Controller [8033]" "Hewlett-Packard Company [103c]" "Unknown device [309b]"
06:04.4 "SD Host controller [0805]" "Texas Instruments [104c]" "PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [8034]" "Hewlett-Packard Company [103c]" "Unknown device [309b]"
06:06.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Hewlett-Packard Company [103c]" "Unknown device [309b]"
dan@dan-laptop:~$ uname -a
Linux dan-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
dan@dan-laptop:~$ 
```

---

### Post by Jamie Jackson on 2008-08-12
> **BlackholeZ said:**
> Sorry, I've been away from the internet for a bit. I will try the suggested drivers, and once I get it working, I will definitely let you know what worked. Here is my lsmod:

dan@dan-laptop:~$ lsmod

It seems you still need to find the right driver, but in the meantime, here are your custom temporary and permanent (respectively) commands.

```
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

/etc/modprobe.d/ndiswrapper
```
install ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;
```

---

### Post by Jamie Jackson on 2008-08-12
> **BlackholeZ said:**
> Tried the latest driver you suggested, restarted, still no wireless. lshw -C network did not show any "module=ndiswrapper" or "module=ssb." so I did the temp hardy fix. Now it shows ""module=ndiswrapper" but I still don't have any available APs. Should I try the older drivers? I will probably do that after lunch.Yeah, it doesn't hurt to try them.>  
Here is the readout from everything i did. I don't know how to code the fancy scrollable text boxes, so if my long posts annoy people, maybe you could fill me in. 

You just surround the code with [ code ] [ /code ] , or click the "#" button on the post editor.

---

### Post by BlackholeZ on 2008-08-12
> **Jamie Jackson said:**
> You just surround the code with [ code ] [ /code ] , or click the "#" button on the post editor.

Thanks, posts fixed.

> **Jamie Jackson said:**
> It seems you still need to find the right driver, but in the meantime, here are your custom temporary and permanent (respectively) commands.

```
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

/etc/modprobe.d/ndiswrapper
```
install ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;
```

I tried the temp, and lshw -C network now shows what I think should be good, only one wireless network, and module=ndiswrapper, but I still don't have any wireless APs. I try the other command you gave me, and it tells me permission denied. 
here:

```
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:2c:71:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
dan@dan-laptop:~$ sudo rmmod b43
dan@dan-laptop:~$ sudo rmmod ssb
dan@dan-laptop:~$ sudo rmmod ndiswrapper
dan@dan-laptop:~$ sudo modprobe ndiswrapper
dan@dan-laptop:~$ sudo modprobe ssb
dan@dan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:2c:71:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bb:ff:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.233.167 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
dan@dan-laptop:~$ /etc/modprobe.d/ndiswrapper
bash: /etc/modprobe.d/ndiswrapper: Permission denied
```

---

### Post by Jamie Jackson on 2008-08-12
> **BlackholeZ said:**
> Thanks, posts fixed.



I tried the temp, and lshw -C network now shows what I think should be good, only one wireless network, and module=ndiswrapper, but I still don't have any wireless APs.


Right, that's what the lshw is supposed to look like. It could be that the driver's not quite right, so do try the others. Before you do that, please post the output of "iwlist wlan0 scanning".

>  I try the other command you gave me, and it tells me permission denied. 

In order to edit that file (to put in the line I recommended, and to remove the previously inserted line), issue "gksu gedit /etc/modprobe.d/ndiswrapper"

---

### Post by BlackholeZ on 2008-08-12
> **Jamie Jackson said:**
> Right, that's what the lshw is supposed to look like. It could be that the driver's not quite right, so do try the others. Before you do that, please post the output of "iwlist wlan0 scanning".

I've tried the new driver you listed and went back and tried the step 2a drivers again, both times lshw -c network readout looks correct, and the command you asked me to run had the same results:
```
dan@dan-laptop:~$ iwlist wlan0 scanning
wlan0     No scan results

dan@dan-laptop:~$ 
```


> **Jamie Jackson said:**
> In order to edit that file (to put in the line I recommended, and to remove the previously inserted line), issue "gksu gedit /etc/modprobe.d/ndiswrapper"

so I run "gksu gedit /etc/modprobe.d/ndiswrapper" and it opens the editor. I delete the line that was there and insert 
"install ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;"
and save?

---

### Post by Jamie Jackson on 2008-08-12
> **BlackholeZ said:**
> I've tried the new driver you listed and went back and tried the step 2a drivers again, both times lshw -c network readout looks correct, and the command you asked me to run had the same results:
```
dan@dan-laptop:~$ iwlist wlan0 scanning
wlan0     No scan results

dan@dan-laptop:~$ 
```




so I run "gksu gedit /etc/modprobe.d/ndiswrapper" and it opens the editor. I delete the line that was there and insert 
"install ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;"
and save?

Yes.

Also, when I was saying to try other drivers, I meant that you could try some of the other drivers listed on that HP support page for your machine that I gave earlier (assuming that's exactly the right model of your machine). So, you can give one of those other ones a shot.

---

### Post by Kevin Aylesworth on 2008-08-12
Dell Studio 1535-125B.   0c:00.0 Network controller Broadcom Corporation BCM4312 802.11b/g (rev 01)
 -- I get inconsistent info See [1] below.  0c:00.0 0280: 14e4:4315 (rev 01). Ubuntu 8.04.1.  2.6.24-19-generic i686 32 bit.  
No extra boot options that I'm aware of.  I did not have to compile the NDISWrapper. Version 2e of Step 2 worked, 2b did not. 
I had to apply the Hardy Bug Fix, I used version 3.

[1] Right after a fresh install of Ubuntu, the wireless model is listed as BCM4310 XXXXXXX (rev 01).  I applied all updates then rebooted. 
When the computer came back up, the wl driver took control of the wireless and lspci | grep Broadcom returns: 
Broadcom Corporation BCM4312 802.11b/g (rev 01). I disabled the wl driver and rebooted. All has been fine since. 

Thanks!

---

### Post by arqbrulo on 2008-08-12
It's not working for me. The first time I tried it on my Hardy machine, I did the "temporary fix" and it was able to find wireless networks (it was taking a while so I decided to just quit). I then did the "permanent fix" and after I rebooted, nothing. I did the temp fix again and nothing. Here are my specs:

[LIST]
[*]Dell Inspiron 1720
[*]03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
[*]0c:00.0 0280: 14e4:4311 (rev 01)
[*]Description:	Ubuntu 8.04.1
[*]2.6.24-19-generic x86_64
[*]I DID compile NDISWrapper
[*]I used step 2a
[*]and as stated above, I DID apply the "Hardy Bug Fix"
[/LIST]

EDIT: Oh, boy, how stupid am I... I forgot I had my wifi switch on "off". After turning it on, I was able to connect.

---

### Post by weigh2tall on 2008-08-13
First Jamie, thanks for the great post, it's helped me get a lot further than I would have gotten on my own.  I've managed to get to where everything works except the permanent fix.  Here's the answers to the tutorial questions:

# Machine Brand and Model
Dell Inspiron 9100

# Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

# Wireless Chipset: lspci -n | grep '14e4:43'
02:03.0 0280: 14e4:4320 (rev 02)

#Ubuntu Version: lsb_release -d :: Ubuntu 8.04.1

#  Kernel/architecture (including 32 vs. 64 bit) : uname -mr :: 2.6.24-19-generic i686
# Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.) :: no extra boot options
# Whether or not you had to compile NDISWrapper  :: Have not had to compile NDISwrapper yet
# Which version of Step 2 you used :: I used step 2f
# If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not, and if you used it, which version you used
  I've tried to use v3 of the Hardy fix and it works but if I leave it I can't restart.  The computer hangs in the loading bar section of the bootup.  Eventually I get dumped to a text screen which says the hardware drivers failed to load.  

Here's the output of lsmod:

```
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0 
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
b43legacy             127776  0 
ac97_bus                3072  1 snd_ac97_codec
mac80211              165652  1 b43legacy
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
cfg80211               15112  1 mac80211
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
serio_raw               7940  0 
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ndiswrapper           192920  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
battery                14212  0 
intel_agp              25492  1 
dcdbas                  9504  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  2 drm,intel_agp
evdev                  13056  6 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_piix               19588  2 
b44                    28432  0 
mii                     6400  1 b44
ssb                    34308  2 b43legacy,b44
ata_generic             8324  0 
ohci1394               33584  0 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               27024  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```

Please let me know if you need/want more information.

Thanks again for the tutorial

---

### Post by BlackholeZ on 2008-08-13
> **Jamie Jackson said:**
> Yes.

Also, when I was saying to try other drivers, I meant that you could try some of the other drivers listed on that HP support page for your machine that I gave earlier (assuming that's exactly the right model of your machine). So, you can give one of those other ones a shot.

That is the right model, I have tried both drivers on that page, but I haven't tried the older ones recently. The plaque on the bottom of my laptop says:
Product: hp pavilion dv8000
s/n: CND551199B
p/n: EP407UA#ABA
dv8140US

_____________________________________________________________

OK, I feel like a total tool. 
 I was looking around for this dv8140US, ended up reading a review, which mentioned a "wireless switch" and indicator light. No way it could be that easy, but it's worth a try. Sure enough, now I have access points, but I can't connect to wep keyed networks. This is on the step 2a drivers. I loaded the newest drivers from the dell site and it works! 

Thanks for all the help! I'll post my info in a little bit. 
-Dan

---

### Post by BlackholeZ on 2008-08-13
# Machine Brand and Model
-HP Pavilion dv8000

# Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
-06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

# Wireless Chipset: lspci -n | grep '14e4:43'
-06:02.0 0280: 14e4:4319 (rev 02)

#Ubuntu Version: lsb_release -d
-Description:	Ubuntu 8.04.1

# Kernel/architecture (including 32 vs. 64 bit) : uname -mr 
-2.6.24-19-generic i686

# Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
-None

# Whether or not you had to compile NDISWrapper:
- Did not have to compile ndiswrapper

# Which version of Step 2 you used:
-I modified step 2a with drivers from dell:
```
dan@dan-laptop:~$ wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
--11:25:49--  ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
           => `sp33008.exe'
Resolving ftp.hp.com... 15.201.49.21, 15.192.45.138
Connecting to ftp.hp.com|15.201.49.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.
Length: 4,318,656 (4.1M) (unauthoritative)

100%[====================================>] 4,318,656    141.31K/s    ETA 00:00

11:26:21 (137.92 KB/s) - `sp33008.exe' saved [4318656]

dan@dan-laptop:~$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
dan@dan-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
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
```

# If you're on Hardy, whether you had to apply the "Hardy Bug Fix" 
-I used a custom line that Jamie gave me for ndiswrapper:
```
"gksu gedit /etc/modprobe.d/ndiswrapper"
"install ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;"
```

Thanks greatly for all the help, especially Jamie Jackson. If you need any more info from me, let me know.

Thanks,
Dan Jennings

---

### Post by intrusion on 2008-08-13
4312 rev01; inspiron 1525.

I followed 2b, and not only did it not work, but now it won't recognize ethernet :-/.

Any ideas?

---

### Post by Ayuthia on 2008-08-14
> **intrusion said:**
> 4312 rev01; inspiron 1525.

I followed 2b, and not only did it not work, but now it won't recognize ethernet :-/.

Any ideas?

Can you post the results of:
```
lshw -C network
```
It sounds like you might have a Broadcom ethernet card.  Have you tried (if you have a Broadcom 44xx series ethernet card_:
```
sudo modprobe -r b44 ssb
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by intrusion on 2008-08-14
I reinstalled :-/.  I figured it was easier.

The lshw module listing had ndiswrapper for the wireless and sky2 for the hardline ethernet.  My ethernet is a marvell yukon 88E8040 though :-/.

Here's the current output with the reinstall (not gone through the guide again out of fear):

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d9:c0:3e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.2 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:83:71:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

---

### Post by D. Y. Lewis on 2008-08-14
Well, I forgot to do "lsmod" before the wiki, but here is the rest of my info.

Fresh Install 

Acer Aspire 4520 (AMD 64 Athlon X2)

07:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

07:00.0 0280: 14e4:4311 (rev 01)

Description:	Ubuntu 8.04.1

2.6.24-19-rt x86_64    ***I believe it is rt b/c I am using Ubuntu Studio***

Don't know of any extra boot options

I Did not compile Ndiswrapper

Did step 2a

Did apply the bug fix, and it seemed to go ok.

Sadly I am still having to sit on the floor b/c I am trapped by all these wires. Network Manager is still not seeing any wireless connections. Any extra advice?

BTW very nice wiki. This is probably the best organized page on this subject. Thanks.

---

### Post by Jamie Jackson on 2008-08-14
> **BlackholeZ said:**
> That is the right model, I have tried both drivers on that page, but I haven't tried the older ones recently. The plaque on the bottom of my laptop says:
Product: hp pavilion dv8000
s/n: CND551199B
p/n: EP407UA#ABA
dv8140US

_____________________________________________________________

OK, I feel like a total tool. 
 I was looking around for this dv8140US, ended up reading a review, which mentioned a "wireless switch" and indicator light. No way it could be that easy, but it's worth a try. Sure enough, now I have access points, but I can't connect to wep keyed networks. This is on the step 2a drivers. I loaded the newest drivers from the dell site and it works! 

Thanks for all the help! I'll post my info in a little bit. 
-Dan

Woohoo! Just to make 100% I get the right download, would you post the URL? I'll add that driver to the wiki.

---

### Post by Jamie Jackson on 2008-08-14
> **BlackholeZ said:**
> That is the right model, I have tried both drivers on that page, but I haven't tried the older ones recently. The plaque on the bottom of my laptop says:
Product: hp pavilion dv8000
s/n: CND551199B
p/n: EP407UA#ABA
dv8140US

_____________________________________________________________

OK, I feel like a total tool. 
 I was looking around for this dv8140US, ended up reading a review, which mentioned a "wireless switch" and indicator light. No way it could be that easy, but it's worth a try. Sure enough, now I have access points, but I can't connect to wep keyed networks. This is on the step 2a drivers. I loaded the newest drivers from the dell site and it works! 

Thanks for all the help! I'll post my info in a little bit. 
-Dan

That's two of you who recently report being burned by the hardware switch. I'll have to add that to the wiki...

---

### Post by Jamie Jackson on 2008-08-14
> **Kevin Aylesworth said:**
> Dell Studio 1535-125B.   0c:00.0 Network controller Broadcom Corporation BCM4312 802.11b/g (rev 01)
 -- I get inconsistent info See [1] below.  0c:00.0 0280: 14e4:4315 (rev 01). Ubuntu 8.04.1.  2.6.24-19-generic i686 32 bit.  
No extra boot options that I'm aware of.  I did not have to compile the NDISWrapper. Version 2e of Step 2 worked, 2b did not. 
I had to apply the Hardy Bug Fix, I used version 3.

[1] Right after a fresh install of Ubuntu, the wireless model is listed as BCM4310 XXXXXXX (rev 01).  I applied all updates then rebooted. 
When the computer came back up, the wl driver took control of the wireless and lspci | grep Broadcom returns: 
Broadcom Corporation BCM4312 802.11b/g (rev 01). I disabled the wl driver and rebooted. All has been fine since. 

Thanks!

Which way did you disable the wl, by the way?

---

### Post by Jamie Jackson on 2008-08-14
> **weigh2tall said:**
> First Jamie, thanks for the great post, it's helped me get a lot further than I would have gotten on my own.  I've managed to get to where everything works except the permanent fix.  Here's the answers to the tutorial questions:

# Machine Brand and Model
Dell Inspiron 9100

# Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

# Wireless Chipset: lspci -n | grep '14e4:43'
02:03.0 0280: 14e4:4320 (rev 02)

#Ubuntu Version: lsb_release -d :: Ubuntu 8.04.1

#  Kernel/architecture (including 32 vs. 64 bit) : uname -mr :: 2.6.24-19-generic i686
# Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.) :: no extra boot options
# Whether or not you had to compile NDISWrapper  :: Have not had to compile NDISwrapper yet
# Which version of Step 2 you used :: I used step 2f
# If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not, and if you used it, which version you used
  I've tried to use v3 of the Hardy fix and it works but if I leave it I can't restart.  The computer hangs in the loading bar section of the bootup.  Eventually I get dumped to a text screen which says the hardware drivers failed to load.  

Here's the output of lsmod:

```
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0 
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
b43legacy             127776  0 
ac97_bus                3072  1 snd_ac97_codec
mac80211              165652  1 b43legacy
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
cfg80211               15112  1 mac80211
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
serio_raw               7940  0 
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ndiswrapper           192920  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
battery                14212  0 
intel_agp              25492  1 
dcdbas                  9504  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  2 drm,intel_agp
evdev                  13056  6 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_piix               19588  2 
b44                    28432  0 
mii                     6400  1 b44
ssb                    34308  2 b43legacy,b44
ata_generic             8324  0 
ohci1394               33584  0 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               27024  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```

Please let me know if you need/want more information.

Thanks again for the tutorial

That lsmod that you posted, was that before or after running the modprobe commands? If it's after, would you comment out everything in the /etc/modprobe.d/ndiswrapper file (if you haven't already), reboot, and re-post the lsmod? (I want to see what it looks like before you start hacking.)

After getting that clean lsmod, run the temporary fix and post all of its output.

Then, post the output of "lshw -C network", and also let me know if you can connect at this point.

---

### Post by Jamie Jackson on 2008-08-14
> **intrusion said:**
> 4312 rev01; inspiron 1525.

I followed 2b, and not only did it not work, but now it won't recognize ethernet :-/.

Any ideas?

Please comment out the "ndiswrapper" line, using "gksu gedit /etc/modules" 

UPDATE: Then, reboot. (Forgot to mention that detail.)

At this point, ndiswrapper won't be working, and your ethernet should work (as a side note).

Before doing anything else, post the output of "lsmod", so we can make sure we've got your own personal temporary and permanent fixes.

---

### Post by Jamie Jackson on 2008-08-14
> **D. Y. Lewis said:**
> Well, I forgot to do "lsmod" before the wiki, but here is the rest of my info.

Fresh Install 

Acer Aspire 4520 (AMD 64 Athlon X2)

07:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

07:00.0 0280: 14e4:4311 (rev 01)

Description:	Ubuntu 8.04.1

2.6.24-19-rt x86_64    ***I believe it is rt b/c I am using Ubuntu Studio***

Don't know of any extra boot options

I Did not compile Ndiswrapper

Did step 2a

Did apply the bug fix, and it seemed to go ok.

Sadly I am still having to sit on the floor b/c I am trapped by all these wires. Network Manager is still not seeing any wireless connections. Any extra advice?

BTW very nice wiki. This is probably the best organized page on this subject. Thanks.

Okay, let's do a few things, and in the following order:
[LIST=1]
[*]make sure you don't have a wifi hardware switch in the off position, but if it's off, turn it on and see how you do, and if you need to continue onto the next steps...
[*]post output of "lshw -C network"
[*]"gksu gedit /etc/modules" and comment out the "ndiswrapper" line
[*]reboot
[*]post the output of "lsmod"
[/LIST]

---

### Post by weigh2tall on 2008-08-14
> **Jamie Jackson said:**
> That lsmod that you posted, was that before or after running the modprobe commands? If it's after, would you comment out everything in the /etc/modprobe.d/ndiswrapper file (if you haven't already), reboot, and re-post the lsmod? (I want to see what it looks like before you start hacking.)

After getting that clean lsmod, run the temporary fix and post all of its output.

Then, post the output of "lshw -C network", and also let me know if you can connect at this point.

That was the lsmod that was output after commenting out the line that comes after the #Hardy Fix 'date' line  & I believe before I ran the modprobes... 
From an earlier post, my ndiswrapper file has several other lines proceeding it that don't make a whole lot of sense.  I'll try commenting them out and posting those results.  (It maybe this evening before I can get it all together for you) Thanks for the help so far!

_______________________________________________________________

Here's the output of the commands you requested...

modeprobe.d/ndiswrapper on initial start 

```
alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
#Hardy ssb/ndiswrapper workaround, added 11Aug2008
#install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper$
```

## At this point the computer boots and the Network manager applet shows "Wireless Networks" in the drop down but doesn't list any AP's

Going to comment all the lines out in this file and see what happens :)

```
#alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
#Hardy ssb/ndiswrapper workaround, added 11Aug2008
#install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper$
```

This is the lsmod output after rebooting with the above ndiswrapper file
```
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0 
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43legacy             127776  0 
mac80211              165652  1 b43legacy
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
cfg80211               15112  1 mac80211
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  6 
agpgart                34760  2 drm,intel_agp
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
b44                    28432  0 
ata_piix               19588  2 
ssb                    34308  2 b43legacy,b44
ohci1394               33584  0 
mii                     6400  1 b44
ata_generic             8324  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```
This is the output of ndiswrapper -l (before running anything)

```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

```

Now I'm going to run the modprobe commands for the Hardy bug fix
Here are the commands and their output
```
~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
~$ sudo rmmod b44
~$ sudo rmmod b43legacy
~$ sudo rmmod ssb
~$ sudo rmmod ndiswrapper
~$ sudo modprobe ndiswrapper
~$ sudo modprobe ssb
~$ sudo modprobe b44
```

Now I can see AP's in the Network Manager drop down
I was able to connect to a WPA encrypted network at this point

Here's the output of lshw -C network
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:14:6e:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:74:f2:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.103 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```
## The /etc/modprobe.d/ndiswrapper has not changed at this point (i.e. all the lines remain commented out)

---

### Post by D. Y. Lewis on 2008-08-14
Well your solution worked like a charm! Wasn't the switch, but it almost got me :lolflag:  But I got signal after the reboot.

```

lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:c5:6b:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=10.0.0.7 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:1d:d9:63:ed:2d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g 
``````
daniel@danlap:~$ lsmod
Module                  Size  Used by
ipv6                  319560  10 
af_packet              27784  4 
snd_rtctimer            5344  1 
rfcomm                 48416  2 
l2cap                  29312  13 rfcomm
bluetooth              69796  4 rfcomm,l2cap
rfkill_input            6784  0 
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_stats           8704  0 
cpufreq_ondemand       11280  1 
cpufreq_conservative    10632  0 
cpufreq_powersave       3200  0 
cpufreq_userspace       6308  0 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    18064  0 
container               6784  0 
sbshc                   9088  1 sbs
dock                   13392  0 
iptable_filter          4736  0 
ip_tables              24232  1 iptable_filter
x_tables               23944  1 ip_tables
sbp2                   27784  0 
parport_pc             41512  0 
lp                     16132  0 
parport                45324  3 ppdev,parport_pc,lp
loop                   22148  0 
joydev                 15872  0 
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9604  1 ecb
snd_hda_intel         440792  2 
snd_pcm_oss            48032  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                93320  2 snd_hda_intel,snd_pcm_oss
b43                   127400  0 
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
rfkill                 10512  3 rfkill_input,b43
snd_hwdep              12680  1 snd_hda_intel
mac80211              194324  1 b43
snd_seq_dummy           5764  0 
cfg80211               18064  1 mac80211
input_polldev           6928  1 b43
snd_seq_oss            39424  0 
snd_seq_midi           10688  0 
snd_rawmidi            30240  1 snd_seq_midi
serio_raw               9220  0 
psmouse                46620  0 
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
video                  23572  0 
output                  5760  1 video
snd_seq                64256  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               62596  0 
nvidia               8860260  26 
snd_timer              28424  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32         11136  1 uvcvideo
videodev               31232  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            22016  3 uvcvideo,compat_ioctl32,videodev
snd                    71880  17 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               29440  1 nvidia
acer_acpi              21976  0 
led_class               7304  2 b43,acer_acpi
wmi_acer               11204  1 acer_acpi
shpchp                 38428  0 
pci_hotplug            35760  1 shpchp
ac                      8328  0 
button                 10912  0 
battery                17032  0 
evdev                  15616  8 
sdhci                  21764  0 
mmc_core               60424  1 sdhci
ricoh_mmc               5376  0 
k8temp                  7808  0 
soundcore              11040  1 snd
pcspkr                  4992  0 
ext3                  149776  1 
jbd                    58408  1 ext3
mbcache                11776  1 ext3
sr_mod                 20516  0 
cdrom                  41384  1 sr_mod
sg                     42136  0 
sd_mod                 33920  3 
pata_amd               16900  0 
ahci                   33284  2 
pata_acpi               9984  0 
ssb                    38020  1 b43
ohci1394               37172  0 
ata_generic            10116  0 
forcedeth              55436  0 
ieee1394              109400  2 sbp2,ohci1394
libata                176816  4 pata_amd,ahci,pata_acpi,ata_generic
scsi_mod              180184  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               42252  0 
ohci_hcd               27524  0 
usbcore               171952  4 uvcvideo,ehci_hcd,ohci_hcd
thermal                20000  0 
processor              41960  3 powernow_k8,thermal
fan                     6792  0 
fuse                   57136  1 

```I have been working on this for at least a day. I don't know how I didn't find your wiki page earlier. Thank You again. I am glad to be firmly back on the couch!

---

### Post by BlackholeZ on 2008-08-14
> **Jamie Jackson said:**
> Woohoo! Just to make 100% I get the right download, would you post the URL? I'll add that driver to the wiki.

Here is the exact download link:
```
ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
```

which I got off this page:

```
http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-41607-1&lc=en&cc=us&lang=en&os=228&product=500449&dlc=en
```

---

### Post by Jamie Jackson on 2008-08-14
> **weigh2tall said:**
> That was the lsmod that was output after commenting out the line that comes after the #Hardy Fix 'date' line  & I believe before I ran the modprobes... 
From an earlier post, my ndiswrapper file has several other lines proceeding it that don't make a whole lot of sense.  I'll try commenting them out and posting those results.  (It maybe this evening before I can get it all together for you) Thanks for the help so far!

_______________________________________________________________

Here's the output of the commands you requested...

modeprobe.d/ndiswrapper on initial start 

```
alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
#Hardy ssb/ndiswrapper workaround, added 11Aug2008
#install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper$
```

## At this point the computer boots and the Network manager applet shows "Wireless Networks" in the drop down but doesn't list any AP's

Going to comment all the lines out in this file and see what happens :)

```
#alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
#Hardy ssb/ndiswrapper workaround, added 11Aug2008
#install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper$
```

This is the lsmod output after rebooting with the above ndiswrapper file
```
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0 
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43legacy             127776  0 
mac80211              165652  1 b43legacy
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
cfg80211               15112  1 mac80211
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  6 
agpgart                34760  2 drm,intel_agp
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
b44                    28432  0 
ata_piix               19588  2 
ssb                    34308  2 b43legacy,b44
ohci1394               33584  0 
mii                     6400  1 b44
ata_generic             8324  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```
This is the output of ndiswrapper -l (before running anything)

```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

```

Now I'm going to run the modprobe commands for the Hardy bug fix
Here are the commands and their output
```
~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
~$ sudo rmmod b44
~$ sudo rmmod b43legacy
~$ sudo rmmod ssb
~$ sudo rmmod ndiswrapper
~$ sudo modprobe ndiswrapper
~$ sudo modprobe ssb
~$ sudo modprobe b44
```

Now I can see AP's in the Network Manager drop down
I was able to connect to a WPA encrypted network at this point

Here's the output of lshw -C network
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:14:6e:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:74:f2:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.103 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```
## The /etc/modprobe.d/ndiswrapper has not changed at this point (i.e. all the lines remain commented out)

Your /etc/modprobe.d/ndiswrapper got borked somehow. Add the following line (use "gksu gedit /etc/modprobe.d/ndiswrapper"):

```
install ndiswrapper modprobe -r b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
```

Somehow, your line got chopped (probably due to wrapping on the wiki page).

This should get you sorted.

---

### Post by Jamie Jackson on 2008-08-14
> **BlackholeZ said:**
> Here is the exact download link:
```
ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
```

which I got off this page:

```
http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-41607-1&lc=en&cc=us&lang=en&os=228&product=500449&dlc=en
```

Interesting, thanks. Let me sum up a few things, because it gets hard to look through old posts to get all the info.

"lspci | grep Broadcom" yields "Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)", correct?

"lspci -n | grep '14e4:43'" yields "06:02.0 0280: 14e4:4319 (rev 02)", correct?

What's interesting about this is that according to your info, now two different chipsets call themselves "BCM4311 (Rev 02)", which makes it all the more important to ignore the label, and just look at the PCI ID/chipset.

A couple more things:

The driver you used is the same driver as my step 2b, so I've added your device to the device/model/driver table, and pointed people with your chipset to step 2b.

Finally, I'm curious as to whether you've tried step 2a, now that you've figured out the hardware switch issue. If you haven't tried 2a after enabling the device, would you, please? I'd like to know whether or not 2a will work for your chipset, or not.

Thanks for the info to date. It's important, since this is a new device to the wiki.

---

### Post by BlackholeZ on 2008-08-14
> **Jamie Jackson said:**
> Interesting, thanks. Let me sum up a few things, because it gets hard to look through old posts to get all the info.

"lspci | grep Broadcom" yields "Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)", correct?

"lspci -n | grep '14e4:43'" yields "06:02.0 0280: 14e4:4319 (rev 02)", correct?

What's interesting about this is that according to your info, now two different chipsets call themselves "BCM4311 (Rev 02)", which makes it all the more important to ignore the label, and just look at the PCI ID/chipset.


That is correct, the 2 different numbers was throwing me too.

> **Jamie Jackson said:**
> A couple more things:

The driver you used is the same driver as my step 2b, so I've added your device to the device/model/driver table, and pointed people with your chipset to step 2b.

Finally, I'm curious as to whether you've tried step 2a, now that you've figured out the hardware switch issue. If you haven't tried 2a after enabling the device, would you, please? I'd like to know whether or not 2a will work for your chipset, or not.

Thanks for the info to date. It's important, since this is a new device to the wiki.
When I first found the button, I was on the step 2a drivers. I could see available wireless networks, but the only one I could log in on has a WEP key, and it would not connect, just keep asking for the password like I was getting it wrong. lshw -C network looked good, and i did not have a free (unkeyed) network to try. I then switched to the new (your step2b) drivers and it worked right away. All the final data I posted was after I installed the newest (step2b) drivers.

---

### Post by weigh2tall on 2008-08-14
> **Jamie Jackson said:**
> Your /etc/modprobe.d/ndiswrapper got borked somehow. Add the following line (use "gksu gedit /etc/modprobe.d/ndiswrapper"):

```
install ndiswrapper modprobe -r b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
```

Somehow, your line got chopped (probably due to wrapping on the wiki page).

This should get you sorted.

Unfortunately,  That's what I had in it except for the b43legacy bit (because it had errored during the temp fix), but I copied yours in and am trying it again.

I'll post an edit with any updates
____________________________

Ok so I'm posting this wirelessly after a reboot!  Sooo looks like your version of the line worked.  :guitar:

Here are the two lines.... and they match with the exception of the b43legacy
```
#install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
install ndiswrapper modprobe -r b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

```

The only other change is that I commented out all the beginning lines

```
#alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper

```

I think the b43legacy line is important but I'm also going to see what happens when I uncomment the alias lines?

Thanks a million!

---

### Post by weigh2tall on 2008-08-14
> **weigh2tall said:**
> 
The only other change is that I commented out all the beginning lines

```
#alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
#alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper

```


When I rebooted with these lines active (uncommented) I was back to square one, I could see "Wireless Networks" in the Network Manager applet, but no networks.  
Commenting them out and rebooting the computer connected automatically to my AP!!

HTH, thanks for yours Jamie!

---

### Post by Kevin Aylesworth on 2008-08-14
> **Jamie Jackson said:**
> Which way did you disable the wl, by the way?
I'm in transition from Windows to Linux, so I disabled it via the GUI . . .

System-->Administration-->Hardware drivers, then unchecked the "Enabled" check box.

---

### Post by Jamie Jackson on 2008-08-15
> **BlackholeZ said:**
> That is correct, the 2 different numbers was throwing me too.


When I first found the button, I was on the step 2a drivers. I could see available wireless networks, but the only one I could log in on has a WEP key, and it would not connect, just keep asking for the password like I was getting it wrong. lshw -C network looked good, and i did not have a free (unkeyed) network to try. I then switched to the new (your step2b) drivers and it worked right away. All the final data I posted was after I installed the newest (step2b) drivers.

Got it, thanks. The wiki reflects this info now.

---

### Post by Ameet on 2008-08-17
I am not getting this working.  It is a new laptop and I am doing my best to follow the wiki.  But my networking/hardware skills are not high.  Any help would be great!
    
All Users, After Following the Wiki

[LIST]
[*][COLOR=DarkRed]Machine Brand and Model[/COLOR]
[/LIST]
Dell Inspiron 1525

[LIST]
[*][COLOR=DarkRed]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom[/COLOR]
[/LIST]
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

[LIST]
[*][COLOR=DarkRed]Wireless Chipset: lspci -n | grep '14e4:43'[/COLOR]
[/LIST]
0b:00.0 0280: 14e4:4315 (rev 01)

*Note: this does not match up with the tabl**e in the Wiki Step 2, so I'm going with the chipset ID, and following Step 2e.*

[LIST]
[*][COLOR=DarkRed]Ubuntu Version: lsb_release -d[/COLOR]
[/LIST]
Description:    Ubuntu 8.04.1

[LIST]
[*][COLOR=DarkRed]Kernel / Architecture: uname -mr[/COLOR]
[/LIST]
2.6.24-19-generic i686

[LIST]
[*][COLOR=DarkRed]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)[/COLOR]
[/LIST]
None.

[LIST]
[*][COLOR=DarkRed]Whether or not you had to compile NDISWraipper[/COLOR]
[/LIST]
n00b alert.  Not sure what this means.  So I guess the answer is "No". :confused:

[LIST]
[*][COLOR=DarkRed]Which version of Step 2 you used **(If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)**[/COLOR]
[/LIST]
I followed Step 2e.  It didn't work.  I can see the wireless networks but can't connect to mine.

[LIST]
[*][COLOR=DarkRed]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not[/COLOR]
[/LIST]
I ran "lshw -C network", and and got a wireless interface with "driver=wl"
I don't know what "ssb" is (n00b again) but it didn't say it.
I then did the "Temporary steps".  I got an error the first time on the step:
```
sudo rmmod ssb
```Then running lshw again, I see 
>       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11gHowever, I still can't connect with the wireless, even though I can see the networks.

Finally, I went to [http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R174291&SystemID=INS_PNT_PM_1525&servicetag=1TT1QF1&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R174291&SystemID=INS_PNT_PM_1525&servicetag=1TT1QF1&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819)

and downloaded the driver for "Dell Wireless 1395 WLAN MiniCard" (89 Mb).  It gives me a file called "Dell_multi-device_A17_R174291.exe".  I ran:
```

$ cabextract Dell_multi-device_A17_R174291.exe 
Dell_multi-device_A17_R174291.exe: no valid cabinets found

All done, errors in processing 1 file(s)
$ file Dell_multi-device_A17_R174291.exe 
Dell_multi-device_A17_R174291.exe: MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit

```So, any help on this?  Thanks.

---

### Post by Ayuthia on 2008-08-18
> **Ameet said:**
> 

Finally, I went to [http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R174291&SystemID=INS_PNT_PM_1525&servicetag=1TT1QF1&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R174291&SystemID=INS_PNT_PM_1525&servicetag=1TT1QF1&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=5&impid=-1&formatcnt=1&libid=5&fileid=236819)

and downloaded the driver for "Dell Wireless 1395 WLAN MiniCard" (89 Mb).  It gives me a file called "Dell_multi-device_A17_R174291.exe".  I ran:
```

$ cabextract Dell_multi-device_A17_R174291.exe 
Dell_multi-device_A17_R174291.exe: no valid cabinets found

All done, errors in processing 1 file(s)
$ file Dell_multi-device_A17_R174291.exe 
Dell_multi-device_A17_R174291.exe: MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit

```So, any help on this?  Thanks.

Dell tends to zip their .exe files so you can try to unzip it:
```
unzip Dell_multi-device_A17_R174291.exe
```

If you still cannot connect, try this:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper

```It does not look like you need the b44 module since your lspci -n |grep 14e4 did not return a Broadcom wired ethernet card.  However, if you do lose your wired connection just do the following:
```
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```
And that should get it back.  Loading the b44 module should automatically load the ssb module.

If you are still not connected, please come back and post the results of:
```
lsmod|grep -i -e wl -e b43 -e ssb -e b44 -e ndiswrapper
```

---

### Post by Ameet on 2008-08-18
> **Ayuthia said:**
> Dell tends to zip their .exe files so you can try to unzip it:
```
unzip Dell_multi-device_A17_R174291.exe
```If you still cannot connect, try this:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper

```It does not look like you need the b44 module since your lspci -n |grep 14e4 did not return a Broadcom wired ethernet card.  However, if you do lose your wired connection just do the following:
```
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```And that should get it back.  Loading the b44 module should automatically load the ssb module.

If you are still not connected, please come back and post the results of:
```
lsmod|grep -i -e wl -e b43 -e ssb -e b44 -e ndiswrapper
```

OK.  You were right about unzipping the Dell driver package, that did it.  It doesn't matter, because:
```

$ cmp bcmwl5.inf /etc/ndiswrapper/bcmwl5/bcmwl5.inf
$

```...it is identical to the driver I got from the Wiki, Step 2 "pruned" driver package.

I got no errors on the "sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43x" sequence.  Wired connection remained active, but still no wireless.  Finally:

```

$ lsmod|grep -i -e wl -e b43 -e ssb -e b44 -e ndiswrapper
b44                    28432  0 
mii                     6400  1 b44
ssb                    34308  1 b44
ndiswrapper           192920  0 
usbcore               146028  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,uhci_hcd

```Also, this is the result of lshw:
```

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:06:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.43 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:19:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

Any other info which might help diagnose the diffiiculty???
Thanks,Ameet

---

### Post by Ayuthia on 2008-08-18
> **Ameet said:**
> OK.  You were right about unzipping the Dell driver package, that did it.  It doesn't matter, because:
```

$ cmp bcmwl5.inf /etc/ndiswrapper/bcmwl5/bcmwl5.inf
$

```...it is identical to the driver I got from the Wiki, Step 2 "pruned" driver package.

I got no errors on the "sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43x" sequence.  Wired connection remained active, but still no wireless.  Finally:

```

$ lsmod|grep -i -e wl -e b43 -e ssb -e b44 -e ndiswrapper
b44                    28432  0 
mii                     6400  1 b44
ssb                    34308  1 b44
ndiswrapper           192920  0 
usbcore               146028  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,uhci_hcd

```Also, this is the result of lshw:
```

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:06:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.43 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:19:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

Any other info which might help diagnose the diffiiculty???
Thanks,Ameet

If you are not using encryption on your router (WEP/WPA), you could try turning off network manager and try connecting manually:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient -r
sudo iwconfig wlan0 essid name-of-router
sudo dhclient wlan0
```
This will turn off network manager for this session.  Just replace name-of-router with the name of your router.  I am thinking that there might just be an issue with network manager but I could be wrong.

---

### Post by Ameet on 2008-08-18
OK.  Here's the result:

```

~$ **[COLOR=DarkGreen]sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop[/COLOR]**
[sudo] password for ameet: 
 * Stopping network events dispatcher NetworkManagerDispatcher[ OK ] 
~$ **[COLOR=DarkGreen]sudo /etc/dbus-1/event.d/25NetworkManager stop[/COLOR]**
 * Stopping network connection manager NetworkManager         [ OK ] 
~$ [COLOR=DarkGreen]**sudo dhclient -r**[/COLOR]
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:22:69:19:f4:1d
Sending on   LPF/wlan0/00:22:69:19:f4:1d
Listening on LPF/eth0/00:21:9b:e0:06:00
Sending on   LPF/eth0/00:21:9b:e0:06:00
Sending on   Socket/fallback
~$ [COLOR=DarkGreen]**sudo iwconfig wlan0 essid RAV404**[/COLOR]
~$ [COLOR=DarkGreen]**sudo dhclient wlan0**[/COLOR]
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:22:69:19:f4:1d
Sending on   LPF/wlan0/00:22:69:19:f4:1d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
~$ 
```My network (RAV404) is unsecured.  But this did not help.  Anything else I can try?

---

### Post by Jamie Jackson on 2008-08-18
> **Ameet said:**
> 
```

~$ [COLOR=DarkGreen]**sudo iwconfig wlan0 essid RAV404**[/COLOR]
~$ [COLOR=DarkGreen]**sudo dhclient wlan0**[/COLOR]
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:22:69:19:f4:1d
Sending on   LPF/wlan0/00:22:69:19:f4:1d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
~$

```
My network (RAV404) is unsecured.  But this did not help.  Anything else I can try?

This happens to be the same sort of thing that you'd get if that essid didn't exist. While in this manual mode, would you please issue "iwlist wlan0 scan" and post the results?

Update: And more to the point, after trying to associate with your AP ("sudo iwconfig wlan0 essid RAV404"), please run "sudo iwconfig wlan0", and let's see if you even associated.

---

### Post by Ameet on 2008-08-18
> **Jamie Jackson said:**
> This happens to be the same sort of thing that you'd get if that essid didn't exist. While in this manual mode, would you please issue "iwlist wlan0 scan" and post the results?

Update: And more to the point, after trying to associate with your AP ("sudo iwconfig wlan0 essid RAV404"), please run "sudo iwconfig wlan0", and let's see if you even associated.

OK.  Results much as before.  No wireless connection.  Here's the printout:
```

~$ **[COLOR=DarkGreen]sudo iwconfig wlan0[/COLOR]**
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$

```I am attaching two screenshots from the setup page for my modem (Westell Versalink Model 327W).  I am, of course, accessing this when I have an ethernet connection.  They show the wireless settings on the modem-router.  Maybe you can recognize it, in case I have botched something up there.  Thanks,
Ameet.

Here's more info on what is being sniffed by the wireless card.  This shows that my router is broadcasting a decent signal with the ESSID I am requesting.  Am I right about that?
```

~$ **[COLOR=DarkGreen]iwlist scan[/COLOR]**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:8A:5E:50
                    ESSID:"07FX09054567"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:E0:98:FF:8F:C1
                    ESSID:"RAV404"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

~$ 

```

---

### Post by Maverynthia on 2008-08-18
I tried the fix for Hardy however my card doesn't even list the module:
>  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
maverynthia@danniex:~/bcm43xx$ 


---

### Post by Ayuthia on 2008-08-18
> **Maverynthia said:**
> I tried the fix for Hardy however my card doesn't even list the module:

Can you post the results of:
```
lspci -nnmvkd 14e4:*
ndiswrapper -l
```

Also, please let us know which driver you used from the guide.  Thanks!

By the way, the first command that I ask will help provide a more information about your Broadcom card.  The main part that we need to know is the vendor and device numbers, but I am still trying to see if there is more information linked to the subvendor information.

---

### Post by R-C-S on 2008-08-18
My apologies in advance if this is answered and I missed the post:

I have a Dell Inspiron 5100. I have Hardy installed. I've followed through the steps and do see the wireless networks I expect. Mine happens to be an Airport Extreme! running WPA/WPA2 Personal. My problem is that I can not get my laptop to authenticate and get an IP address.

If I turn of all encryption it gets an IP and runs fine.

What is the trick of getting WPA running with these Broadcom cards?

---

### Post by ShaxxiE on 2008-08-19
Hi :)

Ive got a bit of a problem, my wireless connection is there and showing; however i cannot connect to it, it just goes into a loop and then goes back to my wired connection; yes, i have also tried to take my wired connection out but then it says "no Network connection" or words similar to that affect.

Ive been trying to sort this out for two days, its just not working out! - please see my accompanying thread [here]("http://ubuntuforums.org/showthread.php?t=893491") where Ayuthia has been really helping.

Any help would be much appreciated! 

> [LIST]
[*]Machine Brand and Model
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
[*]Wireless Chipset: lspci -n | grep '14e4:43'
[*]Ubuntu Version: lsb_release -d
[*]Kernel / Architecture: uname -mr
[*]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper
[*]Which version of Step 2 you used **(If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)**
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
[/LIST]

lsmod:

```
shaheen@shaheen-desktop:~/bcm43xx$ lsmod
Module                  Size  Used by
b44                    33168  0 
mii                     7552  1 b44
b43legacy             141992  0 
ssb                    39428  2 b44,b43legacy
ndiswrapper           243872  0 
nls_iso8859_1           6656  1 
nls_cp437               8320  1 
vfat                   16256  1 
fat                    60592  1 vfat
isofs                  39464  1 
udf                    91048  0 
ipv6                  311848  8 
af_packet              27272  2 
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
powernow_k8            16608  0 
cpufreq_powersave       3200  0 
cpufreq_stats           8416  0 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
container               6656  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
zc0301                 56580  0 
snd_emu10k1_synth       9472  0 
snd_emux_synth         40960  1 snd_emu10k1_synth
bt878                  13672  0 
snd_seq_virmidi         9344  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
tuner                  49056  0 
tea5767                 7812  1 tuner
tda8290                13828  1 tuner
tuner_simple           10632  1 tuner
mt20xx                 14600  1 tuner
tea5761                 6916  1 tuner
tvaudio                28188  0 
usb_storage            82496  1 
usbhid                 35296  0 
snd_emu10k1           162272  4 snd_emu10k1_synth
gspca                 657872  0 
libusual               23520  1 usb_storage
hid                    44992  1 usbhid
arc4                    3456  2 
evdev                  14976  4 
ecb                     5248  2 
blkcipher               9476  1 ecb
snd_ac97_codec        123224  1 snd_emu10k1
nvidia               8115088  34 
ac97_bus                3840  1 snd_ac97_codec
snd_bt87x              19076  1 
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12552  2 snd_emux_synth,snd_emu10k1
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  4 snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_pcm_oss
bttv                  214772  1 bt878
snd_seq_dummy           5764  0 
ir_common              39812  1 bttv
mac80211              192532  1 b43legacy
snd_seq_oss            38912  0 
serio_raw               9092  0 
compat_ioctl32         11136  3 zc0301,gspca,bttv
i2c_algo_bit            8452  1 bttv
snd_seq_midi           10688  0 
psmouse                46236  0 
snd_rawmidi            29856  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     10112  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
cfg80211               17680  1 mac80211
videobuf_dma_sg        17028  1 bttv
videobuf_core          22020  2 bttv,videobuf_dma_sg
btcx_risc               6792  1 bttv
snd_seq                63232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 10912  0 
i2c_viapro             11672  0 
tveeprom               20624  1 bttv
pcspkr                  4992  0 
k8temp                  7680  0 
snd_timer              27912  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10644  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
i2c_core               28544  12 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,tvaudio,nvidia,bttv,i2c_algo_bit,i2c_viapro,tveeprom
videodev               30720  3 zc0301,gspca,bttv
v4l2_common            21888  6 zc0301,tuner,tvaudio,bttv,compat_ioctl32,videodev
v4l1_compat            15492  2 bttv,videodev
snd                    70856  23 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
snd_page_alloc         13200  3 snd_emu10k1,snd_bt87x,snd_pcm
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sr_mod                 20132  1 
cdrom                  41512  1 sr_mod
ata_generic             9988  0 
pata_acpi               9856  0 
sg                     41880  0 
sd_mod                 33280  5 
floppy                 69096  0 
ehci_hcd               41996  0 
uhci_hcd               29856  0 
pata_via               15620  3 
sata_via               14596  0 
sata_sil               14472  0 
usbcore               169904  9 ndiswrapper,zc0301,usb_storage,usbhid,gspca,libusual,ehci_hcd,uhci_hcd
skge                   47888  0 
libata                176432  5 ata_generic,pata_acpi,pata_via,sata_via,sata_sil
scsi_mod              178488  6 sbp2,usb_storage,sr_mod,sg,sd_mod,libata
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 
```

Machine Brand & Make: Custom Made - hope the followin helps for my peripheral list:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 05)
00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0d.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:0e.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)

```

Wireless model & make:

```
shaheen@shaheen-desktop:~/bcm43xx$ lspci | grep Broadcom
00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

Wireless chipset:
```

shaheen@shaheen-desktop:~/bcm43xx$ lspci -n | grep '14e4:43'
00:0a.0 0280: 14e4:4320 (rev 02)
```

Ubuntu Version:
```
shaheen@shaheen-desktop:~/bcm43xx$ lsb_release -d
Description:	Ubuntu 8.04.1
```

Kernal Architecture:
```
shaheen@shaheen-desktop:~/bcm43xx$ uname -mr
2.6.24-19-generic x86_64
```

Boot options:
I dont think i have any... only GRUB (if that what you mean)

Compalation of NDISWrapper:
Used the one from step 2F - I didnt compile it myself.

Step 2 option:
Step 2F

Hardy Bug Fix:
Didnt work for me, i still had *'module=ssb'* after the temp fix.

```
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b43legacy #this step added Apr 27 2008
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod ssb
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ssb
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe b44 #this step added May 1 2008
shaheen@shaheen-desktop:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 12
       serial: 00:50:8d:f7:0f:16
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A ip=192.168.1.10 latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:13:a6:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

Thanks for reading... :popcorn:

---

### Post by Ayuthia on 2008-08-19
> **ShaxxiE said:**
> 
Wireless model & make:

```
shaheen@shaheen-desktop:~/bcm43xx$ lspci | grep Broadcom
00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

Kernal Architecture:
```
shaheen@shaheen-desktop:~/bcm43xx$ uname -mr
2.6.24-19-generic x86_64
```


@Jamie Jackson - SaxxiE is using Ubuntu 64-bit, but the driver in 2f is only for 32-bit.  Do you know of a 64-bit version?

---

### Post by Ameet on 2008-08-19
> **Ameet said:**
> OK.  Results much as before.  No wireless connection.  Here's the printout:
```

~$ **[COLOR=DarkGreen]sudo iwconfig wlan0[/COLOR]**
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$
```
Any further thoughts out there about what may be going on?  My card is detecting the router; the signal strength is excellent; but I cannot associate, even manually.

A further problem is that I now have lost the automatic wifi sniffing on the network panel icon.  Used to be when I left-clicked on the network icon I would get a drop-down list of available wireless networks (not that I could successfully connect to any of them)... now, all I get is "Manual configuration..." (see the mini-screenshot, attached.).

How do I at least get my original GUI menu back?  I don't want to have broken anything permanently in this install. Please remember to dumb down any answers.  I know basic linux but I'm in deep waters with this wireless business. Thanks!

---

### Post by Jamie Jackson on 2008-08-19
> **Ayuthia said:**
> @Jamie Jackson - SaxxiE is using Ubuntu 64-bit, but the driver in 2f is only for 32-bit.  Do you know of a 64-bit version?

How do you know it's 32 bit only? (I'm not saying you're wrong, I'm just curious.) I have yet to see a driver that worked for 32-bit, but not 64-bit, systems. Maybe this is a first, but maybe not...

---

### Post by ShaxxiE on 2008-08-19
> **Jamie Jackson said:**
> How do you know it's 32 bit only? (I'm not saying you're wrong, I'm just curious.) I have yet to see a driver that worked for 32-bit, but not 64-bit, systems. Maybe this is a first, but maybe not...

I have got a 64 bit version from somewhere - its called 'b43-fwcutter_011-1_amd64.deb'

I double click on it, it installs and says i already have the same version (i think i may have installed it about 100 times before)

S

---

### Post by Ameet on 2008-08-19
OK, this is a bit bizarre now.  I took my laptop to the local coffee shop with public wifi access (remember this is a new machine so it's never been out of the home yet).  Guess what, everything WORKS.  :confused:  I was able to connect through the network icon in the panel > "Manual Configuration..." > "Wireless connection" > selecting the public network.  Here is some data on the connection and on what I am scanning on my system.  We are talking same frequency, same channel, also unencrypted, just as at home.

But, other laptops can connect to my home modem wirelessly.  So what could be going on?  Any thoughts??  Is there some compatibility quirk between Broadcom and the Westell Versalink modem at my home?

```

~$ **[COLOR=DarkGreen]lshw -C network[/COLOR]**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:06:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:19:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. ip=192.168.1.176 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
~$ **[COLOR=DarkGreen]sudo iwconfig wlan0[/COLOR]**
[sudo] password for ameet: 
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:BE:83:F5   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$**[COLOR=DarkGreen] iwlist scan[/COLOR]**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:BE:83:F5
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:10:A0:B9:05
                    ESSID:"Roofscapes"
...
          Cell 03 - Address: 00:12:0E:83:DB:6D
                    ESSID:"07B407417185"
...
          Cell 04 - Address: 00:13:10:34:E3:3F
                    ESSID:"linksys"
...
          Cell 05 - Address: 00:14:BF:ED:FE:DB
                    ESSID:"birdnest"
...
~$
```Also, I still would like to know how I could get back the list of available networks from the pull-down network panel icon.  I think I disabled it when I ran the following code (recommended by Ayuthia).  The computer has been rebooted several times since then but, while the network icon is back, the list of available wifi networks is not.

> **Ayuthia said:**
> If you are not using encryption on your router (WEP/WPA), you could try turning off network manager and try connecting manually:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient -r
sudo iwconfig wlan0 essid name-of-router
sudo dhclient wlan0
```This will turn off network manager for this session. Just replace name-of-router with the name of your router. I am thinking that there might just be an issue with network manager but I could be wrong.

---

### Post by Ayuthia on 2008-08-19
> **Jamie Jackson said:**
> How do you know it's 32 bit only? (I'm not saying you're wrong, I'm just curious.) I have yet to see a driver that worked for 32-bit, but not 64-bit, systems. Maybe this is a first, but maybe not...

The 64-bit files usually use the bcmwl564.sys files and this one did not have it.  I also looked in the .inf file for any mention of a 64-bit and could not find anything on it.  I could be completely wrong about it, but all the other files usually have the some mention of 64-bit in the .inf file.

---

### Post by Ayuthia on 2008-08-19
> **ShaxxiE said:**
> I have got a 64 bit version from somewhere - its called 'b43-fwcutter_011-1_amd64.deb'

I double click on it, it installs and says i already have the same version (i think i may have installed it about 100 times before)

S
The b43-fwcutter is the firmware cutter for the b43 driver.  It is a different driver than NDISwrapper and generally causes conflicts with NDISwrapper and that is why the driver gets blacklisted.

---

### Post by Ayuthia on 2008-08-19
> **Ameet said:**
> OK, this is a bit bizarre now.  I took my laptop to the local coffee shop with public wifi access (remember this is a new machine so it's never been out of the home yet).  Guess what, everything WORKS.  :confused:  I was able to connect through the network icon in the panel > "Manual Configuration..." > "Wireless connection" > selecting the public network.  Here is some data on the connection and on what I am scanning on my system.  We are talking same frequency, same channel, also unencrypted, just as at home.

But, other laptops can connect to my home modem wirelessly.  So what could be going on?  Any thoughts??  Is there some compatibility quirk between Broadcom and the Westell Versalink modem at my home?

```

~$ **[COLOR=DarkGreen]lshw -C network[/COLOR]**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:06:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:19:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. ip=192.168.1.176 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
~$ **[COLOR=DarkGreen]sudo iwconfig wlan0[/COLOR]**
[sudo] password for ameet: 
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:BE:83:F5   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$**[COLOR=DarkGreen] iwlist scan[/COLOR]**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:BE:83:F5
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:10:A0:B9:05
                    ESSID:"Roofscapes"
...
          Cell 03 - Address: 00:12:0E:83:DB:6D
                    ESSID:"07B407417185"
...
          Cell 04 - Address: 00:13:10:34:E3:3F
                    ESSID:"linksys"
...
          Cell 05 - Address: 00:14:BF:ED:FE:DB
                    ESSID:"birdnest"
...
~$
```Also, I still would like to know how I could get back the list of available networks from the pull-down network panel icon.  I think I disabled it when I ran the following code (recommended by Ayuthia).  The computer has been rebooted several times since then but, while the network icon is back, the list of available wifi networks is not.

As far as I know, the command that I gave you should not have disable the list of networks because it just stops the process from running and should not change the configuration of network manager.  However, if it did, I think you should be able to get them back by looking for the wireless icon and changing it back to roaming mode.

---

### Post by Ayuthia on 2008-08-19
> **Ameet said:**
> OK, this is a bit bizarre now.  I took my laptop to the local coffee shop with public wifi access (remember this is a new machine so it's never been out of the home yet).  Guess what, everything WORKS.  :confused:  I was able to connect through the network icon in the panel > "Manual Configuration..." > "Wireless connection" > selecting the public network.  Here is some data on the connection and on what I am scanning on my system.  We are talking same frequency, same channel, also unencrypted, just as at home.

But, other laptops can connect to my home modem wirelessly.  So what could be going on?  Any thoughts??  Is there some compatibility quirk between Broadcom and the Westell Versalink modem at my home?

```

~$ **[COLOR=DarkGreen]lshw -C network[/COLOR]**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:06:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:19:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. ip=192.168.1.176 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
~$ **[COLOR=DarkGreen]sudo iwconfig wlan0[/COLOR]**
[sudo] password for ameet: 
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:BE:83:F5   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$**[COLOR=DarkGreen] iwlist scan[/COLOR]**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:BE:83:F5
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:10:A0:B9:05
                    ESSID:"Roofscapes"
...
          Cell 03 - Address: 00:12:0E:83:DB:6D
                    ESSID:"07B407417185"
...
          Cell 04 - Address: 00:13:10:34:E3:3F
                    ESSID:"linksys"
...
          Cell 05 - Address: 00:14:BF:ED:FE:DB
                    ESSID:"birdnest"
...
~$
```Also, I still would like to know how I could get back the list of available networks from the pull-down network panel icon.  I think I disabled it when I ran the following code (recommended by Ayuthia).  The computer has been rebooted several times since then but, while the network icon is back, the list of available wifi networks is not.

As far as I know, the command that I gave you should not have disable the list of networks because it just stops the process from running and should not change the configuration of network manager.  However, if it did, I think you should be able to get them back by looking for the wireless icon and changing it back to roaming mode.  Unfortunately, I am currently in Arch using KDE so I can't point you to the exact location.

---

### Post by Jamie Jackson on 2008-08-19
> **ShaxxiE said:**
> I have got a 64 bit version from somewhere - its called 'b43-fwcutter_011-1_amd64.deb'

I double click on it, it installs and says i already have the same version (i think i may have installed it about 100 times before)

S

As Ayuthia mentioned, that deb from above is contrary to ndiswrapper.

Question: You said your machine's custom, correct? What is the make/model/version that's on your wireless device's sticker (or on the box it came in, assuming you've got it)? (e.g., LinkSys/WRFOOBAR/v2)

I want to take a look at its support site to compare with what I've got. If it's a hassle, don't worry about it.

---

### Post by Jamie Jackson on 2008-08-19
> **Ameet said:**
> Also, I still would like to know how I could get back the list of available networks from the pull-down network panel icon.  I think I disabled it when I ran the following code (recommended by Ayuthia).  The computer has been rebooted several times since then but, while the network icon is back, the list of available wifi networks is not.

For kicks, please post the output of "cat /etc/network/interfaces"

It should only have:
```
auto lo
iface lo inet loopback
```

---

### Post by Jamie Jackson on 2008-08-19
> **Ayuthia said:**
> The 64-bit files usually use the bcmwl564.sys files and this one did not have it.  I also looked in the .inf file for any mention of a 64-bit and could not find anything on it.  I could be completely wrong about it, but all the other files usually have the some mention of 64-bit in the .inf file.

Okay, I'll wait and see what ShaxxiE's device's physical label says, so I can check that vendor's support site/driver against what I've got.

The 32/64-bit thing might be a red herring, but we'll see.

---

### Post by ShaxxiE on 2008-08-19
> **Jamie Jackson said:**
> Okay, I'll wait and see what ShaxxiE's device's physical label says, so I can check that vendor's support site/driver against what I've got.

The 32/64-bit thing might be a red herring, but we'll see.

Hello

Ive just opened up my computer and checked the label.  The only thing thing i can see with any relevance was:

Linksys Wireless Adapter

WMP54G
FCCID: PKW_WMP54G
IC: 3839A-WMP54G

I do not have the original box.  Hope this helps

---

### Post by Jamie Jackson on 2008-08-19
> **ShaxxiE said:**
> Hello

Ive just opened up my computer and checked the label.  The only thing thing i can see with any relevance was:

Linksys Wireless Adapter

WMP54G
FCCID: PKW_WMP54G
IC: 3839A-WMP54G

I do not have the original box.  Hope this helps

Maybe it's a version 1? Sorry to make you jump through hoops, but please double check that you didn't overlook the version number. (Instructions [here]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843981&packedargs=sku%3DWMP54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4398143981B01&displaypage=download").)

Update: Oh, and do download and try the drivers from the Linksys support site (for WinXP, not Vista), for whatever version you find that you have.

Update 2: You must have version 1. I [looked up the FCCID]("https://fjallfoss.fcc.gov/oetcf/eas/reports/ViewExhibitReport.cfm?mode=Exhibits&RequestTimeout=500&calledFromFrame=N&application_id=279670&fcc_id=%27PKW-WMP54G%27"), and looked at the label they have on file, and it has no explicit version printed (as you indicated).

---

### Post by Ayuthia on 2008-08-19
> **Jamie Jackson said:**
> Maybe it's a version 1? Sorry to make you jump through hoops, but please double check that you didn't overlook the version number. (Instructions [here]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843981&packedargs=sku%3DWMP54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4398143981B01&displaypage=download").)

Update: Oh, and do download and try the drivers from the Linksys support site (for WinXP, not Vista), for whatever version you find that you have.
Here is ShaxxiE's lspci -nnm info link from the other post:
[http://ubuntuforums.org/showpost.php?p=5618462&postcount=20](http://ubuntuforums.org/showpost.php?p=5618462&postcount=20)
To summarize:
```
00:0a.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Linksys [1737]" "Unknown device [0013]"
```
It doesn't seem that the rev numbers match up.  From one of the .inf files that I looked at, it looks like it could be a version 01.

@ShaxxiE - you might try out WPC300N+others-x64 from that [link]("http://www.savefile.com/projects/1042021") in your other thread.  To prevent more jumping around, let's try to keep the conversation on this thread.  I think that others can benefit more from this one because this thread is becoming very popular.

---

### Post by ShaxxiE on 2008-08-19
Hello

Okay ill stick to this thread from now on.

I do think i have Version 1 as it definitely doesn't have a version written on my Wlan adapter, and i got this W Adapter when Wireless first because popular... a good few years ago.....

I have just installed this 64bit driver from [>ubunturules<]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+handy") thread but again i am getting 1 light on the WLAN in System Area at top left of screen when its trying to log into my network.... but still no connection.

The WPC300N_others-x64 drivers do not work at all, they completely remove the wireless altogether.

Ive spent over 12 solid hours on this.  I think ive earnt myself a new WLAN card.  Which is the best one compatible with Ubuntu Hardy?

---

### Post by Ayuthia on 2008-08-19
> **ShaxxiE said:**
> Hello

Okay ill stick to this thread from now on.

I do think i have Version 1 as it definitely doesn't have a version written on my Wlan adapter, and i got this W Adapter when Wireless first because popular... a good few years ago.....

I have just installed this 64bit driver from [>ubunturules<]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+handy") thread but again i am getting 1 light on the WLAN in System Area at top left of screen when its trying to log into my network.... but still no connection.

The WPC300N_others-x64 drivers do not work at all, they completely remove the wireless altogether.

Ive spent over 12 solid hours on this.  I think ive earnt myself a new WLAN card.  Which is the best one compatible with Ubuntu Hardy?

Well, I appreciate the effort that you put into this.  I wish that I could tell you what card is the most compatible.  I ended up getting a Linksys PCI card, but it had the RaLink hardware inside.  It did work out of the box with Ubuntu using the rt61pci module and it works well with the rt61 from serialmonkey on Arch.  Unfortunately, the Linksys cards are hit and miss because of the various chips that they use.

---

### Post by Ameet on 2008-08-19
> **Jamie Jackson said:**
> For kicks, please post the output of "cat /etc/network/interfaces"

It should only have:
```
auto lo
iface lo inet loopback
```

OK.  Ayuthia's idea to switch to "roaming mode" did the trick.  I have my list of networks back (still can't connect to my own, but at least the interface works).  And, I have exactly what you predict in /etc/network/interfaces", Jamie.

I really appreciate the step-by-step help from both of you.  Any thoughts on where I should take this problem next with trying to connect to my own home router?

Thanks, Ameet.

---

### Post by Ayuthia on 2008-08-19
> **Ameet said:**
> OK.  Ayuthia's idea to switch to "roaming mode" did the trick.  I have my list of networks back (still can't connect to my own, but at least the interface works).  And, I have exactly what you predict in /etc/network/interfaces", Jamie.

I really appreciate the step-by-step help from both of you.  Any thoughts on where I should take this problem next with trying to connect to my own home router?

Thanks, Ameet.

I am assuming that you are back at home.  If so, can you post the results of:
```
sudo iwlist scan
```Let's see if we can see your home router.

EDIT:  I just figured out that the your last scan was not from your place and that is why I did not see your home router.  The previous scan did show that there are two sites (yours and another site) and they are using the same channel.  Both signals are somewhat strong.  You might try changing the channel of your router (something else less than 12) and then try to connect.

---

### Post by Ameet on 2008-08-19
> **Ayuthia said:**
> I am assuming that you are back at home.  If so, can you post the results of:
```
sudo iwlist scan
```Let's see if we can see your home router.

EDIT:  I just figured out that the your last scan was not from your place and that is why I did not see your home router.  The previous scan did show that there are two sites (yours and another site) and they are using the same channel.  Both signals are somewhat strong.  You might try changing the channel of your router (something else less than 12) and then try to connect.

I changed the channel to 8 (the other routers on my street are on channel 6).  I wasn't able to make a connection.  I then also changed the beacon interval from 200 ms to 100 ms (I don't know what this is about, but it seems to be 100 on a number of other routers I have sniffed.)  Well, that didn't help either.  Here's the scan:
```

~$ **[COLOR=DarkGreen]sudo iwlist scan[/COLOR]**
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:FF:8F:C1
                    ESSID:"RAV404"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-24 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:12:0E:8A:5E:50
                    ESSID:"07FX09054567"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:12:0E:75:0A:95
                    ESSID:"07B404591928"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

eth0      Interface doesn't support scanning.

```

---

### Post by graafh on 2008-08-20
**After trying and reading (a lot of both) I got my Broadcom 4328 working, stable, and relatively fast, with WPA2 and static address.**
[http://ubuntuforums.org/showthread.php?t=779754&page=21](http://ubuntuforums.org/showthread.php?t=779754&page=21)
Post #206

---

### Post by Jamie Jackson on 2008-08-20
> **ShaxxiE said:**
> Hello

Okay ill stick to this thread from now on.

I do think i have Version 1 as it definitely doesn't have a version written on my Wlan adapter, and i got this W Adapter when Wireless first because popular... a good few years ago.....

I have just installed this 64bit driver from [>ubunturules<]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+handy") thread but again i am getting 1 light on the WLAN in System Area at top left of screen when its trying to log into my network.... but still no connection.

The WPC300N_others-x64 drivers do not work at all, they completely remove the wireless altogether.

Ive spent over 12 solid hours on this.  I think ive earnt myself a new WLAN card.  Which is the best one compatible with Ubuntu Hardy?

I hear you, I personally hate the Broadcom devices, and their unwillingness to be Linux-friendly. Here's a [USB option]("http://ph.ubuntuforums.com/showpost.php?p=5099678&postcount=647") that had a great bang for the buck for me (got it plugged into the "kitchen laptop"), though you'll likely find more reliable information on wireless devices on some Linux compatibility chart.

I'm sure we can get your existing device working, though I don't know how much more time you're willing to put into it. ;-)

---

### Post by Jamie Jackson on 2008-08-20
> **ShaxxiE said:**
> Hello

Okay ill stick to this thread from now on.

I do think i have Version 1 as it definitely doesn't have a version written on my Wlan adapter, and i got this W Adapter when Wireless first because popular... a good few years ago.....

I have just installed this 64bit driver from [>ubunturules<]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+handy") thread but again i am getting 1 light on the WLAN in System Area at top left of screen when its trying to log into my network.... but still no connection.

The WPC300N_others-x64 drivers do not work at all, they completely remove the wireless altogether.

Ive spent over 12 solid hours on this.  I think ive earnt myself a new WLAN card.  Which is the best one compatible with Ubuntu Hardy?

BTW, have you tried the [version 1 driver from the linksys site]("http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3Dwmp54g_driver_utility_v1.4.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1193764846549&ssbinary=true&lid=4890443981B02") yet? If not, please do.

---

### Post by Jamie Jackson on 2008-08-20
> **Ameet said:**
> I changed the channel to 8 (the other routers on my street are on channel 6).  I wasn't able to make a connection.  I then also changed the beacon interval from 200 ms to 100 ms (I don't know what this is about, but it seems to be 100 on a number of other routers I have sniffed.)  Well, that didn't help either.  Here's the scan:
```

~$ **[COLOR=DarkGreen]sudo iwlist scan[/COLOR]**
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:FF:8F:C1
                    ESSID:"RAV404"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-24 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:12:0E:8A:5E:50
                    ESSID:"07FX09054567"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:12:0E:75:0A:95
                    ESSID:"07B404591928"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

eth0      Interface doesn't support scanning.

```

Some folks seem to have a low opinion of that router. Here are some voodoo things to try, FWIW:

1. Power cycle the router

If you still can't connect:

2. Reset router to factory defaults, and see if you can connect.

As I said, this is voodoo, but number 1 is easy enough...

---

### Post by tymek666 on 2008-08-20
Thanks for this HowTo, works great on HP 2570US :)
Best,
tym

---

### Post by Ayuthia on 2008-08-20
> **tymek666 said:**
> Thanks for this HowTo, works great on HP 2570US :)
Best,
tym

Can you tell us your lspci -nnm and which driver option you used?  We were having problems with another 4306 rev 02 card on a 64-bit platform.

---

### Post by Grepomate on 2008-08-20
Tried this HowTo on an Dell Inspiron 1705 with Hardy installed. It worked fine. i will post detailed feedback later on, first i want to enjoy my newly acquired wifi capability on Ubuntu!!

regards,
Grepo

---

### Post by tymek666 on 2008-08-21
> **Ayuthia said:**
> Can you tell us your lspci -nnm and which driver option you used?  We were having problems with another 4306 rev 02 card on a 64-bit platform.
lspci output:
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS200/RS200M AGP Bridge [IGP 340M] [cbb2]" -r02 "" ""
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "PCI Bridge [IGP 340M] [7010]" "" ""
00:06.0 "Multimedia audio controller [0401]" "ALi Corporation [10b9]" "M5451 PCI AC-Link Controller Audio Device [5451]" -r02 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:07.0 "ISA bridge [0601]" "ALi Corporation [10b9]" "M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [1533]" "ALi Corporation [10b9]" "ALi M1533 Aladdin IV/V ISA Bridge [1533]"
00:08.0 "Modem [0703]" "ALi Corporation [10b9]" "M5457 AC'97 Modem Controller [5457]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Compaq Computer Corporation [0e11]" "Unknown device [00e7]"
00:0a.0 "CardBus bridge [0607]" "O2 Micro, Inc. [1217]" "OZ601/6912/711E0 CardBus/SmartCardBus Controller [6972]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0b.0 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r50 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0b.1 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r50 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0b.2 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "USB 2.0 [3104]" -r51 -p20 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0c.0 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [8026]" -p10 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:10.0 "IDE interface [0101]" "ALi Corporation [10b9]" "M5229 IDE [5229]" -rc4 -pfa "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:11.0 "Bridge [0680]" "ALi Corporation [10b9]" "M7101 Power Management Controller [PMU] [7101]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:12.0 "Ethernet controller [0200]" "National Semiconductor Corporation [100b]" "DP83815 (MacPhyter) Ethernet Controller [0020]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon IGP 330M/340M/350M [4337]" "Hewlett-Packard Company [103c]" "Radeon IGP 345M [0850]"

I don't use any special ndiswrapper opitions, just follow this guide, except windows driver installations, i have different file.
Do you have 64-bit windows driver for 4306?
Best,
Tym

---

### Post by Ayuthia on 2008-08-21
> **tymek666 said:**
> lspci output:
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS200/RS200M AGP Bridge [IGP 340M] [cbb2]" -r02 "" ""
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "PCI Bridge [IGP 340M] [7010]" "" ""
00:06.0 "Multimedia audio controller [0401]" "ALi Corporation [10b9]" "M5451 PCI AC-Link Controller Audio Device [5451]" -r02 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:07.0 "ISA bridge [0601]" "ALi Corporation [10b9]" "M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [1533]" "ALi Corporation [10b9]" "ALi M1533 Aladdin IV/V ISA Bridge [1533]"
00:08.0 "Modem [0703]" "ALi Corporation [10b9]" "M5457 AC'97 Modem Controller [5457]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Compaq Computer Corporation [0e11]" "Unknown device [00e7]"
00:0a.0 "CardBus bridge [0607]" "O2 Micro, Inc. [1217]" "OZ601/6912/711E0 CardBus/SmartCardBus Controller [6972]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0b.0 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r50 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0b.1 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r50 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0b.2 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "USB 2.0 [3104]" -r51 -p20 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:0c.0 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [8026]" -p10 "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:10.0 "IDE interface [0101]" "ALi Corporation [10b9]" "M5229 IDE [5229]" -rc4 -pfa "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:11.0 "Bridge [0680]" "ALi Corporation [10b9]" "M7101 Power Management Controller [PMU] [7101]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
00:12.0 "Ethernet controller [0200]" "National Semiconductor Corporation [100b]" "DP83815 (MacPhyter) Ethernet Controller [0020]" "Hewlett-Packard Company [103c]" "Unknown device [0850]"
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon IGP 330M/340M/350M [4337]" "Hewlett-Packard Company [103c]" "Radeon IGP 345M [0850]"

I don't use any special ndiswrapper opitions, just follow this guide, except windows driver installations, i have different file.
Do you have 64-bit windows driver for 4306?
Best,
Tym

That is what we are researching.  I am thinking that the No-Fluff guide might have a 32-bit only, but I am looking for a confirmation on it.  Can you let us know where you got your Windows driver?

---

### Post by Grepomate on 2008-08-21
tst.

---

### Post by tymek666 on 2008-08-21
> **Ayuthia said:**
> That is what we are researching.  I am thinking that the No-Fluff guide might have a 32-bit only, but I am looking for a confirmation on it.  Can you let us know where you got your Windows driver?
Directly from HP website. Can you use 32bit windows driver under AMD64 linux?

---

### Post by Ayuthia on 2008-08-21
> **tymek666 said:**
> Directly from HP website. Can you use 32bit windows driver under AMD64 linux?

As far as I know, you can't.  When I have seen ndiswrapper try to use a 32-bit driver in a 64-bit environment, it rejects it.  The HP website usually bundles the wireless driver with a 32 and 64 bit version.

---

### Post by xebian on 2008-08-21
I thought BCM43xx issue is a thing of the past.  The bcm43xx-fwcutter and the b43-fwcutter packages make it easy as a pie.

---

### Post by Jamie Jackson on 2008-08-21
> **xebian said:**
> I thought BCM43xx issue is a thing of the past.  The bcm43xx-fwcutter and the b43-fwcutter packages make it easy as a pie.

There are two problems with that, AFAIK:
[LIST]
[*]They don't work for everyone
[*]They limit you to 11Mb/s instead of 54Mb/s
[/LIST]

---

### Post by Jamie Jackson on 2008-08-21
> **tymek666 said:**
> Directly from HP website. Can you use 32bit windows driver under AMD64 linux?

Would you provide the direct URL to the driver bundle? If the direct URL is hard to get, would you please describe your path through HP support, so I can find the exact package that worked for your device?

Others will benefit from this information, since you seem to have found a 64-bit compatible driver.

---

### Post by jarome on 2008-08-21
> **Jamie Jackson said:**
> [SIZE="3"]

All Users, After Following the Wiki
[LIST]
[*]Machine Brand and Model
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
[*]Wireless Chipset: lspci -n | grep '14e4:43'
[*]Ubuntu Version: lsb_release -d
[*]Kernel / Architecture: uname -mr
[*]Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper
[*]Which version of Step 2 you used **(If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)**
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
[/LIST]

Good luck,
Jamie
Last edited by Jamie Jackson; May 6th, 2008 at 11:34 PM. Reason: hardy update

Unsuccessful :-((
HP mini-note 2133 with Broadcom BCM4312 (rev 2)
> 
jar@jarhp:~$ lspci -n | grep '14e4:43'
02:00.0 0280: 14e4:4312 (rev 02)
jar@jarhp:~$ lsb_release -d
Description:    Ubuntu 8.04.1
jar@jarhp:~$ uname -mr
2.6.24-19-generic i686

No special boot options
Did not compile ndiswrapper
Used step 2a
Did not need to apply the Hardy bug fix:
s$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 02
       serial: 00:21:00:36:db:fd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,01/23/2008, 4.170. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:07:03.0
       logical name: eth0
       version: 03
       serial: 00:1f:29:9a:e4:14
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5788-v3.27 ip=192.168.1.28 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s

Wireless worked with no encryption. But it refuses to work on my wpa2-personal Linksys LAN. Not only that, the Network Settings app keeps resetting the security back to WPA-personal and forgetting my password.

It now claims I have two wirelesses: wlan1 and wlan1:avahi. Neither of them can be set in the Network Tools App. Says they are not there.

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9a:e4:14  
          inet addr:192.168.1.28  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:29ff:fe9a:e414/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5262368 (5.0 MB)  TX bytes:460212 (449.4 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128800 (125.7 KB)  TX bytes:128800 (125.7 KB)

wlan1     Link encap:Ethernet  HWaddr 00:21:00:36:db:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:fdffc000-fe000000 

wlan1:avahi Link encap:Ethernet  HWaddr 00:21:00:36:db:fd  
          inet addr:169.254.9.33  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Memory:fdffc000-fe000000 


$ lspci -nnm
00:00.0 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "P4M900 Host Bridge [0364]" "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:00.1 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "P4M900 Host Bridge [1364]" "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:00.2 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "P4M900 Host Bridge [2364]" "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:00.3 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "P4M900 Host Bridge [3364]" "" ""
00:00.4 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "P4M900 Host Bridge [4364]" "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:00.5 "PIC [0800]" "VIA Technologies, Inc. [1106]" "P4M900 I/O APIC Interrupt Controller [5364]" -p20 "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:00.6 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "P4M900 Security Device [6364]" "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:00.7 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "P4M900 Host Bridge [7364]" "" ""
00:01.0 "PCI bridge [0604]" "VIA Technologies, Inc. [1106]" "VT8237 PCI Bridge [b198]" "" ""
00:02.0 "PCI bridge [0604]" "VIA Technologies, Inc. [1106]" "P4M900 PCI to PCI Bridge Controller [a364]" -r80 "" ""
00:03.0 "PCI bridge [0604]" "VIA Technologies, Inc. [1106]" "P4M900 PCI to PCI Bridge Controller [c364]" -r80 "" ""
00:0f.0 "IDE interface [0101]" "VIA Technologies, Inc. [1106]" "Unknown device [5372]" -p8f "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:10.0 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -rb0 "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:10.2 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -rb0 "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:10.3 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -rb0 "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:10.4 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "USB 2.0 [3104]" -r90 -p20 "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:11.0 "ISA bridge [0601]" "VIA Technologies, Inc. [1106]" "VT8237S PCI to ISA Bridge [3372]" "Hewlett-Packard Company [103c]" "Unknown device [3030]"
00:11.7 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "VT8251 Ultra VLINK Controller [287e]" "VIA Technologies, Inc. [1106]" "Unknown device [337e]"
00:13.0 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "VT8237A Host Bridge [337b]" "" ""
00:13.1 "PCI bridge [0604]" "VIA Technologies, Inc. [1106]" "VT8237A PCI to PCI Bridge [337a]" -p01 "" ""
01:00.0 "VGA compatible controller [0300]" "VIA Technologies, Inc. [1106]" "Chrome9 HC IGP [3371]" -r01 "Hewlett-Packard Company [103c]" "Unknown device [3030]"
02:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11a/b/g [4312]" -r02 "Hewlett-Packard Company [103c]" "Broadcom 802.11a/b/g WLAN [1370]"
07:03.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetXtreme BCM5788 Gigabit Ethernet [169c]" -r03 "Broadcom Corporation [14e4]" "Unknown device [969c]"
80:01.0 "Audio device [0403]" "VIA Technologies, Inc. [1106]" "VIA High Definition Audio Controller [3288]" -r10 "Hewlett-Packard Company [103c]" "Unknown device [3030]"

I also get an error doing:

root@jarhp:/etc/ndiswrapper# ndiswrapper -m
module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 322.
module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 324.

But line 324 was blank....

I just tried turning off security on the WRT54G router. "The wireless then gets its DHCP address and works just fine. So it must be something to do with the encryption support." Well, maybe not. As soon as I pulled out the ethernet cable, it stopped working. The wlan1 interface got an ip address, but was sending out through the ethernet port!

r# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9a:e4:14  
          inet addr:192.168.1.28  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:29ff:fe9a:e414/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19326900 (18.4 MB)  TX bytes:157377626 (150.0 MB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2169246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2169246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123297139 (117.5 MB)  TX bytes:123297139 (117.5 MB)

wlan1     Link encap:Ethernet  HWaddr 00:21:00:36:db:fd  
          inet addr:192.168.1.29  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe36:dbfd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1044 (1.0 KB)  TX bytes:4432 (4.3 KB)
          Interrupt:21 Memory:fdffc000-fe000000

 Does anyone else have WPA2-Personal working?

I hope you can help, because I am getting desperate.

Thanks,
Jim

---

### Post by tymek666 on 2008-08-22
I think its a little misunderstanding. I run i386 Opengeu on Laptop with Broadcom and 64-bit Kubuntu on intel-based laptop. I didn't say that my windos drivers work in 64-bit linux.

---

### Post by Ayuthia on 2008-08-22
> **tymek666 said:**
> I think its a little misunderstanding. I run i386 Opengeu on Laptop with Broadcom and 64-bit Kubuntu on intel-based laptop. I didn't say that my windos drivers work in 64-bit linux.

That is good to know, but still if you could provide us the link we can check and see if it will work with 64-bit.  I have seen that the if the HP driver worked in 32-bit, their 64-bit counterpart works also.

I just haven't seen the 4306 rev 02 chipset work on 64-bit with the driver supplied in the guide (and I feel that it would not work) so I would like to have a backup version that does have a 64-bit driver included.

---

### Post by tymek666 on 2008-08-22
> **Ayuthia said:**
> That is good to know, but still if you could provide us the link we can check and see if it will work with 64-bit.  I have seen that the if the HP driver worked in 32-bit, their 64-bit counterpart works also.

I just haven't seen the 4306 rev 02 chipset work on 64-bit with the driver supplied in the guide (and I feel that it would not work) so I would like to have a backup version that does have a 64-bit driver included.

Direct link to this driver:
[ftp://ftp.hp.com/pub/softpaq/sp28501-29000/sp28537.exe](ftp://ftp.hp.com/pub/softpaq/sp28501-29000/sp28537.exe)

Best,
Tym

---

### Post by Theberge43 on 2008-08-22
Ok ... I've made some progress with you wiki
```
*-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:6e:03:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:93:3a:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

My Wireless is not desactivated anymore ... but I still can't see my router or connect to the network. I'm a total newbe, so the problem could be 36 inches from the screen ;)

---

### Post by muppis on 2008-08-24
Hello.
Bugfix 0.3 with chip 4306 worked when I removed modprobes for ssb and b44 modules.
Ah, almost forgot. I have via-rhino -module for wired, and I don't use it regularly.


Thanks again.

---

### Post by Jamie Jackson on 2008-08-25
> **Theberge43 said:**
> Ok ... I've made some progress with you wiki
```
*-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:6e:03:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:93:3a:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

My Wireless is not desactivated anymore ... but I still can't see my router or connect to the network. I'm a total newbe, so the problem could be 36 inches from the screen ;)

Hi Theberge43, please post the pieces of information I ask for in the first post of this thread, and we'll see if we can help.

---

### Post by Jamie Jackson on 2008-08-25
> **jarome said:**
> Unsuccessful :-((
HP mini-note 2133 with Broadcom BCM4312 (rev 2)


I also get an error doing:

root@jarhp:/etc/ndiswrapper# ndiswrapper -m
module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 322.
module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> 

Would you post the contents of your /etc/modprobe.d/ndiswrapper file, please?

---

### Post by hooby3dfx on 2008-08-27
Hi, I have a Dell Vostro 1400 with a 1390 wifi card built in.
With the stock install of Hardy I got working wifi but I ran into the problem of it being really slow - like not exceeding ~20 kb/s. 
I googled that, and tried out ndiswrapper a few weeks ago with excellent results. (Sorry I didnt post my success remarks :( )
Anyways, up until installing some Ubuntu updates the other day it was working fine, but after them the speed is back down again. 

Has anyone else had this problem?  When I try the lshw -C network command, it shows driver=ndiswrapper, but I dont know why the speed would have dropped down again.
Also, strangely I tried using bittorrent the program said its port was blocked, but the port is being forwarded and it worked fine before, so its like as if there is some firewall crap.

Any thoughts or suggestions?
I had to use the Hardy fix by the way. 

Thanks.

---

### Post by arqbrulo on 2008-08-28
@hooby3dfx
You might have upgrated to the latest kernel, and this MIGHT have screwed up your installation. Try following the same steps as before, see if that helps, if not, then I can no longer help you.

---

### Post by Jamie Jackson on 2008-08-28
> **hooby3dfx said:**
> Hi, I have a Dell Vostro 1400 with a 1390 wifi card built in.
With the stock install of Hardy I got working wifi but I ran into the problem of it being really slow - like not exceeding ~20 kb/s. 
I googled that, and tried out ndiswrapper a few weeks ago with excellent results. (Sorry I didnt post my success remarks :( )
Anyways, up until installing some Ubuntu updates the other day it was working fine, but after them the speed is back down again. 

Has anyone else had this problem?  When I try the lshw -C network command, it shows driver=ndiswrapper, but I dont know why the speed would have dropped down again.
Also, strangely I tried using bittorrent the program said its port was blocked, but the port is being forwarded and it worked fine before, so its like as if there is some firewall crap.

Any thoughts or suggestions?
I had to use the Hardy fix by the way. 

Thanks.

Would you post the output of "lsmod," please? I want to see if some other (presumably new) module is interfering.

Actually, I doubt this will tell me anything, since you still show ndiwrapper in lshw -C network

Does it help to boot into the previous kernel, BTW?

---

### Post by Jamie Jackson on 2008-08-28
> **arqbrulo said:**
> @hooby3dfx
You might have upgrated to the latest kernel, and this MIGHT have screwed up your installation. Try following the same steps as before, see if that helps, if not, then I can no longer help you.

Unless nooby had compiled ndiswrapper from source when he went through the instructions the first time, I don't think doing them over will help.

---

### Post by hooby3dfx on 2008-08-28
> **Jamie Jackson said:**
> Would you post the output of "lsmod," please? I want to see if some other (presumably new) module is interfering.

Actually, I doubt this will tell me anything, since you still show ndiwrapper in lshw -C network

Does it help to boot into the previous kernel, BTW?
output from lsmod:
```
Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  10 
snd_rtctimer            4640  1 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
nfsd                  228848  13 
lockd                  67720  2 nfsd
nfs_acl                 4608  1 nfsd
auth_rpcgss            43424  1 nfsd
sunrpc                185500  9 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                6016  1 nfsd
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
b44                    28432  0 
mii                     6400  1 b44
ssb                    34308  1 b44
ndiswrapper           193436  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
nvidia               7825536  36 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  19856  14 
output                  4736  1 video
wmi_acer                9644  0 
i2c_core               24832  1 nvidia
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
battery                14212  0 
button                  9232  0 
ac                      6916  0 
sdhci                  19076  0 
intel_agp              25492  0 
snd                    56996  19 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
agpgart                34760  2 nvidia,intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  8 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
dcdbas                  9504  0 
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
ata_piix               19588  2 
pata_acpi               8320  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
tg3                   116228  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
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
how would i boot into the old kernel?
is there a log of updates so i can check what was installed?
> **Jamie Jackson said:**
> Unless nooby had compiled ndiswrapper from source when he went through the instructions the first time, I don't think doing them over will help.
its HOOBY!
i did compile it from source - i was following a different howto for the 1390 along with this one since they seemed mostly the same.
thanks.

---

### Post by Jamie Jackson on 2008-08-29
> **hooby3dfx said:**
> 
how would i boot into the old kernel?
is there a log of updates so i can check what was installed?

its HOOBY!
i did compile it from source - i was following a different howto for the 1390 along with this one since they seemed mostly the same.
thanks.

Sorry HOOBY!

You might need to recompile ndiswrapper for the new kernel, as the other poster mentioned. Or, the stock ndiswrapper is new enough that it should work fine. That's what I'd recommend. (In other words, uninstall the compiled ndiswrapper, then "sudo apt-get install ndiswrapper-utils-1.9".)

To boot into an older kernel, pay attention during your bootup, and you might get a short prompt to get into GRUB (you hit f2, or something), and you can select an older kernel from there.

---

### Post by Theberge43 on 2008-08-29
> **Jamie Jackson said:**
> Hi Theberge43, please post the pieces of information I ask for in the first post of this thread, and we'll see if we can help.

Ok so here it goes ... still no luck [wlan0 is disabled].

* **Machine Brand and Model** : Desktop PC Clone

* **Wireless Brand and Model (please post the whole line):**
```
lspci | grep Broadcom
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

* **Wireless Chipset: lspci -n | grep '14e4:43'**
```
lspci -n | grep '14e4:43'
01:09.0 0280: 14e4:4320 (rev 03)
```

* **Ubuntu Version: lsb_release -d**
```
lsb_release -d
Description:	Ubuntu 8.04.1
```

*** Kernel / Architecture: uname -mr**
```
uname -mr
2.6.24-19-generic i686
```

* **Any extra boot options you might be using :**None fresh install

* **Whether or not you had to compile NDISWrapper** : No

*** Which version of Step 2 you used :**2f

* **If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not :** No not yet, waiting for the proper approach
```
lsmod
Module                  Size  Used by
ndiswrapper           192920  0 
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
isofs                  36388  0 
udf                    88612  0 
ipv6                  267780  8 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5504  0 
ppdev                  10372  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
loop                   18948  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144420  0 
parport_pc             36260  1 
rfkill                  8592  29 rfkill_input,b43
parport                37832  3 ppdev,lp,parport_pc
mac80211              165652  1 b43
evdev                  13056  30 
analog                 13600  0 
cfg80211               15112  1 mac80211
gameport               16008  1 analog
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_nforce2             7680  0 
nvidia_agp              9628  1 
i2c_core               24832  1 i2c_nforce2
agpgart                34760  2 drm,nvidia_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
pata_acpi               8320  0 
pata_amd               14212  2 
8139cp                 24704  0 
floppy                 59588  0 
ata_generic             8324  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ssb                    34308  1 b43
libata                159344  3 pata_acpi,pata_amd,ata_generic
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
ohci_hcd               25348  0 
usbcore               146028  7 ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
```

---

### Post by Jamie Jackson on 2008-08-29
> **Theberge43 said:**
> 
* **Wireless Chipset: lspci -n | grep '14e4:43'**
```
lspci -n | grep '14e4:43'
01:09.0 0280: 14e4:4320 (rev 03)
```


14e4:4320 (rev 03)

I don't have one of these yet. This means that my guide *probably* doesn't have a driver for this device yet (but you're going to help me find one). ;-) What's the make/model/version of your device? (What's on the label?) 

Also, please post the output of "lspci -nnm"

---

### Post by Theberge43 on 2008-08-29
> **Jamie Jackson said:**
> 14e4:4320 (rev 03)

I don't have one of these yet. This means that my guide *probably* doesn't have a driver for this device yet (but you're going to help me find one). ;-) What's the make/model/version of your device? (What's on the label?) 

Also, please post the output of "lspci -nnm"

Linksys WMP54G

```
lspci -nnm
00:00.0 "Host bridge [0600]" "nVidia Corporation [10de]" "nForce2 IGP2 [01e0]" -rc1 "" ""
00:00.1 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 1 [01eb]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.2 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 4 [01ee]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.3 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 3 [01ed]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.4 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 2 [01ec]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.5 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 5 [01ef]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:01.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "nForce2 ISA Bridge [0060]" -ra4 "Giga-byte Technology [1458]" "Unknown device [0c11]"
00:01.1 "SMBus [0c05]" "nVidia Corporation [10de]" "nForce2 SMBus (MCP) [0064]" -ra2 "Giga-byte Technology [1458]" "Unknown device [0c11]"
00:02.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "nForce2 USB Controller [0067]" -ra4 -p10 "Giga-byte Technology [1458]" "Unknown device [5004]"
00:02.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "nForce2 USB Controller [0067]" -ra4 -p10 "Giga-byte Technology [1458]" "Unknown device [5004]"
00:02.2 "USB Controller [0c03]" "nVidia Corporation [10de]" "nForce2 USB Controller [0068]" -ra4 -p20 "Giga-byte Technology [1458]" "Unknown device [5004]"
00:06.0 "Multimedia audio controller [0401]" "nVidia Corporation [10de]" "nForce2 AC97 Audio Controler (MCP) [006a]" -ra1 "Giga-byte Technology [1458]" "Unknown device [a002]"
00:08.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "nForce2 External PCI Bridge [006c]" -ra3 "" ""
00:09.0 "IDE interface [0101]" "nVidia Corporation [10de]" "nForce2 IDE [0065]" -ra2 -p8a "Unknown vendor [f458]" "Unknown device [5002]"
00:1e.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "nForce2 AGP [01e8]" -rc1 "" ""
01:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Linksys [1737]" "Unknown device [0014]"
01:0b.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Giga-byte Technology [1458]" "GA-7VM400M/7VT600 Motherboard [e000]"
02:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RV350 AS [Radeon 9550] [4153]" "ASUSTeK Computer Inc. [1043]" "Unknown device [003c]"
02:00.1 "Display controller [0380]" "ATI Technologies Inc [1002]" "RV350 AS [Radeon 9550] (Secondary) [4173]" "ASUSTeK Computer Inc. [1043]" "Unknown device [003d]"
```

---

### Post by Jamie Jackson on 2008-08-30
> **Theberge43 said:**
> Linksys WMP54G

```
lspci -nnm
00:00.0 "Host bridge [0600]" "nVidia Corporation [10de]" "nForce2 IGP2 [01e0]" -rc1 "" ""
00:00.1 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 1 [01eb]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.2 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 4 [01ee]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.3 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 3 [01ed]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.4 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 2 [01ec]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:00.5 "RAM memory [0500]" "nVidia Corporation [10de]" "nForce2 Memory Controller 5 [01ef]" -rc1 "nVidia Corporation [10de]" "Unknown device [0c17]"
00:01.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "nForce2 ISA Bridge [0060]" -ra4 "Giga-byte Technology [1458]" "Unknown device [0c11]"
00:01.1 "SMBus [0c05]" "nVidia Corporation [10de]" "nForce2 SMBus (MCP) [0064]" -ra2 "Giga-byte Technology [1458]" "Unknown device [0c11]"
00:02.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "nForce2 USB Controller [0067]" -ra4 -p10 "Giga-byte Technology [1458]" "Unknown device [5004]"
00:02.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "nForce2 USB Controller [0067]" -ra4 -p10 "Giga-byte Technology [1458]" "Unknown device [5004]"
00:02.2 "USB Controller [0c03]" "nVidia Corporation [10de]" "nForce2 USB Controller [0068]" -ra4 -p20 "Giga-byte Technology [1458]" "Unknown device [5004]"
00:06.0 "Multimedia audio controller [0401]" "nVidia Corporation [10de]" "nForce2 AC97 Audio Controler (MCP) [006a]" -ra1 "Giga-byte Technology [1458]" "Unknown device [a002]"
00:08.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "nForce2 External PCI Bridge [006c]" -ra3 "" ""
00:09.0 "IDE interface [0101]" "nVidia Corporation [10de]" "nForce2 IDE [0065]" -ra2 -p8a "Unknown vendor [f458]" "Unknown device [5002]"
00:1e.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "nForce2 AGP [01e8]" -rc1 "" ""
01:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Linksys [1737]" "Unknown device [0014]"
01:0b.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Giga-byte Technology [1458]" "GA-7VM400M/7VT600 Motherboard [e000]"
02:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RV350 AS [Radeon 9550] [4153]" "ASUSTeK Computer Inc. [1043]" "Unknown device [003c]"
02:00.1 "Display controller [0380]" "ATI Technologies Inc [1002]" "RV350 AS [Radeon 9550] (Secondary) [4173]" "ASUSTeK Computer Inc. [1043]" "Unknown device [003d]"
```

Okay, might as well try the driver you've got now:

```
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

And see if you have wireless.

However, I suspect you won't yet, as I don't know if that's exactly the right driver for you.

I do think that the XP driver found in [here]("http://dlcdnet.asus.com/pub/ASUS/wireless/WL-100g-03/Driver_3607.zip") will be the right driver, though.

Once you get the right driver, and get it working temporarily (using the commands above), you can make it permanent by issuing:

```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```

Let us know if you need any assistance working through the above.

---

### Post by Theberge43 on 2008-08-30
It does something, because like I said in my 1st post my wlan0 is not disabled anymore, but it doesn't connect.

```
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:6e:03:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:93:3a:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

What should I try next ? I'm really a n00b on Linux.

---

### Post by Jamie Jackson on 2008-08-30
> **Theberge43 said:**
> It does something, because like I said in my 1st post my wlan0 is not disabled anymore, but it doesn't connect.

```
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:6e:03:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:93:3a:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

What should I try next ? I'm really a n00b on Linux.

I figure that driver's only half working, since I don't think it's perfectly suited to your device.

Try these commands, one at a time, at the command line:

```

# go home
cd ~ 
# make and go to a temporary directory
mkdir bcm43xx; cd bcm43xx 
# download what i *think* is the correct driver
wget http://dlcdnet.asus.com/pub/ASUS/wireless/WL-100g-03/Driver_3607.zip
# unzip the driver
unzip Driver_3607.zip 
# change to the XP driver directory
cd Driver/WinXP/
# remove the ndiswrapper module
sudo modprobe -r ndiswrapper
# remove the previously installed driver
sudo ndiswrapper -r bcmwl5
# install the new driver
sudo ndiswrapper -i bcmwl5.inf
# list ndiswrapper's driver (doesn't do anything, just a confirmation step)
ndiswrapper -l

```

Then, the ssb workaround:
```

# unload b43 (you don't need it with ndiswrapper, depending on whether you've rebooted, this may or may not throw an error. don't worry about it.)
sudo rmmod b43
# unload ssb
sudo rmmod ssb
# unload ndiswrapper (it's already unloaded, so you'll get an error, probably)
sudo rmmod ndiswrapper
# reload ndiswrapper
sudo modprobe ndiswrapper
# reload ssb
sudo modprobe ssb

```

Check to see if it finds access points, etc.

Then, report back...

Update: The lines beginning with "#" are comments. They're just notes to you, and you don't need to issue them at the command prompt.

---

### Post by Theberge43 on 2008-08-31
Oh yessss ! 8)

Now let's make it permanent !!!

Edit : Performance is not top notch ... but hey it works.

---

### Post by Jamie Jackson on 2008-08-31
> **Theberge43 said:**
> Oh yessss ! 8)

Now let's make it permanent !!!

Edit : Performance is not top notch ... but hey it works.

Unfortunately, I can help get it working, but I don't know much about getting it to perform *better.*

Anyway, issue this and try rebooting, and see if it works after the reboot. (It should connect automatically--you shouldn't have to do anything after rebooting.)

```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```

---

### Post by Theberge43 on 2008-08-31
You are officially my hero !!!
Thanks !

---

### Post by Jamie Jackson on 2008-08-31
> **Theberge43 said:**
> You are officially my hero !!!
Thanks !

And thank you! This device is now covered in the wiki as step 2g.

---

### Post by hugo humpel on 2008-08-31
I am an absolute newcomer on UBUNTU and trying to fix my WLAN connection for 2 days now. ...does not work.

Can you help me? Here are my detailed data.

Best regards
Hugo

    * ACER Aspire 3000
    hb@b:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:f0:d4:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.101 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:55:23:a3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
hb@b:~$ lspci | grep Broadcom
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
hb@b:~$ lspci -n | grep '14e4:43'
00:0b.0 0280: 14e4:4318 (rev 02)
hb@b:~$ uname -mr
2.6.24-19-generic i686
hb@b:~$ 
*Step 2a
*Hardy Bug Fix was needed

---

### Post by Jamie Jackson on 2008-09-01
> **hugo humpel said:**
> I am an absolute newcomer on UBUNTU and trying to fix my WLAN connection for 2 days now. ...does not work.

Can you help me? Here are my detailed data.

Best regards
Hugo

    * ACER Aspire 3000
    hb@b:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:f0:d4:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.101 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:55:23:a3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
hb@b:~$ lspci | grep Broadcom
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
hb@b:~$ lspci -n | grep '14e4:43'
00:0b.0 0280: 14e4:4318 (rev 02)
hb@b:~$ uname -mr
2.6.24-19-generic i686
hb@b:~$ 
*Step 2a
*Hardy Bug Fix was needed

Hi Hugo,

How's it failing? Also what's "iwlist wlan0 scan" give you?

---

### Post by sgrantham on 2008-09-01
Thank you, thank you, thank you.

Feisty was ndiswrapper, Gutsy -> fwcutter, Hardy back to ndiswrapper.  I appreciate Ubuntu's struggle to get wireless libraries working and up to snuff but it sure seems with Hardy, things were going backwards.   With broadcom you have saved the day again.  Thanks again for all and especially for the Hardy patch.

Sep.1 2008

---

### Post by him610 on 2008-09-01
Feedback 

Dell Dimension 4400
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:09.0 0280: 14e4:4320 (rev 02)
Description:	Ubuntu 8.04.1
2.6.24-19-generic i686
Not necessary to compile ndiswrapper
Used Step 2f
Applied Hardy Bug Fix 

As always, this procedure worked great.

---

### Post by hooby3dfx on 2008-09-03
> **Jamie Jackson said:**
> Sorry HOOBY!

You might need to recompile ndiswrapper for the new kernel, as the other poster mentioned. Or, the stock ndiswrapper is new enough that it should work fine. That's what I'd recommend. (In other words, uninstall the compiled ndiswrapper, then "sudo apt-get install ndiswrapper-utils-1.9".)

To boot into an older kernel, pay attention during your bootup, and you might get a short prompt to get into GRUB (you hit f2, or something), and you can select an older kernel from there.

Thanks for the advice.
I'm running into this problem:
```
 sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

---

### Post by Ayuthia on 2008-09-03
> **hooby3dfx said:**
> Thanks for the advice.
I'm running into this problem:
```
 sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

It sounds like you are still using the compiled version of ndiswrapper.  If that is the case, you will need to compile ndiswrapper for the older kernel.

---

### Post by Jamie Jackson on 2008-09-03
> **hooby3dfx said:**
> Thanks for the advice.
I'm running into this problem:
```
 sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

Have you uninstalled the compiled ndiswrapper?

To restate (more clearly) what I mentioned earlier, here's what I'd recommend:

1. [Remove the compiled version]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/")
2. Install the *packaged* ndiswrapper using "sudo apt-get install ndiswrapper-utils-1.9"

It's been a while since the compiled version was appreciably superior to the packaged version, so I don't think there's any real advantage to compiling ndiswrapper, for the time being.

Furthermore, packaged versions (of any software) are managed automagically, so you won't have to worry about recompiling to work with system upgrades, etc.

---

### Post by hooby3dfx on 2008-09-03
> **Jamie Jackson said:**
> Have you uninstalled the compiled ndiswrapper?

To restate (more clearly) what I mentioned earlier, here's what I'd recommend:

1. [Remove the compiled version]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/")
2. Install the *packaged* ndiswrapper using "sudo apt-get install ndiswrapper-utils-1.9"

It's been a while since the compiled version was appreciably superior to the packaged version, so I don't think there's any real advantage to compiling ndiswrapper, for the time being.

Furthermore, packaged versions (of any software) are managed automagically, so you won't have to worry about recompiling to work with system upgrades, etc.

:( I had uninstalled my compiled version and installed ndiswrapper-utils-1.9. Still no luck.  
:confused:
Wheres the module?

---

### Post by Ayuthia on 2008-09-03
> **hooby3dfx said:**
> :( I had uninstalled my compiled version and installed ndiswrapper-utils-1.9. Still no luck.  
:confused:
Wheres the module?

You can check and see if you can find the module by doing the following:
```
uname -r
sudo updatedb
sudo locate ndiswrapper.ko
```
If you are able to find a ndiswrapper.ko file in /lib/modules that matches the uname -r result, then the module is there.  You can update the modules list by doing the following:
```
sudo depmod -a
```

If that doesn't work, does the following produce valid results:
```
ndiswrapper -v
ndiswrapper -l
```

---

### Post by hooby3dfx on 2008-09-04
Results:
```
bryan@bryan-laptop:~$ uname -r
2.6.24-19-generic
bryan@bryan-laptop:~$ sudo updatedb
[sudo] password for bryan: 
bryan@bryan-laptop:~$ sudo locate ndiswrapper.ko
bryan@bryan-laptop:~$ ndiswrapper -v
modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
bryan@bryan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

```

---

### Post by Ayuthia on 2008-09-05
> **hooby3dfx said:**
> Results:
```
bryan@bryan-laptop:~$ uname -r
2.6.24-19-generic
bryan@bryan-laptop:~$ sudo updatedb
[sudo] password for bryan: 
bryan@bryan-laptop:~$ sudo locate ndiswrapper.ko
bryan@bryan-laptop:~$ ndiswrapper -v
modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
bryan@bryan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

```

It looks like you were able to get ndiswrapper-utils-1.9 but it does not look like ndiswrapper-common is installed.  You can verify that it is installed by doing the following from the Terminal:
```
aptitude search ndiswrapper
```
If there is an i at the beginning of the line, then the package is installed.  For example:
```

i   ndiswrapper-common                                                                                       - Common scripts required to use the utilities for ndiswrapper
v   ndiswrapper-modules-1.9                                                                                  -
i   ndiswrapper-utils-1.9                                                                                    - Userspace utilities for the ndiswrapper Linux kernel module

```This would show ndiswrapper-common and ndiswrapper-utils-1.9 is installed.

---

### Post by hooby3dfx on 2008-09-05
```
bryan@bryan-laptop:~$ aptitude search ndiswrapper
i A ndiswrapper-common              - Common scripts required to use the utiliti
v   ndiswrapper-modules-1.9         -                                           
i   ndiswrapper-utils-1.9           - Userspace utilities for the ndiswrapper Li

```

---

### Post by Crafty Kisses on 2008-09-05
Appreciate this, worked like a charm for my friend. :)

---

### Post by Ayuthia on 2008-09-05
> **hooby3dfx said:**
> Results:
```

bryan@bryan-laptop:~$ ndiswrapper -v
modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net

```

Ok.  Since your last post shows that you have ndiswrapper-common installed, then your home directory must have something called ndiswrapper there.  The ndiswrapper -v command tends to get tricked whenever that happens.  Can you try the following:
```
cd /home
ndiswrapper -v

```
I am guessing that there should not be any ndiswrapper files in your /home directory.  Hopefully that will produce a better result.

---

### Post by magerbak on 2008-09-05
Thanks, success! 

Dell Inspiron 1525 laptop, 32bit. Ubuntu 8.04.1. 2.6.24-19-generic i686.

Dell Wireless-N 1505 minicard: 
0b:00.0 Network Controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03), 14e4:4328.

Used option 2d, no Hardy fix, no ndiswrapper recompile.

Earlier attempts with ndiswrapper failed using the latest Vista driver R173590 (driver loaded but no wireless interface appeared). Had to go get older driver specified in 2d.

---

### Post by hooby3dfx on 2008-09-06
> **Ayuthia said:**
> Ok.  Since your last post shows that you have ndiswrapper-common installed, then your home directory must have something called ndiswrapper there.  The ndiswrapper -v command tends to get tricked whenever that happens.  Can you try the following:
```
cd /home
ndiswrapper -v

```
I am guessing that there should not be any ndiswrapper files in your /home directory.  Hopefully that will produce a better result.

Nope, same thing.

---

### Post by hooby3dfx on 2008-09-07
List of installed files for ndiswrapper-common:
```
/.
/sbin
/sbin/loadndisdriver
/usr
/usr/sbin
/usr/sbin/ndiswrapper
/usr/share
/usr/share/doc
/usr/share/doc/ndiswrapper-common
/usr/share/doc/ndiswrapper-common/README
/usr/share/doc/ndiswrapper-common/AUTHORS
/usr/share/doc/ndiswrapper-common/README.Debian
/usr/share/doc/ndiswrapper-common/copyright
/usr/share/doc/ndiswrapper-common/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-common/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/ndiswrapper.8.gz
/usr/share/man/man8/loadndisdriver.8.gz
/etc
/etc/ndiswrapper


```

---

### Post by dudenamedsteve on 2008-09-11
Got it, finally.  Thanks for this, it's quite helpful. A few years back i stumbled through this for a week with an old IBM T23.  I wish I had found this guide way back then.  Really, quite fantastic stuff.  Anyway, results:
I'm running Fiesty on a **Dell Latitude D420** with a Broadcom Corporation D**ell Wireless 1390 WLAN Mini-PCI Card** (rev 01) (0c:00.0 0280: **14e4:4311 (rev 01)**).  

**2.6.20-15-generic i686** kernal.

I didn't have to compile NDISWrapper.  So i've got that going for me...which is nice.

I went with Step 2a.

Again, thanks for this.

---

### Post by Ayuthia on 2008-09-11
> **hooby3dfx said:**
> List of installed files for ndiswrapper-common:
```
/.
/sbin
/sbin/loadndisdriver
/usr
/usr/sbin
/usr/sbin/ndiswrapper
/usr/share
/usr/share/doc
/usr/share/doc/ndiswrapper-common
/usr/share/doc/ndiswrapper-common/README
/usr/share/doc/ndiswrapper-common/AUTHORS
/usr/share/doc/ndiswrapper-common/README.Debian
/usr/share/doc/ndiswrapper-common/copyright
/usr/share/doc/ndiswrapper-common/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-common/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/ndiswrapper.8.gz
/usr/share/man/man8/loadndisdriver.8.gz
/etc
/etc/ndiswrapper


```

Sorry for not replying sooner, I was working on some sound issues in OpenSUSE on my laptop.  It looks like you are missing some of the modules in linux-ubuntu-modules.  You can reinstall it by doing the following:
```
sudo aptitude reinstall linux-ubuntu-modules-`uname -r`
```That will load the ndiswrapper.ko file back for you.

---

### Post by MegaJim on 2008-09-11
+1 working with the no-fluff on a new dell inspiron 1525 (with step 2e).

It just took one restart after completing the instructions in order for ndiswrapper to claim the device, and now full enterprise encryption is working.  Thanks a million!:guitar:

---

### Post by hooby3dfx on 2008-09-15
> **Ayuthia said:**
> Sorry for not replying sooner, I was working on some sound issues in OpenSUSE on my laptop.  It looks like you are missing some of the modules in linux-ubuntu-modules.  You can reinstall it by doing the following:
```
sudo aptitude reinstall linux-ubuntu-modules-`uname -r`
```That will load the ndiswrapper.ko file back for you.

Thank you!!!

---

### Post by guitarmaster on 2008-09-18
Well, that worked an absolute treat for me on my Dell inspiron 1501. It's a shame the wireless client that shipped with ubuntu didn't just work though.

Thank you! For a while there I thought I was going to have to go back to you-know-who as my OS provider.

Awesome.

---

### Post by neilmorr on 2008-09-19
Ok I went through all of the steps and at the end of step 3 I get module=tg3. I'm assuming I have a problem because it is not reading module=ndiswrapper. Anybody know what I should do? Should I try the bug fix and if so how should I do it?

---

### Post by neilmorr on 2008-09-19
Oh I'm sorry I think I was looking in the wrong place. I was looking under my ethernet network. Under wireless it says module=wl. So still it's not saying module=ndiswrapper or module=ssb. Any ideas?

---

### Post by Ayuthia on 2008-09-19
> **neilmorr said:**
> Oh I'm sorry I think I was looking in the wrong place. I was looking under my ethernet network. Under wireless it says module=wl. So still it's not saying module=ndiswrapper or module=ssb. Any ideas?

The wl driver is a new one that was introduced within the last few months.  It is one of the four options that are now available for some of the Broadcom cards.  If you want to see if the ndiswrapper module works, you can try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
sudo iwlist scan
```
If all goes well, you should see a list of wireless access points.  If it does work, you will need to add the wl module to the list of blacklisted modules:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by VorDesigns on 2008-09-20
* Machine Brand and Model
		Dell D830
    * Wireless Brand and Model 
		Broadcom Corporation BCM4312 802.11b/g (rev 01)
    * Wireless Chipset:  
		14e4:4315 (rev 01)
    * Ubuntu Version: 
		lsb_release -d
		(Used Dell Recovery download)
    * Kernel / Architecture: 
		2.6.24-19-generic i686
    * Whether or not you had to compile NDISWrapper
		No
    * Which version of Step 2 
		2e
		Note this was for BCM4310 (rev 01)
    * "Hardy Bug Fix" workaround or not
		not

Did not work work until I did what Rastus did
"I noted that the 'wl'driver was still listed so I tried to use the

sudo modprobe -d ndiswrapper
but it said that -d was an invalid argument.

So I went to the System > Administration > Hardware drivers and unchecked the "wl" driver and rebooted."

Selected the appropriate AP, entered WPA key, viola!

Cheers.

---

### Post by neilmorr on 2008-09-20
Thanks for the reply Ayuthia.

Ok, all of my wireless access points showed up. I still can't connect to any of them yet though. Where should I go from here?

---

### Post by Jamie Jackson on 2008-09-20
> **neilmorr said:**
> Thanks for the reply Ayuthia.

Ok, all of my wireless access points showed up. I still can't connect to any of them yet though. Where should I go from here?

Please have a look at the first post of this thread, and post the information requested. Please also post output of "lshw -C network"

---

### Post by neilmorr on 2008-09-20
Ok I just did what VorDesigns did (unchecked wl in the driver section) and it is working now! Thanks everyone.

---

### Post by jarome on 2008-09-20
I had good luck installing wicd as my connection manager. WPA2 never worked for me with the Ubunto/gnome one.

---

### Post by Jamie Jackson on 2008-09-20
I've added considerations for "wl" to the wiki:

First thing, is blacklisting "wl" for future boots. I added the wl blacklisting to the /etc/modprobe.d/blacklist
```
echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist

```

Until that first reboot happens, here's what I added to the temporary fix:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod wl #this step added Sep 20 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008
```

This is all in the wiki now, so it should just be a matter of following those instructions.

---

### Post by gordwait on 2008-09-20
> **hooby3dfx said:**
> Thank you!!!

I also needed to reload the modules. 
I suspect all my hacking about trying to get my 4306 to run left things in a mucked up state.

I now have ndiswrapper1.9 installed as the module (I had the ssb in 8.10 Hardy Heron issue). Now hopefully the wireless link will stay connected!
(I had it limping along before I tried this, and it would disconnect every so often, forcing me to reboot to get it back)..

Keeping my fingers crossed that it's working fully now!
Thanks,
Gord Wait

---

### Post by ronnietx on 2008-09-22
has anyone got a broadcom or linksys WMP54GS to work with 8.04 ?
I have no problem getting the card to find my routers but it WILL NOT connect to any of them. Open, WEK, WPA makes no difference, trying to connect to an OPEN router should be the easiest but that's a joke. Looking at the log files it tries to login no matter what and there is no easy way to disable security.

I have tried just about every suggestion in these forums and nothing works.

The wireless structure of Ubuntu has a long way to go before Windoz users will ever accept it.

---

### Post by Jamie Jackson on 2008-09-22
> **ronnietx said:**
> has anyone got a broadcom or linksys WMP54GS to work with 8.04 ?
I have no problem getting the card to find my routers but it WILL NOT connect to any of them. Open, WEK, WPA makes no difference, trying to connect to an OPEN router should be the easiest but that's a joke. Looking at the log files it tries to login no matter what and there is no easy way to disable security.

I have tried just about every suggestion in these forums and nothing works.

The wireless structure of Ubuntu has a long way to go before Windoz users will ever accept it.

Please post the details requested in the first post, as well as "lshw -C network"

---

### Post by wapa17 on 2008-09-24
Dell Vostro 1510 - Broadcom 4312.
lspci -n | grep '14e4:43' says: 14e4:4315 (rev 01)

Working with Ndiswrapper and first the XP-drivers directly from the DELL-website, and with wpa_supplicant I managed the connection to WPA and WPA2 with dhcp (WEP worked from the beginning).

Bought a dlink 300 router for homeuse. Could connect only the first day  without problems, the second day with a router - reset and from the third day on never more. :(

Messing around a bit, trying the (Beta)-version of network-manager 0.7 with the same results.

Then I got the idea to configure an static IP-reservation of my laptop in the wireless router ..  AND IT WORKED, although my wireless-interface use dhcp !

output of syslog
```

Sep 24 15:27:53 walter-laptop NetworkManager: <info>  dhclient started with pid 7540 
Sep 24 15:27:53 walter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 24 15:27:53 walter-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Sep 24 15:27:53 walter-laptop dhclient: Listening on LPF/wlan0/00:1f:e1:89:f3:fa
Sep 24 15:27:53 walter-laptop dhclient: Sending on   LPF/wlan0/00:1f:e1:89:f3:fa
Sep 24 15:27:53 walter-laptop dhclient: Sending on   Socket/fallback
Sep 24 15:27:55 walter-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Sep 24 15:27:55 walter-laptop dhclient: DHCPOFFER of 192.168.0.103 from 192.168.0.1
Sep 24 15:27:55 walter-laptop dhclient: DHCPREQUEST of 192.168.0.103 on wlan0 to 255.255.255.255 port 67
Sep 24 15:27:55 walter-laptop dhclient: DHCPACK of 192.168.0.103 from 192.168.0.1
Sep 24 15:27:55 walter-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Sep 24 15:27:55 walter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Sep 24 15:27:55 walter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Sep 24 15:27:55 walter-laptop NetworkManager: <info>    address 192.168.0.103 
Sep 24 15:27:55 walter-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Sep 24 15:27:55 walter-laptop NetworkManager: <info>    gateway 192.168.0.1 
Sep 24 15:27:55 walter-laptop NetworkManager: <info>    nameserver '192.168.0.1' 

``` 

Restarting several times - wireless connection ok.

Sure.. its not "the" solution, but it could help somebody with similar problems.

---

### Post by adramalech on 2008-10-02
okay so here is my problem...

okay so i don't know if anybody here can help my issue but i have had problems with getting wireless internet to work with ubuntu 8.04 hardy heron.

i recently upgraded from ubuntu 7.10 and am kindof trying to understand how wireless know works...since in 7.10 i used ndiswrapper i was kind of leaning towards doing that...so that is what i did..

now to make the story fast i looked at many url's to find out about how to go about it...so i used this page to do it...which for step two pointed to the ubuntu wiki help page (aka the url address after this one)

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

so i had an issue with ssb always showing as the value for module = ssb, even after i did the sudo rmmod ssb!!!  so i did fix #3 to have ndiswrapper ignore loading ssb, b44, b43, etc...


these are the steps from the first url...
the url list in this was the one where i got the hot fix for the bug where no matter what i did module =ssb and not ndiswrapper!!!

don't worry about the fact that bcm4312 is what the guy based this off of...it is generic for all version of bcm43xx and step 2 is the only thing that differs between all the versions of bcm43xx!!
```

I used the following steps to enable my Broadcom Wireless BCM4312 (rev 02).

Step 1 (run in terminal)

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

For Step 2, You can check your Broadcom wireless version with this command in terminal : "lspci | grep Broadcom Corporation",if your wireless device is different from BCM4312 (rev 02), please refer to the following link for this step and you can continue again with step 3 onwards:

https://help.ubuntu.com/community/Wi...f971ca757b2851


Step 2 (run in terminal)

sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe
cabextract sp34152.exe

Step 3 (run in terminal)

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto loniface lo inet loopbackn' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Step 4 (run in terminal)

sudo aptitude remove b43-fwcutter

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9

Restart your machine and enjoy the freedom from those wires....

```


after doing all the steps i still didn't have interent so i went through and ran some commands to see where i was...

```

adramalech@adramalech:~$ dmesg | grep ndiswrapper
[   39.680713] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.823469] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   39.824892] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   39.833388] ndiswrapper: using IRQ 11
[   40.179903] usbcore: registered new interface driver ndiswrapper
[   44.660025] ndiswrapper: device wlan0 removed
[   44.660411] usbcore: deregistering interface driver ndiswrapper
[   44.716300] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   44.730874] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   44.732363] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   44.741210] ndiswrapper: using IRQ 11
[   45.086258] usbcore: registered new interface driver ndiswrapper
adramalech@adramalech:~$

```

i also did  sudo lspci-nn

```

03:07.0 Network Controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

```

adramalech@adramalech:~$ sudo lshw -C network
[sudo] password for adramalech: 
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:02:da
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.131 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:07:1c:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
adramalech@adramalech:~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl
b44                    33168  0 
mii                     7552  1 b44
ssb                    39428  1 b44
ndiswrapper           243872  0 
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd

```

furthermore, after redoing the entire thing i still couldn't hit [FN] +[F2] and have the wireless light come on!!

i did ndiswrapper -l and it shows the bcmwl5.inf module installed correctly...


CAN SOMEONE PLLZZZ HELP ME!!

---

### Post by Jamie Jackson on 2008-10-02
> **adramalech said:**
> 
furthermore, after redoing the entire thing i still couldn't hit [FN] +[F2] and have the wireless light come on!!

i did ndiswrapper -l and it shows the bcmwl5.inf module installed correctly...


CAN SOMEONE PLLZZZ HELP ME!!

Please post the info requested in the first post of this thread (except the items that don't apply yet).

---

### Post by adramalech on 2008-10-02
okay well i have a 

gateway m7510gx

broadcom 4318 rev 02 

i have ubuntu 8.04 amd64 with the hotfix for the ssb module always showing...even if it was just rmmod!!

i have boot with noapic...

i have a windows xp home partition on my hardrive on top of ubuntu...

i had to compile ndiswrapper from a .tar

i have kernel version 2.6.24.19-generic

i used step 2a...

---

### Post by Jamie Jackson on 2008-10-03
> **adramalech said:**
> okay well i have a 

gateway m7510gx

broadcom 4318 rev 02 

i have ubuntu 8.04 amd64 with the hotfix for the ssb module always showing...even if it was just rmmod!!

i have boot with noapic...

i have a windows xp home partition on my hardrive on top of ubuntu...

i had to compile ndiswrapper from a .tar

i have kernel version 2.6.24.19-generic

i used step 2a...

Okay, thanks for that.

Now, please post the output of each the following:
```
ndiswrapper -l
lsmod
```

Then, issue the following, and copy/post your commands and the machine's response to all of the following.

```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod wl
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

lshw -C network
```

Also, assuming this is the file that you "hot fixed," please paste in its contents: /etc/modprobe.d/ndiswrapper 

Finally, paste in the contents of: /etc/modprobe.d/ndiswrapper

I know that's a lot of stuff, but it gives us a better chance of figuring this out in one shot.

Thanks,
Jamie

---

### Post by lkraemer on 2008-10-03
Jamie,
THANKS!  What a life saver.


    * Machine Brand and Model
      Compaq V5201US  
    * Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
      06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    * Wireless Chipset: lspci -n | grep '14e4:43'
      06:02.0 0280: 14e4:4318 (rev 02)
    * Ubuntu Version: lsb_release -d
      Description:	Ubuntu 8.04.1
    * Kernel / Architecture: uname -mr
      2.6.24-19-generic i686
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
      NONE
    * Whether or not you had to compile NDISWrapper
      NO
    * Which version of Step 2 you used (If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)
      2A
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
      NO

After fussing with other writeups all day, and well into the evening, I gave up.
This morning I found your writeup.  I had just formatted the partition and installed
Ubuntu 8.04 LTS, and your writeup did the trick.  THANKS.

lkraemer

---

### Post by adramalech on 2008-10-04
okay here is the result of all the commands you wanted me too:

```

adramalech@adramalech:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
adramalech@adramalech:~$ lsmod
Module                  Size  Used by
af_packet              27272  2 
ipt_LOG                 8192  3 
xt_limit                4608  3 
ipt_addrtype            3328  3 
xt_state                4096  2 
xt_tcpudp               4992  8 
nf_conntrack_ipv4      21904  4 
xt_conntrack            5248  2 
ip6table_filter         4352  1 
ip6_tables             17800  1 ip6table_filter
nf_nat_irc              4352  0 
nf_conntrack_irc        8992  1 nf_nat_irc
nf_nat_ftp              5120  0 
nf_nat                 23980  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ftp       11688  1 nf_nat_ftp
nf_conntrack           79216  8 xt_state,nf_conntrack_ipv4,xt_conntrack,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ftp
ipv6                  311848  10 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
b44                    33168  0 
mii                     7552  1 b44
ssb                    39428  1 b44
ndiswrapper           243872  0 
ppdev                  11400  0 
powernow_k8            16608  0 
cpufreq_stats           8416  0 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
cpufreq_powersave       3200  0 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
dock                   12960  0 
sbshc                   8960  1 sbs
container               6656  0 
iptable_filter          4608  1 
ip_tables              24104  1 iptable_filter
x_tables               23560  8 ipt_LOG,xt_limit,ipt_addrtype,xt_state,xt_tcpudp,xt_conntrack,ip6_tables,ip_tables
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
pcmcia                 45976  0 
snd_atiixp             24340  3 
snd_atiixp_modem       19724  0 
snd_ac97_codec        123224  2 snd_atiixp,snd_atiixp_modem
ac97_bus                3840  1 snd_ac97_codec
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
fglrx                1804800  23 
snd_pcm                92168  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
sky2                   53892  0 
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
battery                16776  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               9092  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      8328  0 
psmouse                46236  0 
yenta_socket           30092  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            46116  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4              11148  0 
snd                    70856  18 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
button                 10912  0 
i2c_core               28544  1 i2c_piix4
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
snd_page_alloc         13200  3 snd_atiixp,snd_atiixp_modem,snd_pcm
k8temp                  7680  0 
evdev                  14976  6 
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
ide_cd                 35488  0 
cdrom                  41512  1 ide_cd
ide_disk               19072  3 
pata_atiixp            10496  0 
pata_acpi               9856  0 
ata_generic             9988  0 
libata                176432  3 pata_atiixp,pata_acpi,ata_generic
scsi_mod              178488  2 sbp2,libata
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
atiixp                  6672  0 [permanent]
ide_core              136600  3 ide_cd,ide_disk,atiixp
ehci_hcd               41996  0 
ohci_hcd               27524  0 
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  3 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 
adramalech@adramalech:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
adramalech@adramalech:~$ sudo rmmod b44
adramalech@adramalech:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
adramalech@adramalech:~$ sudo rmmod wl
ERROR: Module wl does not exist in /proc/modules
adramalech@adramalech:~$ sudo rmmod ssb
adramalech@adramalech:~$ sudo rmmod ndiswrapper
adramalech@adramalech:~$ sudo modprobe ndiswrapper
adramalech@adramalech:~$ sudo modprobe ssb
adramalech@adramalech:~$ sudo modprobe b44
adramalech@adramalech:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:02:da
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.131 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:07:1c:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
adramalech@adramalech:~$ 

```

---

### Post by TuckEverlasting on 2008-10-05
Hi Jamie,

I tried the steps in your guide, and it worked! The first time. So I restarted my computer to make sure it would work upon restarting, and - it doesn't. And not only that, but re-doing the instructions no longer works, either.

I'm using a Studio 15 with a BCM4322. The output of lshw -C network is:

[I]*-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0[/I]

That 'configuration' line used to read something else, when the wireless was working, but I don't remember what it was.

Thanks for putting that guide together, FWIW.

---

### Post by nadavkav on 2008-10-05
i got my HP Pavilion tx2520ej + BCM4310 (14e4:4315) to work
with Broadcom's wl driver and not with ndiswrapper.
i tried MANY versions of windows drivers with ndiswrapper
and none worked, lucky me.

i got the wl sources from :
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and compiled the x64 bit version according to the README

now it works :-)

here is some hardware info:

product: BCM4310 USB Controller [14E4:4315]
vendor: Broadcom Corporation [14E4]
bus info: pci@0000:08:00.0
logical name: wlan0
version: 01
serial: 00:21:00:34:08:ce
width: 64 bits
clock: 33MHz
capabilities:
	Power Management,
	Message Signalled Interrupts,
	PCI Express,
	bus mastering,
	PCI capabilities listing,
	ethernet,
	Physical interface,
	Wireless-LAN
configuration:
	broadcast: yes
	driver: wl
	ip: 192.168.1.101
	latency: 0
	module: wl
	multicast: yes
	wireless: IEEE 802.11bg

lspci:
Network controller:
```
 Broadcom Corporation BCM4310 USB Controller (rev 01)
```

uname -mr
```
2.6.26-1-amd64 x86_64
```

```
Debian Sid
```

i used these lines inside /etc/network/interfaces

```
allow-hotplug wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid our-ap-name
```

---

### Post by Jamie Jackson on 2008-10-07
> **TuckEverlasting said:**
> Hi Jamie,

I tried the steps in your guide, and it worked! The first time. So I restarted my computer to make sure it would work upon restarting, and - it doesn't. And not only that, but re-doing the instructions no longer works, either.

I'm using a Studio 15 with a BCM4322. The output of lshw -C network is:

[I]*-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0[/I]

That 'configuration' line used to read something else, when the wireless was working, but I don't remember what it was.

Thanks for putting that guide together, FWIW.

Doing it twice isn't really advisable, but let's try to see where you are now.

First, please post all of the information requested in the very first post of this thread. Second, please post the information for which I asked [this other person]("http://ubuntuforums.org/showpost.php?p=5899373&postcount=196").

---

### Post by Jamie Jackson on 2008-10-07
> **adramalech said:**
> okay here is the result of all the commands you wanted me too:

After you ran this, you did not get your wireless light? According to the command output, the driver had loaded.

Anyway, there's one command you missed, and a couple I should have mentioned:
```

cat /etc/modprobe.d/ndiswrapper
cat /etc/network/interfaces
cat /etc/modules

```

**Please ignore the following**, it's a note to myself about your system. Don't run this yet.
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

```

---

### Post by Wee Aldo on 2008-10-07
Worked perfectly first time on my Dell Latitude 5400, ndiswrapper loaded on reboot, but I remembered to put /etc/init.d/networking restart in the init,d file to stop having to enter the wpa password.

---

### Post by adramalech on 2008-10-08
well the light didn't light up showing that i had wireless internet:confused:!!

i will post those output to those commands and show you what the files consist of..

---

### Post by jearod on 2008-10-08
Hello all,
I've had very little experience with Ubuntu/Linux in general so I'm asking for some help.
First, I bought a Dell Mini 9 with XP on it, clean installed 8.04.1
and got everything to work right except wifi.
The restricted wl driver worked, but only on open networks. Tried the ndiswrapper route but I guess I'm not technically advanced enough to make that work...
However, after a little more research I came across this page for dell-branded wireless cards:

[http://direct2dell.com/one2one/archive/2008/10/03/linux-driver-available-for-dell-wireless-cards.aspx](http://direct2dell.com/one2one/archive/2008/10/03/linux-driver-available-for-dell-wireless-cards.aspx)

Which you can read to get the idea, and the download link on the page is broken but I got this out of it:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


So after I tried using ndiswrapper with the xp drivers (and failed), Network manager no longer sees my wireless card. I read somewhere where 8.10 fixes a network manager problem so I upgraded last night and wouldn't you know the only package that couldn't install was the network manager! So that did absolutely nothing for me.

If anyone experiments with the above drivers with success please give me a little insight on how to get out of my situation.

Thanks!

And YES, I followed the readme but it is not very intuitive.

---

### Post by jearod on 2008-10-08
Nevermind. I guess I did something right...or I just didn't notice when I upgraded to 8.10 but....

Went into system-administrator-hardware drivers and there was option to activate.
Works great with WPA2!

---

### Post by Kahomono on 2008-10-10
Dell Latitude D800

lspci | grep Broadcom ==> 
 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
 02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

lspci -n | grep '14e4:43' ==>
 02:03.0 0280: 14e4:4324 (rev 02)

lsb_release -d ==> 
 Description: Ubuntu 8.04.1

uname -mr ==>
 2.6.24-19-generic i686

I used version 2a in Step 2, based on it being Rev 02.  Never got as far as trying to compile the NDISWRAPPER, because when I started the Hardy Bug fix and it got to >sudo modprobe ndiswrapper, the machine locked up tight.  Happened twice, had to power-cycle to get it back.  Not really wanting to proceed further until I get some counsel here....

Thanks,
--David

---

### Post by adramalech on 2008-10-11
okay well here are the outputs to the commands you wanted me to run...i hope this helps...

```

adramalech@adramalech:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Fri Sep 26 19:01:30 PDT 2008 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
adramalech@adramalech:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

adramalech@adramalech:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
ndiswrapper

adramalech@adramalech:~$ 

```

i was told by a friend that if i was to say take the windows driver for my broadcom card and 7 zip them then put it on my linux distro it should be able to work...

i am hoping that the driver from the manufacture of the laptop will help me be able to get to my goal of having the wireless working...

is there any chance that ubuntu 8.10 will be have a better ability to utilize wireless on broadcoms???

---

### Post by Ayuthia on 2008-10-11
> **adramalech said:**
> 
is there any chance that ubuntu 8.10 will be have a better ability to utilize wireless on broadcoms???
The answer is yes, but only for some of the Broadcom cards.  The 4311, 4312, 4322, and 4328 cards are going to have the option of using the wl driver which is included in the 8.10 liveCD.  That means that those cards will work out of the box.  However, I have not heard of any specific changes in the b43 driver for the 4318 card.  I do know that the driver is improved and that new firmware is used so the 4318 might work better with the b43 driver.  As for ndiswrapper, I have not heard of any changes for Intrepid.

---

### Post by akacool15 on 2008-10-11
I am still having trouble after following all the instructions posting the details asked for, please help, i am ready to pull my hair out. Thanks in advance for your time

# Machine Brand and Model
#Acer Wlmi 5002
Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
#00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Wireless Chipset: lspci -n | grep '14e4:43'
#00:0b.0 0280: 14e4:4318 (rev 02)
Ubuntu Version: lsb_release -d
#Ubuntu 8.04.1
Kernel/architecture (including 32 vs. 64 bit) : uname -mr
#2.6.24-19-generic x86_64
# Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
none
# Whether or not you had to compile NDISWrapper
no
# Which version of Step 2 you used
2a did not work then tried 2c did not work
# If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not, and if you used it, which version you used. 
yes 0.3 but did not work
**********
Wooo hooo i am on now,  I also added steps 6 thru 9 in the below post, i am good now , thanks everyone for the posts and help
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by Jamie Jackson on 2008-10-13
> **Kahomono said:**
> Dell Latitude D800

lspci | grep Broadcom ==> 
 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
 02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

lspci -n | grep '14e4:43' ==>
 02:03.0 0280: 14e4:4324 (rev 02)

lsb_release -d ==> 
 Description: Ubuntu 8.04.1

uname -mr ==>
 2.6.24-19-generic i686

I used version 2a in Step 2, based on it being Rev 02.  Never got as far as trying to compile the NDISWRAPPER, because when I started the Hardy Bug fix and it got to >sudo modprobe ndiswrapper, the machine locked up tight.  Happened twice, had to power-cycle to get it back.  Not really wanting to proceed further until I get some counsel here....

Thanks,
--David

Hi David,

One other user had luck with step 2b for this chipset. Would you try that, please?

That same user claimed that they had to compile ndiswrapper, in addition to using step 2b. However, I would prefer if you didn't compile ndiswrapper.

So, please try 2b. If that doesn't work, please post the make, model, and revision/version (three pieces of information) for your card, so we can find exactly the right driver (as your chipset isn't listed on the wiki yet).

Thanks,
Jamie

---

### Post by Jamie Jackson on 2008-10-13
> **adramalech said:**
> i was told by a friend that if i was to say take the windows driver for my broadcom card and 7 zip them then put it on my linux distro it should be able to work...

i am hoping that the driver from the manufacture of the laptop will help me be able to get to my goal of having the wireless working...

Unfortunately all the stuff you're posting looks fine. The only two remaining thoughts I have:

1. Check to make sure that your hardware switch for the wireless device is in the "on" position. This has bitten more than one follower of this guide. My hardware switch for the wireless happens to be on the left side of my machine (on a Dell Latitude), yours might be in a different spot.
2. Double check the version of step 2 that you used, and if need be, reinstall the correct step 2 version.

As to your questions, yes, if the above doesn't work, and you want to try out your windows drivers. You may use the XP driver from your XP installation (but not a Vista installation). Be sure to grab the .sys and the .inf files.

---

### Post by gopchandani on 2008-10-13
Hey,

After following a bunch of tutorials, I discovered that the latest driver of my Dell 1395 won't work. So I got an older version and installed them and it started working, i.e. driver got installed, I can see the wireless interface, it can scan and show my my home Wireless Network.

But here's the problem, I am trying to connect to my home wireless router on WPA but it won't connect for the same settings Vista works! Now I did read some threads suggesting some problem with WPA encryption but could not make sense of that.

I came across a link for older Ubuntu version saying that the problem gets fixed with installing WPASupplicant but when I tried to install WPASupplicant, discovered that it is already there with a later version in my Ubuntu (8.04)

I did the Enable = 0 thing and rebooted but did not work.

Now can anyone help me what can be the trouble? Is it something my device specific, if so, any available hacks to fix it? Any suggestions/pointers etc would really help.

---

### Post by alancsi on 2008-10-14
* Machine Brand and Model
[COLOR="Navy"]Dell Inspiron E1505[/COLOR]
    * Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
[COLOR="Navy"]03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/COLOR]

    * Wireless Chipset: lspci -n | grep '14e4:43'
[COLOR="Navy"]0b:00.0 0280: 14e4:4311 (rev 01)[/COLOR]
    * Ubuntu Version: lsb_release -d
[COLOR="Navy"]Description:	Ubuntu 8.04.1[/COLOR]
    * Kernel / Architecture: uname -mr
[COLOR="Navy"]2.6.24-19-generic i686[/COLOR]
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
    * Whether or not you had to compile NDISWrapper
[COLOR="Navy"]NO[/COLOR]
    * Which version of Step 2 you used (If you try the recommended step 2, and it doesn't work, and then you find some other, presumably newer, driver version that *does* work, please provide a link to the download, for inclusion consideration.)
[COLOR="Navy"]2a[/COLOR]
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
[COLOR="Navy"]YES[/COLOR]

I am now able to see my wireless network by:
[COLOR="Navy"]sudo iwlist scanning 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:88:9D:62:99
                    ESSID:"XXXXXXX"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

eth0      Interface doesn't support scanning.[/COLOR]


Also-
[COLOR="Navy"]ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)[/COLOR]


So I think I'm almost there.
However no networks show up under Network Manager. I have tried a previous release, and the current release. No go.
Little help?
Thanks!

[COLOR="Red"]
Solved. Reinstalled latest version of Network Manager.
Working now.[/COLOR]

Thanks for your great instructions!

---

### Post by Jamie Jackson on 2008-10-15
> **gopchandani said:**
> Hey,

After following a bunch of tutorials, I discovered that the latest driver of my Dell 1395 won't work. So I got an older version and installed them and it started working, i.e. driver got installed, I can see the wireless interface, it can scan and show my my home Wireless Network.

But here's the problem, I am trying to connect to my home wireless router on WPA but it won't connect for the same settings Vista works! Now I did read some threads suggesting some problem with WPA encryption but could not make sense of that.

I came across a link for older Ubuntu version saying that the problem gets fixed with installing WPASupplicant but when I tried to install WPASupplicant, discovered that it is already there with a later version in my Ubuntu (8.04)

I did the Enable = 0 thing and rebooted but did not work.

Now can anyone help me what can be the trouble? Is it something my device specific, if so, any available hacks to fix it? Any suggestions/pointers etc would really help.

Did you try the driver mentioned in the wiki? If there is no driver listed for your device, please post all the information in the first post of this thread, as well as the make, model, and revision of your device (the information on the device's label or box).

---

### Post by Jamie Jackson on 2008-10-15
> **Ayuthia said:**
> The answer is yes, but only for some of the Broadcom cards.  The 4311, 4312, 4322, and 4328 cards are going to have the option of using the wl driver which is included in the 8.10 liveCD.  That means that those cards will work out of the box.  However, I have not heard of any specific changes in the b43 driver for the 4318 card.  I do know that the driver is improved and that new firmware is used so the 4318 might work better with the b43 driver.  As for ndiswrapper, I have not heard of any changes for Intrepid.

Notes to self: 

Today, my machined pulled kernel 2.6.24-21 during the auto upgrade, and after reboot I had a restricted drivers manager notification on my panel, I didn't check it out right away.

On another reboot, there is no notification, but I do see "Broadcom STA wireless driver" listed in System > Administration > Hardware drivers. I haven't yet investigated this option yet.

I guess this is probably the "wl" driver, and if it is, I think it will claim to be the (working) native driver that I've been waiting for. However, even if it is, I don't think it's theoretically capable of the same throughput as the ndiswrapper option.

I'll have to investigate further when I have time, but it would be great if the wl driver makes more of of these Broadcom cards work out of the box, even if it doesn't match ndiswrapper's capabilities.

I wonder why others got the wl option so much earlier than I did. Maybe they're running more bleeding edge systems than I am?

---

### Post by Ayuthia on 2008-10-15
> **Jamie Jackson said:**
> Notes to self: 

Today, my machined pulled kernel 2.6.24-21 during the auto upgrade, and after reboot I had a restricted drivers manager notification on my panel, I didn't check it out right away.

On another reboot, there is no notification, but I do see "Broadcom STA wireless driver" listed in System > Administration > Hardware drivers. I haven't yet investigated this option yet.

I guess this is probably the "wl" driver, and if it is, I think it will claim to be the (working) native driver that I've been waiting for. However, even if it is, I don't think it's theoretically capable of the same throughput as the ndiswrapper option.

I'll have to investigate further when I have time, but it would be great if the wl driver makes more of of these Broadcom cards work out of the box, even if it doesn't match ndiswrapper's capabilities.

I wonder why others got the wl option so much earlier than I did. Maybe they're running more bleeding edge systems than I am?

It is because you are the great leader of this thread and guide!  :)

It looks like they have finally moved the kernel out of hardy-proposed.  Most people would have seen it from there or else have compiled and installed it themselves.

As for the wl driver, it does work really well (for those who can use it).  At least it does for the 4311 rev 01.  It has the best signal out of all three for me and it does have pretty good throughput (the fastest that I have seen for my card).

I am about to test out the speeds on 2.6.27 to see if the b43 driver has caught up yet or not.

As for testing it out for yourself, don't do it!!!!!  We still need you here!

---

### Post by Jamie Jackson on 2008-10-15
> **Ayuthia said:**
> It is because you are the great leader of this thread and guide!  :)

It looks like they have finally moved the kernel out of hardy-proposed.  Most people would have seen it from there or else have compiled and installed it themselves.

As for the wl driver, it does work really well (for those who can use it).  At least it does for the 4311 rev 01.  It has the best signal out of all three for me and it does have pretty good throughput (the fastest that I have seen for my card).

I am about to test out the speeds on 2.6.27 to see if the b43 driver has caught up yet or not.

As for testing it out for yourself, don't do it!!!!!  We still need you here!

:redface:

Help me understand something: Do the native drivers (e.g., wl) break the theoretical 11Mb/s throughput barrier that, (I think) fwcutter had?

So, is wl theoretically capable of 54Mb/s, the way ndiswrapper-wrapped drivers are?

I'd like to get some definitive answer on the theoretical upper limits of these drivers in Linux. (Even though what really matters in the end is empirical throughput.)

Also, if I made any false assumptions above, please set me straight.

---

### Post by Ayuthia on 2008-10-15
> **Jamie Jackson said:**
> :redface:

Help me understand something: Do the native drivers (e.g., wl) break the theoretical 11Mb/s throughput barrier that, (I think) fwcutter had?

So, is wl theoretically capable of 54Mb/s, the way ndiswrapper-wrapped drivers are?

I'd like to get some definitive answer on the theoretical upper limits of these drivers in Linux. (Even though what really matters in the end is empirical throughput.)

Also, if I made any false assumptions above, please set me straight.

The wl driver should be able to break the barrier.  I will need to time the .iso transfer on my network, but the wl driver is definitely the fastest.

I will be testing the b43 drivers soon to see if they get better throughput.  I'll PM you with my results when I get them.

However, I am sure that your card will have terrible times because ndiswrapper is better for you... :)  Actually, I am not for sure what card you have.  We just need you here. :)

---

### Post by Jamie Jackson on 2008-10-15
> **Ayuthia said:**
> The wl driver should be able to break the barrier.  I will need to time the .iso transfer on my network, but the wl driver is definitely the fastest.

I will be testing the b43 drivers soon to see if they get better throughput.  I'll PM you with my results when I get them.

However, I am sure that your card will have terrible times because ndiswrapper is better for you... :)  Actually, I am not for sure what card you have.  We just need you here. :)

:D Well, I can always go back and forth! (I've got the same card as you, BTW.)

BTW, I was interested to learn about [iperf]("http://ubuntuforums.org/showthread.php?t=528609") for testing throughput. Maybe you know about it, maybe not...

(Not necessarily directed toward Ayuthia: ) So which drivers are/were inherently crippled (limited to 11Mb/s, or wireless-B speeds)? Is that only the case with fwcutter, and if so, has that situation changed?

---

### Post by Ayuthia on 2008-10-15
> **Jamie Jackson said:**
> :D Well, I can always go back and forth! (I've got the same card as you, BTW.)

BTW, I was interested to learn about [iperf]("http://ubuntuforums.org/showthread.php?t=528609") for testing throughput. Maybe you know about it, maybe not...

(Not necessarily directed toward Ayuthia: ) So which drivers are/were inherently crippled (limited to 11Mb/s, or wireless-B speeds)? Is that only the case with fwcutter, and if so, has that situation changed?

I just installed iperf and I am getting 32 Mbits/sec for all of them:
```

wl - 32.2
ndiswraper - 32.1
b43 - 32.1
```
As for the 11Mb/s, that issue was with the 4311 cards but I am not for sure if there were others also.  That problem was to have gone away in 2.6.22, but there were transmission issues until 2.6.24.  2.6.24 fixed the issues, but reported slower speeds and was not as fast as ndiswrapper.  However for 2.6.27, they all look about the same.  Of course, I tested all of this in Arch using the 2.6.27 kernel.  The results should be about the same in Intrepid though because Linux is pretty much Linux.

---

### Post by Jamie Jackson on 2008-10-15
> **Ayuthia said:**
> I just installed iperf and I am getting 32 Mbits/sec for all of them:
```

wl - 32.2
ndiswraper - 32.1
b43 - 32.1
```
As for the 11Mb/s, that issue was with the 4311 cards but I am not for sure if there were others also.  That problem was to have gone away in 2.6.22, but there were transmission issues until 2.6.24.  2.6.24 fixed the issues, but reported slower speeds and was not as fast as ndiswrapper.  However for 2.6.27, they all look about the same.  Of course, I tested all of this in Arch using the 2.6.27 kernel.  The results should be about the same in Intrepid though because Linux is pretty much Linux.

Brilliant, thanks for the info!

---

### Post by BigAce on 2008-10-20
Hi
I couldn't get wifi connexion since 2.6.24-21-generic i686 upgrade (16th of october 08).
Before this event, I had nothing to do, everything worked well. I installed Hardy on my brand new DELL VOSTRO 1510 2 months ago. And WIFI networks appeared in my network-manager window (2 black computers on the up right), and I had no problem to connect.
But, since I've upgrade from 2.6.24-19-generic to 2.6.24-21-generic, I couldn't see wifi networks.
Then, I wasted a lot of time to try to understand and to correct it.

And ... I've just found the solution : the small button of my DELL VOSTRO 1510 wifi card, on the left side, was off !!! And it is very difficult to know that, because, nothing is visible to know it.

So, if this could help any DELL VOSTRO 1510 user : before anything, check this small button is in the correct way !

---

### Post by adramalech on 2008-10-20
okay so what i did was install wine and had wine extract them to a file on my windows xp partition...

i then took the c:\cab\... to my desktop i then uninstalled the old driver and rmmod ndiswrapper i then changed directory's to the gateway's xp driver for my bcm4318 card...

then i said ndiswrapper -i bcmwl5.inf and then i said modprobe ndiswrapper

i then ndiswrapper -l and it said the bcmwl5 was primary driver but i still had the ssb on there as the secondary!!!

i then restarted and the light still didn't come on!! and i was like wtf!!

in the extracted gateway xp driver was the .sys and .inf file along with alot of other stuff...should i just have the .sys and .inf file in the file?? also should i move the files somewhere else other than the desktop??

i also totally deleted the other driver...

---

### Post by adramalech on 2008-10-21
okay well from what i did above everything is good i just screwed up because gateway is idiots and don't have a 64bit broadcom driver so i had to uninstall the last driver and redo it...so i got the light working when i used a different driver a 64bit bcm4318 driver...it then would light up and would not connect to anything...

so i physically deleted the ssb, b44, b43xx, b43, .ko files and directories...now it won't light up at all!!! with using the same drivers....

idk wtf i did wrong...it only should use ndiswrapper...

i then thought well maybe reinstall ndiswrapper...so what i did was i got rid of ndiswrapper and reinstalled the ndiswrapper 1.53 from sourceforge.net it then successfully installed and still i don't have internet at all...i am thinking of just reinstallin the 32bit version of linux because the 64bit driver has become a total pain in the ***!!!

idk how anybody got it working because logically i would think that most of all the ubuntu 8.04 users with the bcm4318 driver got it working me using the same steps would work but no it didn't and i have done it many different ways...

bottom line is that it showed the drivers installed correctly and hardware is present but either the light came on and didn't connect...or light wouldn't come on and everything was installed correctly...

---

### Post by Jamie Jackson on 2008-10-22
> **adramalech said:**
> okay well from what i did above everything is good i just screwed up because gateway is idiots and don't have a 64bit broadcom driver so i had to uninstall the last driver and redo it...so i got the light working when i used a different driver a 64bit bcm4318 driver...it then would light up and would not connect to anything...

so i physically deleted the ssb, b44, b43xx, b43, .ko files and directories...now it won't light up at all!!! with using the same drivers....

idk wtf i did wrong...it only should use ndiswrapper...

i then thought well maybe reinstall ndiswrapper...so what i did was i got rid of ndiswrapper and reinstalled the ndiswrapper 1.53 from sourceforge.net it then successfully installed and still i don't have internet at all...i am thinking of just reinstallin the 32bit version of linux because the 64bit driver has become a total pain in the ***!!!

idk how anybody got it working because logically i would think that most of all the ubuntu 8.04 users with the bcm4318 driver got it working me using the same steps would work but no it didn't and i have done it many different ways...

bottom line is that it showed the drivers installed correctly and hardware is present but either the light came on and didn't connect...or light wouldn't come on and everything was installed correctly...

Wiping out ssb probably isn't a good idea. I think you probably don't have quite the right driver.

Installing 32 bit Ubuntu is an option, but first...

I don't think you've posted your pci id yet. Would you post the unedited output of the following, please?
```
lspci -n | grep '14e4:43'
```

---

### Post by mattiastbs on 2008-10-29
This guide worked wonderful..

* Compaq nx7300
* 10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
* 10:00.0 0280: 14e4:4311 (rev 01)
* Ubuntu 8.10
* Kernel / Architecture: 2.6.27-7-generic i686
* I had to compile NDISWrapper
* I used Step 2a and it worked just fine.

//Mattias in Sweden

---

### Post by Leo the Lion on 2008-11-01
Hi all,
I followed the "how to" with no success.
I did a fresh install of Hardy, did all of the updates and followed the how to.

When I run lspci | grep Broadcom I get:

```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-Tx (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

When I run lspci -n | grep '14e4:43' I get:

```
0b:00.0 0280: 14e4:4311 (rev 01)
```

So I did STEP 1, then STEP 2a, and finally STEP 3. 

When I ran lshw -C network, this is what I get:

```
 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:85:09:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.46 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:cc:a5:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

So, as you can see, there is nothing under "configuration" for the wireless that would indicate to what "module" is being used. Now I have no idea what is wrong.

Any help would be greatly appreciated.

Thanks all.

---

### Post by Ayuthia on 2008-11-01
> **Leo the Lion said:**
> Hi all,
I followed the "how to" with no success.
I did a fresh install of Hardy, did all of the updates and followed the how to.

When I run lspci | grep Broadcom I get:

```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-Tx (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

When I run lspci -n | grep '14e4:43' I get:

```
0b:00.0 0280: 14e4:4311 (rev 01)
```

So I did STEP 1, then STEP 2a, and finally STEP 3. 

When I ran lshw -C network, this is what I get:

```
 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:85:09:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.46 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:cc:a5:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

So, as you can see, there is nothing under "configuration" for the wireless that would indicate to what "module" is being used. Now I have no idea what is wrong.

Any help would be greatly appreciated.

Thanks all.

If ndiswrapper is showing that the device is present, you can try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe b43
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```If all is well, you should see a list of wireless sites.  You have a Broadcom wired card that requires the ssb module (the b44 module) so you will need to use the ssb workaround so that you are able to use ndiswrapper and also your wired card. This set of commands will only work for this connection.  If this works, ou can follow the version 0.3 on how to make it permanent.

---

### Post by blis102 on 2008-11-02
Hello everyone,

I followed the instructions in the Wiki (step 2a and Hardy Bug Fix step) and successfully got my Linksys WPC54GS to work on my old Viao laptop with no problems on Ubuntu 8.1 Intrepid. 

Thanks a ton!
Dana

---

### Post by kevdog on 2008-11-14
Jamie

Haven't heard from you in a while --- good to know your beans are not burnt!  Have you tried any of your instructions with Intrepid -- just trying to get some feedback. 

Thanks.

---

### Post by Jamie Jackson on 2008-11-15
> **kevdog said:**
> Jamie

Haven't heard from you in a while --- good to know your beans are not burnt!  Have you tried any of your instructions with Intrepid -- just trying to get some feedback. 

Thanks.

Hey kevdog,

Good to hear from you. Things seem to have settled down a bit, and I figure it's because native drivers are finally starting to work for people.

Since my Intrepid upgrade, I've switched to the restricted driver (STA version?) for my 14e4:4311 (rev 01). This ends up showing as the "wl" driver.

I haven't done any scientific comparisons between the two, but the wl signal seems stronger, and generally works less flakily than the ndiswrapper version.

I still plan to support this thread, but I'm happy to know that my device works out of the box in Intrepid now.

Cheers,
Jamie

---

### Post by kevdog on 2008-11-15
What chipsets does the wl driver specifically work with -- I've only read it works with one particular chipset ID.

I'll have to pull out my old Linksys wireless card and try it.  I found an old Atheros card last year and have never looked back after it worked out of the box with madwifi drivers that were included with the Ubuntu by default.

Whatever happened to the official ndiswrapper site -- the one with all of the instuctions?  It doesn't seem to work any logner.

---

### Post by Jamie Jackson on 2008-11-15
> **kevdog said:**
> What chipsets does the wl driver specifically work with -- I've only read it works with one particular chipset ID.


I'm not sure, I haven't done much research on the native drivers. However, I can vouch for it working with 14e4:4311 (rev 01).
> 

I'll have to pull out my old Linksys wireless card and try it.  I found an old Atheros card last year and have never looked back after it worked out of the box with madwifi drivers that were included with the Ubuntu by default.

Whatever happened to the official ndiswrapper site -- the one with all of the instuctions?  It doesn't seem to work any logner.

I haven't been able to find that site for a while. I don't have it bookmarked, and I couldn't even tell you where it used to be.

---

### Post by Ayuthia on 2008-11-15
> **kevdog said:**
> What chipsets does the wl driver specifically work with -- I've only read it works with one particular chipset ID.

I'll have to pull out my old Linksys wireless card and try it.  I found an old Atheros card last year and have never looked back after it worked out of the box with madwifi drivers that were included with the Ubuntu by default.

Whatever happened to the official ndiswrapper site -- the one with all of the instuctions?  It doesn't seem to work any logner.

From the wl.ko file, the alias info shows 432D, 432C, 432B, 432A, 4329, 4328, 4315, 4313, 4312, 4311.  It looks like Intrepid is having some problems with the 4311 rev 02 and some 4328 cards.  I have seen that some of the cards have problems with WEP/WPA, but I have not been able to confirm if it is an issue with network manager or the driver.

I am still looking to get an Atheros card.  It would be fun to play with a different card, but I would like one that does not work out of the box (where's the fun in one that "just works"?).  I bought a Linksys wireless pci card in hopes that it was the 4318 version, but it ended up being a ralink that worked out of the box.

As for ndiswrapper, the SVN section looks somewhat active (last entry looks like it was 2 weeks ago from pgiri), but the mailing list has been quiet and there is no mention of the website at all.  I know that ndiswrapper 1.53 does not compile with 2.6.27 without a patch, but other than that, there has not been too much info from them.

---

### Post by kevdog on 2008-11-15
Hmm, seem like the support for the ndiswrapper module is waning.  Where did you find the patch file?  

As far as the Atheros card -- if you want to do anything fancy like aircrack -- you need to compile with a patched version of madwifi --- so all the fun isn't completely eliminated.

Seems like some of my Broadcom knowledge is dated.  I don't really use Network Manager at all -- found it very buggy -- so I'm not good at passing off troubles people are having on the drive or NWM.  I used to use WICD, but I haven't seen the WICD author (name not mentioned for privacy reasons) respond in quite awhile.   Seems like that project may have ground to a halt also.  I'm not too sure.

---

### Post by Jamie Jackson on 2008-11-16
> **Ayuthia said:**
> As for ndiswrapper, the SVN section looks somewhat active (last entry looks like it was 2 weeks ago from pgiri), but the mailing list has been quiet and there is no mention of the website at all.  I know that ndiswrapper 1.53 does not compile with 2.6.27 without a patch, but other than that, there has not been too much info from them.

FWIW, best we've got is what's in the Internet Archive, as mentioned in this [forums post]("http://forums.opensuse.org/network-internet/wireless/399276-where-ndiswrapper-compatibility-list.html#post1893471").

However, since that post was made, a newer version (from Feb 2008) has appeared there (since there is a ~6 month lag between collection and post time on the Internet Archive). [Here's the index]("http://web.archive.org/web/*/http://ndiswrapper.sourceforge.net/joomla/index.php"), so we can easily find the most current version.

---

### Post by d2718 on 2009-01-16
Greetings. I just installed XUbuntu on my girlfriend's old Compaq Presario which seemed to have died from Windows XP. The last time I touched a UNIX implementation (not counting OS X which, well, doesn't count) was 10 years ago in college.

I found this guide extremely handy, except that editing /etc/modprobe.d/ndiswrapper doesn't seem to make this change permanent. Every time I reboot, it is necessary (and sufficient) that I

```

sudo rmmod b43
sudo rmmod b44

```
.

I would greatly appreciate if anyone could give me any further advice.

For the record, here is...

```

dhill@mr-Dan-gerous:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Fri Jan 16 00:26:30 EST 2009 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

```

and the rest of the requested information:

* Compaq Presario V2000 (EP442UA#ABA) w/ 1.8GHz Mobile AMD Sempron
* Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
* 05:02.0 0280: 14e4:4318 (rev 02)
* version 8.10 (Intrepid)
* kernel 2.6.27-9-generic i686 
* boot option noacpi
* I did not have to compile ndiswrapper
* I used driver option 2a
* and, like I said, I had to apply the Hardy workaround, but only those first two commands seem to be required to get my wireless card working

and here's lsmod:

```

dhill@mr-Dan-gerous:~$ lsmod
Module                  Size  Used by
ssb                    40580  0 
ndiswrapper           196380  0 
ipv6                  263972  8 
af_packet              25728  4 
rfkill_input           12672  0 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  0 
ecb                    10880  0 
crypto_blkcipher       25476  1 ecb
rfkill                 17176  1 rfkill_input
evdev                  17696  10 
psmouse                45200  0 
serio_raw              13444  0 
snd_atiixp             24204  2 
snd_seq_dummy          10884  0 
video                  25104  0 
output                 11008  1 video
snd_atiixp_modem       20360  0 
snd_seq_oss            38528  0 
snd_ac97_codec        111652  2 snd_atiixp,snd_atiixp_modem
snd_seq_midi           14336  0 
battery                18436  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_rawmidi            29824  1 snd_seq_midi
snd_pcm                83204  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
yenta_socket           31756  1 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ac                     12292  0 
rsrc_nonstatic         19072  1 yenta_socket
pcspkr                 10624  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29960  2 snd_pcm,snd_seq
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
wmi                    14504  0 
snd                    63268  15 snd_atiixp,snd_atiixp_modem,snd_seq_oss,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
button                 14224  0 
i2c_piix4              16144  0 
k8temp                 12416  0 
ati_agp                14988  0 
agpgart                42184  2 drm,ati_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_core               31892  1 i2c_piix4
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
8139too                31616  0 
pata_atiixp            12800  2 
libata                177312  3 ata_generic,pata_acpi,pata_atiixp
ohci_hcd               31888  0 
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
ehci_hcd               43276  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  4 ndiswrapper,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 

```

Thanks again.

---

### Post by Ayuthia on 2009-01-16
> **d2718 said:**
> Greetings. I just installed XUbuntu on my girlfriend's old Compaq Presario which seemed to have died from Windows XP. The last time I touched a UNIX implementation (not counting OS X which, well, doesn't count) was 10 years ago in college.

I found this guide extremely handy, except that editing /etc/modprobe.d/ndiswrapper doesn't seem to make this change permanent. Every time I reboot, it is necessary (and sufficient) that I

```

sudo rmmod b43
sudo rmmod b44

```
.

I would greatly appreciate if anyone could give me any further advice.

For the record, here is...

```

dhill@mr-Dan-gerous:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Fri Jan 16 00:26:30 EST 2009 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

```

and the rest of the requested information:

* Compaq Presario V2000 (EP442UA#ABA) w/ 1.8GHz Mobile AMD Sempron
* Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
* 05:02.0 0280: 14e4:4318 (rev 02)
* version 8.10 (Intrepid)
* kernel 2.6.27-9-generic i686 
* boot option noacpi
* I did not have to compile ndiswrapper
* I used driver option 2a
* and, like I said, I had to apply the Hardy workaround, but only those first two commands seem to be required to get my wireless card working

and here's lsmod:

```

dhill@mr-Dan-gerous:~$ lsmod
Module                  Size  Used by
ssb                    40580  0 
ndiswrapper           196380  0 
ipv6                  263972  8 
af_packet              25728  4 
rfkill_input           12672  0 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  0 
ecb                    10880  0 
crypto_blkcipher       25476  1 ecb
rfkill                 17176  1 rfkill_input
evdev                  17696  10 
psmouse                45200  0 
serio_raw              13444  0 
snd_atiixp             24204  2 
snd_seq_dummy          10884  0 
video                  25104  0 
output                 11008  1 video
snd_atiixp_modem       20360  0 
snd_seq_oss            38528  0 
snd_ac97_codec        111652  2 snd_atiixp,snd_atiixp_modem
snd_seq_midi           14336  0 
battery                18436  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_rawmidi            29824  1 snd_seq_midi
snd_pcm                83204  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
yenta_socket           31756  1 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ac                     12292  0 
rsrc_nonstatic         19072  1 yenta_socket
pcspkr                 10624  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29960  2 snd_pcm,snd_seq
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
wmi                    14504  0 
snd                    63268  15 snd_atiixp,snd_atiixp_modem,snd_seq_oss,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
button                 14224  0 
i2c_piix4              16144  0 
k8temp                 12416  0 
ati_agp                14988  0 
agpgart                42184  2 drm,ati_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_core               31892  1 i2c_piix4
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
8139too                31616  0 
pata_atiixp            12800  2 
libata                177312  3 ata_generic,pata_acpi,pata_atiixp
ohci_hcd               31888  0 
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
ehci_hcd               43276  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  4 ndiswrapper,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 

```

Thanks again.

I can't see anything wrong with the workaround script however I do see that the ssb module is still listed in your lsmod.  You might try to blacklist the b43 and b44 modules in /etc/modprobe.d/blacklist:
```
echo blacklist b43 |sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b44 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
```

If that does not work, you might try using the 0.1 or 0.2 versions from the no-fluff guide.  Normally, the workaround script should work, but there have been some rare cases where it does not but the 0.1/0.2 versions work.  The 0.3 version is the recommended version because it is a little cleaner in comparison to the other two options.

---

### Post by d2718 on 2009-01-17
Huh. Blacklisting the modules didn't work, but version 0.2 did. I have next to no clue what's going on, but it's almost as if the modules have to load and then get removed in order for the OS to interface with the wireless card properly.

Anyway, thank you so much!

---

### Post by Ayuthia on 2009-01-17
> **d2718 said:**
> Huh. Blacklisting the modules didn't work, but version 0.2 did. I have next to no clue what's going on, but it's almost as if the modules have to load and then get removed in order for the OS to interface with the wireless card properly.

Anyway, thank you so much!

I think the issue lies with the initramfs (what the kernel uses while the system is booting).  I think that update-initramfs -u would have fixed the problem, but I have not fully understood what the command is doing and I don't want to recommend it until I know that it will not remove any needed modules.  Glad to see that 0.2 worked for you.

---

### Post by d2718 on 2009-01-19
I, too. Thanks again.

---

### Post by dschach on 2009-01-21
Just reporting that the instructions worked for me.  Wireless works fine and at full speed now. Ubuntu 8.10 wireless drivers only ran only at 1mb/sec. Here are the details

1. Dell Inpsiron 5150 with internal Dell 1300 mini pci 
2. 02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
3. 02:02.0 0280: 14e4:4320 (rev 02)
4. Ubuntu 8.10
5. 2.6.27-9-generic i686
6. did not have to recompile NDISWrapper
7. downloaded and extracted Dell driver on a windows machine then copied to ubuntu machine
8. Used [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003) to fix boot so ndis loaded in right order

---

### Post by Grets Sirob on 2009-01-23
Hey, I don't know if this question has been answered before or not, but there's an awful lot of pages to dig through, so here's my problem.
Wireless isn't working (I pretty much expected that). However, for some reason or another, my ethernet died as I was attempting to retrieve updates (I hadn't gotten to the part where I could install them yet). Now, neither Windows XP or Xubuntu can get anything through the ethernet, so I'm thinking something finally broke in my poor old Compaq Presario R4000.
Basically, no internet in Xubuntu at all.
So, I decided to try and get the wireless working and found this ndiswrapper how-to. The non-compiled version didn't seem to work (unless I missed something, I followed the direction to the letter). I'm attempting to try to compile it, but I'm stuck on trying to get the build-essential packages. I downloaded all (I think) the necessary packages in Windows and transfered them into Xubuntu, but there's two packages that are giving me a ton of trouble, as they're dependent on each other.
Any suggestions? Or should I try something entirely different?

(By the way, on step 2, I used 2g, if that matters.)

Help? Anyone?

---

### Post by Ayuthia on 2009-01-24
> **Grets Sirob said:**
> Hey, I don't know if this question has been answered before or not, but there's an awful lot of pages to dig through, so here's my problem.
Wireless isn't working (I pretty much expected that). However, for some reason or another, my ethernet died as I was attempting to retrieve updates (I hadn't gotten to the part where I could install them yet). Now, neither Windows XP or Xubuntu can get anything through the ethernet, so I'm thinking something finally broke in my poor old Compaq Presario R4000.
Basically, no internet in Xubuntu at all.
So, I decided to try and get the wireless working and found this ndiswrapper how-to. The non-compiled version didn't seem to work (unless I missed something, I followed the direction to the letter). I'm attempting to try to compile it, but I'm stuck on trying to get the build-essential packages. I downloaded all (I think) the necessary packages in Windows and transfered them into Xubuntu, but there's two packages that are giving me a ton of trouble, as they're dependent on each other.
Any suggestions? Or should I try something entirely different?

(By the way, on step 2, I used 2g, if that matters.)

Help? Anyone?

Can you let us know which version of Ubuntu you are using, if you were able to get the file in 2g, and let us know what two packages that are giving you trouble?

The non-compiled version (ndiswrapper 1.53) does not compile on kernels 2.6.27 or higher without a patch applied to it.  That might be where you are running into problems.  But if you don't have build-essential installed, then that will prevent it from compiling also.

---

### Post by Grets Sirob on 2009-01-24
Haha! Silly me... I tried the Hardy Heron bug fix, and managed to get it working, and from there was able to update and install the proprietary drivers... Seems to be working just fine now. Just chalk it up to the n00b who didn't follow all the instructions... *walks off whistling...*

Thanks for writing this up!

---

### Post by T-RoR on 2009-01-25
Thank you. Wireless works perfect now. Restricted drivers changed connection speed randomly.

1- Dell Inspiron 1300 (M130)
2- Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
3- 02:03.0 0280: 14e4:4318 (rev 02)
4- Ubuntu 8.10
5- 2.6.27-9-generic i686
6- I haven't had to recompile ndiswrapper
7- I have extracted Dell driver to desktop and configured ndiswrapper with it.
8- I have also used [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003) to fix boot so nidiswrapper loads properly.

---

### Post by ntense on 2009-01-27
i cant seem to get this to work for me. i did all the steps in order and even tried the hardy bug fix. the bug fix made ndiswrapper show up when i run "lshw -C network" command. but when i go up to the network manager i still cannot select "wireless networks" after i did the "hardy bug fix" and made it permanent and rebooted the machine in hopes that something may start working. no luck. there is a physical wireless switch on this computer. but its a button.and when i press it, nothing happens. so i dont know if that might be part of the problem. the machine im trying to install this on is a compaq presario m2000 and the version of ubuntu is 8.10 its a fresh install. below is all the output that was in the terminal before reboot.

```
brian@nutslap:~$ echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for brian: 
blacklist bcm43xx
blacklist wl
brian@nutslap:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.4kB of archives.
After this operation, 225kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Get:2 http://us.archive.ubuntu.com intrepid/main ndiswrapper-utils-1.9 1.52-1ubuntu1 [35.1kB]
Fetched 55.4kB in 1s (43.7kB/s)             
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 115620 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.52-1ubuntu1) ...
brian@nutslap:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
brian@nutslap:~/bcm43xx$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
brian@nutslap:~/bcm43xx$ wget http://myspamb8.googlepages.com/Driver_3607.zip
--2009-01-27 12:58:28--  http://myspamb8.googlepages.com/Driver_3607.zip
Resolving myspamb8.googlepages.com... 74.125.47.118
Connecting to myspamb8.googlepages.com|74.125.47.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 308432 (301K) [application/octet-stream]
Saving to: `Driver_3607.zip'

100%[======================================>] 308,432      247K/s   in 1.2s    

2009-01-27 12:58:29 (247 KB/s) - `Driver_3607.zip' saved [308432/308432]

brian@nutslap:~/bcm43xx$ unzip Driver_3607.zip
Archive:  Driver_3607.zip
  inflating: bcmwl5.sys              
  inflating: bcmwl5.inf              
  inflating: bcm43xx.cat             
brian@nutslap:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
brian@nutslap:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
brian@nutslap:~/bcm43xx$ sudo depmod -a
brian@nutslap:~/bcm43xx$ sudo modprobe ndiswrapper
brian@nutslap:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
brian@nutslap:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

brian@nutslap:~/bcm43xx$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

brian@nutslap:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
brian@nutslap:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
brian@nutslap:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:b5:41:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.100 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:f3:a7:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:5f:3b:2f:d1:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
brian@nutslap:~/bcm43xx$ sudo rmmod b43
brian@nutslap:~/bcm43xx$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
brian@nutslap:~/bcm43xx$ sudo rmmod b43legacy #this step added Apr 27 2008
ERROR: Module b43legacy does not exist in /proc/modules
brian@nutslap:~/bcm43xx$ sudo rmmod wl #this step added Sep 20 2008
ERROR: Module wl does not exist in /proc/modules
brian@nutslap:~/bcm43xx$ sudo rmmod ssb
brian@nutslap:~/bcm43xx$ sudo rmmod ndiswrapper
brian@nutslap:~/bcm43xx$ sudo modprobe ndiswrapper
brian@nutslap:~/bcm43xx$ sudo modprobe ssb
brian@nutslap:~/bcm43xx$ sudo modprobe b44 #this step added May 1 2008
brian@nutslap:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:b5:41:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.100 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:f3:a7:90
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+ASUS,03/22/2004, 3.60.7.0 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:5f:3b:2f:d1:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
brian@nutslap:~/bcm43xx$ echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Tue Jan 27 13:16:11 PST 2009 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
brian@nutslap:~/bcm43xx$ 

```

im proabably just a retard (actually i know i am:p) and its something simple that im not doing. so any help would be greatly appreciated. thanks in advance.

---

### Post by Ayuthia on 2009-01-27
> **ntense said:**
> 
im proabably just a retard (actually i know i am:p) and its something simple that im not doing. so any help would be greatly appreciated. thanks in advance.

Can you post the results of:
```
dmesg|grep ndis
```
Everything that you did looks like it should.  Hopefully dmesg will tell us something.

---

### Post by kevdog on 2009-01-27
Where is the ndiswrapper patch for the new Linux kernels?

---

### Post by Ayuthia on 2009-01-27
> **kevdog said:**
> Where is the ndiswrapper patch for the new Linux kernels?

It does not look like 1.54 (Released on 1/22/2009) needs a patch. :p  I just compiled it under 2.6.28.1 and it compiled clean.

If you are looking for the patch for 1.53 and kernels 2.6.27 and higher:
[http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch](http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch)

Here is a simple set of instructions on how to patch it:
[http://gnuwave.org/drupal/node/36](http://gnuwave.org/drupal/node/36)

---

### Post by ntense on 2009-01-27
> **Ayuthia said:**
> Can you post the results of:
```
dmesg|grep ndis
```
Everything that you did looks like it should.  Hopefully dmesg will tell us something.

that command returns ```
brian@nutslap:~$ dmesg|grep ndis
[   21.962357] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   22.069341] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[   22.069655] ndiswrapper 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   22.075268] ndiswrapper: using IRQ 20
[   22.276524] usbcore: registered new interface driver ndiswrapper

```

---

### Post by Ayuthia on 2009-01-27
> **ntense said:**
> that command returns ```
brian@nutslap:~$ dmesg|grep ndis
[   21.962357] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   22.069341] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[   22.069655] ndiswrapper 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   22.075268] ndiswrapper: using IRQ 20
[   22.276524] usbcore: registered new interface driver ndiswrapper

```

Are you able to scan for wireless sites:
```
sudo iwlist scan
```
Also, are you using any encryption (WEP/WPA)?

---

### Post by kevdog on 2009-01-27
Cool -- 1.54 -- I thought the project was dead!!! Good to see this!!! I rarely use ndiswrapper these  days but try to keep current on the implementations for historical reasons.

---

### Post by ntense on 2009-01-28
> **Ayuthia said:**
> Are you able to scan for wireless sites:
```
sudo iwlist scan
```
Also, are you using any encryption (WEP/WPA)?




command returns: ```
[sudo] password for brian: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```


the home network is running WEP. but shouldnt the network still show up in networkmanager even if its encrypted?

---

### Post by Ayuthia on 2009-01-28
> **ntense said:**
> command returns: ```
[sudo] password for brian: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```


the home network is running WEP. but shouldnt the network still show up in networkmanager even if its encrypted?

You might try a different driver (From step 2a):
[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)

As for the WEP/WPA question, you are correct that it would still show up.  The reason for the question was that WPA2 does not work with the driver that you are using.

---

### Post by Dragonbite on 2009-01-30
Hi. I'm a Hardy (8.04) user and tried following the wiki. It didn't work for me. Below I've included the answers to the requested list in the beginning of this thread.

Additional information can be found in [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=935313") where I was being helped.[LIST=1]
[*]The results from lsmod ```
Module                  Size  Used by
ipv6                  267908  8 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
rfkill_input            5760  0 
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144548  0 
irda                  203068  0 
rfkill                  8596  3 rfkill_input,b43
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
dcdbas                  9504  0 
crc_ccitt               3072  1 irda
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
evdev                  13056  8 
input_polldev           5896  1 b43
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
serio_raw               7940  0 
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            35584  0 
psmouse                40336  0 
button                  9232  0 
battery                14212  0 
snd_seq_midi            9376  0 
ac                      6916  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 32128  0 
hid                    38784  1 usbhid
sg                     36880  0 
sd_mod                 30720  5 
ata_generic             8324  0 
ata_piix               19588  4 
ohci1394               33584  0 
pata_acpi               8320  0 
ssb                    34308  1 b43
ieee1394               93752  2 sbp2,ohci1394
tg3                   116228  0 
libata                159600  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  4 sbp2,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
drew@Dragon:~$ clear

drew@Dragon:~$ lsmod
Module                  Size  Used by
ipv6                  267908  8 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
rfkill_input            5760  0 
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144548  0 
irda                  203068  0 
rfkill                  8596  3 rfkill_input,b43
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
dcdbas                  9504  0 
crc_ccitt               3072  1 irda
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
evdev                  13056  8 
input_polldev           5896  1 b43
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
serio_raw               7940  0 
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            35584  0 
psmouse                40336  0 
button                  9232  0 
battery                14212  0 
snd_seq_midi            9376  0 
ac                      6916  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 32128  0 
hid                    38784  1 usbhid
sg                     36880  0 
sd_mod                 30720  5 
ata_generic             8324  0 
ata_piix               19588  4 
ohci1394               33584  0 
pata_acpi               8320  0 
ssb                    34308  1 b43
ieee1394               93752  2 sbp2,ohci1394
tg3                   116228  0 
libata                159600  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  4 sbp2,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```
[*]Machine Brand and Model: _Dell Latitude D400_
[*]Wireless Brand and Model from **lspci | grep Broadcom **: _01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)_
[*]Wireless Chipset from ** lspci -n | grep '14e4:43'**: _01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)_
[*]Ubuntu Version from **lsb_release -d** : _Description:	Ubuntu 8.04.2_
[*]Kernel / Architecture from **uname -mr**: _2.6.24-23-generic i686_
[*]Extra boot options might be using: _none to my knowledge_.
[*]Had to compile NDISWrapper: _ No _
[*]Which version of Step 2 did I use? _2g the first time around (thought it was 4306, not 4309), then ran through 2b the second time after seeing brettpim's entry listing success with the 4309 (25 Jan 2008 )._
[*]Did I apply the "Hardy Bug Fix"? _Yes, and it didn't work._, from **lshw -C network**```
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:11:f5:0a:0e:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
[/LIST]

---

### Post by Ayuthia on 2009-01-30
> **Dragonbite said:**
> Hi. I'm a Hardy (8.04) user and tried following the wiki. It didn't work for me. Below I've included the answers to the requested list in the beginning of this thread.

Additional information can be found in [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=935313") where I was being helped.[LIST=1]
[*]The results from lsmod ```
Module                  Size  Used by
ipv6                  267908  8 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
rfkill_input            5760  0 
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144548  0 
irda                  203068  0 
rfkill                  8596  3 rfkill_input,b43
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
dcdbas                  9504  0 
crc_ccitt               3072  1 irda
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
evdev                  13056  8 
input_polldev           5896  1 b43
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
serio_raw               7940  0 
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            35584  0 
psmouse                40336  0 
button                  9232  0 
battery                14212  0 
snd_seq_midi            9376  0 
ac                      6916  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 32128  0 
hid                    38784  1 usbhid
sg                     36880  0 
sd_mod                 30720  5 
ata_generic             8324  0 
ata_piix               19588  4 
ohci1394               33584  0 
pata_acpi               8320  0 
ssb                    34308  1 b43
ieee1394               93752  2 sbp2,ohci1394
tg3                   116228  0 
libata                159600  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  4 sbp2,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
drew@Dragon:~$ clear

drew@Dragon:~$ lsmod
Module                  Size  Used by
ipv6                  267908  8 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
rfkill_input            5760  0 
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144548  0 
irda                  203068  0 
rfkill                  8596  3 rfkill_input,b43
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
dcdbas                  9504  0 
crc_ccitt               3072  1 irda
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
evdev                  13056  8 
input_polldev           5896  1 b43
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
serio_raw               7940  0 
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            35584  0 
psmouse                40336  0 
button                  9232  0 
battery                14212  0 
snd_seq_midi            9376  0 
ac                      6916  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 32128  0 
hid                    38784  1 usbhid
sg                     36880  0 
sd_mod                 30720  5 
ata_generic             8324  0 
ata_piix               19588  4 
ohci1394               33584  0 
pata_acpi               8320  0 
ssb                    34308  1 b43
ieee1394               93752  2 sbp2,ohci1394
tg3                   116228  0 
libata                159600  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  4 sbp2,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```
[*]Machine Brand and Model: _Dell Latitude D400_
[*]Wireless Brand and Model from **lspci | grep Broadcom **: _01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)_
[*]Wireless Chipset from ** lspci -n | grep '14e4:43'**: _01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)_
[*]Ubuntu Version from **lsb_release -d** : _Description:	Ubuntu 8.04.2_
[*]Kernel / Architecture from **uname -mr**: _2.6.24-23-generic i686_
[*]Extra boot options might be using: _none to my knowledge_.
[*]Had to compile NDISWrapper: _ No _
[*]Which version of Step 2 did I use? _2g the first time around (thought it was 4306, not 4309), then ran through 2b the second time after seeing brettpim's entry listing success with the 4309 (25 Jan 2008 )._
[*]Did I apply the "Hardy Bug Fix"? _Yes, and it didn't work._, from **lshw -C network**```
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:11:f5:0a:0e:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
[/LIST]

Your lsmod info is showing that b43 and ndiswrapper are both running.  According to your lshw -C network info, b43 won out.  You will need to unload b43 and reload ndiswrapper:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
```

---

### Post by Dragonbite on 2009-01-31
> **Ayuthia said:**
> Your lsmod info is showing that b43 and ndiswrapper are both running.  According to your lshw -C network info, b43 won out.  You will need to unload b43 and reload ndiswrapper:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
```

I tried that, and now I don't even see the wireless in ifconfig and can't put it up. Network Manager also doesn't show the option of having wireless up.

When I add ssb back in I see the wireless but then it is running b43 as well and it uses ssb.

This is what I get if I load ndiswrapper and not ssb, b43 or b44:```
 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6e:e3:23
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.11 ip=192.168.1.103 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=32

```

Thank you for your response and patience.

---

### Post by Ayuthia on 2009-01-31
If you try that again and check:
```
lsmod|grep ndiswrapper
```Is ndiswrapper listed?  Also can you check:
```
dmesg|grep ndiswrapper
```It might provide some info about why ndiswrapper did not come up.

---

### Post by Dragonbite on 2009-01-31
> **Ayuthia said:**
> If you try that again and check:
```
lsmod|grep ndiswrapper
```Is ndiswrapper listed?  Also can you check:
```
dmesg|grep ndiswrapper
```It might provide some info about why ndiswrapper did not come up.

I looks loaded
```
lsmod|grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146412  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

```

Just to look, I got this listed when I looked for all modules containing b4```
lsmod|grep b4
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43

```

As for the dmesg I got ```
dmesg|grep ndiswrapper
[   30.075748] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   30.140394] usbcore: registered new interface driver ndiswrapper

```

Just to try it, I tried booting to 7.10. I did the recommendation for Restricted Drivers and it brought me to this same place; shows up in Network Manager but no access points are seen.  OpenSUSE 11.1 didn't do anything different either.

I also just used my work laptop to verify there are networks visible. It has found 3 and one of which is open.

I am beginning to think its hardware, but short of switching wifi cards between my work laptop and my desktop I'm not sure how to verify it or isolate it.

---

### Post by Dragonbite on 2009-02-02
Alright, alright. I admit it!  I'm DUMB! 

The person who gave me the card was surprised to find I was having a problem and asked a simple question... is it turned on?  

Sure enough, it was disabled in the BIOS and once I turned it on in there it immediately picked up the access point when I rebooted!

Thank you, thank you for your patience and help.  It is not wasted because I am using some of the tool we tried with people in my SIG with wireless issues!

Thank you again!

---

### Post by dougalf on 2009-03-08
Many thanks for the HOWTO it has helped me a couple of times now.

I now have working Wi-fi on Jaunty Alpha 5 :-)

Dell Inspiron 1501
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
05:00.0 0280: 14e4:4312 (rev 01)
Description:	Ubuntu jaunty (development branch)
2.6.28-8-generic i686
No extra boot options
Didn't rebuild ndiswrapper
Step 2b
Had to apply the Hardy Bug Fix workaround, ignored the following errors:
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module wl does not exist in /proc/modules
and then made it permanent.

Smashing.

---

### Post by Deathray on 2009-03-15
HP DV6449US = Broadcom 4321 ag or 4328 ag. Not sure.
Step 2d worked like a charm! Someone update the wiki for me please! :)

---

### Post by mathwizard44 on 2009-03-16
Hey, thanks for this guide. I was able to post this reply on my 10-year-old machine. ^_^

Machine Brand/Model: Gateway 450 Desktop (Pentium 3 450 MHz)
Wireless: 00:10.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Chipset: 00:10.0 0280: 14e4:4318 (rev 02)
Version: Xubuntu 8.10
Linux Kernel 2.6.27-7-generic i686
No extra boot options
Did not compile ndiswrapper (installed from CD)
Used Step 2a (and additionally, I tried the drivers that came in the adapter CD; these also worked well)
I also had to do the "Hardy Bug Fix" even here at Interpid (8.10), but I guess that's because they're both Version 8?

Also, when I bought the card it said it was a Linksys WMP54GS.

Thanks again for the helpful guide.

---

### Post by DavidMP on 2009-03-17
Hello,

Thanks for the guide. I have recently reinstalled 8.10 and my BCM4306 card does not detect the networks around me, even with the restricted drivers enabled. If I right click on the network icon it tells me it is enabled and I can find the networks without problem under WinXP (I have double boot) so it is not the card.

I then decided to un-install the restricted driver from the repository and install using ndiswrapper using this guide... Well, I get "module=ssb" even after the fix and I don't have any idea of what else to try. Here is the output of "lshw -C network" in the hopes that someone here knows how to fix this.

```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:6e:bf:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.15.100 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:bc:7f:83
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

For the record;it worked fine under 8.04. any help is greatly appreciated.

---

### Post by jkb_ on 2009-03-17
hi there.

i hope somebody can help me.  i just got my dell mini 9 with ubuntu on it and noticed that ssh didnt work.  so i followed [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6") and got ssh to work.  but after i rebooted the system, my mouse stopped working and i cant get it to work.  i can see the cursor, but i can't move it.

i went into single user mode and chmod'ed 000 /etc/modprobe.d/ndiswrapper and /etc/ndiswrapper but that didnt help me get my mouse workign again.

any tips or pointers?

---

### Post by Ayuthia on 2009-03-18
> **jkb_ said:**
> hi there.

i hope somebody can help me.  i just got my dell mini 9 with ubuntu on it and noticed that ssh didnt work.  so i followed [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6") and got ssh to work.  but after i rebooted the system, my mouse stopped working and i cant get it to work.  i can see the cursor, but i can't move it.

i went into single user mode and chmod'ed 000 /etc/modprobe.d/ndiswrapper and /etc/ndiswrapper but that didnt help me get my mouse workign again.

any tips or pointers?

It sounds like ndiswrapper is conflicting with the driver for your mouse.  If you blacklist ndiswrapper and restart, does your mouse work again?
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by jkb_ on 2009-03-18
> **Ayuthia said:**
> It sounds like ndiswrapper is conflicting with the driver for your mouse.  If you blacklist ndiswrapper and restart, does your mouse work again?
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

nope, didnt help.  i actually tried to undo the steps i took in the instructions and that didnt help either.

---

### Post by Hoya NVA on 2009-03-22
> **jkb_ said:**
> nope, didnt help.  i actually tried to undo the steps i took in the instructions and that didnt help either.

Any luck getting the mouse working?  Got a new Dell Mini 9 two days a, trying to connect to any WPA2 network causes a system crash 100% of the time (verified 15+ times on 3 different WPA2 networks), was going to try the Feisty_nofluff workaround, but since I'm a LINUX novice, I hesitate to start going down paths where other conflicts are going to get generated.

Why Dell would bundle an OS on a netbook where there are wireless card/OS driver issues I have no idea.

Thanks for any help/ideas.

---

### Post by scearley on 2009-03-24
This did not work for me.
I went through ALL required steps, eventually building ndiswrapper, and still there is ZERO response to wireless networks.

I've been wading through tons of entries on getting wireless to work in Ubuntu, and I'm done.  I'm done with ubuntu after 8 hours non-responsive wireless that was promised to work with a simple b43xx update.

You anted feedback, here's my setup:
HP Pavilion zv6000
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:02.0 0280: 14e4:4320 (rev 03)
Ubuntu 8.10 (64 bit)
AMD 3500+ 64 bit chip
I was forced to compile, and I used step 2g (as it's rev 03)
I tried using the Hardy Bug Fix, but that didn't work, so i compiled, as I mentioned.  I used the temporary fix, but since it still showed "=ssb" after the temporary fix, the instructions say not to make a permanent fix, so I went on to compile.

Further details listed in the thread I started desperate for help [here]("http://ubuntuforums.org/showthread.php?t=1104825").

---

### Post by Dragonbite on 2009-03-25
> **scearley said:**
> This did not work for me.
I went through ALL required steps, eventually building ndiswrapper, and still there is ZERO response to wireless networks.

I know it's stupid BUT, when I was having problems and everything said it should be working I found out the wireless was turned off in the BIOS.

Before writing it off, look for any "on/off" switch on the system; BIOS, Function Keys *(which is how I suspect it got turned off in the first place)*, whatever.

---

### Post by scearley on 2009-03-25
> **Dragonbite said:**
> I know it's stupid BUT, when I was having problems and everything said it should be working I found out the wireless was turned off in the BIOS.

Before writing it off, look for any "on/off" switch on the system; BIOS, Function Keys *(which is how I suspect it got turned off in the first place)*, whatever.

I did check BIOS and other hardware switches, they are on.  Installing the b43 driver turned the wifi on, or at least the LED showing that it's on is on.  Removing the b43 driver keeps the light off.

---

### Post by epha on 2009-04-09
hi,
I followed the the no-fluff tutorial and my bcm4306 rev2 card is connecting to the internet ! so, thanks!

but...wpa2 is not working,(I can see my network and I get one green light in the nm-applet and a spinning thing, and ....nothing) can someone help me get it working if it's possible.

thanks

epha

---

### Post by riberet on 2009-04-09
I'm having a similar problem.

Can any one provide me a quick solution in getting connected to my university wireless network which is a WPA2 enterprise encripted network. 
I have  a Dell inspiron 1720 system which comes with the dreaded Broadcom wireless hardware and uses the 'bcm 4315 driver'. Initially I used to get kernel freezes each time I used to connect to the university network. It used to work on other networks though. I am using the Windows Wireless driver application to use the 'bcmwl5' driver. It does not freeze with this driver but I can't connect to the university network. I can see all the networks in the wireless manager.

Any help would be highly appreciated .

Thanks,
Riberet

---

### Post by epha on 2009-04-10
@riberet

hi.  I have my wireless card working with wpa1. The driver doesn't support wpa2 I think. I followed this tutorial to get wpa1 working:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

good luck.

epha.

---

### Post by bruce m beach on 2009-05-06
After weeks of trying to get my wireless chip working I happened on the &quot;WifiDocDriverbcm43xxFeisty_No-Fluff&quot; page and finally got it working 100%.(and easily too) To start up I just:     /sbin/ifconfig wlan0 up           #iwconfig lists wlan0   iwconfig wlan0 essid &quot;WHAT_IM_TRYING_TO_CONNECT_TO&quot;           #associates immediately   /usr/local/sbin/dhcpcd -d wlan0           #no problems at all with dhcpcd In fact works like a dream. Below is the requested information.  Machine Brand and Model:     emachines D620 (super deluxe ultra-cheap)  Wireless Brand and Model: lspci | grep Broadcom:      Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  Wireless Chipset: lspci -n | grep '14e4:43'      05:00.0 0280: 14e4:4315 (rev 01)  Ubuntu Version: lsb_release -d      Don't use any distribution. Roll my own.  Kernel/architecture (including 32 vs. 64 bit) : uname -mr      2.6.29.2 i686 32bit AMD Processor  Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)     Nothing except root=/dev/sda1  Whether or not you had to compile NDISWrapper      Yes I compiled it. No problems. Which version of Step 2 you used      Step 2e: R174291 Driver Download/Extraction  Well I don't know why thing (editpost.php?) totally mangles the text that I enter. I tried. Any way thanks a lot for the site. Bruce

---

### Post by dsiddens on 2009-05-08
Failed.
HP dv8000 laptop
lspci | grep Broadcom 06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
lspci -n | grep '14e4:43'
06:02.0 0280: 14e4:4319 (rev 02)
lsb_release -d Description:	Ubuntu 8.10
uname -mr 2.6.27-11-generic x86_64
Did not try (knowledge/confidence) to compile.
Step 2b tried.
Hardy fix tried.

---

### Post by ktat on 2009-05-27
Hi,

I've just bought an Asus wl-138g v2 and am trying to get it installed - I've seen documentation on the web stating it should work "out of the box" but so far no luck.

I am running Jaunty and initially used system>administration>hardwaredrivers which gave me the option to install b43.  Before completing, this error came up.  **"Sorry, the Jockey backend crashed"**

Since then I've tried working through a number of different how to's.  The last one being [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions")

It wasn't working after going through the main steps so I tried the "Hardy Bug Fix", here is output

[IMG]http://i663.photobucket.com/albums/uu356/ktat_2009/Screenshot-3.png[/IMG]

then I tried lshw -C network...

[IMG]http://i663.photobucket.com/albums/uu356/ktat_2009/Screenshot-4.png[/IMG]

I'm guessing that module=ssb should be reading module=ndiswrapper.  I would really appreciate some help with this :(

---

### Post by aptdude on 2009-06-16
Howdy,
Upon cleaning up after the celebration of getting wlan0 working with the Linksys WMP11, the fates decided to freeze the system.  After the subsequent cold boot, wlan0 doesn't show up.  lshw -C network is showing ssb as the module.  I guess I'm just trying to shoot for a results approach with ndiswrapper.  Right now, on bootup, b44 picks up the card and that fails with a -22 error, according to syslog.  So, I've removed both b44 and ssb and now lshw -C network shows that interface as "UNCLAIMED".  What command binds a driver (like ndiswrapper) to this hardware?  I'd even go for a Fred Flintstone direct approach rather than pci discovery methods.
Any help would be greatly appreciated!

---

### Post by Ayuthia on 2009-06-16
> **aptdude said:**
> Howdy,
Upon cleaning up after the celebration of getting wlan0 working with the Linksys WMP11, the fates decided to freeze the system.  After the subsequent cold boot, wlan0 doesn't show up.  lshw -C network is showing ssb as the module.  I guess I'm just trying to shoot for a results approach with ndiswrapper.  Right now, on bootup, b44 picks up the card and that fails with a -22 error, according to syslog.  So, I've removed both b44 and ssb and now lshw -C network shows that interface as "UNCLAIMED".  What command binds a driver (like ndiswrapper) to this hardware?  I'd even go for a Fred Flintstone direct approach rather than pci discovery methods.
Any help would be greatly appreciated!

Can you let us know which version of Ubuntu you are using (Jaunty, Intrepid, Hardy, etc.) along with posting the results of:
```
lshw -C network
```

What happens when you do the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by aptdude on 2009-06-17
[LEFT]Thank you very much for your interest and help!


Here's the details that you requested. I don't have many options for output, other than transcription (maybe pictures) without the wireless.  


Info brought forward:
Dell Dimension XPS_R (bought in 1996)
[Linksys WMP11] 00:0f.0 Network Controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
14e4:4301 (rev 02) 
Ubuntu 8.04.2; 2.6.24-23-server i686
boot option acpi=off
No compile of ndiswrapper required
Used step 2a
Used Hardy bug fix – permanent by version 0.3
additional – used drivers from [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php) burned onto cd, installed driver to ndiswrapper using package ndisgtk.


On boot after a cold halt:
ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128
UP LOOKBACK RUNNING MTU:16436 Metric: 1
RX packets:76 errors:0 dropped:0 overruns:0 frame:0
TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3800 (3.7 KB) TX bytes:3800 (3.7 KB)


iwconfig
lo no wireless extensions


eth0 no wireless extensions


lshw -C network
*-network:0 DISABLED
description: Ethernet Interface
product: 82559 InBusiness 10/100
vendor: Intel Corporation
physical id: e
bus info: pci@0000:00:0e.0
logical name: eth0
version: 08
serial: 00:d0:b7:5d:57:23
width: 32 bits
clock: 33 Mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
*-network:1
description: Network controller
product: BCM4303 802.11b Wireless LAN Controller
vendor: Broadcom Corporation
physical id: f
bus info: pci@0000:00:0f.0
version: 02
width: 32 bits
clock: 33Mhz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=64 module=ssb


sudo modprobe -r b43 b44 ssb ndiswrapper wl
FATAL: Module wl not found
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
sudo iwlist scan
lo Interface doesn't support scanning.


eth0 Interface doesn't support scanning.


lshw -C network
*-network:0 DISABLED
description: Ethernet Interface
product: 82559 InBusiness 10/100
vendor: Intel Corporation
physical id: e
bus info: pci@0000:00:0e.0
logical name: eth0
version: 08
serial: 00:d0:b7:5d:57:23
width: 32 bits
clock: 33 Mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
*-network:1 UNCLAIMED
description: Network controller
product: BCM4303 802.11b Wireless LAN Controller
vendor: Broadcom Corporation
physical id: f
bus info: pci@0000:00:0f.0
version: 02
width: 32 bits
clock: 33Mhz
capabilities: bus_master cap_list
configuration: latency=64


Thanks in advance! Please note that I performed the changes from the website, which includes blacklisting b43 and b43legacy.  [/LEFT]

---

### Post by Ayuthia on 2009-06-17
> **aptdude said:**
> [LEFT]Thank you very much for your interest and help!


Here's the details that you requested. I don't have many options for output, other than transcription (maybe pictures) without the wireless.  


Info brought forward:
Dell Dimension XPS_R (bought in 1996)
[Linksys WMP11] 00:0f.0 Network Controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
14e4:4301 (rev 02) 
Ubuntu 8.04.2; 2.6.24-23-server i686
boot option acpi=off
No compile of ndiswrapper required
Used step 2a
Used Hardy bug fix – permanent by version 0.3
additional – used drivers from [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php) burned onto cd, installed driver to ndiswrapper using package ndisgtk.


On boot after a cold halt:
ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128
UP LOOKBACK RUNNING MTU:16436 Metric: 1
RX packets:76 errors:0 dropped:0 overruns:0 frame:0
TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3800 (3.7 KB) TX bytes:3800 (3.7 KB)


iwconfig
lo no wireless extensions


eth0 no wireless extensions


lshw -C network
*-network:0 DISABLED
description: Ethernet Interface
product: 82559 InBusiness 10/100
vendor: Intel Corporation
physical id: e
bus info: pci@0000:00:0e.0
logical name: eth0
version: 08
serial: 00:d0:b7:5d:57:23
width: 32 bits
clock: 33 Mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
*-network:1
description: Network controller
product: BCM4303 802.11b Wireless LAN Controller
vendor: Broadcom Corporation
physical id: f
bus info: pci@0000:00:0f.0
version: 02
width: 32 bits
clock: 33Mhz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=64 module=ssb


sudo modprobe -r b43 b44 ssb ndiswrapper wl
FATAL: Module wl not found
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
sudo iwlist scan
lo Interface doesn't support scanning.


eth0 Interface doesn't support scanning.


lshw -C network
*-network:0 DISABLED
description: Ethernet Interface
product: 82559 InBusiness 10/100
vendor: Intel Corporation
physical id: e
bus info: pci@0000:00:0e.0
logical name: eth0
version: 08
serial: 00:d0:b7:5d:57:23
width: 32 bits
clock: 33 Mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
*-network:1 UNCLAIMED
description: Network controller
product: BCM4303 802.11b Wireless LAN Controller
vendor: Broadcom Corporation
physical id: f
bus info: pci@0000:00:0f.0
version: 02
width: 32 bits
clock: 33Mhz
capabilities: bus_master cap_list
configuration: latency=64


Thanks in advance! Please note that I performed the changes from the website, which includes blacklisting b43 and b43legacy.  [/LEFT]

I am getting too old.  I forgot to add the b43legacy module.  Can you try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan

```
If it does not provide any scan results, can you post the results of:
```
dmesg|grep ndis
ndiswrapper -l
```
It will hopefully provide some information about what is happening with ndiswrapper.

---

### Post by aptdude on 2009-06-17
> **Ayuthia said:**
> I am getting too old. I forgot to add the b43legacy module. Can you try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan

```
If it does not provide any scan results, can you post the results of:
```
dmesg|grep ndis
ndiswrapper -l
```
It will hopefully provide some information about what is happening with ndiswrapper.
 
Okay,
Here's those results (I included b44 in the module remove, since it is assigned to the wireless):
```

 
[LEFT]sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
sudo iwlist scan
lo Interface doesn't support scanning.


eth0 Interface doesn't support scanning.

[/LEFT]
 
 
[LEFT]lshw -C network
*-network:0 DISABLED
description: Ethernet Interface
product: 82559 InBusiness 10/100
vendor: Intel Corporation
physical id: e
bus info: pci@0000:00:0e.0
logical name: eth0
version: 08
serial: 00:d0:b7:5d:57:23
width: 32 bits
clock: 33 Mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
*-network:1 UNCLAIMED
description: Network controller
product: BCM4303 802.11b Wireless LAN Controller
vendor: Broadcom Corporation
physical id: f
bus info: pci@0000:00:0f.0
version: 02
width: 32 bits
clock: 33Mhz
capabilities: cap_list
configuration: latency=64[/LEFT]
 
 
[LEFT]dmesg | grep ndis
[ 73.112730] ndiswrapper version 1.52 loaded (smp=yes, preempt =no)
[ 74.282845] usbcore: registered new interface driver ndiswrapper
[ 265.799907] usbcore: deregistering interface driver ndiswrapper
[ 265.894256] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 265.934596] usbcore: registered new interface driver ndiswrapper[/LEFT]
 
 
[LEFT]ndiswrapper -l
bcmwl5 : driver installed
device (14E4:4301) present (alternate driver: bcm43xx)[/LEFT]

```
 
[LEFT]If I read the dmesg output right - is this trying to put ndiswrapper on the USB? As a result, it's unavailable for wlan0?
Thanks![/LEFT]

---

### Post by Ayuthia on 2009-06-17
The usbcore information is normal.  Ndiswrapper can also be used for some USB devices so they are hooked together.

It seems that we are missing a module somewhere.  Can you post the results of:
```
lsmod
```The only thing that I can think of is that the bcm43xx module is there.  The ndiswrapper information looks fine.  Is there a switch to turn on your wireless?  If so, can you flip the switch just to make sure that it is on?

---

### Post by aptdude on 2009-06-17
> **Ayuthia said:**
> The usbcore information is normal. Ndiswrapper can also be used for some USB devices so they are hooked together.
 
It seems that we are missing a module somewhere. Can you post the results of:
```
lsmod
```The only thing that I can think of is that the bcm43xx module is there. The ndiswrapper information looks fine. Is there a switch to turn on your wireless? If so, can you flip the switch just to make sure that it is on?
 
Well, that wasn't fun... ;) There's no switch on this card. In fact, I swapped back to the Win2000 drive to make sure this card was working, and it is.
 
A bit of context - I haven't rebooted.  This is the module map after issuing the last set of commands.
 
```

 
[LEFT]lsmod
Module Size Used by
af_packet 23684 0
ndiswrapper 192664 0
isofs 36260 1
udf 88356 0
ipv6 272932 15
iptable_filter 3840 0
ip_tables 14820 1 iptable_filter
x_tables 16132 1 ip_tables
lp 12324 0
loop 19076 0
parport_pc 36644 1
parport 37704 2 lp,parport_pc
snd_cs4232 15412 0
evdev 12928 1
serio_raw 7940 0
snd_opl3_lib 12928 1 snd_cs4232
ns558 5760 0
snd_hwdep 10500 1 snd_opl3_lib
snd_cs4231_lib 26624 1 snd_cs4232
snd_mpu401_uart 9728 1 snd_cs4232
snd_cs46xx 86728 0
gameport 16008 3 ns558,snd_cs46xx
snd_rawmidi 25632 2 snd_mpu401_uart,snd_cs46xx
snd_seq_device 9612 2 snd_opl3_lib,snd_rawmidi
snd_ac97_codec 100772 1 snd_cs46xx
ac97_bus 3072 1 snd_ac97_codec
snd_pcm 78596 3 snd_cs4231_lib,snd_cs46xx,snd_ac97_codec
shpchp 34452 0
i2c_piix4 9612 0
snd_timer 24836 3 snd_opl3_lib,and_cs4231_lib,snd_pcm
intel_agp 25620 1
pci_hotplug 30880 1 shpchp
i2c_core 24832 1 i2c_piix4
snd 56868 11 snd_cs4232,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
agpgart 34760 1 intel_agp
soundcore 8800 1 snd
snd_page_alloc 11528 3 snd_cs4231_lib,snd_cs46xx,snd_pcm
psmouse 40208 0
pcspkr 4224 0
ext3 136584 1
jbd 48404 1 ext3
mbcache 9600 1 ext3
sg 36496 0
sr_mod 17828 1
cdrom 37280 1 sr_mod
sd_mod 30720 3
pata_acpi 8320 0
ata_piix 19588 3
ata_generic 8324 0
uhci_hcd 27152 0
floppy 59332 0
libata 159600 3 pata_acpi,ata_piix,ata_generic
e100 37516 0
mii 6400 1 e100
usbcore 146284 3 ndiswrapper,uhci_hcd
scsi_mod 151180 4 sg,sr_mod,sd_mod,libata
fbcon 42656 0
tileblit 3456 1 fbcon
font 9472 1 fbcon
bitblit 6784 1 fbcon
softcursor 3072 1 bitblit
fuse 50580 1[/LEFT]

```
[LEFT]Sorry about the formatting - best I can do with the transcription. I'm going to close up, so take your time and I'll get back to you tomorrow.
Thanks again![/LEFT]

---

### Post by Ayuthia on 2009-06-18
Everything looks right.  The ndiswrapper module is loaded and has no errors.  The other possible conflicting wireless modules are not loaded but for some reason, the card is not turning on.  Can you post/attach your /etc/modprobe.d/ndiswrapper file?  

You might check and see if there are files in /etc/ndiswrapper/bcmwl5.  That is where ndiswrapper stores the Windows driver.

Have you ever installed the firmware for the b43legacy module?  Can you check:
```
dmesg|grep -e b43 -e bcm43xx
```I just want to see if the system does try to load those modules at all.

---

### Post by aptdude on 2009-06-18
I'll do that when I get home.  I would like to try a different tactic, too.  wlan0 did work once for a short time.  I'd like to try to replicate that and get the repeatability of it down.  In order to do it, I'll need to undo the blacklists from the "up in 5 minutes" forum (b43 and b43legacy).  There are two parts at play here - first ndiswrapper needs to be associated with the hardware; second, the driver in ndiswrapper needs to be able to start the device.  Let me know what you think.  Thanks!

---

### Post by Ayuthia on 2009-06-18
I think that sounds fine.  Just let us know how it goes!

---

### Post by aptdude on 2009-06-18
> **Ayuthia said:**
> Everything looks right. The ndiswrapper module is loaded and has no errors. The other possible conflicting wireless modules are not loaded but for some reason, the card is not turning on. Can you post/attach your /etc/modprobe.d/ndiswrapper file? 
 
You might check and see if there are files in /etc/ndiswrapper/bcmwl5. That is where ndiswrapper stores the Windows driver.
 
Have you ever installed the firmware for the b43legacy module? Can you check:
```
dmesg|grep -e b43 -e bcm43xx
```I just want to see if the system does try to load those modules at all.
 
I don't have a simple method of getting files from this system right now, so sorry about that.  The response to the dmesg query was nothing, just another prompt.  Though, I have started poking in the syslog.  
The one time that I had success, on bootup, b44 initially took this device.  For some unknown reason, b43legacy later took it and started the radio on it.  b43legacy couldn't fully communicate with it, since it didn't have firmware.  When I removed module b43legacy and modprobed ndiswrapper, ndiswrapper attached and it could communicate.
So, what I think I'll try is to blacklist b44 and b43.  With any luck, b43legacy should get it on boot and turn on the radio.  Then I can rmmod b43legacy and ndiswrapper, modprobe ndiswrapper - and it should work.  That way, I can check out all of the various ndiswrapper drivers until I can find one that works without crashing.

---

### Post by aptdude on 2009-06-18
I think that I have a repeatable setup... I'll need to test it a bit further, but this does work (at least a couple of times).
Precondition:  b44 and ssb have the wireless card
```

sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe b43legacy

```
At this point, the card's light comes on. iwconfig shows wmaster and wlan0.
```

sudo rmmod b43legacy
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper

```
And I enter my wireless config info and I'm up.  Of course, it's on a windows driver that crashes the system, but at least I can try different ones until I find one that's stable.
Thanks for the help... I'm going to keep plodding along this line!  I'll let you know if I find a method more efficient than this.

---

### Post by w5gcx on 2010-06-13
I am new to Ubuntu, using 10.04 and had tried 3 other options.  Following are specifics

Success immediately  !!  Thanks much  ....specifics beow

**Macchine Brand and Model :**
HP Pavilliono DV5140US

**Wireless Brand and Model:**
Broadcom Corp BCM4311 (Airforce 54g) 802.11a/b/g PCI Expositions Rev 2 card.

**Wireless Chipset:    **could not get

**Ubuntu Version:** 10.04 LTS

**Kernel Arch;  **2.6.3222 generic i686 

**extra boot opt:  **no

**Compile NDIS Wrapper**  NO

**Step 2 used**  2B

**Hardy  **NO

---

### Post by c.lisco on 2012-08-25
Hi guys, anyone is still following this threat in order to help. I'd really apprecciate. Here I post my configuration: 

- Acer TravelMate 2600; 
- Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03); 
- 14e4:4320 (rev 03); 
- Ubuntu 11.10; [ distro WaTTOS r5 ] 
- 3.0.0-16-generic i686; 
- *Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)* .. I do not know if I am using these things, I'm a newbie at all; 
- I compiled NDISWrapper following the instrunctions of your guide; 
- step2: 2g; 
- I do not know if I am on Hardy.. I think not since I'm on 11.10 wattos, anyway.. 

My problem is: following the ndiswrapper configuration guide I succeded in make my pc see the available wireless connections, but, even giving the right key I could not connect. Furthermore, I could not save the ndiswrapper configuration. I tried giving the commands you listened to do it, but it did not: rebooting my pc means losing that configuration. 

Any help'd be absolutely appreciate.

---

### Post by c.lisco on 2012-08-25
anybody??

---

### Post by jerryf196 on 2012-10-08
I have a companq r4000 and installed Ubuntu 12.10beta and no idea how to get the wireless to work. Older versions of ubuntu use to have the restricted driver support.

---

