---
title: "[SOLVED] hostap the simple way"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by measekite on 2007-10-09
I have no experience in compiling source code for Linux in C or C++ languages.  I want to install what ever modules of hostap I need to get my Linksys WMP version 1 (Intersel Prism 2.5 chipset) working under Feisty.  

Right now I do not care for a though understanding of the hows and whys until I get it working.  Then I would like to know the detailed information.

Right now I need a step by step approach including the proper installation of ndiswrapper.  Everyone says the card should work.

In some of my reading some information points to the fact that it is already included in 2.6.15 kernel.  When I do a search I do see some hostap names but when I try to configure the network all I see is the wired card and not the wireless.  I think I must be missing something.

A step by step please.

---

### Post by Lambert on 2007-10-10
> **measekite said:**
> I have no experience in compiling source code for Linux in C or C++ languages.  I want to install what ever modules of hostap I need to get my Linksys WMP version 1 (Intersel Prism 2.5 chipset) working under Feisty.  

Right now I do not care for a though understanding of the hows and whys until I get it working.  Then I would like to know the detailed information.

Right now I need a step by step approach including the proper installation of ndiswrapper.  Everyone says the card should work.

In some of my reading some information points to the fact that it is already included in 2.6.15 kernel.  When I do a search I do see some hostap names but when I try to configure the network all I see is the wired card and not the wireless.  I think I must be missing something.

A step by step please.

Post the output of the following commands.

```


lspci -nn

lshw 

lsmod | grep host


```

Look at posts by kevdog, he has given links to a good ndiswrapper howto if that's what you want to do. Otherwise your device should be natively supported by the hostap driver. If you post the output to the above commands, we can start there.

On the lshw command, you can post just the section on your wireless device.

And question on the connection. PCI, PCMCIA, OR USB device?

---

### Post by measekite on 2007-10-11
> **Lambert said:**
> Post the output of the following commands.

```


lspci -nn

lshw 

lsmod | grep host


```Look at posts by kevdog, he has given links to a good ndiswrapper howto if that's what you want to do. Otherwise your device should be natively supported by the hostap driver. If you post the output to the above commands, we can start there.

On the lshw command, you can post just the section on your wireless device.

And question on the connection. PCI, PCMCIA, OR USB device?


I posted some of this information with levdog.  Here is what you requested.

**The card is a PCI card in a desktop computer.**


```
~$ **ndiswrapper -v**
[COLOR=Red]utils Error: no version specified![/COLOR]
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 

```

```
~$ **lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82815 815 Chipset AGP Bridge [8086:1131] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 01)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 [8086:244b] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus [8086:2443] (rev 01)
01:00.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G400/G450 [102b:0525] (rev 82)
[COLOR=Red]02:0b.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)[/COLOR]
```

```
~$ **lshw**
WARNING: you should run this program as super-user.
mymachine              
    
      
          [COLOR=Red] *-network DISABLED[/COLOR]
                description: Ethernet interface
                product: **Prism 2.5 Wavelan chipse**t
                vendor: **Intersil** Corporation
                physical id: b
                bus info: pci@02:0b.0
                logical name: **wlan0**
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes **driver=prism2_pci** latency=32 multicast=yes
                resources: iomemory:f5000000-f5000fff irq:9
```
         
        

          
```
~$ **lsmod | grep host**
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap


```

```
~$ **lshw -C network**
WARNING: you should run this program as super-user.
[COLOR=Red]  *-network DISABLED [/COLOR]     
       description: Ethernet interface
       product: **Prism 2.5 Wavelan chipset**
       vendor: **Intersil** Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes **driver=prism2_pci **latency=32 multicast=yes
       resources: iomemory:f5000000-f5000fff irq:9
```

Anything you or any other reader can do to help.  I am new to Linux.  I have a couple of weeks experience and have never used a C compiler before.  First and foremost I would like to get this working.  Then I would like to understand what is going on.

I have installed and uninstalled ndiswrapper 1.18 and 1.38 and have tried many drivers others have indicated will work.  I also made an attempt to install hostap but may not have done that correctly.  I even tried to use the drivers that came on a CD with the card.  

I also upgraded the firmware to what ever Linksys recommends on their website.

---

### Post by Lambert on 2007-10-11
Ok, need one more thing as there seems to be 3 different native drivers that might be loading for this.

Post the entire output of

```

lsmod

```

And to try something just to test run the following commands.

```

sudo ifdown wlan0
sudo modprobe -r ndiswrapper
sudo modprobe -r orinoco_pci
sudo modprobe -r hostap_pci
sudo modprobe -r prism2_pci
sudo modprobe orinoco_pci

```

Now post the output of 

```

sudo lshw -C network

```

You can also at this point try to use wireless and connect. If nothing works, we'll take it from what your output says.

The card/chipset you're using has a couple different native drivers in linux. Before moving on with ndiswrapper, I'm trying to see if card will work with one of those drivers. And need to make sure there aren't two different drivers loading and causing a conflict.

---

### Post by measekite on 2007-10-11
> **Lambert said:**
> Ok, need one more thing as there seems to be 3 different native drivers that might be loading for this.

