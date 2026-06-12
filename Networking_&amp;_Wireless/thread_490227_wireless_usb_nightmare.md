---
title: "wireless usb nightmare"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by kwalters on 2007-07-02
I am very much a newcomer and trying to set up Feisty 7.04 as dual boot with Win XP.
Got both programs running OK and eventually (but only with help from this forum) managed to change the OS order in the Grub 'Bootloader

Next step was to get my Belkin FSD 7050A usb wireless dongle working so as to access the web via my  home network.  Visited a lot of forums and websites and studied 2 solutions in some depth:  serialmonkey and ndis wrapper.  The former never managed to do what it said on the box, although I ended up with a driver marked 2570 somewhere.  I even moved it to a different directory after some web site said modprobe would not work unless that file was in a particular directory.  Neither would it after I moved it

Reverted to t rying ndis wrapper.  The installation of this worked as advertised but, when I went looking for the Windows drivers for the device, I have a problem.  In my Windows\syustem32 directory there is a file called rt2500usb.sys (and that is quoted as the driver if you go to device manager via control panel.  Howevder, I cannot find any file with a .INF suffux anyshere.  Went into the install cdrom and that, too, only has the one .SYS file and no .INF file.   

Saw some CAB files on the install CD and read somewhere that you can unpack these with "cabextract"
Tried to install that but it told me it would not  work without the "universe" component.  I dont know whether unpacking the CAB files would solve my problems or not.   I do know (or think I know) that I cannot install the universe component without internet access.  If  I had it, of course, I would not be bothering with all this frustration as my USB dongle would be working.

Is there any way I could download files in Windows on my other machine and transfer them to the Ubuntu machine to install the universe component?

Alternatively, does anyone know where I can get the .INF file to complement the .SYS file I already have?  I tried the Belking support website and downloaded an enormous file of "drivers for this device"   However all it would do was install the device without sharing any files with me

I think my main problem as a complete novice to this OS, is that I have not a clue about half the things I am trying to do.  I copy, verbatim, incredibly long command lines without a clue about what their various elements are for.  I think I will give it another week or so (on top of the week in which I have already devoted every spare minute to this problem) then I will give up on Linux.  Feisty is, from memory, the fifth distribution I have tried, using 4 dfferent computers, and this is the furthest I have got; and still no internet access.

KW

---

### Post by Austin_KW on 2007-07-02
The serialmonkey driver probably was the correct one, but you may have a driver conflict,

What is the output of the following terminal commands
ifconfig -a
lsusb
lsmod

---

### Post by kwalters on 2007-07-03
Sorry for the delay.  Had to go to work.  I finally found the right .INF file on another of my computers, and did the ndiswriapper bit.  It appeared to work and found the driver and hardware, but announced the driver (rt2500usb.sys) as invalid driver.  The command modprobe ndiswrapper did nothing exept return me to the original prompt.

rt2500usb.sys is DEFINITELY the driver that works the dongle in WinXP, although I seem to remmber reading that it was for cards and the 2750 variant (see below) was for the dongles

Outputs as requested are below; and I think there is a clue in the third.  It mentions rt2750 (under usbcore), which is what I was trying to install via serialmonkey before it became too difficult.  I remember moving that particular file to another directory because somebody's suggestion was that modprobe would not work unless it was in a certain directory. 

keith@study:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:21:B8:C2:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x6c00 

eth0:avah Link encap:Ethernet  HWaddr 00:19:21:B8:C2:A4  
          inet addr:169.254.8.192  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)

keith@study:~$ 


keith@study:~$ lsusb
Bus 003 Device 004: ID 058f:6377 Alcor Micro Corp. 
Bus 003 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:009d Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
keith@study:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
button                  8720  0 
battery                10756  0 
dock                   10268  0 
ac                      6020  0 
asus_acpi              17308  0 
video                  16388  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
backlight               7040  1 asus_acpi
lp                     12452  0 
fuse                   46612  0 
rt2570                187072  0 
rt73usb                33536  0 
rt2x00lib              11904  1 rt73usb
crc_itu_t               3072  1 rt73usb
sg                     36252  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
sd_mod                 23428  2 
prism54usb             16896  0 
prism54common          12288  1 prism54usb
mac80211              175364  4 rt73usb,rt2x00lib,prism54usb,prism54common
cfg80211               22920  1 mac80211
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
parport_pc             36388  1 
xpad                    9988  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
i2c_piix4               9740  0 
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
ati_agp                10124  0 
agpgart                35400  1 ati_agp
i2c_core               22784  2 i2c_ec,i2c_piix4
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
8139too                27648  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
usb_storage            72256  1 
libusual               17936  1 usb_storage
generic                 5124  0 [permanent]
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
atiixp                  7440  0 [permanent]
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  10 rt2570,rt73usb,prism54usb,xpad,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
sata_sil               12808  0 
ata_generic             9092  0 
libata                125720  2 sata_sil,ata_generic
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
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
keith@study:~$ 

