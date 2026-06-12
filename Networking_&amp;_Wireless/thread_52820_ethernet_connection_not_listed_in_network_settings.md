---
title: "ethernet connection not listed in network settings"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by nighttime on 2005-07-29
I was told I had to activate the ethernet connection from network settings in order to access the internet, but there's only a 'modem connection' listed, and there's no 'add' button in the interface to add a new connection.

help?

---

### Post by skyboy on 2005-07-29
can you copy paste the result of this command in a console
$ifconfig

and copy paste the file /etc/network/interfaces

---

### Post by nighttime on 2005-07-29
ok, theis is the result of iconfig:

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         Rx packets:1176 errors:0 dropped:0 overruns:0 frame:0
         TX packets:1176 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:100535 (98.1 KiB)  TX bytes: 100535 (98.1 KiB)

And fileetc/network/interfaces contains:

# This file describes the network interfaces available on your system.
# and how to activate them. For more information, see interfaces (5).

# The loopback network interface auto lo
iface lo inet loopback

---

### Post by heimo on 2005-07-29
Seems that no network card is detected or no correct kernel module was loaded. Do you know what network interface card (nic) is in your computer? Could you send output of command lspci?

EDIT: Oh, and output of lsmod could help too.

---

### Post by nighttime on 2005-07-29
Im runnung ubuntu in another computer, and it doesn't seem to be able to write to a floppy, see, I wanna take the files to this computer so I can paste them here but I cant... I insert the floppy in the ubuntu computer and I try writing files to it and all it does is say "no space left"...

Also, the slot where you plug the cable that comes out of the modem, the network card slot, it has a LED right? well, mine has an orange LED and it's allways on, does this mean it's messed up or something?

---

### Post by heimo on 2005-07-29
Network card or the integrated network card, has a RJ45-connector ( a bit wider, but looks like phone connector RJ11).
[http://www.kelley.iu.edu/itlabs/2004_Lab_Manuals/bonus/physicalCrossoverVsStraight/PhysicalLayer.html](http://www.kelley.iu.edu/itlabs/2004_Lab_Manuals/bonus/physicalCrossoverVsStraight/PhysicalLayer.html)

Cards have typically couple leds, green ones to indicate connection speed 10/100Mbps and orange one, which is activity led. It should not be lit if cable's not connected and when there's no traffic. When everyhing is ok, it blinks when data is transferred. However, there may be other type of cards - this is the most typical I've seen.

Run lspci and check for lines with anything to do with network / nic. That line is handy to recognize which card is installed. If it's broken, you probably don't see any line for your card. If you can find which card it is, then we need to load corresponding driver (in Linux world, this is most of the time also kernel module, however kernel module is not always device driver). 

Modules reside under /lib/modules/, where you can find structure for all kinds of stuff, video, audio, graphics and so on. Loading modules is done with modprobe - usually something like *modprobe 3c59x* (for some 3Com card).

If module loads successfully, you won't get any errors and running ifconfig again should show a new interface, eth0 (your first ethernet device).

Hopefully this gets you closer to solution.

BTW, skyboy - sorry if I stepped on your toes here, feel free to jump back. :) Just trying to help out.

---

### Post by skyboy on 2005-07-29
heimo, 
Don't worry you were faster and it's good ! I wouldn't have done better than you on that one :)
BTW, where from finland are you ? mä oon tamperella :)

---

### Post by nighttime on 2005-07-29
Ok, so there's nothing with network / nic in lspci, BUT I was finally able to write the output of lsmod to a floppy so here it is:

Module                  Size  Used by
nls_cp437               5888  1 
msdos                   8320  1 
fat                    37792  1 msdos
ipv6                  229504  6 
proc_intf               4100  0 
freq_table              4100  0 
cpufreq_userspace       4572  0 
cpufreq_ondemand        6172  0 
cpufreq_powersave       1920  0 
video                  16260  0 
sony_acpi               6280  0 
pcc_acpi               11264  0 
button                  6800  0 
battery                10244  0 
container               4608  0 
ac                      4996  0 
snd_via82xx            25248  2 
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  1 
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
i2c_viapro              7436  0 
i2c_core               21264  1 i2c_viapro
uhci_hcd               30224  0 
usbcore               107384  2 uhci_hcd
pci_hotplug            30512  0 
via_agp                 9216  1 
agpgart                31784  1 via_agp
floppy                 54864  1 
pcspkr                  3816  0 
rtc                    12216  0 
md                     43856  0 
dm_mod                 53116  1 
capability              5000  0 
commoncap               7808  1 capability
tsdev                   7488  0 
evdev                   9088  0 
psmouse                19336  0 
mousedev               11160  1 
parport_pc             34372  1 
lp                     10792  0 
parport                33480  2 parport_pc,lp
ide_cd                 38532  0 
cdrom                  36508  1 ide_cd
ext3                  120968  1 
jbd                    54168  1 ext3
ide_generic             1664  0 
via82cxxx              12956  1 
ide_disk               18176  3 
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  701 
thermal                13576  0 
processor              22708  1 thermal
fan                     4612  0 
fbcon                  34048  0 
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

what can you tell me?

---

### Post by skyboy on 2005-07-29
we can say that you don't seem to have any ethernet card in your laptop or at least that it isn't recognised. What is weird, is that the command lspci doesnt return anything to you !! try again maybe ... and check something like "ethernet controller"
What is the type of network card you have ??

