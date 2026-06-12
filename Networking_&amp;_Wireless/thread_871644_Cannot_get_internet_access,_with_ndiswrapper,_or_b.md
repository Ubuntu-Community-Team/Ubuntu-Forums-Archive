---
title: "Cannot get internet access, with ndiswrapper, or b43 legacy, or as is"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by xandr55 on 2008-07-27
Hello again all,
I am driving myself a little bit crazy trying to get the wireless up and running. I am very new to this obviously... I feel somewhat like I have tried everything. It is a recent install on an Inspiron 5100, with a Dell Wireless 1470 Dual-Band WLAN miniPCI Card which has BCM4309 chipset. First off here are results from the following commands:
lspci

```
sherry@sherry-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
sherry@sherry-laptop:~$

```
ifconfig

```
sherry@sherry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:ab:16:0b  
          inet addr:192.168.0.236  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feab:160b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12973650 (12.3 MB)  TX bytes:419680 (409.8 KB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87100 (85.0 KB)  TX bytes:87100 (85.0 KB)


```

iwconfig

```
sherry@sherry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```


lsmod

```
sherry@sherry-laptop:~$ lsmod
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
ipv6                  267780  8 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
dcdbas                  9504  0 
evdev                  13056  8 
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
serio_raw               7940  0 
snd_seq_midi            9376  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
psmouse                40336  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ndiswrapper           193436  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
battery                14212  0 
ac                      6916  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              25492  1 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
ata_piix               19588  3 
ohci1394               33584  0 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
b44                    28432  0 
ssb                    34308  1 b44
mii                     6400  1 b44
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  5 sbp2,sg,sd_mod,sr_mod,libata
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
sherry@sherry-laptop:~$ 
```

Initially the wireless connection was shown in the network manager, and at some point it disappeared. Since then I have tried to install drivers via the ndiswrapper. I finally succeeded just at installing ndiswrapper, and I also opted for the graphical interface. When I installed the driver how ever, an error would pop up saying no hardware found, but within the graphical interface under the driver that was listed it would say hardware present and it would succesfully show up in terminal as well to the prompt ndiswrapper -l. Eventually I found this site [HTML]http://linuxwireless.org/en/users/Drivers/b43[/HTML]
and tried to go through their instructions, and although it seemed successful nothing seems to have changed, and it still does not show up in network manager, as a possible connection. Here is what happened when I tried to follow their instructions, because I may have done them very incorrectly:
```

sherry@sherry-laptop:~$ export FIRMWARE_INSTALL_DIR="/lib/firmware"
sherry@sherry-laptop:~$ wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
--04:50:00--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      271.06K/s             

04:50:03 (270.24 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

sherry@sherry-laptop:~$ sudo ./b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR"
[sudo] password for sherry: 
sudo: ./b43-fwcutter-011/b43-fwcutter: command not found
sherry@sherry-laptop:~$ sudo ./b43-fwcutter/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR"
sudo: ./b43-fwcutter/b43-fwcutter: command not found
sherry@sherry-laptop:~$ sudo ./b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR"
sudo: ./b43-fwcutter-011/b43-fwcutter: command not found
sherry@sherry-laptop:~$ sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR"
b43-fwcutter version 011

A tool to extract firmware for a Broadcom 43xx device
from a proprietary Broadcom 43xx device driver file.

Usage: b43-fwcutter [OPTION] [proprietary-driver-file]
  --unsupported         Allow working on extractable but unsupported drivers
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -v|--version          Print b43-fwcutter version
  -h|--help             Print this help

Example: b43-fwcutter -w /lib/firmware wl_apsta.o
         to extract the firmware blobs from wl_apsta.o and store
         the resulting firmware in /lib/firmware
sherry@sherry-laptop:~$ b43-fwcutter -w /lib/firmware wl_apsta.o
Cannot open input file wl_apsta.o
sherry@sherry-laptop:~$ b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.0
Cannot open input file wl_apsta-3.130.20.0.0
sherry@sherry-laptop:~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
sherry@sherry-laptop:~$ wl_apsta-3.130.20.0.o
bash: wl_apsta-3.130.20.0.o: command not found
sherry@sherry-laptop:~$ 
```

any ideas would be greatly appreciated, 
thanks again for your help,
Xander

---

### Post by xandr55 on 2008-07-27
SO, when I turned the computer on today the wireless network was back..... not sure where it came from or why, but it is there. When I try to configure it however, it makes the motion of the two dots, and the swirly but never connects to the network, and does not seem to find other networks.........:confused:

---

### Post by mfrag on 2008-07-29
Hey there.  I feel for you.  I just spent the past 2 days getting my wireless up and running.  I also have a broadcom card, but it is a 4310.  I followed the instructions found at 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

You might try step 2b according to the remarks from others.

I'm also new at this wireless thing, but I simply cut and pasted all the steps while connected to the net through a landline and now wireless is working fine.  I had to do the Hardy bugfix and also needed to add the steps to make it permanent.  

I should mention that I went through these steps twice.  The first time I didn't get things up and running.  I then stumbled around reading posts and trying different things.  Finally I decided to reinstall and go back to trying the ndiswrapper since so many people have gotten it to work.  One thing I did different this time was remove or turn of the wl module which was running. I ran 

sudo rmmod wl

to do this.  Then I followed the steps above. 


Good luck.

---

### Post by wvn on 2008-09-08
Hi all. Please follow the instructions below.

_Make sure FIRST that you installed ndiswrapper from the latest live Ubuntu CD_
------------------------------------------------------------------
> echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local

sudo su
nano /etc/modprobe.d/blacklist

and add these lines
# BroadCom wireless ndiswrapper
blacklist ssb
blacklist b43
blacklist bcm43xx

[B]
Next step is to set ndiswrapper to be loaded at boot:[/B]

nano /etc/modules

**and add ndiswrapper to the bottom of that list.**


**Now go to the wireless windows drivers GUI that you previously installed and choose the driver for your card and press OK to install. Then exit the gui.**


**Then again in terminal:**

sudo su
ndiswrapper -l
ndiswrapper -m



Reboot and you are done!

---

### Post by wgroth2 on 2008-10-13
Hi folks,
   One big problem, the driver files is no longer at [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Does anyone know where I could get this now?

Also, its sounds from the post like all i have to do is install ndiswrapper and then install the new driver, right?

---

### Post by Ayuthia on 2008-10-13
> **wgroth2 said:**
> Hi folks,
   One big problem, the driver files is no longer at [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Does anyone know where I could get this now?

Also, its sounds from the post like all i have to do is install ndiswrapper and then install the new driver, right?

I was just able to download the file from that link.  However, this is the firmware for the b43legacy driver and not for ndiswrapper.  If you need the Windows driver for ndiswrapper, you need to go to:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

