---
title: "Help! New user, comletely confused. (hardy heron)"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by familyguy1 on 2008-08-03
Ok, so I installed 8.04 on an old desktop pc yesterday. Went fine, everything was working. I tried to get my linsys WUSB11 v 2.8 working (this is an external usb wireless network adapter). I've looked at seemingly all of the tutorials on how to get this thing running, but to no avail. I really do not know much about linux, but I am very interested in learning, however this is difficult with no internet access! 

[[IMG]http://content.imagesocket.com/thumbs/DSC020917f6.JPG[/IMG]](http://imagesocket.com/view/DSC020917f6.JPG) 

if the above image is too blurry, the boxed text says:
"/netusb : driver installed"
"device (1915:223) present (alternate driver: at76_usb)"

[[IMG]http://content.imagesocket.com/thumbs/DSC02092450.JPG[/IMG]](http://imagesocket.com/view/DSC02092450.JPG) 

In this picture, the wireless connection doesnt even exist! its normally above "wired connection", right?:confused:

[[IMG]http://content.imagesocket.com/thumbs/DSC0209312c.JPG[/IMG]](http://imagesocket.com/view/DSC0209312c.JPG) 

I have installed ndswrapper, and installed the .inf file that came on the installation cd, and the above pictures are what has resulted. 

Again, here is says the hardware is present, but if it is, how do I connect to the internet if the wireless connection isn't even there in the network settings? Has it moved somewhere else because the wireless connection has been set up using the linksys drivers?

Also, where can I get this "at76_usb" alternate driver if this one doesn't work? 

If there are no easy solutions, I am willing to spend some money on a usb wireless adapter that would work *out of the box*. Does anyone know of one that isn't too pricey? 

from this page:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

It looks like the WUSB54GC  would work, but I have found some places on the internet of people complaining it doesn't! Again, if anyone knows if this, or any other external usb network adapters will work out of the box (this means without any setup, right?) I would greatly appreciate it. 

Also, any help with my current adapter (WUSB11 v. 2.8)is also appreciated.

And sorry for my lack of technical linux know-how, I just started using it yesterday!:)

---

### Post by cybrsaylr on 2008-08-03
Just hang in there. I had the same problem when first using Ubuntu and had to stay hardwired to get on the net till someone gave me the solution to get wireless working. Now my wireless flys. The problem may be there are so many linux distros and versions of them same distros out there that all hook up a bit different. This forum is the place for help. It solved my wireless problems so far.

---

### Post by familyguy1 on 2008-08-03
> **cybrsaylr said:**
> Just hang in there. I had the same problem when first using Ubuntu and had to stay hardwired to get on the net till someone gave me the solution to get wireless working. Now my wireless flys. The problem may be there are so many linux distros and versions of them same distros out there that all hook up a bit different. This forum is the place for help. It solved my wireless problems so far.

thanks,
I'm hoping I'll be able to hardwire it soon, but that's not in the near future, so I'd like to be able to get this wireless working, especially because I can't download any new apps or anything until it establishes a connection.

---

### Post by bwainscott on 2008-08-03
with the wireless device plugged in, please provide a paste of your lspci and lsmod commands so we can see what is loaded.

---

### Post by familyguy1 on 2008-08-03
> **bwainscott said:**
> with the wireless device plugged in, please provide a paste of your lspci and lsmod commands so we can see what is loaded.

you got it:

lspci:
> saam@saam-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02) 
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02) 
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02) 
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02) 
01:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08) 
01:0a.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
01:0a.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
01:0a.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
01:0a.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) 
01:0b.0 Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01) 
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) 


lsmod
> saam@saam-desktop:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1           4992  1  
nls_cp437               6656  1  
vfat                   14464  1  
fat                    54556  1 vfat 
usb_storage            73664  1  
libusual               19108  1 usb_storage 
ipv6                  267780  8  
rfcomm                 41744  2  
l2cap                  25728  13 rfcomm 
bluetooth              61156  4 rfcomm,l2cap 
ppdev                  10372  0  
speedstep_lib           6532  0  
cpufreq_conservative     8712  0  
cpufreq_ondemand        9740  0  
cpufreq_powersave       2688  0  
cpufreq_userspace       5284  0  
cpufreq_stats           7104  0  
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats 
video                  19856  0  
output                  4736  1 video 
sbs                    15112  0  
sbshc                   7680  1 sbs 
container               5632  0  
dock                   11280  0  
battery                14212  0  
iptable_filter          3840  0  
ip_tables              14820  1 iptable_filter 
x_tables               16132  1 ip_tables 
ac                      6916  0  
lp                     12324  0  
usbhid                 31872  0  
hid                    38784  1 usbhid 
ndiswrapper           192920  0  
snd_ens1371            27168  3  
gameport               16008  1 snd_ens1371 
snd_ac97_codec        101028  1 snd_ens1371 
ac97_bus                3072  1 snd_ac97_codec 
snd_pcm_oss            42144  0  
snd_mixer_oss          17920  1 snd_pcm_oss 
snd_pcm                78596  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss 
evdev                  13056  3  
parport_pc             36260  1  
parport                37832  3 ppdev,lp,parport_pc 
snd_seq_dummy           4868  0  
snd_seq_oss            35584  0  
snd_seq_midi            9376  0  
snd_rawmidi            25760  2 snd_ens1371,snd_seq_midi 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              24836  2 snd_pcm,snd_seq 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    56996  17 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               8800  1 snd 
snd_page_alloc         11400  1 snd_pcm 
i2c_core               24832  0  
button                  9232  0  
pcspkr                  4224  0  
iTCO_wdt               13092  0  
iTCO_vendor_support     4868  1 iTCO_wdt 
intel_agp              25492  1  
shpchp                 34452  0  
agpgart                34760  1 intel_agp 
pci_hotplug            30880  1 shpchp 
ext3                  136712  1  
jbd                    48404  1 ext3 
mbcache                 9600  1 ext3 
sg                     36880  0  
sr_mod                 17956  0  
cdrom                  37408  1 sr_mod 
sd_mod                 30720  5  
pata_acpi               8320  0  
8139too                27520  0  
ata_generic             8324  0  
floppy                 59588  0  
uhci_hcd               27024  0  
ehci_hcd               37900  0  
ohci_hcd               25348  0  
8139cp                 24704  0  
mii                     6400  2 8139too,8139cp 
usbcore               146028  8 usb_storage,libusual,usbhid,ndiswrapper,uhci_hcd,ehci_hcd,ohci_hcd 
ata_piix               19588  2  
libata                159344  3 pata_acpi,ata_generic,ata_piix 
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata 
thermal                16796  0  
processor              36872  1 thermal 
fan                     5636  0  
fbcon                  42912  0  
tileblit                3456  1 fbcon 
font                    9472  1 fbcon 
bitblit                 6784  1 fbcon 
softcursor              3072  1 bitblit 
fuse                   50580  3  



