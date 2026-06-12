---
title: "Marvell w8300 PCI Card Wont Work"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by Johnsie on 2005-10-13
Hi... Device Manager says that I have a Marvell w8300 PCI Card
0000:00:09.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 80 2.11 Adapter (rev 07)

The card doesn't appear in "Network Settings"

Please can someone tell me how to get it working. 




Thanks in advance, 
John

---

### Post by bladesE on 2005-10-13
hi 

did you have the option to configure this card during the install

---

### Post by Johnsie on 2005-10-14
no

---

### Post by bladesE on 2005-10-15
i did a "apci=off" as one of the boot options and it worked for me

i am running on an Toshiba A4

---

### Post by Johnsie on 2005-10-30
How does one go about doing that?

---

### Post by skunkydog on 2005-10-30
how you set acpi=off in the boot options depends on if you have lilo or grub installed. for lilo, set it in the lilo.conf file. for grub, set it in the menu.lst file. i think some grub versions use grub.conf but i'm not sure.

for lilo:
1. find the config file. use **locate lilo.conf**, but it should be **/etc/lilo.conf**
2. edit the file (make a backup first!). i use gedit so i use **sudo gedit /etc/lilo.conf**
3. find where it boots into linux (it says **image=/boot/vmlinuz** or something) and look for an indented line that says **append=** somewhere under it. if it is not there you'll have to add it.
4. add the **noacpi** or **acpi=off** option at the end, but inside the quotes.
it should look something like **append=" ro quiet splash acpi=off**
5. save and reboot.

for grub (pretty much the same):
1. edit the file **/boot/grub/menu.lst**
2. look for the line that begins [/B]kernel[/B].
3. add acpi=off at the end of it.

---

### Post by basementjack on 2005-12-03
I have a wireless card from ASUS, which identifies itself as _Marvell W8300 802.11 Adapter (rev 07)_ and tried the **noacpi/acpi=off** solution on both Hoary and Breezy with no luck.

I even tried to install Breezy with "**boot parameters:linux acpi=off**"....

Still it only shows up with *lspci* or Device Manger, and does not up show in "System > Administration > Networking" as an option.

Did I do something wrong or does anyone have an other solution?

---

### Post by Lambert on 2005-12-03
There's no linux driver currently for a marvell chipset. You need to use an app called ndiswrapper to make the windows drivers work. There's a link in my signature that should get you going for ndiswrapper.

---

### Post by basementjack on 2005-12-03
Hey again.. I followed the guide and it does say:

[B]Installed ndis drivers:
mrv8k51 driver present, hardware present[/B]

But, my card does not show up ifconfig... I doublechecked everything..
By the way is the *modprobe* command supposed to "reply", because it doesn't..

---

### Post by Lambert on 2005-12-03
No it shouldn't but you can check if ndiswrapper is loaded by this command

lsmod | grep ndis

---

### Post by basementjack on 2005-12-03
Hey again.... I have put my brain back in and discovered that *ifconfig* does not show it, but *iwconfig* does!.. :)

Cannot continue making it work right now, since I adjusted the time 3 hours back.... So the *sudo* command won't work for an hour or so... After reading *man sudo* it seem to be no way of resetting it.

---edit---
All is well with the world now.. :) I set my network up reading the section **Configuring interfaces** at this site [Ndiswrapper installation guide]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") and now it also shows up in *ifconfig*.

---

### Post by usererror on 2007-09-12
> **basementjack said:**
> Hey again.... I have put my brain back in and discovered that *ifconfig* does not show it, but *iwconfig* does!.. :)

Cannot continue making it work right now, since I adjusted the time 3 hours back.... So the *sudo* command won't work for an hour or so... After reading *man sudo* it seem to be no way of resetting it.

---edit---
All is well with the world now.. :) I set my network up reading the section **Configuring interfaces** at this site [Ndiswrapper installation guide]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") and now it also shows up in *ifconfig*.

This thread got me in the right direction for my D-Link G510 Rev 7 card as well (aka Marvell 8300 Rev 7 according to lspci output).

I downloaded Ndiswrapper 1.4.7 and the driver for the D-Link card from ndiswrapper's website.  The exact file names are:

ndiswrapper-1.47.tar.gz  and  dwlg510_driver_100.zip

I then followed the INSTALL file instructions from the ndiswrapper exactly.  It works great!

---

### Post by iAmNewbee on 2007-10-03
I'm trying to setup my home network. The LG R400 laptop has a build-in network card called

Marvel Yukon 88E8039

Unfortunately when I go to the Network-Settings it cannot detect the card. It even doesn't have a button 'Add' for adding a new network interface.

I tried using NDISwrapper. It installed a driver for Win XP, that I found in internet. The driver inf-file was called: yk60x86.inf

But network-settings still doesn't show the eth0 interface!

What's wrong with me? 

Here is the relevant part of the output of lspci:

```
...
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4353 (rev 15)
0000:05:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
...
```

---

### Post by Lambert on 2007-10-03
> **iAmNewbee said:**
> I'm trying to setup my home network. The LG R400 laptop has a build-in network card called