Thanks for your help, which sounds promising

KW

---

### Post by Austin_KW on 2007-07-03
lusb is reporting your device as "Bus 003 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi" but if it is useing the rt2500usb.sys under windows then I think you are correct and it is in fact a version 2000 or rt2570.

As you noticed the driver rt2570 is loaded but also rt73usb and prism54usb. These are for version 1000 and 3000 of the belkin usb. 

I think you need to blacklist the two conflicting drivers to stop them from loading  
gksudo gedit /etc/modprobe.d/blacklist  
and add the following lines
```

blacklist rt73usb
blacklist prism54usb

```

And reboot, then rt2570 should be able to get control of the device.

FYI, Similarly, now that you have installed rt2570, if you wanted to use ndiswrapper with the windows driver you would have to blacklist rt2570 to avoid conflicts.
Hope this helps.

---

### Post by kwalters on 2007-07-03
Thanks

However, you are starting to lose me.  What you are suggesting looks like code rather than c ommand line  -  and I don't know how to do code.  Do I just type what you have printed at the command prompt and then move on to the 2 subsequent lines from 2 successive prompts?

KW

---

### Post by Austin_KW on 2007-07-03
type "gksudo gedit /etc/modprobe.d/blacklist " at the command line, this will open an editor with the blacklist file.

Add the two blacklist lines to the end of the file, save and exit,

reboot 

After rebooting use "ifconfig -a" to check for the wireless interface.

---

### Post by kwalters on 2007-07-04
Thanks for that. You can see how new I am

I did that, edited and saved the file and rebooted.  To be more precise, I attempted to reboot but it would not.  It got nearly to the end of the orange strip (just before the stage where I am normally invited to log in) and froze.

I have rebooted several more times but it still refuses to go beyond that point.

I can start up in recovery mode (merely a command prompt) but am not sure what I can do in that mode to recover from this latest problem.  I did manage to use the VI editor to take out the changes I had made to the blacklist file;  but that still does not allow me to reboot

Unless someone can come up with a simple exercise that would allow me to "recover" the installation, I suspect I will be stuck with taking it out altogether and reinstalling from scratch

KW

---

### Post by Austin_KW on 2007-07-04
Unplug the wireless adapter and i think it should boot, still sounds like a driver problem.  

You can also blacklist rt2570 and then try the ndiswrapper. Or you might try blacklisting ndiswrapper but I do not see it loading.

---

### Post by kwalters on 2007-07-05
In the end I uninstalled Ubuntu and did a clean reinstall.  At least that should have got rid of any residual drivers

I have been right through the ndis process again. However I am a little unsure as to whether it has worked or not.  I appear to have a WLAN0 if I go to system/administrative tasks/network.  The output from ifconfig shows also a WLAN0 (posted below)

When I attempted to redo the ndis wrapper, it told me that rt2500usb was already installed; but you will see that it does not feature in the printouts, only rt2570.  Could the install program be changing it itself?

Meanwhile, if I do a modprobe rt2570 I am told it does not exist

If I go to system/administration etc in the graphical interface I can set up WLAN0 with the IP addresses etc that work in Windows   - that is the only reason I think for my information and masks being in the printout.  But I still cannot get online.

I followed a fascinating and similar thread on this forum.  It was headed "hp strange wireless problem"  I got exactly the same printout that kevdog was looking for with ndis wrapper -v.  But then I rather lost the plot when they started worrying about how they got version 1.38.  I too have been through that:  if you download ndiswrapper-1.47.tar.gz you get version 1.38; the ndiswrapper-1.47.tar.tar gives the 1.47 version

Can anyone help me get further towards linking to the internet and the other computers on my home network.

Printout follows
printouts after wlan0 appeared 050707