thank you *so* much for the help

---

### Post by Tripp_mongo on 2008-08-04
I just installed 8.04 today, and I too am having the same problem.  I did notice a few things though.  If I boot with the Linksys wusb11 v. 2.8 attached, then I have no recognition of a wireless device.  If I boot, enter the X Server, and then attach the device, wait about 10 seconds, then a left click on the network icon on the upper panel gives me a list of wireless networks and their signal strengths.  The problem that I am now having deals with bridging the connection.  

It worked once for about 10 seconds as it allowed me to visit yahoo, but then I tried another site, and I could not get it to load.  The network icon switched a couple of times from wireless connected to no connection.  I have tried rebooting the system many times since.  I even turned off all security on my access point including MAC filtering, but I have not been able to duplicate the connection.  Any ideas?

---

### Post by drzolo on 2008-08-04
let see your output of lsusb,
It might have something usefull.

you can get that at76_usb at 
[http://at76c503a.berlios.de/](http://at76c503a.berlios.de/)

Make sure you read the readme and any other installation instructions

---

### Post by Tripp_mongo on 2008-08-04
Familyguy, please try like I did by attaching the device after you have booted, and see if you can get a list of routers/access points in the area.  Left click on the network icon; if you get no results, then right click on it to see if wireless is enabled.  

There seems to be a conflict for me as my keyboard hangs when the device is attached and activated. If you cannot get to where I am, then I shall start a new post.  If you get the same results, then we are probably having the same problem.

Oddly enough, this Linksys WUSB11 v. 2.8 did work with older versions of Ubuntu and the old kernel.

---

### Post by familyguy1 on 2008-08-04
here is my lsusb:
> saam@saam-desktop:~$ lsusb 
Bus 006 Device 001: ID 0000:0000   
Bus 005 Device 003: ID 1915:2233   
Bus 005 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse 
Bus 005 Device 001: ID 0000:0000   
Bus 004 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   


do you guys think its worth downloading at76_usb now or waiting to see if this setup will work?


> Familyguy, please try like I did by attaching the device after you have booted, and see if you can get a list of routers/access points in the area. Left click on the network icon; if you get no results, then right click on it to see if wireless is enabled.

sorry, I tried that but it gave me nothing when i did that. Upon left click on the network icon it gave me 2 options: wired network (which was greyed out)and manual configuration. When I right click it, it comes up with: Enable networking (which is checked), Connection information (greyed out), edit wireless networks, and About.

Can you post a link to your thread, I can probably get some info there as well. 
And again, thanks everybody for looking/helping.

---

### Post by Tripp_mongo on 2008-08-04
Familyguy, here is the link to my post.

[http://ubuntuforums.org/showthread.php?p=5524269#post5524269](http://ubuntuforums.org/showthread.php?p=5524269#post5524269)

I am sure that we shall both have our adapters working soon.  There are some really awesome people at this forum.

---

### Post by familyguy1 on 2008-08-04
> **Tripp_mongo said:**
> Familyguy, here is the link to my post.

[http://ubuntuforums.org/showthread.php?p=5524269#post5524269](http://ubuntuforums.org/showthread.php?p=5524269#post5524269)

I am sure that we shall both have our adapters working soon.  **There are some really awesome people at this forum.**

too true


Update to everyone:
I found another adapter in my basement that may also work. Its a belkin F5D7050. 

new lsusb for the belkin
> saam@saam-desktop:~$ lsusb 
Bus 006 Device 007: ID 12f7:1e23   
Bus 006 Device 006: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi 
Bus 006 Device 001: ID 0000:0000   
Bus 005 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse 
Bus 005 Device 001: ID 0000:0000   
Bus 004 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   


I have gone through ndswrapper with no success (for the belkin), however, I do get my wireless network to show up. Once i type in my wep key, it simply thinks for 30 seconds or so and then returns to the "wireless network key required" box. 

here are some pictures (sorry if they are blurry)
[[IMG]http://content.imagesocket.com/thumbs/DSC020940bd.JPG[/IMG]](http://imagesocket.com/view/DSC020940bd.JPG) 

[[IMG]http://content.imagesocket.com/thumbs/DSC02097d0c.JPG[/IMG]](http://imagesocket.com/view/DSC02097d0c.JPG) 

all help for the old linksys or this belkin is HUGELY appreciated
thanks!:)

---