---

### Post by nighttime on 2005-07-29
I have no idea what kind of network card I have... I opened the computer up and I remember the connector was attatched to the motherboard, like it was part of it... anyway, there were only a few numbers on the side of the connector: p35-121-16b9, I looked them up in google but they don't seem to be the name of the model or anything... I was wondering... is it possible that I don't have a network card at all? I mean, the slot is there, I can connect a modem to it, but does this necessarily mean there is a network card?

oh, and it's not a laptop

---

### Post by skyboy on 2005-07-30
> I mean, the slot is there, I can connect a modem to it, but does this necessarily mean there is a network card?

I'm a bit confised now !! are you try to connect a modem to the ethernet network card ?? because modem and network card are totally different !!!  Network card is for ethernet and modem for (xDLS, v56 ...)
Sor be sure what you want to connect and where !

---

### Post by heimo on 2005-07-30
I second Skyboy. Do you know what your internet connection is? Is it cable, ADSL or dial-up? Have you used it earlier? Do you have network cable (not phone cable) which connects to the back of your computer? It *is* possible to physicly connect RJ11 (phone cable) to network connector (RJ45), but this is most probably not what you want to do.

Those integrated cards which I've seen, have two leds, green and orange and at least on my computer the orange one is lit if the cable is connected, but blinks a bit when there's network traffic. Green one stays lit when cable is connected - both are unlit when cable is unconnected.

skyboy: I live about 150 kilometers south from you.

---

### Post by nighttime on 2005-07-31
I connect through cable.

I don't know the exact technical terms but this is how it is: I connect a tvcable-like cable to a box (the cable modem, that's what it says on the front of the box) and then from this modem comes out a cable wich I connect to the network card, it's a connector just like the ones you showed me in a past reply.

And it works, at least on this computer... I just can't get it to work in my other computer, the one with Ubuntu... come to think about it, I couldn't make it work when the same computer had windows2000... hmm... maybe I should get some real-world 3D help or something...

---

### Post by heimo on 2005-07-31
This is a long shot. From the lsmod list I can see that your system is based on Via chipset, and it could use via_rhine module for integrated ethernet. Or if it's a quite new computer, it could use via_velocity (that's for 1Gbps network card).

If I were you, I would try:
 ```
sudo modprobe via_rhine
ifconfig eth0

```

Please post all the output of those commands, and if the first one gives error messages, also try modprobe via_velocity (I'm quite sure it's not this one, but it doesn't cost much to try).

I'd like to clear one thing - on the computer you have Ubuntu, do you have exactly same kind of connector for the cable that comes from the cable modem? You can physicly connect the same cable that goes to your Windows machine, to this machine that we here are trying to get working? Do you know the manufacturer and model of this computer?

Thanks!

---

### Post by heimo on 2005-07-31
[QUOTE=nighttime]Ok, so there's nothing with network / nic in lspci, BUT I was finally able to write the output of lsmod to a floppy so here it is:
[/QUOTE]

Can you also post the output of lspci? Or recheck that if you have anything to do with Ethernet in there? For example:
 ```
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
```

---

### Post by nighttime on 2005-07-31
Neither 

sudo modprobe via_rhine

or

sudo modprobe via_velocity

produced any output, and I only got an error message from ifconfig eth0

eth0: error fetching interface information: device not found

And yes, I can physically plug the cable from the modem to the Ubuntu computer, the one with the phone line-looking (except bigger) connector. As to the model of my computer, its from some obscure mexican brand, ALASKA, I tried visiting the website but it no loger exists ([www.alaska.com.mx](www.alaska.com.mx)) Also theres no model number or anything written on the computer box, except the word ALASKA.

Tomorrow Ill post some pictures of the back of my computer so you can see the network card slot and the mysterious orange LED thats allways on.

And theres no ethernet controller, just:

Host bridge
PCI bridge
ISA bridge
IDE interface
USB controller
Usb controller
Bridge
Multimedia audio controller
VGA compatible controller

---

### Post by heimo on 2005-07-31
Well. It doesn't sound promising. Network card is not found on the output of lspci, but the connector on back of your computer does suggest that it has one. Maybe it's broken - or... it could be disabled in BIOS. Do you know how to change BIOS settings? When booting, at the very beginning you have to enter del button, or F1, or F10 (depends on computer), sometimes there's a brief moment when this text appears on screen "Hit del to enter BIOS" or something like that.

When in BIOS, you should go through all the menus to find any hints about ethernet, or nic or network card or eth, and make sure that it's not disabled. If you found the disable/enable setting, try again the things we've gone through on this thread. You should now see new device in output of lspci and ifconfig.

Otherwise, I'd probably just get some new or used 10/100 PCI ethernet card. Most of them will "just work".

---

### Post by Wintermute on 2005-07-31
Hi! 

I guess I have a problem similar to nighttime....

But I cannot even install ubuntu cause it seems that my net card is not compatible or something...
The installation program freezes during net card detection!!!!

Please, can you refer to [this](http://ubuntuforums.org/showthread.php?t=53123)  for help?

Thanks...  :smile:

---

### Post by nighttime on 2005-07-31
Ok, so I'll try with BIOS... or I'll buy a new NC in case that doesn't work... anyway, thanx for your time man!

---

