---
title: "ndiswrapper problem"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by phil46 on 2007-10-29
Hi

Using Gutsy on an acer 2700 I have installed with ndiswrapper the windows driver for the built in wifi card 
neti2200.inf winXP verion (taken from the supplied acer cdrom) with the INPROCOMM IPN 2220

This seems to be installed ok  but I have no wifi connection, below is the  output I got checking to see what was going on. apart  from  that there is no IE80211 module in lsmod, all seems correct

After looking myself for some days now I have decided to post a question  as I am not getting any further on this, I have read a lot of posts here including the one by crazycucumber below who had the same problem that is now solved but maybe he is not on gutsy, (I have seen that this could be related to gutsy having the intel/atheros wifi chipset)?? 
 
So am I  am missing something else ?  but I dont see what!!

I am adding to this as an afterthough; I have also winxp installed on this lap-top is there anyway i can get to use those drivers??

!

Thanks! 

********************
lspci

02:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)


********************

ndiswrapper -m
module configuration already contains alias directive


ndiswrapper -l
neti2220 : driver installed
        device (17FE:2220) present

**********************

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

************************

lshw

 *-network:0 UNCLAIMED
                description: Ethernet controller
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=32 mingnt=32

********************


lsmod
Module                  Size  Used by
radeon                125472  2 
drm                    83348  3 radeon
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
container               5504  0 
video                  18060  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_atiixp             21132  1 
pcmcia                 41388  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
joydev                 11328  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_atiixp_modem       17160  0 
snd_ac97_codec        100644  2 snd_atiixp,snd_atiixp_modem
irda                  202300  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
serio_raw               8068  0 
crc_ccitt               3072  1 irda
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd_timer              24324  2 snd_seq,snd_pcm
psmouse                39952  0 
snd                    54660  13 snd_atiixp,snd_seq_oss,snd_rawmidi,snd_seq,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_atiixp,snd_atiixp_modem,snd_pcm
ati_agp                10124  1 
agpgart                35016  2 drm,ati_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
evdev                  11136  5 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
ide_cd                 32672  0 
cdrom                  37536  2 sr_mod,ide_cd
ide_disk               18560  6 
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  0 
libusual               18448  1 usb_storage
8139cp                 25088  0 
atiixp                  7056  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,atiixp
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  4 sg,sr_mod,usb_storage,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by JawsThemeSwimming428 on 2007-10-29
Can you post the contents of your /etc/network/interfaces file?

sudo gedit /etc/network/interfaces

---

### Post by phil46 on 2007-10-29
Hi
Thanks for the answer, I thought that somebody would ask that! Thats what I moved on to afterwards but I did not get anywhere, There is nothing in the file !!

etc/network/interface
******
auto lo
iface lo inet loopback
******

It does not seem right to me,
should be something like : 

********
# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid MYWIFINETWORK

auto ath0
********

:confused:


********


BUt if I try this nothing changes?

---

### Post by phil46 on 2007-10-30
From what i understand the ndiswrapper source has to also be installed,

I did this :

dpkg -i ndiswrapper-source_1.47-2_all.deb 

then with module assistant
sudo m-a a-i -f ndiswrapper

So now I should see ndiswrapper in modules  with lsmod ??
But I dont IMO[U] this is the problem!!!
[/U]
> root@marie-laptop:/home/marie# ndiswrapper -m
module configuration already contains alias directive



> root@marie-laptop:/home/marie# ndiswrapper -l
neti2220 : driver installed
        device (17FE:2220) present



So why does this not work!

I had  network manager show me for a while the available wifi networks but i could not hook up, but then it vanished  on the next reboot
:frown:

---

### Post by JawsThemeSwimming428 on 2007-10-30
You should definitely browse this how to and the rest of the thread. When I was installing my USB adapter it didn't work after I read the how to but then I figured it out based on a reply that someone else made. 
To reply to your post, yes your /etc/network/interfaces file needs to be configured (I use wlan0 as my wireless connection, if you use another interface change it accordingly). You can leave the 'lo' connection in your interface file :

auto lo
iface lo inet loopback

However, I am not familiar with the others you posted. I would add:

auto wlan0
iface wlan0 inet dhcp

Again, if you do not use wlan0 you need to change it to the correct interface. As far as your ndiswrapper issues, it probably is best if you completely remove ndiswrapper and reinstall based on the how to by wieman01. He is very knowledgeable and has always been able to help me get my wireless functioning. Post back here with your results/questions.

---

### Post by phil46 on 2007-11-01
Thanks  JawsThemeSwimming428.

I got a good insight about how to go about it but I suspect that the acer firmaware just did not work, 
everything was declared and  I  got all the right output from console interogation. but heck I had this little netgear USB wifi key hanging around,  I stuck it in and the the thing lit up and i was connected immediately. 
End of story here ;-D

I tend to use DELL Ubuntu lap tops now the wifi works out of the box (not the ati driver though) but thats an other story..

Thanks!

---

### Post by Ayuthia on 2007-11-01
I have two questions:
1) Have you tried sudo modprobe ndiswrapper?
2) Is ndiswrapper in /etc/modules?

---

### Post by JawsThemeSwimming428 on 2007-11-03
No problem, glad to hear you got it working.

---

### Post by phil46 on 2007-11-04
Ayuthia
> 
I have two questions:
1) Have you tried sudo modprobe ndiswrapper?
2) Is ndiswrapper in /etc/module
Yes  to both.

It was quite an experience.
I had to return the computer to the owner so was not able to persue....
But the little netgear adapter worked first go! So everybody is happy. 

Wifi can be tough with  laptops, like I said I just recommend getting the Ubuntu  Dell laptop, that works first go.

:guitar:

---

