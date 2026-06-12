---
title: "[SOLVED] no Internet after updating to 8.10 from 8.04..."
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by sheepfish on 2008-11-18
Hello there ubuntu community,thisis my first post ever not because i dont use ubuntu often but because i always ,till now, found the answers to my problem!So this is my time :P
 First of all  i have installed ubuntu 8.04 through wubi and when tis was done everything worked fine from the first time i logged in,i ddint have t odo no configurations to the router or stuff!!i started to use ubuntu all the time and replaced totally windows!I was a very happy user!Then i had the great idea to upgrade to 8.10!I can tell i am a bit disappointed with that distro till now...nevermind!  On the other hand now,on 8.10!there is no Internet connection!when i first log in (everytime),i see the little "dual monitor icon",that means connected to network..(ethernet not wi-fi)
when i close my router(microcom)it cannot detect i suppose!there is "monitor with a warning icon "
i have a gigabyte 965(i think) motherboard and  the network adapter is on  it,Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller!i googled around and there may be a driver problem with the update!how can i configure it so i can use my 8.04 settings for the network dirver?
another thing,when i am in windows and type [http://10.0.0.2](http://10.0.0.2) i go to my router settings page,on 8.10 i cant do it,adress not found it says.,on 8.04 i never tried it!
thank you !

---

### Post by superprash2003 on 2008-11-19
go to the terminal and type ifconfig and post output.. just incase its a drivers issue , go to system->admin->hardware drivers and see if there are any drivers you could use for your ethernet card..

---

### Post by sheepfish on 2008-11-24
sorry for not posting the results imidiatetlly,i was really busyand thank you for your time!before posting the results of some commands i want to say what have i done till now and didnt work.
i searched through ubuntu forums before posting my trouble,but unfortunatelly the posted  solutions for similar problems couldnt help me out of mine!
the first thing i tried was to download the latest drivers from marvell ,but the process of repatching the kernel was a big problem,i didnt have the time ,knowledge and patient to do a thing like this,so i searched for other solutons that worked in other pcs but for( at leatst) ubuntu 8.04 !
so the thing i did was to  the binary kernel driver sky2.ko to recognize the problematic PCI ID. 

i did it by typing the following commands( i dont know exactly what i did,just copy and paste as its without change):
# rmmod sky2
# cd /lib/modules/2.6.24-16-generic/kernel/drivers/net
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko

i dont know if i had to change anything in the code above but i didnt!i just pasted command by command in my terminal(even the cp -p sky2.ko{,.orig} i pasted it as it is!
as to what you suggested superprash2003 to go to check the hardware drivers,i did it but the only drivers i saw there were nvidia drivers and nothing else!
so that's what i did the last days and here is the output of some commands!!please help me!:P

**ifconfig**

sheepfish@sheepfish-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:e6:88:b6:ed  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4286 (4.2 KB)  TX bytes:2952 (2.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

**[B]dhclient**[/B]

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No buffer space available
Listening on LPF/pan0/3e:5e:b8:df:3c:c2
Sending on   LPF/pan0/3e:5e:b8:df:3c:c2
Listening on LPF/eth0/00:16:e6:88:b6:ed
Sending on   LPF/eth0/00:16:e6:88:b6:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Message too long
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


**lspci**

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


**lsmod **


ipv6                  314312  14 
af_packet              29568  10 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,bnep,sco,l2cap
ppdev                  16904  0 
cpufreq_userspace      12420  0 
cpufreq_ondemand       16400  0 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
freq_table             13568  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    16392  0 
wmi                    15808  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
video                  28948  0 
output                 11776  1 video
container              12288  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
sbp2                   32652  0 
lp                     19588  0 
snd_hda_intel         489392  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
joydev                 20736  0 
psmouse                51612  0 
snd_seq_oss            42368  0 
iTCO_wdt               21072  0 
evdev                  20512  7 
pcspkr                 11136  0 
serio_raw              14596  0 
iTCO_vendor_support    12420  1 iTCO_wdt
snd_seq_midi           15872  0 
nvidia               7804864  36 
snd_rawmidi            34176  1 snd_seq_midi
i2c_core               36128  1 nvidia
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             44200  1 
parport                50096  3 ppdev,lp,parport_pc
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 15904  0 
intel_agp              39280  0 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
loop                   26380  2 
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
usbhid                 39776  0 
hid                    59072  1 usbhid
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
ata_piix               29444  1 
usb_storage            92864  1 
ata_generic            14212  0 
sg                     45408  0 
libusual               31784  1 usb_storage
pata_jmicron           12288  0 
pata_acpi              13568  0 
ohci1394               41524  0 
ahci                   43148  0 
ieee1394              110592  2 sbp2,ohci1394
libata                200160  5 ata_piix,ata_generic,pata_jmicron,pata_acpi,ahci
scsi_mod              183160  6 sbp2,sd_mod,sr_mod,usb_storage,sg,libata
dock                   18464  1 libata
sky2                   61444  0 
ehci_hcd               49036  0 
uhci_hcd               34336  0 
usbcore               175632  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  1 thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  7 


**modinfo sky2**


filename:       /lib/modules/2.6.27-8-generic/kernel/drivers/net/sky2.ko
version:        1.22
license:        GPL
author:         Stephen Hemminger <shemminger@linux-foundation.org>
description:    Marvell Yukon 2 Gigabit Ethernet driver
srcversion:     EB10B5581EEE4FE40416B52
alias:          pci:v000011ABd00004380sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004370sv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Dsv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Csv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Bsv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Asv*sd*bc*sc*i*
alias:          pci:v000011ABd00004369sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004368sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004367sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004366sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004365sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004364sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004363sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004362sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004361sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004360sv*sd*bc*sc*i*
alias:          pci:v000011ABd0000435Asv*sd*bc*sc*i*
alias:          pci:v000011ABd00004357sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004356sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004355sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004354sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004353sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004352sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004351sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004350sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004347sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004346sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004345sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004344sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004343sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004342sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004341sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004340sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B03sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B02sv*sd*bc*sc*i*
alias:          pci:v00001186d00004001sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B00sv*sd*bc*sc*i*
alias:          pci:v00001148d00009E00sv*sd*bc*sc*i*
alias:          pci:v00001148d00009000sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.27-8-generic SMP mod_unload modversions 
parm:           debug: Debug level (0=none,...,16=all) (int)
parm:           copybreak: Receive copy threshold (int)
parm:           disable_msi: Disable Message Signaled Interrupt (MSI) (int)

[B]
gksudo pon dsl-provider
[/B]
/usr/sbin/pppd: no device specified and stdin is not a tty
please someone...!!!

---

### Post by sheepfish on 2008-11-25
fixed!!!!i configured dhcp manually!found the ip of my router's ,dns adn gateway!then i added
in etc/netwrok/interfaces file this lines:auto eth0
iface eth0 inet dhcp and everything is working!

---

