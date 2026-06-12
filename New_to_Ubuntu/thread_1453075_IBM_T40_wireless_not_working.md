---
title: "IBM T40 wireless not working"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by semibase on 2010-04-12
hi,
i am new to this forum and there seems to be some smart people offering advise to newbies like myself.
My problem is that i recently installed Ubuntu 9.10 and everything installed dandy but i cant get my wireless to work. I saw a few posts regarding this and tried following them but none worked.
Basically, i have the Aeronet wireless (seen by the system) but its showing disabled, which means i am unable to configure wireless on the laptop. I tried configuring blacklist.conf file and rebooting as suggested but that didnt work.
Let me know if there is anything i can do new to make it work.
regards,
 - fred

---

### Post by anewguy on 2010-04-12
I'm assuming this is the PCMCIA version?  Please do the following in a terminal window and post back the output:

lspcmcia <press enter>

lsmod <press enter>


Also, I found this in another post that you may want to try:

in a terminal window:

sudo gedit /etc/modprobe.d/blacklist.conf

go to the end of that file and add the following lines:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

Save the file, exit the editor, exit the terminal window and reboot.  See if that helps any.

Dave ;)

---

### Post by semibase on 2010-04-13
i tried the blacklist option where i needed to reboot, but that didnt work. The PCMIA - not sure, i know that the T40 has built-in wireless with a monitor light below the lcd which doesnt light up (Fn + F5). 
I'll give your first suggestion a try and let you know.
Thanks, fred.

---

### Post by anewguy on 2010-04-13
I'll assume that if you already did the blacklist thing, you did it to the correct file - the file name is blacklist.conf instead of just blacklist like it used to be.  I'll also assume that if you tried the blacklisting that you also tried the modprobe?  

Since the wireless adapter is built-in, do the following in a terminal window and post the output back here:

lspci <press enter>

lsusb <press enter>

Thanks
Dave ;)

---

### Post by anewguy on 2010-04-13
Forgot to add on the above post - if indeed you edited the correct blacklist.conf file, then I would also go back in reverse the changes made there since they had no effect.  Better to start with a clean point there.

Dave ;)

---

### Post by semibase on 2010-04-13
hi dave,
here is the info. of the commands. Also, i did revert back the blacklist as you had suggested.
 - fred

lspci......
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

lsusb.....
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

---

### Post by semibase on 2010-04-13
oops.. copied it twice, here are the results of the lsusb...

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by anewguy on 2010-04-13
I also found this in a bug report on launchpad for this adapter:

marcogoni  wrote on 2008-02-21:  	  #4

Hi, I bypassed the problem in a crude way.
Since the problem comes from the padlock_aes module that of course does not find any hardware on my pc, I went in the /lib/modules/2.6.24-xxx/modules.alias and I commented out the first two occurrences of AES that link to padlock and geode hardware.
So, the airo driver works perfectly now and the boot process is smooth as usual. Somebody should modify the configuration in a way that aes_generic or something like that is used on normal hardware.

Hope it works for you too!
marco


So, open a terminal window, then, since that was an older post, your kernel version will probably be something like 2.6.31-20-generic - just check in /lib/modules and pick the newest one and go to that folder.  Once there:

sudo gedit modules.alias

use find and search for aes - when you get to the 2 lines referenced in the post (link to padlock and to geode - mine were quite far down in the file), just add # and a space to the front of those lines, save the file and reboot.

See if your wireless is working then or not.

Also, please post back the output of:

lsmod


Thanks,
Dave ;)

---

### Post by semibase on 2010-04-14
thanks for the info, i did as you mentioned and now i dont see the network connections on the top task bar. Although i am able to connect in the wired mode. I also cannot tell if wireless is enabled and not sure how to set this up through network connections. Here is what i got with the command lsmod you had requested...

Module                  Size  Used by
binfmt_misc             8356  1 
pcmcia                 36808  0 
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
joydev                 10240  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
airo                   72924  0 
yenta_socket           24296  2 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   6688  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
psmouse                56500  0 
serio_raw               5280  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
parport_pc             31940  1 
thinkpad_acpi          66916  0 
led_class               4096  1 thinkpad_acpi
nvram                   7528  1 thinkpad_acpi
nsc_ircc               20976  0 
irda                  189564  1 nsc_ircc
crc_ccitt               1852  1 irda
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
e100                   32420  0 
mii                     5212  1 e100
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
floppy                 54916  0 
intel_agp              27676  1 
agpgart                34988  3 ttm,drm,intel_agp
 - thank, ferd

---

### Post by anewguy on 2010-04-14
Well, if nothing is showing now, I'd reverse what we last did so that should be back to "normal" after a reboot. 

Next, please do the following:

- be sure the hard-wire cable is unplugged

- in a terminal window:

sudo lshw -C network 

and post the output back here.

Thanks,
Dave ;)

---

### Post by semibase on 2010-04-15
here are the results of the output....

sudo lshw -C network

  *-network:0 DISABLED    
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:a3:17:3c
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0200000-c0203fff memory:c0400000-c07fffff memory:c0800000-c09fffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:09:6b:5f:51:6c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:c0204000-c0204fff ioport:8400(size=64)

thanks, ferd

---

### Post by anewguy on 2010-04-15
Hummmmm.....I'm a little confused here.  It does show the module airo loaded, and that is the driver the device is using.  But like you said, it still shows the device as disabled.

Please try the following in a terminal window:

ifup eth1  (I don't remember if that requires su priviledges or not)

This tells ubuntu to enable the eth1 interface, so hopefully it will enable your network.

Check under network manager afterwards and see if any wireless networks appear.

Dave ;)

---

### Post by anewguy on 2010-04-15
Also - be sure to disconnect any hard-wire ethernet cable prior to trying to use the wireless.

Dave ;)

---

### Post by semibase on 2010-04-15
i tried the ifup command but it displays the following...
Ignoring unknown interface eth1=eth1

then i check with the command..
sudo lshw -C network
and it shows as disabled.

I took the cable out and tried but nothing and also did a ping.
 regards, ferd

---

### Post by anewguy on 2010-04-15
Not sure - maybe it doesn't need eth1.  Here's what I would try:

- disconnect hard-wire ethernet cable

- ifup

see if that even works or not, if it does, check your wireless again under network manager.

Also - I don't remember off hand where, and I'm on Windows right now or I'd try to look - but I seem to remember another place you could enable wireless networking -> maybe under system/administration/networking (or some such animal)?

I'm sort of running out of ideas, but I know this can work as there are posts about it on the net (try a Yahoo, Google, Bing, or whoever search with ubuntu aironet 802.11b driver and see what comes up.

Sorry if I can't help you more!

Dave ;)

---

### Post by semibase on 2010-04-15
hi dave,
np, thanks for trying to help.
I noticed that this is a common problem for some users. I am leaning towards having an external PCMIA wireless card and get it going this way. Hopefully, this should be easy if i use one of the recommended devices.
regards, ferd

---

