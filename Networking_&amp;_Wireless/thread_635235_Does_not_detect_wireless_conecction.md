---
title: "Does not detect wireless conecction?"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by soviet911 on 2007-12-08
I instaled Xubunto onto an HP ominbook 6100 and trying to use the wireless internet. I tried to set it up in the Network configuration but it sees only 2 wired conection and one of them is named Wlan 0 wich i assume is the wirless connection but it sees it as awired connection. i instaled wifi-radar and that didnt help eather. So what do i need to do to get it to work?

---

### Post by jimbob on 2007-12-08
First you need to determine what kind of wireless chip you have.  Open a terminal window and enter lspci and look for a line or two that says something about wireless.

---

### Post by soviet911 on 2007-12-08
srry about that its Integrated Wireless 802.11b Actiontec Prism also when i type in lspci i cant find it on the list. also the other thing is that when i try to start up and the WIFI is on the pc gets to the load screen and then shuts down yet when i turn it off it loads up fine.

---

### Post by jimbob on 2007-12-09
Do you have XP on this laptop also?  See if you can find any info there under sysadmin->device manager.
   It looks like the Actiontec chips are mostly supported from the googling I did but more specific info is needed.

  Post the output of lspci and lsmod so we can see it.

---

### Post by soviet911 on 2007-12-09
I dont have any windows on it, windows 2000 that was installed on it took up all of the space of 20 gig drive and i could not free any space through it since it crashed on boot up :mad: so there is no windows on it now. also here is what the lspci and lsmod look like, I dont know why but im pretty sure the network adapter is the wireless, and also a i read with wlan-ng wich is instaled with xubunto it should work, and i think it does, but except its seen as a wired connection.Im not familiar with lunix (this is my first time ) so i have no clue what the problem is. Thanks again

lspci
soviet911@Soviet911portable:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 Communication controller: 3Com Corporation Mini PCI 56k Winmodem
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:04.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:05.0 CardBus bridge: Texas Instruments PCI1420
02:05.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 41)
soviet911@Soviet911portable:~$ 

lsmod
Module                  Size  Used by
ipv6                  268960  8 
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
acpi_cpufreq           10056  1 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
container               5248  0 
battery                10756  0 
button                  8720  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
video                  16388  0 
asus_acpi              17308  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
lp                     12452  0 
snd_maestro3           27012  4 
snd_ac97_codec         98464  1 snd_maestro3
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 39212  0 
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco
joydev                 10816  0 
snd                    54020  16 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
prism2_pci             70784  0 
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               8672  1 snd
p80211                 31884  1 prism2_pci
serio_raw               7940  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
pcspkr                  4224  0 
af_packet              23816  2 
intel_agp              26140  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  2 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
floppy                 59524  0 
e100                   36232  0 
mii                     6528  1 e100
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by jimbob on 2007-12-09
OK, here is your wireless pci (integrated):

02:04.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

and it is using the orinoco driver(s) which have been loaded:

orinoco_pci 8064 0
orinoco 43028 1 orinoco_pci
hermes 8448 2 orinoco_pci,orinoco

The basics are all in place so all we have to do is figure out why the wireless locks up.
Have you done any searches on Ubuntu for others who have installed using this particular HP setup?  I have had success with helping others get the Broadcom chips up and running so will look around tomorrow and see what I can find on Orinoco.  Right now I have to wrap Christmas presents.

---

### Post by soviet911 on 2007-12-10
I searched the forums but didn't find anything, i found a page with a person who installed lunix (not ubuntu) [http://www.nyx.net/~dwiebold/omnibook6100-linux.html](http://www.nyx.net/~dwiebold/omnibook6100-linux.html) but he only installed wlan ng drivers and in 2003 orinoko update and it ran on knoppix 3.2 and said that it woke up and worked. I wounder why it sees it as wired connection and not wireless, wounder if there is a way to force it to think that its wireless. 

Thanks again for looking into this.

---

### Post by jimbob on 2007-12-10
Here is a post that you may be able to use.  Read it through carefully before trying anything since it appears they went in the wrong direction a couple of times.  
Good luck.

[http://ubuntuforums.org/showthread.php?t=446010&highlight=prism](http://ubuntuforums.org/showthread.php?t=446010&highlight=prism)

---

### Post by soviet911 on 2007-12-10
thank you that seemed to help now it sees it as a wireless connection, i used the instruction on this linkhttps://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989 
except after i did that it disapered from the network list completly so then i ran command sudo modprobe  prism2_pci and now it sees it as a wireless connection the problem was that multiple drivers were trying to make it work and confused the thing to think into that it was wired, but now it seems to work gonna go over to my friends house and see if it will connect to the wireless connection he got at home. and then report back. Thanks again

---

