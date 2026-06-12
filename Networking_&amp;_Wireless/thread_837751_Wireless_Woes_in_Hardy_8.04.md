---
title: "Wireless Woes in Hardy 8.04"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by NearlyALaugh on 2008-06-22
Hi, I'm having trouble getting Ubuntu to recognize wireless cards on my laptop (**Sony VAIO PCG-9G1L**). I have tried several cards (**Netgear WPN111**, **Microsoft Wireless Notebook Adapter MN-520**, and **Dynex DX-E201**) without Ubuntu recognizing them. I would prefer to use the Dynex card, but my main priority is getting online.

Is there a straightforward way to set up my wireless card in Ubuntu? I have browsed blogs, forums, and official documentation, but all I have found is a jumble of suggestions to install packets, drivers, and enter various command-prompt operations. I've attempted to follow all the relevant instructions without success.

My network connections icon says "No network connections", and no connections appear under Network Settings (System > Administration > Network).

I installed ndiswrapper on my system to no avail: My Dynex installation CD includes a folder entitled "LINUX" which contains a document "**dxe201.c**" written in C that is supposed to be the driver for the wireless card, but ndiswrapper (presumably System > Administration > Windows Wireless Drivers) wants an .inf file. When I tell the C file to run on its own, nothing happens. There is no useful help information on the Dynex CD or on their website. Someone had a similar problem in [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5235791#post5235791"), but the suggestions didn't work. According to *pytheas22*, my Dynex card has an **rtl8129** chipset (whatever that means!).

Below are the results of the **lsmod**, **ifconfig**, and **iwconfig **commands. I'm not sure if my card is recognized to begin with.

```
taylor@taylor-laptop:~$ lsmod
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
usbhid                 31872  0 
libusual               19108  1 usb_storage
hid                    38784  1 usbhid
ipv6                  267780  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
sony_laptop            35292  0 
sonypi                 23192  0 
ppdev                  10372  0 
powernow_k7             9000  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
freq_table              5536  3 powernow_k7,cpufreq_ondemand,cpufreq_stats
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
ac97_bus                3072  1 snd_ac97_codec
evdev                  13056  6 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         9728  1 snd_via82xx
serio_raw               7940  0 
psmouse                40336  0 
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
pcspkr                  4224  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
button                  9232  0 
snd                    56996  19 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27276  2 
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_viapro              9876  0 
soundcore               8800  1 snd
i2c_core               24832  1 i2c_viapro
via686a                15244  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
via_agp                11136  1 
agpgart                34760  1 via_agp
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
8139too                27520  0 
floppy                 59588  0 
ohci1394               33584  0 
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
uhci_hcd               27024  0 
pata_via               13316  3 
ata_generic             8324  0 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
usbcore               146028  5 usb_storage,usbhid,libusual,uhci_hcd
libata                159344  3 pata_via,ata_generic,pata_acpi
scsi_mod              151436  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  3 powernow_k7,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  5 
```
```
taylor@taylor-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:6f:7d:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:219148 (214.0 KB)  TX bytes:219148 (214.0 KB)
```
```
taylor@taylor-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

I tried the command-line suggestions in [[COLOR="Blue"]the thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5235791#post5235791") I linked to above; here are the commands that returned anything at all:
```
taylor@taylor-laptop:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

taylor@taylor-laptop:~$ mii-tool -F 10baseT-HD
no MII interfaces found

taylor@taylor-laptop:~$ mii-tool -R
no MII interfaces found
```
I presume that means Ubuntu doesn't know the card exists at all? Any help would be appreciated. I'm using a portable hard drive to shuttle information from my desktop computer (online) to my laptop (offline) on which I'm running my Ubuntu experiment.

Any help would be appreciated. Thanks in advance!

*May all beings be well and happy!~*

---

### Post by pytheas22 on 2008-06-22
Incidentally I just happened upon your post while looking through the unanswered list (I am in the thread you link to above).

Let's first make sure that the interface definitely isn't being recognized by the system at all.  If you type:
```

iconfig -a
```

do you see anything besides an entry for 'lo?'  I realize it's hard for you to copy and paste (since you don't have an Internet connection) so I won't ask you to do that, but let me know if there's anything there *other than* a block of text that looks similar to:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112861 (110.2 KB)  TX bytes:112861 (110.2 KB)

```

If you don't see anything besides lo, please try running:

```
sudo rmmod 8139cp
sudo modprobe 8139too

```

and then look at ifconfig again.  Anything else there?

If not, try:
```

sudo rmmod 8139too
sudo modprobe 8139cp
```

and please look again.

If none of the stuff above yields anything interesting, then the next thing to do I think is to look at dmesg.  Run:
```

dmesg | grep -e eth -e rlt
```

and please copy the output here.  If the output is too much to type, you can pipe it into a text file by adding a > to the command, e.g.:

```

dmesg | grep -e eth -e rlt > ~/Desktop/output.txt
```

would cause the output from dmesg to be dumped to a file on your desktop called 'output.txt.'  Then you could copy it onto a USB stick and bring it to a machine where you have Internet access and copy and paste on there into this thread.

Please try these things and post your results.  As I wrote in the first thread, I really don't think it's necessary to have to compile the source code that you have on your CD.  I think it's just a matter of figuring out why the driver won't recognize your card, which shouldn't be too hard really.

Also, which version of *Ubuntu are you using?

---

### Post by pytheas22 on 2008-06-22
After reading your post more thoroughly, I have some more questions.  I didn't realize that your goal is to get wireless.

First, isn't the Dynex card just an ethernet (wired) interface, not wireless?  I don't own one but that was the impression I got from helping the user in the other thread.  Also from your iwconfig output, it looks like the Dynex card is recognized as an ethernet interface and should work if you plug a cable into it.

Second, if you plug in all three of your wireless devices and run these commands:
```

lspci > ~/Desktop/lspci.txt
lsusb > ~/Desktop/lsusb.txt
```

and copy the text files that they create on your Desktop onto your Windows machine so that you can post them here, it would be helpful.  This will display the chipsets of the devices, and with that information it shouldn't be hard to figure out what you need to do to make them work.

Also, to answer your question about a straightforward way to set up wireless: unfortunately, if your card doesn't just work out of the box (as many do, depending on how friendly their manufacturers are towards Linux/open-source), then no, there's really not a simple way to configure it.  There are lots of different kinds of drivers and the procedures for each is different.  But once you figure out which driver you need (which is the point of seeing the lspci and lsusb output), it's usually not hard to find instructions on how to configure it.

---

### Post by NearlyALaugh on 2008-06-23
Hmm, well it *would* make it hard to find information on how to get wireless on my Dynex card if it isn't a wireless card!

That was the problem with Dynex. :roll:

Now trying the Microsoft card...

Recall that it is a **Microsoft Wireless Notebook Adapter MN-520**.

**ifconfig**:```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160000 (156.2 KB)  TX bytes:160000 (156.2 KB)


```

**iwconfig**: no output

**lsmod**:```
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
ipv6                  267780  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
sony_laptop            35292  0 
sonypi                 23192  0 
ppdev                  10372  0 
powernow_k7             9000  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
freq_table              5536  3 powernow_k7,cpufreq_ondemand,cpufreq_stats
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
evdev                  13056  6 
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
serio_raw               7940  0 
snd_pcm                78596  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         9728  1 snd_via82xx
psmouse                40336  0 
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
pcspkr                  4224  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
ac                      6916  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  19 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               8800  1 snd
i2c_viapro              9876  0 
i2c_core               24832  1 i2c_viapro
via686a                15244  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
via_agp                11136  1 
agpgart                34760  1 via_agp
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
floppy                 59588  0 
ohci1394               33584  0 
8139cp                 24704  0 
mii                     6400  1 8139cp
uhci_hcd               27024  0 
pata_via               13316  3 
ata_generic             8324  0 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
usbcore               146028  2 uhci_hcd
libata                159344  3 pata_via,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  3 powernow_k7,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

**lspci** (with only the Microsoft card inserted):```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
00:0a.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0a.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

According to [[COLOR="Blue"]this post[/COLOR]]("http://amdzone.net/phpbb3/viewtopic.php?f=15&t=80698&p=83119#p81854") at AMDZone.com, the **MN-520** card is supported by Linux, and binds the orinoco_cs (again, whatever that means!). The card is [[COLOR="Blue"]supposed to[/COLOR]]("http://ubuntuforums.org/showthread.php?p=1153040&highlight=MN-520#post=1153040") work out of the box

Following the example in [[COLOR="Blue"]another thread[/COLOR]]("http://ww.ubuntuforums.org/showthread.php?p=76741") (for I don't really know what I'm doing, if you haven't figured it out already!), I edited the file /etc/pcmcia/config.opts to include these lines:```
card "Microsoft Wireless Notebook Adapter MN-520 1.0.3"
version "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
bind "orinoco_cs"
```

I restarted Ubuntu, but the Microsoft card still doesn't appear to be recognized. Neither the "Wireless" nor the "Power" light is on or blinking. There's nothing new in "Network Settings".

Thanks~!

---

### Post by Pjotr123 on 2008-06-23
Try this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by pytheas22 on 2008-06-23
From what I can tell from other threads, the Microsoft card should just work, and it if it doesn't, editing /etc/pcmcia/config.opts as you did should solve the problem.  So the only advice I have for that is first to make sure that the card is definitely firmly in the pcmcia slot (you'd be surprised how many problems come down to stuff like this).  I don't see your card being detected by lspci so I wonder if it's really in place.

If you're sure that it is, then I'd look at dmesg output to see why the card isn't being brought up.  In other words, what does:
```

dmesg | grep -e eth -e wlan
```

tell you?

Or if you want to give it a shot with your third card instead of this Microsoft one, please post the lspci and ifconfig -a information after you've inserted that

---

### Post by fmouse on 2008-06-23
A note on ndiswrapper:  You need ndiswrapper *only* if your wireless card isn't supported, or properly supported, natively in Linux.  If you do need it, what *it* needs is the *Windows* driver for your card, not a Linux driver.  You'll find this on the CD that came with the card.  

ndiswrapper has both a kernel module and a run-time binary for configuring the kernel module.  Browse the CD that came with the card and find the directory containing the Windows driver for it.  You'll see a .inf file there, as well as a .sys file, possibly some .hlp files and others as well.  The .inf file is the one you want.  Then execute:

```
ndiswrapper -i /full/path/to/the/inf/file [... so to speak]
```

ndiswrapper will read and stash the .inf file and the .sys file which is referenced in the .inf file, and thereafter it should just work.  If you're using a laptop, make sure you have wireless turned on from your keyboard.

BTW, Linux drivers that come with proprietary hardware in the form of C files are often pretty lame.  Compiling them isn't hard - usually there's a README or INSTALL for them somewhere - but compiles often fail based on the kernel version, and even if they compile they won't install or work.  Many proprietary hardware makers don't give a rat's behinder about Linux, and they throw on a C file just so they can say they support Linux, but don't keep up with whether or not it works in current versions of the kernel.

---

### Post by NearlyALaugh on 2008-06-23
I checked the Microsoft card and it *wasn't* firmly in place. Now it is, but the "Wireless" and "Power" lights still aren't blinking, even after restarting the computer. There is nothing new in "Network Settings".

**ifconfig** (eth0 is new):```
eth0      Link encap:Ethernet  HWaddr 08:00:46:6f:7d:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:147876 (144.4 KB)  TX bytes:147876 (144.4 KB)


```

**lspci** (nothing new here):```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
00:0a.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0a.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

**dmesg** (the same, whether card is in or not):```
[  208.874581] eth0: RealTek RTL8139 at 0x1800, 08:00:46:6f:7d:1d, IRQ 10
[  208.874585] eth0:  Identified 8139 chip type 'RTL-8139C'
[  209.488134] Driver 'sd' needs updating - please use bus_type methods
[  209.488515]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  336.193334] eth0: link down
[  707.391315] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
It appears that there is no power going to the card, or that it is not recognized... but it worked when Windows XP was installed on the laptop.

---

### Post by NearlyALaugh on 2008-06-23
This may be irrelevant, but before I installed Ubuntu I ran [[COLOR="Blue"]Darik's Boot and Nuke (Hard Drive Disk Wipe)[/COLOR]]("http://dban.sourceforge.net/"). Could that've messed something up?

---

### Post by pytheas22 on 2008-06-23
Was the Dynex card inserted when you were gathering the output for your last post?  Because I see an ethernet card (eth0) but still no wireless device, even in the output of lspci.  If the Dynex card wasn't in the machine, are you sure that the device that was inserted is a wireless card?  I know it has wireless in its name, but maybe you're confusing it with another device or something?  If the Dynex card was in the computer, though, then that explains it all...

But please let me know.

Also is there any way you can test the device in a Windows machine just to make sure it still works?

---

### Post by NearlyALaugh on 2008-06-23
Nope, the Dynex card is out of the picture.

The Microsoft card is a wireless card, and it worked in the past with XP.

I just loaded the card into a laptop that runs XP, and the lights came on immediately. The card works.

---

### Post by pytheas22 on 2008-06-23
Is the Microsoft card also an ethernet card?  In other words, is there a place to plug a wire in?  Because Ubuntu really, really thinks it's ethernet with an rtl8139 chipset, as lspci shows:

> lspci (with only the Microsoft card inserted):
Code:

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
00:0a.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0a.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
**00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

Unless there's also ethernet built in to the computer (there's not, right...or did I miss something?), then the only thing that could be the source of that ethernet entry is the Microsoft card.  If the card does both ethernet and wireless, it would make a little more sense (but not that much, because I still don't know why no wireless of any kind is showing up in lspci).

And by the way, the disk wipe thing wouldn't have had any conceivable effect on any of this.

---

### Post by NearlyALaugh on 2008-06-23
Nope, the card is just a plain old wireless card.

[img]http://reviews.digitaltrends.com/images/reviews/1245/20040229_2001021.gif[/img]

The laptop has a "network" slot which I presume is ethernet. (I can't explain the whole Dynex thing... this laptop was given to me recently, so I'm not wholly familiar with the layout.) lspci doesn't change whether or not the card is inserted.

---

### Post by pytheas22 on 2008-06-23
In that case, I guess the ethernet that exists is internal (you could probably use it if it makes it easier to post output to here, by the way).

I'm wondering if the pcmcia card isn't showing up because of a problem recognizing the pcmcia bus.  The only way that I know to check it out is to see the entire output of:

```
sudo lshw
```

Please post it when you get a chance.  I've never heard of Ubuntu failing to do something as basic as detect a system bus, but if you have a weird motherboard, I guess it's possible.

Also just to rule out hardware failure completely, are you sure that the pcmcia bridge actually works?  Do you have anything else that you could stick in just to see if it lights up?  Did you (or the person who gave you the machine) see it working recently?

I'm sorry this issue is turning so complicated, but I'm sure we'll figure it out eventually.

---

### Post by NearlyALaugh on 2008-06-23
I don't have anything else that'd fit in the slot.

Here's the output of **sudo lshw**:```
taylor-laptop
    description: Notebook
    product: PCG-FXA63(UC)
    vendor: Sony Corporation
    version: 01
    serial: 28105030-3124130
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook uuid=EBB5D280-3708-11D4-8203-0800466F7D1D
  *-core
       description: Motherboard
       product: Q3-Project
       vendor: Sony Corporation
       physical id: 0
       version: 1A
       serial: 01234567-01234567
     *-firmware
          description: BIOS
          vendor: Sony Corporation
          physical id: 0
          version: R0121K5 (08/13/2002)
          size: 102KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect socketedrom edd acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: mobile AMD Athlon(tm) XP 1600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.0
          slot: Socket A
          size: 1400MHz
          capacity: 1400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts fid vid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: synchronous external write-through
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 512MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: CN24
             size: 256MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: CN25
             size: 256MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 64
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-isa:0
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64 module=pata_via
           *-disk
                description: ATA Disk
                product: HITACHI_DK23DA-2
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00J2
                serial: 146AX3
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=dededede
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 8cd86de1-6032-45e5-bb1a-bebe6d89d50d
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-21 15:26:49 filesystem=ext3 modified=2008-06-23 17:52:33 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-06-23 17:41:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 839MiB
                   capacity: 839MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 839MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: UJDA730 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-isa:1
             description: ISA bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.6
             bus info: pci@0000:00:07.6
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB12LV26 IEEE-1394 Controller (Link)
             vendor: Texas Instruments
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: eth0
             version: 10
             serial: 08:00:46:6f:7d:1d
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
```I noticed two entries for pcmcia in the output above, though there is only one usable slot in the laptop. (There is a space for a slot beneath the one that holds my card, but it is blocked off.

Might reinstalling Ubuntu help?

I don't recall the last time I saw the wireless card functioning correctly. I don't recall ever seeing it not working before now, either.

I loaded my copy of the Knoppix 5.3.1 Live Distro DVD to see if that'd have any effect... it didn't. The card is still dark. I tried to configure internet connections through Knoppix and it says "No wireless network card found."

My USB wireless device isn't recognized in either of my (functioning) USB slots, which is the only thing that gives me hope that it's *not* a hardware problem.

Thanks for all your help so far.

---

### Post by pytheas22 on 2008-06-24
Thanks again for all of the information.  It looks like the pcmcia bus is fine, so I'm really at a loss as to why that card wouldn't be working.  The only other suggestion I have is to plug the device in and see what the output of:
```

cardctl status
```

says.  This is supposed to tell you what's in the slot, so we'll at least know whether the system sees anything or not.

Beyond that, we could go for the USB stick.  If you post the output of:
```

lsusb
```

while the card is inserted, hopefully there will be a simple procedure for getting it working.

You definitely don't seem to have good luck with network cards!

---

### Post by NearlyALaugh on 2008-06-24
```
taylor@taylor-laptop:~$ cardctl status
bash: cardctl: command not found
```

**lsusb** with Netgear USB card inserted:```
taylor@taylor-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 1385:5f01 Netgear, Inc
Bus 001 Device 001: ID 0000:0000
```

---

### Post by pytheas22 on 2008-06-24
The USB device at least seems normal.  I found this [thread]("http://ph.ubuntuforums.com/showthread.php?t=652910") for making it work with ndiswrapper, a utility that allows you to drive wireless cards using their Windows drivers.  That guide is for 7.10 but it should work just fine in Hardy too.  If you can plug your laptop in to get an Internet connection temporarily, follow those instructions and hopefully they'll get you up and running--most of the feedback in that thread is very positive so I assume the directions are good.  They also seem as straight-forward as they could be, but of course if you need something to be clarified, post.

If you can't get a wired connection on the laptop, let me know and I'll adapt the instructions to address that.

---

### Post by NearlyALaugh on 2008-06-25
The Netgear device works -- blinks, receives wireless signals -- but it doesn't connect to my wireless network ("NETGEAR"). The taskbar icon says "Waiting for Network Key for the wireless network 'NETGEAR'...", and eventually it gives up. My password is correct.

---

### Post by pytheas22 on 2008-06-25
> he Netgear device works -- blinks, receives wireless signals -- but it doesn't connect to my wireless network ("NETGEAR"). The taskbar icon says "Waiting for Network Key for the wireless network 'NETGEAR'...", and eventually it gives up. My password is correct.

oh no, so close....

If possible, try turning off encryption on your router and see if it works.  At least then we'll be able to narrow the problem down and figure out how to resolve it.

It could also be the fault of Network Manager.  You could try using [wicd]("http://wicd.sourceforge.net") instead; it usually gives better results.

Finally, if you post the output of:
```

iwlist scanning
```

I can give you instructions for connecting using the command-line to see if that would work.

---

### Post by NearlyALaugh on 2008-06-26
Originally I had the encryption wrong. I corrected it and I even got a connection! The Network Manager showed two bars and 28% connection strength (which is about normal where I am). However, I couldn't connect to the internet, and I couldn't get reconnected when I tried again.

I connected to the internet via router and downloaded and installed Wicd. The Netgear card lights up whenever I plug it in now, which is good (it used to take a restart to get the light to come on), but Wicd says "No wireless networks." I told it that the correct driver is ndiswrapper, but it doesn't recognize the device. I don't know what to put for "Wireless Interface" under "Preferences".

It tells me that I'm "Connected to None" when I put "lo" in for "Wireless Interface" as just a guess.

---

### Post by pytheas22 on 2008-06-27
Yeah, wicd is sort of dumb in that it doesn't try to autodetect your wireless card for you, and it won't work until you tell it the correct name of the "wireless interface."  So that's the problem.

Try telling it wlan0.  If that doesn't work, it's whichever wireless interface name you get when you type "iwconfig"--there should be only one.  But I'm pretty sure that ndiswrapper will have named it wlan0.

So please try that and see if you can connect.

---

### Post by NearlyALaugh on 2008-06-27
It was **wlan0** -- I now see a list of wireless networks. However, Wicd doesn't seem to have the correct type of encryption. My router has WPA-PSK TKIP encryption, but it is not listed under "Use Encryption":[list][*]WPA 1/2
[*]WEP (Hex)
[*]WEP (Passphrase)
[*]LEAP with WEP
[*]TTLS with WEP
[*]EAP-FAST
[*]PEAP with GTC
[*]PEAP with TKIP[/list]I can't connect using WPA 1/2.

---

### Post by pytheas22 on 2008-06-27
Under Preferences in wicd you can specify which wpa_supplicant driver to use (I think default is wext).  Try using the ndiswrapper driver instead.

Another approach is to click System>Administration>Network and manually configure your wireless settings there.

Hopefully either of these will help.  I'm really sorry this is turning out to be so difficult.

---

### Post by NearlyALaugh on 2008-06-30
Thanks for your continued support. I haven't been at the computer to reply the past few days.

I had already selected the ndiswrapper driver, so I don't think that was the problem. I entered the correct settings under System>Administration>Network, but I didn't find any way to connect.

---

### Post by pytheas22 on 2008-06-30
The last thing I can think to try before going back to the drawing board on the USB stick is to attempt to connect from the command line.  This would do it:
```

sudo iwconfig wlan0 mode Managed rate 11M essid "YOUR NETWORK NAME(INSIDE QUOTES)" channel CHANNEL-NUMBER key s:YOUR-PASSWORD
sudo dhclient wlan0
```

if that fails, try:

```

sudo iwconfig wlan0 mode Managed rate 11M essid "YOUR NETWORK NAME(INSIDE QUOTES)" channel CHANNEL-NUMBER key YOUR-PASSWORD
sudo dhclient wlan0
```

and last shot:

```
sudo iwconfig wlan0 mode Managed rate 11M essid "YOUR NETWORK NAME(INSIDE QUOTES)" channel CHANNEL-NUMBER key restricted YOUR-PASSWORD
sudo dhclient wlan0
```

If you don't know the channel that your network is on, use the command "iwlist wlan0 scan" and it will tell you.

The commands above are three variations on negotiating the key, which I suspect is the problem.  TKIP I think just means WPA1, so it should be connecting with that option in wicd, but maybe something's wrong.

Also, if there's any way to turn off encryption on your network temporarily (or trying different variations of WPA) and trying to connect, that would be useful for at least pinpointing the source of the failure to connect.

---

### Post by NearlyALaugh on 2008-06-30
I tried all the commands with the "s:" prefix before my password (otherwise it thinks it's a command), but they failed to connect. The DHCP client opened up alright, and it tried to connect:```
Listening on LPF/wlan0/00:18:4d:dc:22:e9
Sending on LPF/wlan0/00:18:4d:dc:22:e9
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
```but eventually gave up:```
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping
```

I'm not in charge of the network, and others depend on it, so I'd be afraid to fiddle with it. If that makes it impossible to proceed then we can just call it quits and I'll hope for success on my next laptop. (My current one is an old Sony I'm just experimenting with.)

Thanks!:KS

---

### Post by aimwin on 2008-06-30
**[COLOR="Red"]Have you try it the GUI ways[/COLOR]**
[B][I][U]
[http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111)[/U][/I][/B]

Now I have successful install a "very stable" internet connection with wpn111 Using the above GUI ways.


But if you try the above GUI ways and get no where.
If you still have problems, see if you have the same as mine...in my old post in another thread...using [email]aim@mail.nu[/email] before I got that GUI ways.
And I don't recommended the manual command line installation.

[http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111&page=5](http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111&page=5)

---

### Post by pytheas22 on 2008-07-01
I'm sorry it still doesn't work even after all you've gone through.

If aimwin's guide doesn't work, I have one last-ditch shot for you to try, if you're interested, based on a very strict interpretation of instructions at [http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910) .  If you feel inclined:

First, download [this file]("http://ubuntuforums.org/attachment.php?attachmentid=54577&d=1198939980") and [this file]("http://ubuntuforums.org/attachment.php?attachmentid=54578&d=1198939980") and save them to your desktop.

Then:

```

cd ~/Desktop
sudo apt-get install build-essential
tar -zxvf ndiswrapper-1.51*
cd ndiswrapper-1.51*
sudo make uninstall; sudo make uninstall; sudo make uninstall
sudo make distclean
make
sudo make install
cd ..
tar -zxvf win-drivers.tar.gz
cd win-drivers
sudo ndiswrapper -i netwpn11.inf
sudo depmod -a
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

In a perfect world, you would be able to connect now.  If not, I'm still happy to keep trying other things to get you a wireless connection...being unemployed till September, I have enough time and patience on my hands right now to go at this for months.

But I can understand that you're possibly at the point where you just want to give it a rest.  If that's the case, my apologies again that this has all been so convoluted and futile, and I hope you will get a chance soon to try Ubuntu again with hardware that will work better.  Yours is almost certainly the worst luck I've ever seen with wireless on Linux...it's often not as easy as it should be to get wireless up, but I've never run into anyone with three different devices that are entirely impossible to get working.  Anyway, thanks for keeping positive through the whole ordeal.

---

### Post by NearlyALaugh on 2008-07-01
aimwin's guide seems to duplicate much of what I've already done, and it relies on the Network Manager and some other things I've already altered.

And unfortunately, the command-line installation in the last post just duplicated the results I had earlier. Wicd doesn't act any differently -- it shows the networks but doesn't allow me to connect.

I suspect the problems have to do with my laptop, but there's no way to know that for sure. I generally don't trust Sony, but that's just me.

I think I'll give up on the wireless for now and reinstall Windows in a partition. Thanks for all the help. If nothing else, I learned a lot about using Ubuntu. :)

</experiment>

---

### Post by NearlyALaugh on 2008-07-01
Well it turns out I *don't* have Windows on CD! I won't be on for a week or so, but I guess I have no choice but to be open for further suggestions if you have any. Thanks in advance!

---

### Post by pytheas22 on 2008-07-01
Alright, then I'll suggest that you go back to Network Manager, since wicd doesn't seem to be be helping:
```

sudo apt-get install network-manager-gnome
```

will bring NM back.  Then please try connecting again a few times (remember to select the right type of key)--I know you said that NM got you connected once, so give it a few shots to do it again.  If it doesn't connect after three or four tries, please open a terminal and type:
```

dmesg
```

and post the output here.  Hopefully that will give some useful information about why it doesn't want to connect.

It would also still be useful to see if you can connect to an open network.  If it's hard, then don't worry about it, but if you get a chance ever to go to a library or coffee shop or wherever and want to see if you can connect to a network that's not encrypted, it would be helpful to know the results.

---

### Post by aimwin on 2008-07-05
> **NearlyALaugh said:**
> The Netgear device works -- blinks, receives wireless signals -- but it doesn't connect to my wireless network ("NETGEAR"). The taskbar icon says "Waiting for Network Key for the wireless network 'NETGEAR'...", and eventually it gives up. My password is correct.

Excellent --- Congratulation with you.

It prove that your NETGEAR adapter is working.
And also the driver is working.

And that error you got was exactly the same as my errors, and I can produce it every time even now. I know how to produce it.

I guess you are using WPA or WPA2.

If you are using WPA or WPA2 don't use Network Mananager to auto connect.
(DON'T CLICK ON THE WIRELESS NETWORK AVAILABE LIST, when you left click on the Network Manager or Network Icon or that TASK BAR ICON you mentioned).

Please look at my comments at the last part on my tutorial.
[http://ubuntuforums.org/showthread.php?p=5289197#post5289197](http://ubuntuforums.org/showthread.php?p=5289197#post5289197)

About using Manual Configuration, I did that and can connect immediately.
However many times when I try to do it again to prove it is correct, it will not work.

And I have to "SHUTDOWN" AND UNPLUG usb ADAPTER and reinsert after it half way booting the process. And a few times have to do it 3 times before it will work under WPA and WPA2.

[COLOR="Red"]But with WEB password type...==>> 100% after "SHUTDOWN" AND turn on[/COLOR].
Never once has problem, and that is using Network Icon connect automatically. 
(By CLICKING on the wireless network available, and enter password, and password type and DHCP/or others.)

---

### Post by aimwin on 2008-07-05
> **NearlyALaugh said:**
> aimwin's guide seems to duplicate much of what I've already done, and it relies on the Network Manager and some other things I've already altered.
</experiment>

Have you try exact steps in my tutorial. 
[http://ubuntuforums.org/showthread.php?p=5289197#post5289197](http://ubuntuforums.org/showthread.php?p=5289197#post5289197)

1. Very important please install fresh copy of UBUNTU 8.04 and UPDATE every packages it suggests. I found that I must have mess up UBUNTU after tried it so many things manual and use sudo and even root password. It behaved (for me) totally different after I install fresh UBUTU and the updates.

2. I have included wpn111 drivers in the tutorial already so you can try to download that. Forget the verification with XP, and hope your wpn111 is hardware_working 100%.

And refer to the previous posts, [COLOR="Red"]I hope that post shows your wpn111 is working[/COLOR] otherwise it should not be blinking. (How ever I have 1 faulty pcmcia card that led blinking but it is actually dead, and it is netgear and dead under windowsXP too.)

And try those "non command line" installation in my tutorial.
Since you can not accidentally harm the system at all.
And I hope you will try to do it exact steps first, if it doesn't work then you can try variations.

It took me 70 odd hours to get that conclusions and I repeated them 3 times 100% the same before I post that.

3. I have to emphasize that the [COLOR="Red"]PASSWORD authentication is more troublesome than to get the drivers and the adapter to work[/COLOR].

I found finally WPA and WPA2 is not as reliable as WEP 128 Hex.
So I recommend to change Access Point to WEP authentication.

EVEN WEB caught me many dead connections, I accidentally chosed WEP ASCII or the Phrase, and even 64 bit instead of 128 bit HEX.

So please Check.

WPA WPA2 has many configurations too. AES, TPK, Personal ...etc....

[COLOR="Red"]VERY important, What pytheas22 said in previous posts:

"if possible, try turning off encryption on your router and see if it works. At least then we'll be able to narrow the problem down and figure out how to resolve it."[/COLOR]

I would like to add to that too, since I also made stupid mistake again when I test wg111v2 with my mentioned tutorial today. (made that also many times in the past too).

Please make sure you turn off "Mac Address Filtering" in the Wireless Access Point [COLOR="Red"]off[/COLOR] too. Or make sure that it is [COLOR="Red"]correctly added[/COLOR] before you attempt to connect.

Let us know your result, good luck.

---

### Post by NearlyALaugh on 2008-07-09
> **pytheas22 said:**
> Alright, then I'll suggest that you go back to Network Manager, since wicd doesn't seem to be be helping:
```

sudo apt-get install network-manager-gnome
```

will bring NM back.
That command executes but cannot connect to the online repository: I can no longer get a wired internet connection on the laptop. Wicd does the same thing for the wired network (it reads "Obtaining IP Address..." and then fails) as it does for the wireless network. Is there a command-line way of connecting to a wired network? Is there an alternative to **apt-get**?

[quote=aimwin]Have you try exact steps in my tutorial[?][/quote]
There is nothing in your tutorial that I haven't done over the course of this problem. All of the basic building blocks are in place -- drivers, ndiswrapper, a working wpn111 drive -- but something is holding it up. I doubt that pytheas22's command line instructions caused any problems with the system because they all executed flawlessly.

---

### Post by pytheas22 on 2008-07-09
> That command executes but cannot connect to the online repository: I can no longer get a wired internet connection on the laptop. Wicd does the same thing for the wired network (it reads "Obtaining IP Address..." and then fails) as it does for the wireless network. Is there a command-line way of connecting to a wired network? Is there an alternative to apt-get?

That's strange that you're not getting a wired connection now (did this happen before?).  But basically, to connect manually, you just run the command:
```

sudo dhclient eth0
```

I don't know if that's going to work, though, because that should be pretty much all that wicd is doing.

You could also install the Network Manager packages again by downloading them from [http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager) (base package; install first) and [http://packages.ubuntu.com/hardy/network-manager-gnome](http://packages.ubuntu.com/hardy/network-manager-gnome) (install second), moving them to your computer and double-clicking to install.

But before you do that, I have some other stuff for you to try for getting the wireless going manually, based on a tutorial [here]("http://ubuntuforums.org/showthread.php?t=571188").  If you get a chance, see if this helps:

1. First you need to have wpa_supplicant installed, which you should by default.  If you type "wpa_supplicant" in a terminal and don't get an error message, then it's installed.

2. In a terminal, type:
```

sudo gedit /etc/wpa_supplicant.conf
```

A file will open.  Add to the file these lines:
```

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="ESSID_IN_QUOTES"
        psk="ASCII PSK Password in Quotes"
        key_mgmt=WPA-PSK
        proto=RSN
        pairwise=CCMP
}
```

Then save and close the file.

3. Run these commands, which with any luck will connect you:
```

sudo kill $(ps -e | grep Network)
sudo kill $(ps -e | grep wicd)
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -w -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

Any good news?

---

### Post by NearlyALaugh on 2008-07-10
I was able to get a wired connection before, but I only used it once or twice. I tried **sudo dhclient eth0**, but it didn't connect. I forget what the error message was.

1. wpa_supplicant is installed
2. I added the necessary lines in the .conf file
3. The commands seemed to execute properly (after a couple tries and a restart or two), but things started to get messy at this line: **sudo wpa_supplicant -w -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd**.

I'll post the output of the whole set below:
```
taylor@taylor-laptop:~$ sudo kill $(ps -e | grep Network)
[sudo] password for taylor: 
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
``````
taylor@taylor-laptop:~$ sudo kill $(ps -e | grep wicd)
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
``````
taylor@taylor-laptop:~$ sudo ifconfig wlan0 down
``````
taylor@taylor-laptop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:dc:22:e9
Sending on   LPF/wlan0/00:18:4d:dc:22:e9
Sending on   Socket/fallback
``````
taylor@taylor-laptop:~$ sudo wpa_supplicant -w -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=7):
     4e 45 54 47 45 41 52                              NETGEAR         
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
key_mgmt: 0x2
proto: 0x2
pairwise: 0x10
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='NETGEAR'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:4d:dc:22:e9
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 714 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 722 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 714 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 722 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 714 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 714 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 722 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 714 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN proto match
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:95:c3:b4:29 ssid='2WIRE551' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1b:2f:0d:2e:ca ssid='prhea1st' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
l2_packet_receive - recvfrom: Network is down
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
CTRL-EVENT-TERMINATING - signal 15 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
``````
taylor@taylor-laptop:~$ sudo ifconfig wlan0 up
``````
taylor@taylor-laptop:~$ sudo iwconfig wlan0 mode Managed
``````
taylor@taylor-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7459
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:dc:22:e9
Sending on   LPF/wlan0/00:18:4d:dc:22:e9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
receive_packet failed on wlan0: Network is down
Terminated
```I didn't try opening up a webpage afterwards because I assumed that "Network is down" and "Terminated" means I'm not connected.

Hope that gives you some clues!

I haven't installed Network Manager yet.

---

### Post by pytheas22 on 2008-07-11
First, what are the contents of your /etc/wpa_supplicant.conf file (remember that it contains your WPA password in plain text; if you don't want to post it on the Internet, you can change that part of the file to something else)?  wpa_supplicant doesn't seem to think that your network is in range, even though it's seeing the networks 2WIRE551, NETGEAR and prhea1st, one of which I assume is your network.  Maybe wpa_supplicant.conf is not configured correctly--your network's name should be on the line that says, "ssid="ESSID_IN_QUOTES" (an ESSID is the name of a wireless network). 

If you did specify the network name correctly or after you've fixed it, please try running these commands, which are the same as the first set with a minor change.  I think the "network is down" error has to do with a bug in dhclient, so we'll try a different version of dhclient:
```

sudo kill $(ps -e | grep Network)
sudo kill $(ps -e | grep wicd)
sudo ifconfig wlan0 down
sudo wpa_supplicant -w -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient3 wlan0
```

---

### Post by NearlyALaugh on 2008-07-13
My wpa_supplicant.conf file contains only the lines you directed me to add -- it was empty to start with. What is it supposed to contain?

NETGEAR is my wireless network.

---

### Post by pytheas22 on 2008-07-13
Ah, I actually happened upon [someone else]("http://ubuntuforums.org/showthread.php?t=853762") in a situation very similar to yours: a Netgear wpn111 wireless card and a WPA2 network that he has no control over.

I did a lot of research and it seems that the wpn111 works fine with unsecured networks or WEP, but I wasn't able to find a single person who's ever gotten it to connect to WPA.  Then again, no one seems to have tried too hard.  Ubuntu thinks (according to the system logs) that the wpn111 under ndiswrapper should be totally capable of using WPA, so I think it is going to be possible if we try hard enough (like everything in Linux...).

With the other user, I think we've gotten very close...he can associate (the first half of getting a connection), but not authenticate.  So to get you to the same point as him, please follow these steps:

1. remove anything in /etc/network/interfaces and replace it with:
```

auto lo
iface lo inet loopback
```

2. run this command in a terminal:
```

wpa_passphrase YOUR-NETWORK YOUR-PASSWORD
```

If your network name or password includes blank spaces, put them inside quotes in the command above.

That command will generate output that looks like this:
```

network={
	ssid="NETGEAR"
	#psk="password"
	psk=83937c525af39fcc1dcf867ad38792df4638c9fb7934062bdd7a6feca888625f
}
```

Copy and paste this output into the file /etc/wpa_supplicant.conf (delete anything that's already in the file).

2. Add to /etc/wpa_supplicant.conf this information (verbatim):
```

       scan_ssid=1
       proto=WPA RSN WPA2
       key_mgmt=WPA-PSK
       auth_alg=OPEN
       pairwise=CCMP TKIP
       group=CCMP TKIP
```

Put it inside the {brackets} so that your finished wpa_supplicant.conf looks similar to:

```
network={
	ssid="NETGEAR"
	#psk="password"
        psk=83937c525af39fcc1dcf867ad38792df4638c9fb7934062bdd7a6feca888625f
       scan_ssid=1
       proto=WPA RSN WPA2
       key_mgmt=WPA-PSK
       auth_alg=OPEN
       pairwise=CCMP TKIP
       group=CCMP TKIP
}
```

and save the file.

3. now try to connect with these commands:

```
sudo rm -rf /var/run/wpa_supplicant/wlan0
sudo ifconfig wlan0 down
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D wext -d -t -K 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
sudo dhclient3 wlan0
```

Please post output.  The other user ran into an error trying to authenticate that I'm not sure how to solve right now, but we're working on it.

---

### Post by NearlyALaugh on 2008-07-15
```
taylor@taylor-laptop:~$ sudo rm -rf /var/run/wpa_supplicant/wlan0
``````
taylor@taylor-laptop:~$ sudo ifconfig wlan0 down
``````
taylor@taylor-laptop:~$ sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D wext -d -t -K
1216148509.758021: Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
1216148509.758240: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
1216148509.758272: Reading configuration file '/etc/wpa_supplicant.conf'
1216148509.758587: Priority group 0
1216148509.758620:    id=0 ssid='NETGEAR'
1216148509.758646: Initializing interface (2) 'wlan0'
1216148509.768939: EAPOL: SUPP_PAE entering state DISCONNECTED
1216148509.768977: EAPOL: KEY_RX entering state NO_KEY_RECEIVE
1216148509.768993: EAPOL: SUPP_BE entering state INITIALIZE
1216148509.769022: EAP: EAP entering state DISABLED
1216148509.769052: EAPOL: External notification - portEnabled=0
1216148509.769070: EAPOL: External notification - portValid=0
1216148509.769457: SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
1216148509.769490:   capabilities: key_mgmt 0xf enc 0xf
1216148509.893543: WEXT: Operstate: linkmode=1, operstate=5
1216148509.906177: Own MAC address: 00:18:4d:dc:22:e9
1216148509.906250: wpa_driver_wext_set_wpa
1216148509.907516: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
1216148509.907699: wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
1216148509.907710: wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
1216148509.907722: wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
1216148509.907732: wpa_driver_wext_set_countermeasures
1216148509.907741: wpa_driver_wext_set_drop_unencrypted
1216148509.907812: Setting scan request: 0 sec 100000 usec
1216148509.907837: Added interface wlan0
1216148509.907948: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1216148509.907962: Wireless event: cmd=0x8b06 len=8
1216148509.912370: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1216148509.913030: Wireless event: cmd=0x8b15 len=20
1216148509.913096: Wireless event: new AP: 00:00:00:00:00:00
1216148509.913169: Added BSSID 00:00:00:00:00:00 into blacklist
1216148509.913252: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
1216148509.913300: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
1216148509.917214: wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
1216148509.917419: wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
1216148509.917473: wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
1216148509.917521: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
1216148509.917570: State: DISCONNECTED -> DISCONNECTED
1216148509.917614: wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
1216148509.917656: WEXT: Operstate: linkmode=-1, operstate=5
1216148509.917725: EAPOL: External notification - portEnabled=0
1216148509.917770: EAPOL: External notification - portValid=0
1216148509.917818: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1216148509.917863: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1216148510.008209: State: DISCONNECTED -> SCANNING
1216148510.008495: Starting AP scan (specific SSID)
1216148510.008544: Scan SSID - hexdump_ascii(len=7):
     4e 45 54 47 45 41 52                              NETGEAR         
1216148510.008657: Trying to get current scan results first without requesting a new scan to speed up initial association
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
1216148510.009143: Scan results: -1
1216148510.009195: Failed to get scan results
1216148510.009239: Failed to get scan results - try scanning again
1216148510.009286: Setting scan request: 0 sec 0 usec
1216148510.009340: Starting AP scan (broadcast SSID)
1216148513.012200: Scan timeout - try to get results
1216148513.012744: Received 481 bytes of scan results (2 BSSes)
1216148513.012876: Scan results: 2
1216148513.012992: Selecting BSS from priority group 0
1216148513.013101: Try to find WPA-enabled AP
1216148513.013207: 0: 00:14:6c:07:06:74 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
1216148513.013335:    selected based on WPA IE
1216148513.013440:    selected WPA AP 00:14:6c:07:06:74 ssid='NETGEAR'
1216148513.013554: Try to find non-WPA AP
1216148513.013681: Trying to associate with 00:14:6c:07:06:74 (SSID='NETGEAR' freq=2462 MHz)
1216148513.013794: Cancelling scan request
1216148513.013904: WPA: clearing own WPA/RSN IE
1216148513.014008: Automatic auth_alg selection: 0x1
1216148513.014113: Overriding auth_alg selection: 0x1
1216148513.014261: WPA: using IEEE 802.11i/D3.0
1216148513.014377: WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
1216148513.014490: WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1216148513.014630: WPA: clearing AP RSN IE
1216148513.014739: WPA: using GTK TKIP
1216148513.014850: WPA: using PTK TKIP
1216148513.014962: WPA: using KEY_MGMT WPA-PSK
1216148513.015073: WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1216148513.015213: No keys have been configured - skip key clearing
1216148513.015322: wpa_driver_wext_set_drop_unencrypted
1216148513.015437: State: SCANNING -> ASSOCIATING
1216148513.015548: wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
1216148513.015659: WEXT: Operstate: linkmode=-1, operstate=5
1216148513.015807: wpa_driver_wext_associate
1216148513.017057: Setting authentication timeout: 10 sec 0 usec
1216148513.017973: EAPOL: External notification - EAP success=0
1216148513.018139: EAPOL: External notification - EAP fail=0
1216148513.018291: EAPOL: External notification - portControl=Auto
1216148513.018440: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1216148513.018563: Wireless event: cmd=0x8b06 len=8
1216148513.018680: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1216148513.018795: Wireless event: cmd=0x8b04 len=12
1216148513.018910: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1216148513.019024: Wireless event: cmd=0x8b1a len=15
1216148513.051662: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1216148513.052305: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1216148513.052463: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1216148513.052586: Wireless event: cmd=0x8c07 len=96
1216148513.052697: AssocReq IE wireless event - hexdump(len=88): 00 07 4e 45 54 47 45 41 52 01 08 02 04 0b 16 0c 18 30 48 32 04 12 24 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 dd 09 00 03 7f 01 01 00 0c ff 7f dd 1a 00 03 7f 03 01 00 00 00 00 14 6c 07 06 74 02 14 6c 07 06 74 64 00 2c 01 00 00
1216148513.052928: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1216148513.053046: Wireless event: cmd=0x8c08 len=35
1216148513.057852: AssocResp IE wireless event - hexdump(len=27): 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 09 00 03 7f 01 01 00 0c ff 7f
1216148513.058091: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1216148513.058314: Wireless event: cmd=0x8b15 len=20
1216148513.058433: Wireless event: new AP: 00:14:6c:07:06:74
1216148513.058551: Association info event
1216148513.058659: req_ies - hexdump(len=88): 00 07 4e 45 54 47 45 41 52 01 08 02 04 0b 16 0c 18 30 48 32 04 12 24 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 dd 09 00 03 7f 01 01 00 0c ff 7f dd 1a 00 03 7f 03 01 00 00 00 00 14 6c 07 06 74 02 14 6c 07 06 74 64 00 2c 01 00 00
1216148513.058882: resp_ies - hexdump(len=27): 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 09 00 03 7f 01 01 00 0c ff 7f
1216148513.059028: WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1216148513.059210: State: ASSOCIATING -> ASSOCIATED
1216148513.059327: wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
1216148513.059441: WEXT: Operstate: linkmode=-1, operstate=5
1216148513.059612: Associated to a new BSS: BSSID=00:14:6c:07:06:74
1216148513.059731: No keys have been configured - skip key clearing
1216148513.059853: Associated with 00:14:6c:07:06:74
1216148513.059963: WPA: Association event - clear replay counter
1216148513.060072: EAPOL: External notification - portEnabled=0
1216148513.060265: EAPOL: External notification - portValid=0
1216148513.060382: EAPOL: External notification - EAP success=0
1216148513.060494: EAPOL: External notification - portEnabled=1
1216148513.060603: EAPOL: SUPP_PAE entering state CONNECTING
1216148513.060710: EAPOL: SUPP_BE entering state IDLE
1216148513.060829: Setting authentication timeout: 10 sec 0 usec
1216148513.060950: Cancelling scan request
1216148513.061094: RX EAPOL from 00:14:6c:07:06:74
1216148513.061245: Setting authentication timeout: 10 sec 0 usec
1216148513.061375: IEEE 802.1X RX: version=1 type=3 length=95
1216148513.061492:   EAPOL-Key type=254
1216148513.061598:   key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
1216148513.061711:   key_length=32 key_data_length=0
1216148513.061818:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
1216148513.061936:   key_nonce - hexdump(len=32): c8 16 69 42 b2 c8 b0 20 ee d0 e1 43 62 c1 79 ec f4 88 0d 89 45 f5 10 b8 b7 66 96 5f 11 56 48 5d
1216148513.062118:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1216148513.063239:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1216148513.063394:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1216148513.063515:   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1216148513.063718: State: ASSOCIATED -> 4WAY_HANDSHAKE
1216148513.063840: WPA: RX message 1 of 4-Way Handshake from 00:14:6c:07:06:74 (ver=1)
1216148513.088022: WPA: Renewed SNonce - hexdump(len=32): 62 8f 09 a8 35 26 2f ce 27 c0 57 ba 4e 29 c1 5b f3 ae c6 70 74 5c e6 06 f3 6d a6 5b 45 8e 6d c3
1216148513.088333: WPA: PMK - hexdump(len=32): 62 d7 af e5 97 a0 9c 85 5f 14 dd 17 c2 23 48 b8 28 cf ad 70 06 3c f4 4a bd 43 2b 46 5a e5 c8 d3
1216148513.088390: WPA: PTK - hexdump(len=64): 88 b8 1d 38 ac 3c 6d 36 1b 69 e7 d2 c1 5b 03 9f 6d 1f 1c e1 bd 00 5b 59 23 12 bf 42 39 f1 79 e8 0a 11 32 c8 75 ed 12 a6 00 85 86 03 f2 4a 62 af b8 b3 c4 e5 60 d7 d3 7e c6 7a 84 c4 c8 db 9a 36
1216148513.088476: WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1216148513.088528: WPA: Sending EAPOL-Key 2/4
1216148513.088694: RX EAPOL from 00:14:6c:07:06:74
1216148513.088723: IEEE 802.1X RX: version=1 type=3 length=119
1216148513.088741:   EAPOL-Key type=254
1216148513.088756:   key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
1216148513.088780:   key_length=32 key_data_length=24
1216148513.088795:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
1216148513.088820:   key_nonce - hexdump(len=32): c8 16 69 42 b2 c8 b0 20 ee d0 e1 43 62 c1 79 ec f4 88 0d 89 45 f5 10 b8 b7 66 96 5f 11 56 48 5d
1216148513.088870:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1216148513.088904:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1216148513.088928:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1216148513.088953:   key_mic - hexdump(len=16): ad b6 2e 26 ab 8f 66 89 1d 50 77 15 4f d7 0b 00
1216148513.088999: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
1216148513.089016: WPA: Could not verify EAPOL-Key MIC - dropping packet
1216148513.268776: RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
1216148513.268828: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
l2_packet_receive - recvfrom: Network is down
1216148513.303615: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1216148513.303672: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1216148513.328236: CTRL-EVENT-TERMINATING - signal 15 received
1216148513.328280: Removing interface wlan0
1216148513.328288: State: 4WAY_HANDSHAKE -> DISCONNECTED
1216148513.328297: wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
1216148513.328306: WEXT: Operstate: linkmode=-1, operstate=5
1216148513.328344: wpa_driver_wext_deauthenticate
1216148513.329745: No keys have been configured - skip key clearing
1216148513.329804: EAPOL: External notification - portEnabled=0
1216148513.329812: EAPOL: SUPP_PAE entering state DISCONNECTED
1216148513.329818: EAPOL: SUPP_BE entering state INITIALIZE
1216148513.329830: EAPOL: External notification - portValid=0
1216148513.329838: wpa_driver_wext_set_wpa
1216148513.329860: wpa_driver_wext_set_drop_unencrypted
1216148513.329868: wpa_driver_wext_set_countermeasures
1216148513.329875: No keys have been configured - skip key clearing
1216148513.344536: Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
1216148513.344671: Cancelling scan request
1216148513.344682: Cancelling authentication timeout
1216148513.355991: WEXT: Operstate: linkmode=0, operstate=6
``````
taylor@taylor-laptop:~$ sudo ifconfig wlan0 up
``````
taylor@taylor-laptop:~$ sudo iwconfig wlan0 mode Managed
``````
taylor@taylor-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:dc:22:e9
Sending on   LPF/wlan0/00:18:4d:dc:22:e9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
receive_packet failed on wlan0: Network is down
Terminated
``````
taylor@taylor-laptop:~$ sudo dhclient3 wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:dc:22:e9
Sending on   LPF/wlan0/00:18:4d:dc:22:e9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
receive_packet failed on wlan0: Network is down
Terminated
```

---

### Post by pytheas22 on 2008-07-17
Thanks for all of that information.

It's doing the same thing for you that it was for the other user...it starts to connect but then drops out because it thinks that the passphrase is incorrect.  I'm not sure what's going on, but to track it down, would you mind posting your WPA passphrase and the name of your wireless network?  If you don't want to post the passphrase publicly (you could also private-message it to me), it's alright, but I think it would be helpful in figuring out what's going on here.

Also, I'm travelling now, so I may not be able to respond as quickly as I'd like.

---

### Post by NearlyALaugh on 2008-07-17
My wireless network, as you know, is NETGEAR. I'll PM you the passphrase.

Take your time -- you've certainly earned it! I'll be away from the computer for a while in the coming week.

---

### Post by pytheas22 on 2008-07-28
Sorry for the long silence, but I've got some good news.  Over in the [other thread]("http://ubuntuforums.org/showthread.php?t=853762&page=9") where someone else was trying to figure out the WPN111 and WPA2, after a month of trying, he's finally been able to connect!  We're not 100% certain what exactly made it possible, but try doing these things in order to get in the same situation as him:

1. First, let's clear out ndiswrapper so we can start with a clean slate (actually the best thing would be to reinstall the whole system if possible, but I'm not sure how feasible that is for you):
```

sudo apt-get remove --purge ndiswrapper*
```

2. then reinstall ndiswrapper (I'm assuming that you're still able to get a wired connection on the machine; if you can't, let me know):
```

sudo apt-get install ndiswrapper*
```

3. now get the Windows driver and install it into ndiswrapper as per the instructions at [http://ubuntuforums.org/showthread.php?t=414023](http://ubuntuforums.org/showthread.php?t=414023) 

4. install wicd, if it's not already, using the package from [http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0) 

5. change /etc/wpa_supplicant.conf to:
```

network={
**ssid="your network name in quotes"**
scan_ssid=1
proto=WPA RSN WPA2
key_mgmt=WPA-PSK
auth_alg=OPEN
pairwise=CCMP TKIP
group=CCMP TKIP
**psk="your password in quotes"**
}
```

6. now open wicd, and under the "Advanced Settings" tab, select WPA1/2 encryption and fill in your password in the appropriate field (here is a [screenshot]("http://ubuntuforums.org/showpost.php?p=5476364&postcount=88") of what it should look like).

7. click connect and maybe this will work!

If it doesn't, what is the output of:
```

cat /opt/wicd/encryption/configurations/*
```

---

### Post by itsjareds on 2008-07-28
I also converted my psk to hex in /etc/wpa_supplicant.conf, thats the way I've gotten it to work, but it might work ASCII too.

The psk in the wicd manager that I used was ASCII though.

---

### Post by NearlyALaugh on 2008-08-04
[quote="pytheas22"]Sorry for the long silence, but I've got some good news. Over in the other thread where someone else was trying to figure out the WPN111 and WPA2, after a month of trying, he's finally been able to connect! We're not 100% certain what exactly made it possible, but try doing these things in order to get in the same situation as him[/quote]I was about to apologize for my own long silence!

I'll try your suggestions. I have nothing on the laptop as yet, so I'll reinstall Ubuntu and proceed from there. Thanks!

---

### Post by Claudestephane on 2008-08-04
Having read through the Hardy 8.04 wireless woes, no one has described exactly my predicament. Initial WPA wifi setup worked but then after ~2 months of exclusively wired connectivity, trying wifi again failed to connect, except when tried with the unacceptable encryption disabled mode. Trying both 128 WEP and WPA failed to connect. In an effort to wipe the slate clean, the wifi network was deleted, and new one created with new name. The only way I could get the old one off drop down menu, was to change the SSID broadcast setting on my wireless router temporarily. Now correct wifi network name comes up but connection fails unless I disable security mode. Clearly unacceptable. Thank goodness for ethernet for the moment. Bright ideas welcome.

Claude

---

### Post by pytheas22 on 2008-08-04
> Having read through the Hardy 8.04 wireless woes, no one has described exactly my predicament. Initial WPA wifi setup worked but then after ~2 months of exclusively wired connectivity, trying wifi again failed to connect, except when tried with the unacceptable encryption disabled mode. Trying both 128 WEP and WPA failed to connect. In an effort to wipe the slate clean, the wifi network was deleted, and new one created with new name. The only way I could get the old one off drop down menu, was to change the SSID broadcast setting on my wireless router temporarily. Now correct wifi network name comes up but connection fails unless I disable security mode. Clearly unacceptable. Thank goodness for ethernet for the moment. Bright ideas welcome.

Claude

Claude,

Unless you're using the WPN111, you may want to start a new thread, since your problem probably has nothing to do with the topic of this one (if you do start a new thread, tell us the URL).

To figure out what's going on with your wifi, I would want to see this information:
```

lshw -C Network
lspci
lspci -n
iwlist scan
```

That would help troubleshoot it.

If you are using the WPN111, then please, say so--I will be very excited if you actually had it working reliably for several months.
> 
I'll try your suggestions. I have nothing on the laptop as yet, so I'll reinstall Ubuntu and proceed from there. Thanks! 

Looking forward to hear your results.  I would like to nail down what the deal is with the WPN111 and get a how-to written, because I found lots of people through Google who have had no end of trouble with it, but itsjareds is the only one I know of who ever managed to successfully connect (and even he still has issues, but at least he gets online, which is a major step forward).

---

### Post by NearlyALaugh on 2008-08-08
I reinstalled Ubuntu, but I'm not able to get a wired connection... it recognizes that it is hooked up to a network, but doesn't do anything. After disconnecting and reconnecting, it says "Requesting network address" or something like that.

I still have ndiswrapper-1.51.tar.tar and win-drivers.tar.gz on my portable hard drive, however... but I don't know how to install them. I've extracted both of the files to my desktop. The INSTALL file states this:```
Downloading
===========

Download the latest version of the ndiswrapper sources from here and extract it with the command

   tar zxvf ndiswrapper-version.tar.gz

this will create ndiswrapper-version directory. Change to that directory and run

   make uninstall
   make

Login as root and run
   make install
```I accomplished "make uninstall" and "make", but how do I do the last two lines? Alternatively, how do I install some other way?

Thanks!

I don't know why my wired connection won't work.

---

### Post by pytheas22 on 2008-08-08
> I don't know why my wired connection won't work.

Yeah, that's strange.  What is the output of:
```

lshw -C Network
lspci -nn | grep -i ethernet
```
> 
I accomplished "make uninstall" and "make", but how do I do the last two lines?

Simple: just run:
```

sudo make install
```

from within the same directory where you ran the first two commands.

> Alternatively, how do I install some other way?


If you can't get it to compile from source, ndiswrapper also comes on the Ubuntu live CD.  Enable the CD as a repository using the utility at System>Administration>Software Sources (look under the "Ubuntu Software" tab), then run the command:
```

sudo apt-get install ndiswrapper* ndisgtk
```

and it will install it for you.  It's slightly better in most respects to compile from source, though, so try that first.

---

### Post by NearlyALaugh on 2008-08-08
I installed ndiswrapper from CD using Synaptic Package Manager, and installed the driver afterwards. I installed Wicd successfully. After uninstalling and reinstalling the netwpn11 driver, the device started blinking. However, neither the Wicd Manager nor the Network Configuration utility show any available wireless networks.

I've restarted several times -- either using "Shut Down" or by pressing the power button when the system froze up -- and haven't had any positive results.

Once it shows a wireless network it'll be able to try step #6.

---

### Post by pytheas22 on 2008-08-09
> I installed ndiswrapper from CD using Synaptic Package Manager, and installed the driver afterwards. I installed Wicd successfully. After uninstalling and reinstalling the netwpn11 driver, the device started blinking. However, neither the Wicd Manager nor the Network Configuration utility show any available wireless networks.

Sorry it's still not working well.  What is the output of:
```

iwlist scan
lshw -C Network
ndiswrapper -l
lsmod | grep ndiswrapper
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
```

---

### Post by NearlyALaugh on 2008-08-11
[quote="pytheas22"]Sorry it's still not working well.[/quote]I've got plenty of time to work on it. The freezing problem has nothing to do with our experimenting here -- I've just got a really slow laptop. Anyways, I've got plenty of time for experimenting. It'd be nice if people in the future didn't have to deal with this... though somehow I think the smart thing to do is to just dump WPN111 and find a new wireless card!

Thank you for the continuing support. Unfortunately, I will be offline for about a week starting tomorrow, but when I get back we can pick up where we left off and try out any fresh ideas.

The output of the commands is as follows:```
taylor@taylor-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

taylor@taylor-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 08:00:46:6f:7d:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:dc:22:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.52+NETGEAR,09/26/2005,1.5.0.21 multicast=yes wireless=IEEE 802.11g
taylor@taylor-laptop:~$ ndiswrapper -l
netwpn11 : driver installed
	device (1385:5F01) present
taylor@taylor-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  3 ndiswrapper,uhci_hcd
taylor@taylor-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for taylor: 
taylor@taylor-laptop:~$ dmesg | grep -e ndis -e wlan
[   38.322742] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   38.866610] ndiswrapper: driver netwpn11 (NETGEAR,09/26/2005,1.5.0.2102) loaded
[   38.868579] ndiswrapper (ZwQueryValueKey:2359): not fully implemented (yet)
[   39.875648] wlan0: ethernet device 00:18:4d:dc:22:e9 using NDIS driver: netwpn11, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1385:5F01.F.conf
[   39.936754] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   39.936859] usbcore: registered new interface driver ndiswrapper
```It's interesting that we got hung up at this point this time, for previously I was at least seeing wireless (and also wired) networks. The "*-network DISABLED" message looks like it might have something to do with it, though.

And thus the topic marches on...

Considering it (embarrassingly) started with me trying to get wireless out of a wired ethernet card, I'm somewhat gratified that we're actually working on a problem of substance.

---

### Post by pytheas22 on 2008-08-11
hmmm, strange stuff.  I'm not sure what the "Failed to read scan data : Resource temporarily unavailable" and "NETWORK: disabled" stuff is all about.  Perhaps the devices are "down."  Do these commands cause the above-mentioned error messages to go away:
```

sudo ifconfig eth0 up
sudo ifconfig wlan0 up
```

And by the way, you still can't connect with ethernet on this installation of Ubuntu, right?  It's weird because everything looks right, for both the ethernet and wireless.  There are no physical switches or something that you need to flip to enable the networking, are there?

Also, check to see what the contents of /etc/network/interfaces are.  They should look like:
```

auto lo
iface lo inet loopback
```

If there's anything else in that file, could you please post it here?

If the ifconfig commands above don't help and /etc/network/interfaces looks normal, you might want to try reinstalling Ubuntu.  Although that seems like a drastic step, I'm not sure where else to look.  But maybe over the course of the week I'll think of something; if so, I'll add to this post.

---

### Post by NearlyALaugh on 2008-08-20
The contents of **/etc/network/interfaces** are identical to the code you posted.

I tried to connect through my ethernet cable -- it prompted me for a network ID, which is new, but all I get is a "Connecting" message until it gives up.

Running **sudo ifconfig eth0 up** and **sudo ifconfig wlan0 up** made the "network DISABLED" message disappear.

Correcting several stupid problems fixed the "Failed to read scan data : Resource temporarily unavailable" message. "WPA Supplicant Driver" and "Wireless Interface" were not correctly set in Wicd. Setting them to "ndiswrapper" and "wlan0", respectively, allowed me to view my wireless network. That, in turn, allowed me to set the encryption and password.

Now both commands read thus:```
taylor@taylor-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:07:06:74
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:500 kb/s; 500 kb/s; 1 Mb/s; 2 Mb/s; 3 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

taylor@taylor-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 08:00:46:6f:7d:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:18:4d:dc:22:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.52+NETGEAR,09/26/2005,1.5.0.21 multicast=yes wireless=IEEE 802.11g
```
Wicd still cannot connect to my wireless network, however. As is the case for eth0, I get a "Connecting" message until it gives up.

---

### Post by pytheas22 on 2008-08-20
First of all, what is the MAC address being given to eth0?  You can find out with the ifconfig command; the output will look like this (MAC is in bold):
```

eth0      Link encap:Ethernet  HWaddr **00:19:21:85:0d:87**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe800
```

Also, does this get you an IP on the wired connection:

```
sudo rmmod 8139too
sudo modprobe 8139cp
sudo ifconfig eth0 up
sudo dhclient eth0
```

If not, what about:
```

sudo rmmod 8139cp
sudo modprobe 8139too
sudo ifconfig eth0 up
sudo ifconfig eth0 hw ether 01:23:45:67:89:01
sudo dhclient eth0
```

I don't know about the wireless.  The guy in the other thread who had managed to connect had to reinstall and can't figure it out again...unfortunately it was never concretely clear in the first place what exactly made it possible for him to connect.  But let's first get your ethernet up, since we know that's supposed to work, and go from there, since this will all be easier once you can get online in Ubuntu.

---

### Post by NearlyALaugh on 2008-08-24
The address is given as 08:00:46:6f:7d:1d.
```
taylor@taylor-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:6f:7d:1d  
          inet6 addr: fe80::a00:46ff:fe6f:7d1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116752 (114.0 KB)  TX bytes:5049 (4.9 KB)
          Interrupt:10 Base address:0x1800 

eth0:avahi Link encap:Ethernet  HWaddr 08:00:46:6f:7d:1d  
          inet addr:169.254.4.95  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:147900 (144.4 KB)  TX bytes:147900 (144.4 KB)
```

```
taylor@taylor-laptop:~$ sudo rmmod 8139cp
[sudo] password for taylor: 
taylor@taylor-laptop:~$ sudo modprobe 8139too
taylor@taylor-laptop:~$ sudo ifconfig eth0 up
taylor@taylor-laptop:~$ sudo ifconfig eth0 hw ether 08:00:46:6f:7d:1d
SIOCSIFHWADDR: Device or resource busy - you may need to down the interface
taylor@taylor-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/08:00:46:6f:7d:1d
Sending on   LPF/eth0/08:00:46:6f:7d:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```
taylor@taylor-laptop:~$ sudo rmmod 8139too
taylor@taylor-laptop:~$ sudo modprobe 8139cp
taylor@taylor-laptop:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
taylor@taylor-laptop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 5653
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```
Neither of the codes seemed to work.

---

### Post by pytheas22 on 2008-08-24
I'm not sure if it's relevant, but this line from your ifconfig stands out to me:

```
inet6 addr: fe80::a00:46ff:fe6f:7d1d/64 Scope:Link
```

I wonder if it thinks it's supposed to be using ipv6 for some reason.  You can disable ipv6 with:
```

echo 'blacklist ipv6' | sudo tee -a /etc/modprobe.d/blacklist
```

It should already be blacklisted so I really doubt that it's related to the problem, but it can't hurt to try.

Also, the other guy with the WPN111 wrote up succinct instructions on exactly what he did to make his wireless work (he had to do a reinstall, so now he has a better idea of which steps got him up and running).  You may want to take a look [there]("http://ubuntuforums.org/showpost.php?p=5648752&postcount=127").

---

### Post by NearlyALaugh on 2008-08-28
I tried your suggestion, and then I tried itsjared's steps without reinstalling. No luck, unfortunately. I will reinstall, if you have no other suggestions, though nothing about those steps seems different from things I've tried.

The farthest I got was a "None: Obtaining IP Address" message.

The laptop *is* pretty slow -- could that have anything to do with it?

---

### Post by pytheas22 on 2008-09-01
Sorry for the slow response; I've been moving.

The laptop's being slow shouldn't really prevent it from getting online, so I'm not sure what's going on there.  You may want to try reinstalling, I guess, and then following itsjared's tutorial--he wrote a more streamlined one at [http://ubuntuforums.org/showthread.php?p=5670733](http://ubuntuforums.org/showthread.php?p=5670733)

I also wonder if perhaps your hardware is just flaky.  The things that you've gone through are very strange: the system seemed completely unable to detect the PCMCIA card; your ethernet used to work and now doesn't; you can't connect with your wireless card even though we know that the same card works for others.  You could always put Windows on the machine (temporarily!) just to see if there are weird problems there as well.

---

### Post by NearlyALaugh on 2008-09-01
The flaky theory might well be true -- it's a pretty old laptop. All I know is that it has run wireless on Windows without too much of a hassle. Of course, then it was running on the Microsoft card.

Nonetheless, I suppose I'll reinstall.

Thanks for the continuing support!

---

### Post by NearlyALaugh on 2008-11-17
**_Follow-up:_**

Thank you, **pytheas22** and others for your support; I'm sorry I didn't get back sooner. I just thought I'd post a follow-up about this.

My conclusion is that getting Netgear WPN111 to work on Ubuntu with a WPA/WPA2-encrypted network is not worth the hassle. I made no further tests on the laptop, but the problem was exactly the same on a fresh install of Ubuntu on my (considerably more capable) desktop computer. Following the steps in [itsjared's tutorial](http://ubuntuforums.org/showthread.php?p=5670733) exactly, the device is recognized and able to view wireless networks, but unable to connect to either of the two WPA/WPA2 networks that I tested.

My desktop running Ubuntu is connected via ethernet, and I plan to reinstall Windows XP on the laptop now that I have recovered the formerly misplaced install disks.

Thanks again, and best wishes.

---

### Post by pytheas22 on 2008-11-17
Thanks for letting us know how you ultimately got on.  I agree that the WPN111 probably just isn't worth the hassle.  Even after itsjareds got his working (for reasons that still remain foggy), he had issues with the device crashing arbitrarily.  Plus it's impossible to use it on 64-bit systems, since there are no 64-bit Windows drivers available, hence no 64-bit ndiswrapper.

So to anyone else who has a WPN111 and wants to use WPA and/or 64-bit Linux: make your life easier and spend $20 on a USB stick that will [work out-of-the-box in Ubuntu]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

---