Post the entire output of

```

lsmod

```And to try something just to test run the following commands.

```

sudo ifdown wlan0
sudo modprobe -r ndiswrapper
sudo modprobe -r orinoco_pci
sudo modprobe -r hostap_pci
sudo modprobe -r prism2_pci
sudo modprobe orinoco_pci

```Now post the output of 

```

sudo lshw -C network

```You can also at this point try to use wireless and connect. If nothing works, we'll take it from what your output says.

The card/chipset you're using has a couple different native drivers in linux. Before moving on with ndiswrapper, I'm trying to see if card will work with one of those drivers. And need to make sure there aren't two different drivers loading and causing a conflict.

Here is the output that you requested plus a little more.  I would like to understand what I did a little better.  While it still is not working I did see some encouragement.  I want you to be aware that prior to the restart I did see the "Wireless" in System>Administration>Network but not "Wired".  After reboot I saw "Wired" and not "Wireless"  

When I did see "Wireless" all of the text boxes were greyed out so I could not enter any information like SSID, WEP etc.  Is orinoco the wired card built on the MB?
[B]
[COLOR=Blue]Here is the output:[/COLOR][/B]
```

~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
vfat                   14208  1 
fat                    53916  1 vfat
nls_cp437               6784  2 
isofs                  36284  1 
udf                    85252  0 
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
mga                    62208  2 
drm                    81044  3 mga
speedstep_lib           6148  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
ac                      6020  0 
container               5248  0 
battery                10756  0 
button                  8720  0 
dock                   10268  0 
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
af_packet              23816  0 
ndiswrapper           194608  0 
lp                     12452  0 
fuse                   46612  0 
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_ac97_codec         98336  1 snd_emu10k1
orinoco_pci             8064  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0 
prism2_pci             70784  0 
p80211                 31884  1 prism2_pci
matrox_w1               5120  0 
wire                   24708  1 matrox_w1
snd                    54020  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cn                      9632  1 wire
soundcore               8672  1 snd
emu10k1_gp              4736  0 
gameport               16520  2 emu10k1_gp
psmouse                38920  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
serio_raw               7940  0 
intel_agp              25116  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  2 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_rng               6528  0 
joydev                 10816  0 
evdev                  11008  2 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
ata_generic             9092  0 
floppy                 59524  1 
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 ndiswrapper,xpad,usbhid,ehci_hcd,uhci_hcd
ata_piix               15492  3 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
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
``````
~$ sudo ifdown wlan0

ifdown: interface wlan0 not configured
``````
~$ sudo modprobe -r ndiswrapper
~$ sudo modprobe -r orinoco_pci
~$ sudo modprobe -r hostap_pci
~$ sudo modprobe -r prism2_pci
~$ sudo modprobe orinoco_pci
```[B]
[COLOR=Red]Before Restart[/COLOR]

[/B]```
~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 01
       serial: 00:06:25:03:67:2a
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.2 latency=32 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:f5000000-f5000fff irq:9
```[COLOR=Blue]System>Administration>Network[/COLOR]
Results

Wired Card did no show
**But**
Wireless Card did show
**But**
All text boxes on all tabs were greyed out and you could not enter any information to configure card.


```
~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 


```
[COLOR=Red]**AFTER RESTART (The comparison seems weird)**[/COLOR]
```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=prism2_pci latency=32 multicast=yes
       resources: iomemory:f5000000-f5000fff irq:9
```
Issues like this are why most users are putting up with Windows.  I guess Windows is functional between crashes.

---

### Post by kevdog on 2007-10-11
You removed all those modules in the step above but they were reloaded automatically at boot because they are compiled into the kernel.  In order to prevent this from happening you need to blacklist each of the modules you removed in the /etc/modprobe.d/blacklist file.  One thing I am confused about is that you keep posting information about ndiswrapper (which isnt set up right) but then want to use the orinoco driver??  Which one do you want to use -- ndiswrapper or orinoco??

---

### Post by measekite on 2007-10-11
> **kevdog said:**
> You removed all those modules in the step above but they were reloaded automatically at boot because they are compiled into the kernel.  In order to prevent this from happening you need to blacklist each of the modules you removed in the /etc/modprobe.d/blacklist file.  One thing I am confused about is that you keep posting information about ndiswrapper (which isnt set up right) but then want to use the orinoco driver??  Which one do you want to use -- ndiswrapper or orinoco??


I just typed the commands below at the request of Lambert. I do not know what orinoco is.  I think I removed it and then put it back but am not sure.  Please explain what I did and what I should do.

As I stated previously, I do not know how they all got in the kernel or why there is a conflict.  And prior to the reboot System>Administration>Network showed the Wireless card but not the Wired card.  I think is should have shown both.  In any event after selecting Wirelss and clicking properties all of the text boxes in all of tabs were grayed out so I could not even temporarly configure the card.

[COLOR=Red]Do you think this would work?

Blacklist ndiswrapper and hostap_pci and orinoco and keep prism2_pci

If so then how do I get the standard ethernet card to show up along with the wireless?  I just want to know for an understanding.
[/COLOR]
I think I am getting close.