keith@study:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
video                  16388  0 
dock                   10268  0 
button                  8720  0 
ac                      6020  0 
battery                10756  0 
container               5248  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
af_packet              23816  0 
lp                     12452  0 
fuse                   46612  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
rc80211_simple          6400  1 
prism54usb             16896  0 
prism54common          12288  1 prism54usb
sg                     36252  0 
rt2570                186432  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
rt73usb                33536  0 
rt2x00lib              11904  1 rt73usb
snd_seq_oss            32896  0 
mac80211              175364  5 rc80211_simple,prism54usb,prism54common,rt73usb,rt2x00lib
cfg80211               22920  1 mac80211
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
sd_mod                 23428  2 
crc_itu_t               3072  1 rt73usb
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0 
psmouse                38920  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
i2c_piix4               9740  0 
serio_raw               7940  0 
ati_agp                10124  0 
agpgart                35400  1 ati_agp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
i2c_core               22784  2 i2c_ec,i2c_piix4
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
8139too                27648  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
usb_storage            72256  1 
libusual               17936  1 usb_storage
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_generic             9092  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               34188  0 
atiixp                  7440  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  10 prism54usb,rt2570,rt73usb,xpad,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
sata_sil               12808  0 
libata                125720  2 ata_generic,sata_sil
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
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
keith@study:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:21:B8:C2:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59140 (57.7 KiB)  TX bytes:59140 (57.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:6B:76:12  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-6B-76-12-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

keith@study:~$ sudo modprobe rt2570
Password:
keith@study:~$ sudo modprobe rt2570usb
FATAL: Module rt2570usb not found.
keith@study:~$ 

kw

---

### Post by Austin_KW on 2007-07-05
I can not tell which driver is managing the wlan0. usbcore is still showing conflicting drivers (prism54usb,rt2570,rt73usb)
What is the output of "lshw -C net"

Also in the example you have an ip address, is your network working, or did you just set a static address

---

### Post by kwalters on 2007-07-06
I had already done an output from
lshw -C network

which I assume is the same

I will post it below and, meanwhile I will try blacklisting a different 2 of the drivers you mention for a few iterations and see if anything changes

keith@study:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 10
       serial: 00:19:21:b8:c2:a4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:e400-e4ff iomemory:febefc00-febefcff irq:20
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:6b:76:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
keith@study:~$ 


With regard to the IP addresses, I tried them when nothing was found on DHCP; they are the details that work with Windows

Thanks again for sticking with me

KW

---

### Post by kwalters on 2007-07-06
Since posting the above I have blacklisted the 2 drivers other than 2570 and some changes have appeared.
Firstly WLAN0 has  become rausb0 and, as you can see from the printout below, the driver is still quoted as 2500.  Beats the wotsit out of me.  Any further suggestions?

keith@study:~$ sudo lsmod
Password:
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  268704  10 
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
video                  16388  0 
dock                   10268  0 
button                  8720  0 
ac                      6020  0 
battery                10756  0 
container               5248  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
lp                     12452  0 
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
sg                     36252  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
rt2570                186432  1 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sd_mod                 23428  2 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                38920  0 
serio_raw               7940  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
i2c_piix4               9740  0 
soundcore               8672  1 snd
ati_agp                10124  0 
agpgart                35400  1 ati_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
i2c_core               22784  2 i2c_ec,i2c_piix4
af_packet              23816  8 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
8139too                27648  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
usb_storage            72256  1 
libusual               17936  1 usb_storage
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_generic             9092  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               34188  0 
atiixp                  7440  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  8 rt2570,xpad,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
sata_sil               12808  0 
libata                125720  2 ata_generic,sata_sil
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
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
keith@study:~$ 


keith@study:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:21:B8:C2:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xac00 

eth0:avah Link encap:Ethernet  HWaddr 00:19:21:B8:C2:A4  
          inet addr:169.254.8.192  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6932 (6.7 KiB)  TX bytes:6932 (6.7 KiB)

rausb0    Link encap:Ethernet  HWaddr 00:11:50:6B:76:12  
          inet6 addr: fe80::211:50ff:fe6b:7612/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:409462 (399.8 KiB)  TX bytes:8482 (8.2 KiB)

rausb0:av Link encap:Ethernet  HWaddr 00:11:50:6B:76:12  
          inet addr:169.254.4.37  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

keith@study:~$ 


keith@study:~$ lshw -C net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 10
       serial: 00:19:21:b8:c2:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:e400-e4ff iomemory:febefc00-febefcff irq:20
  *-network
       description: Wireless interface
       physical id: 2
       bus info: firewire@3
       logical name: rausb0
       serial: 00:11:50:6b:76:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN
keith@study:~$ 



KW

---

### Post by kwalters on 2007-07-08
Many thanks for your help.  I now have a working wireless usb dongle and can connect to the internet.  Indeed I am using this site via Ubuntu for the first time.  LIfe will become a lot easier when I do not have to keep dashing upstairs to surf and download in Windows

Still not sure exactly what I changed in the end.  I definitely had to set fixed IP addresses  -  before that I spent a long time with a usb dongle that  claimed to work but with no network access. I also spent a long time unable to access my normal home page at Yahoo ,co,uk,  In Windows I defined it as [www.yahoo.co.uk](www.yahoo.co.uk),  In Ubuntu I have to enter [http://uk.yahoo.com](http://uk.yahoo.com).

One last question before I close this thread.  I have taken encryption off to get this to work.  I normally use WEP 128 bit; but I can see no way of differentiating in Ubuntu between 64 bit and 128 bit.  If I just select  WEP, ASCII and insert the passphrase I use for WEP, should that work?

Thanks again for your patience

KW

---