Marvel Yukon 88E8039

Unfortunately when I go to the Network-Settings it cannot detect the card. It even doesn't have a button 'Add' for adding a new network interface.

I tried using NDISwrapper. It installed a driver for Win XP, that I found in internet. The driver inf-file was called: yk60x86.inf

But network-settings still doesn't show the eth0 interface!

What's wrong with me? 

Here is the relevant part of the output of lspci:

```
...
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4353 (rev 15)
0000:05:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
...
```

ndiswrapper is for a wireless device. The marvell card you listed is a pci-e network card, not a wireless card correct?

This device looks to use the sk98lin driver so open a terminal and try this.

```

sudo modprobe sk98lin

```You shouldn't see any errors or output, just a new line. Now see if you have an eth interface in network manager.

If not, come back here and we'll take the next trouble shooting step.

---

### Post by iAmNewbee on 2007-10-04
> The marvell card you listed is a pci-e network card, not a wireless card correct?

Yes, Marvel is a pci network card (wires needed). So I suppose I was wrong going trough all the steps described in ndiswrapper.

'sudo modprobe sk98lin' makes no output and does nothing. After this command I still don't have my eth0 interface listed in the network-settings..

Please let me know what schould be my next step..

---

### Post by Lambert on 2007-10-04
> **iAmNewbee said:**
> Yes, Marvel is a pci network card (wires needed). So I suppose I was wrong going trough all the steps described in ndiswrapper.

'sudo modprobe sk98lin' makes no output and does nothing. After this command I still don't have my eth0 interface listed in the network-settings..

Please let me know what schould be my next step..

Run these commands and post output here.

```

sudo lsmod

sudo lshw

```

on the lshw command, if you can find just the section on your pci card, post just that.

---

### Post by iAmNewbee on 2007-10-04
_sudo lsmod's output:_

Module                  Size  Used by
ipv6                  265728  6 
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0 
speedstep_centrino      8400  1 
cpufreq_userspace       4696  1 
cpufreq_stats           5636  0 
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
video                  16260  0 
tc1100_wmi              6916  0 
sony_acpi               5644  0 
pcc_acpi               12416  0 
hotkey                 11556  0 
dev_acpi               11140  0 
container               4608  0 
button                  6672  0 
acpi_sbs               19980  0 
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
nls_utf8                2176  2 
ntfs                  103536  2 
dm_mod                 58936  1 
md_mod                 72532  0 
parport_pc             35780  0 
lp                     11844  0 
parport                36296  3 ppdev,parport_pc,lp
joydev                 10048  0 
tsdev                   8000  0 
new_ath_pci            98340  0 
new_ath_rate_sample    14080  1 new_ath_pci
new_wlan              204892  2 new_ath_pci,new_ath_rate_sample
psmouse                36100  0 
wlan                  144924  0 
rtc                    13492  0 
new_ath_hal           191312  2 new_ath_pci,new_ath_rate_sample
serio_raw               7300  0 
snd_hda_intel          18964  1 
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
hw_random               5652  0 
intel_agp              22940  1 
agpgart                34888  1 intel_agp
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
sg                     37920  0 
evdev                   9856  2 
ext3                  135688  1 
jbd                    58772  1 ext3
usb_storage            74176  0 
ide_generic             1536  0 
ehci_hcd               34184  0 
uhci_hcd               33680  0 
usbcore               130692  4 usb_storage,ehci_hcd,uhci_hcd
sd_mod                 19984  5 
ahci                   17284  8 
libata                 78992  1 ahci
scsi_mod              139496  5 sg,usb_storage,sd_mod,ahci,libata
ide_cd                 33028  0 
cdrom                  38560  1 ide_cd
piix                   11012  1 
generic                 5124  0 
thermal                13576  0 
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

_output from 'lshw':_
   *-pci
          description: Host bridge
          product: Mobile Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@02:00.0
                version: 15
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:f4000000-f4003fff ioport:3000-30ff irq:10

---

### Post by Lambert on 2007-10-04
type in this command and post output

```

sudo modinfo sk98lin

```

I do believe this is the correct driver for that card. Currently it's not loading for whatever reason.

I suggest spending sometime doing some searches on google and hopefully you find something. The above command verify's if the module is installed. What version of ubuntu are you using?

use search terms like

sk98lin ~conflict
sk98lin ubuntu
sk98lin marvell
sk98lin module won't load

etc...

---

### Post by iAmNewbee on 2007-10-04
when I modprobe sk98lin and then run lsmod | grep sk there is the following entry:
sk98lin 164832 0

But the network doesn't work.
Thanks for your suggestions, i will google now a little bit to see where could be the problem...

---

### Post by kandarp728 on 2008-05-19
For those of you with 64bit kernels, I just found 64bit drivers for Win2kand XP and used ndiswrapper to load the driver, one reboot later it works fine....I found the driver 

[http://www.64bitdrivers.com/driver.php?id=1346](http://www.64bitdrivers.com/driver.php?id=1346)

I unzipped it and used the 64bit drivers for WINXP_2k, worked like a charm, this after so much googling

---