The following code was typed as a test as per Lambert.
sudo ifdown wlan0
sudo modprobe -r ndiswrapper
sudo modprobe -r orinoco_pci
sudo modprobe -r hostap_pci
sudo modprobe -r prism2_pci
sudo modprobe orinoco_pci

---

### Post by Lambert on 2007-10-11
In your lsmod there are 4 drivers loaded that could work for this card. More then likely there is a driver conflict.

where there is a native linux driver, i always lean in that direction, especially if it's been out a while and shown functional and stable.

As kevdog said, once you reboot it starts all the drivers again. So we need to find one of the drivers that works and then blacklist the others.

I noticed an error in my commands. I unloaded hostap_pci but not hostap and orinoco_pci and not orinoco. What I put here should be correct.

sudo ifdown wlan0
 sudo modprobe -r ndiswrapper
 sudo modprobe -r orinoco
 sudo modprobe -r hostap
 sudo modprobe -r prism2_pci
sudo modprobe -r p80211
 sudo modprobe orinoco

If orinoco doesn't work, the just sudo modprobe -r orinoco and then sudo modprobe hostap. This will unload the orinoco driver and load the hostap driver. I do believe the orinoco driver will work, just need to get all the correct conflicting modules unloaded.

---

### Post by kevdog on 2007-10-11
lambert is right, you might have to play around until you find the right driver.  Once you know what is working, then you can blacklist everything else so changes are kept after rebooting.  Kind of a pain, but thats kind of the story right now!!

---

### Post by measekite on 2007-10-11
> **Lambert said:**
> In your lsmod there are 4 drivers loaded that could work for this card. More then likely there is a driver conflict.

where there is a native linux driver, i always lean in that direction, especially if it's been out a while and shown functional and stable.

As kevdog said, once you reboot it starts all the drivers again. So we need to find one of the drivers that works and then blacklist the others.

I noticed an error in my commands. I unloaded hostap_pci but not hostap and orinoco_pci and not orinoco. What I put here should be correct.

sudo ifdown wlan0
 sudo modprobe -r ndiswrapper
 sudo modprobe -r orinoco
 sudo modprobe -r hostap
 sudo modprobe -r prism2_pci
sudo modprobe -r p80211
 sudo modprobe orinoco

If orinoco doesn't work, the just sudo modprobe -r orinoco and then sudo modprobe hostap. This will unload the orinoco driver and load the hostap driver. I do believe the orinoco driver will work, just need to get all the correct conflicting modules unloaded.

This did not work.  When sudo modprobe -r orinoco I got FATAL in use error
I got the same with sudo modprobe -r hostap

When using the commands you say were in error I did see the wirless card in System>Administration>Network and after I unchecked the enable roaming box I was able to enter my ESSID and the WEP passcode. I found strange stuff.

I looked under DNS tab and did see the my own DHCP server but incorrect DNS servers for my ISP.

I do not know the equal Linux command for ipconf /all in windows that will return all of my network info.

I know I am close and it does sound like a terrible driver conflict but I do not know why it happened or what to do now.  I do appreciate your time and I know we are getting close.

---

### Post by kevdog on 2007-10-11
The equivalent command is ifconfig (kind of) combine with the route -n statement.  Do you have windows xp drivers for this device??  If you do, I say lets kind of change course and just go for ndiswrapper.  These prism devices are tricky, the solution isnt really all that clear, but Ive found a lot of other people who have had success with ndiswrapper.  You need winxp drivers however for the device.

---

### Post by measekite on 2007-10-12
> **kevdog said:**
> T  Do you have windows xp drivers for this device??  If you do, I say lets kind of change course and just go for ndiswrapper.  These prism devices are tricky, the solution isnt really all that clear, but Ive found a lot of other people who have had success with ndiswrapper.  You need winxp drivers however for the device.

I went to the linksys site.  The only WinXP drivers they have are for version 2.7 and version 4 of the card.  I have version 1 with a prism chip.  My CD has drivers for Win2k.  Any ideas?

---

### Post by measekite on 2007-10-12
> **kevdog said:**
> The equivalent command is ifconfig (kind of) combine with the route -n statement.  Do you have windows xp drivers for this device??  If you do, I say lets kind of change course and just go for ndiswrapper.  These prism devices are tricky, the solution isnt really all that clear, but Ive found a lot of other people who have had success with ndiswrapper.  You need winxp drivers however for the device.

I would like to thank kevdog and lambert for the help and information that assisted me in finding a solution to my networking problem.

The solution, once you know what is going on is very simple.

I have a linksys wmp11 wireless version 1 card with an Intersel Prism chipset.  Hardware Manager, on a clean boot reported the card to have a prism2_pci driver.  That driver reported to System>Administration>Network that I had a standard Wired Ethernet Card.  I just blacklisted the prism2_pci card and rebooted my machine.

Hardware Manager upon a clean boot reported the driver to be orinoco_pci and the Wireless Card appeared in System>Administration>Network.  I then configured the card and my network is now working.

I still need to test it completely to make sure I do not have any other problems.  

Again thanks again.

---

