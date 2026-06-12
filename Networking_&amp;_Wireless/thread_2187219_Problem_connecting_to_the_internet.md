---
title: "Problem connecting to the internet"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by rabmcnair89 on 2013-11-11
Hi,

I have recently installed Ubuntu 12.04 LTS as my only OS. Unfortunately, I am unable to connect to the internet now. I have very little knowledge of using Ubuntu, so please keep that in mind if posting any  help to my problem.

As things stand I cannot connect to the internet unless I boot up from CD and select try now and even then I can only connect through wired connection. When I boot up using this method I also get an icon at top right of screen, which gives me option to install drivers.

However, when I try and activate the drivers the process does not complete and I get the following message:

Sorry, installation of this driver failed.

Please have a look at the log file for details: var/log/jockey.log

I think my network card is Broadcom 802.11 and requires driver BCM 4311. The laptop I am using is Dell Inspiron 6400. Please let me know if you require further information and I thank you in advance for any assistance you can provide.

Thanks

lspci results:

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (r
ev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by rabmcnair89 on 2013-11-11
ubuntu@ubuntu:~$ ifconfig
eth4      Link encap:Ethernet  HWaddr 00:19:b9:5c:38:c8  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe5c:38c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2280041 (2.2 MB)  TX bytes:535196 (535.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:202747 (202.7 KB)  TX bytes:202747 (202.7 KB)


===============================================================================================
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth4      no wireless extensions.

================================================================================================
ubuntu@ubuntu:~$ iwconfig wlan0
wlan0     No such device

================================================================================================
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
b44                    31223  0 
dm_crypt               22555  0 
snd_hda_codec_idt      64649  1 
snd_hda_intel          38819  3 
snd_hda_codec         118613  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
r852                   17873  0 
sm_common              16772  1 r852
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
nand                   54027  2 r852,sm_common
mtd                    38990  2 sm_common,nand
joydev                 17329  0 
gpio_ich               13278  0 
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21767  1 nand_bch
nand_ecc               13105  1 nand
r592                   17808  0 
memstick               15885  1 r592
snd                    57014  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             27612  0 
bnep                   17852  2 
coretemp               13324  0 
psmouse                82769  0 
ssb_hcd                12781  0 
dm_multipath           22754  0 
rfcomm                 38400  0 
dell_wmi               12601  0 
serio_raw              13031  0 
dell_laptop            17209  0 
lpc_ich                17048  0 
sparse_keymap          13658  1 dell_wmi
soundcore              12600  1 snd
mac_hid                13077  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
scsi_dh                14418  1 dm_multipath
dcdbas                 14065  1 dell_laptop
bluetooth             211435  10 bnep,rfcomm
ppdev                  12849  0 
microcode              18433  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
squashfs               36095  1 
overlayfs              27557  1 
nls_utf8               12493  1 
isofs                  39595  1 
dm_raid45              76440  0 
xor                    26062  1 dm_raid45
dm_mirror              21817  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18164  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 795833  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18265  0 
sdhci                  32339  1 sdhci_pci
wmi                    18744  1 dell_wmi
i915                  550346  3 
drm_kms_helper         47749  1 i915
ssb                    51554  2 b44,ssb_hcd
drm                   233935  4 i915,drm_kms_helper
i2c_algo_bit           13316  1 i915
video                  19116  1 i915
=======================================================================================================

---

### Post by Bucky Ball on 2013-11-11
Welcome. Yep, that should work out of the box.

You have Ubuntu installed? Restart the machine with the cable plugged in so you are online. When you get to the desktop, do an update then check 'Additional Drivers'. What do you see?

Also, provide the output of these two commands:
```

sudo lshw -C network
iwconfig
```

You will not get anywhere with this booting from the CD to 'Try Ubuntu' as there's nowhere to install the driver. You need to work on the hard drive install.

PS: Please provide the output between [code] tags, please, for clarity. ;)

---

### Post by rabmcnair89 on 2013-11-11
Hi BB,

Unfortunately I am not able to follow your suggestions because when I boot up normally without the installation disk, then I have no internet access.
```

ubuntu@ubuntu:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5c:38:c8
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.7 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

====================================================================================================================================
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by Bucky Ball on 2013-11-11
> **rabmcnair89 said:**
> Hi BB,

Unfortunately I am not able to follow your suggestions because when I boot up normally without the installation disk, then I have no internet access.


Not even with an ethernet cable in? You are saying that when you boot to the installed Ubuntu you are getting no internet even through a cable? So no wireless, no cable connection?

If you can get online with a cable what you need to do is open Additional Drivers, remove STA driver, open Software Centre (or Synaptics), search for 

b43-fwcutter
firmware-b43-installer

... install them and reboot. At the moment you have a b43 driver installed for it but could be the wrong one so might need to be blacklisted first.

I'll wait to hear if you can actually get online with a cable in the installed Ubuntu before continuing.

As I mention, odd, because this card is generally up and running out of the box, but you need to connect to the internet with a cable first. Catch 22. ;)

---

### Post by rabmcnair89 on 2013-11-11
Hi BB,

That is correct, when I boot from my installed Ubuntu 12.04 I do not get option to connect to internet and the ethernet cable is plugged in.This applies to both wired and wireless connection.

I would like to add that when I boot from installed Ubuntu a message displays during boot:

"The disk drive for dev/mapper/cryptswap 1 is not ready or present"

Not sure if it has any significance though.

---

### Post by Bucky Ball on 2013-11-11
> **rabmcnair89 said:**
> 
"The disk drive for dev/mapper/cryptswap 1 is not ready or present"


Might give you some clues here:

[http://askubuntu.com/questions/364136/dev-mapper-ubuntu-vg-swap-1-is-not-ready-or-not-present](http://askubuntu.com/questions/364136/dev-mapper-ubuntu-vg-swap-1-is-not-ready-or-not-present)

... but let's stick to the wireless here, post another thread for that. Try these two commands from chilli555's post in another thread (thanks chilli):
```

ifconfig
```

... with the cable in. Also, when you look in Additional Drivers, is there anything there?

---

### Post by rabmcnair89 on 2013-11-11
```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:5c:38:c8  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe5c:38c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17278770 (17.2 MB)  TX bytes:947502 (947.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30126 (30.1 KB)  TX bytes:30126 (30.1 KB)
```

===============================
With regards to additional drivers the only one it mentions is "Broadcom STA Wireless Driver"

When I try to activate driver it does not complete the process but I am running in try only at the moment. If I boot from installed Ubuntu I do not get the icon at top right for installing drivers.

---

### Post by Bucky Ball on 2013-11-11
Once again, forget the 'Try Ubuntu'. You are trying to get internet up on the hard drive install. The driver will not activate because you are not online. I don't want the output from the terminal commands when running from the CD, only the hard drive install.

All I can suggest for the moment is this:

[http://naveenubuntu.blogspot.com.au/2011/01/broadcom-sta-wireless-driver.html](http://naveenubuntu.blogspot.com.au/2011/01/broadcom-sta-wireless-driver.html)

... or diving into here:

[https://duckduckgo.com/?q=broadcom+no+interet+install+driver](https://duckduckgo.com/?q=broadcom+no+interet+install+driver)

---

### Post by rabmcnair89 on 2013-11-12
Hi BB,

Just wanted to say thanks very much for your patience because this is driving me up the wall at the minute lol.

I must say most of the things I am reading do not make any sense to me as I am a complete noob when it comes to Ubuntu.

I do not have a clue where to find anything but I am trying my best to understand.

When my mum asks me to help her on her Windows PC I need to tell her what icon to click, what will appear next, what to click on next, etc and this is the level at which I am operating with Ubuntu at present, so most of the things I am being asked to do, I really do not know how to do them. Therefore, the more detailed your instructions are the easier I will be able to follow, so please do not take anything for granted or leave any step out.

Anyway I tried my best to follow the help in that blog but only got so far. (unfortunately I cannot post the log of the terminal commands I ran as I did that by booting from Ubuntu on my HDD, I then saved them but they are not accessible at present as I need to run in try only from Boot CD in order to post online)

I know I definetely have a BCM network adaptor.

> 2.1) Browse through the LIVE USB/CD or ISO file of the Ubuntu10.04.  Navigate and install the packages listed below by  double clicking.

a) ../pool/main/d/dkms  
b) ../pool/main/p/patch
c) ../pool/main/f/fakeroot
d) ../pool/restricted/b/bcmwl
I managed to do a,c & d but the file in b was not on the disk.

> 
2.2 ) Under the desktop menu **System > Administration >  Hardware/Additional Drivers**, the **STA** drivers  can be activated for use.
I could not locate the system folder, not sure if I am looking in the correct place.


> 2.3)

a)For temporary use with the LiveCD and LiveUSB  environments, instead of a  computer restart, in a terminal issue the  following commands(in red color):

[COLOR=#CC0000]~$ sudo modprobe -r b43 ssb wl[/COLOR]
[COLOR=#CC0000]~$ sudo modprobe wl[/COLOR]I'm not sure I understand this. Is it asking me to boot from Live CD and select try only and then enter these commands in the command terminal?

I am really hopeful my problem can be rectified as I really want to use Ubuntu but this problem is grinding me down as I have to replace the HDD on my desktop, I have assignments to hand in for my studies and have kids to look after, so do not have as much time to spend on this problem as I would like :(

---

### Post by Bucky Ball on 2013-11-12
Try this approach. You will need a usb dongle or something to save a file to externally. It involves getting the b43-fwcutter stuff from the install CD and downloading some other files when online with the 'Try Ubuntu' from a CD and saving them to a USB dongle, then booting back into the hard drive install and issue some commands in a terminal. I am taking this from this site:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

... so if you want more detail, see there. b43, I think, is what should be used for this card anyway rather than the STA driver.

1/ When booted on the hard drive, insert the install CD, open a terminal and put in these two commands, one at a time hitting return in between:

```
cd /cdrom/pool/main/b/b43-fwcutter/
sudo dpkg -i b43-fwcutter*
```

2/ Now, boot to the LiveCD, click on the link below and save the file to your /home folder that exists in the hard drive install (you should be able to see that in the file manager):

b43 (12.04 Precise Pangolin) - [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2) 

3/ Reboot to the hard drive install, open a terminal and get to the folder you have saved those files to:

cd /home

... if that's where it is, or the path to wherever you have it.

Now issue these two commands:
```

tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```

4/ Restart and see what happens. ;)

---

### Post by rabmcnair89 on 2013-11-12
Hi BB,

I opened up command terminal and typed: > cd /cdrom/pool/main/b/b43-fwcutter/

When I hit enter I got this message:
> No such file or directory

I then opened up the Live CD and located the file "b43-fwcutter", which I double clicked.

By doing that the > Ubuntu Software Centre Opened

and the title was > Utility for extracting broadcom 43xx firmware

the message was > Please install "b3-fwcutter" via your normal software channels. Only install this file if you trust its origin.

I never followed any other steps as I think they may be pointless until we install b43-fwcutter, but that is just a guess.

Thanks :)

---

### Post by Bucky Ball on 2013-11-12
No, you were almost there! You want to install b43-fwcutter from the CD! That is the point of this. You then flip to the LiveCD, download the other stuff. There is no point going on until you do the bit that you were about to do ... get there again and go ahead with installing b43-fwcutter from the CD. You second guessed yourself because you had it right. ;)

See this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

... and follow the steps under 'b43 - No Internet access' carefully. Just do exactly what it says.

---

### Post by rabmcnair89 on 2013-11-12
But I can't follow the steps for no internet access as the file is not on my CD. So the question is how do I get it?


It is like I said a few posts ago, the command terminal command returned saying no file found and then I looked on the CD and found the file but it did not work when I clicked on it and it took me to Ubuntu Software Centre.


I should point out that the disk I used to install Ubuntu is a disk I  burned a while back as I needed a live CD to rescue the data on my  mum's hard drive. Not sure if that makes a difference as I do not know  when b43-fwcutter was added.

---

### Post by Bucky Ball on 2013-11-12
> **rabmcnair89 said:**
> 

It is like I said a few posts ago, the command terminal command returned saying no file found and then I looked on the CD and found the file but it did not work when I clicked on it and it took me to Ubuntu Software Centre.




It opened Software Centre to ask you if you wanted to install it from the CD. That's what you want to do. 

As long as you have a 12.04 LTS disk, you're fine (it is on the others, too, but might be a dated version not suitable for 12.04).

Software Centre gave you this when you clicked the b43-fwcutter file on the disk?

> Please install "b3-fwcutter" via your normal software channels. Only install this file if you trust its origin.

Install it. Sounds like it is a .deb file and SCentre is the to install .debs, among other things.

---

### Post by rabmcnair89 on 2013-11-12
Hi BB,

I shall detail exactly what I am doing and what is happening.

1. I start my laptop, booting from the installed version of Ubuntu on my hard disk.

2. I enter my password and wait for OS to load to desktop.

3. Once fully loaded I insert my Live CD of Ubuntu 12.04 LTS.

4. I open a command terminal using ctrl+alt+t

5. I enter this command: > cd /cdrom/pool/main/b/b43-fwcutter/


6. I get message no such file or directory found.

7. I enter this command in the terminal > sudo dpkg -i b43-fwcutter*
8. I get message saying no such file or directory found.

9. I click on home.

10. I click on the CD

11. I double click pool

12. I double click main

13. I double click b

14. I double click folder "b43-fwcutter"

15. I double click file "b43-cutter"

16. Ubuntu software centre opens

17. I try and click on install but nothing happens as it is greyed out.

18. I double click the only tab that is available and it opens Mozilla but page does not load as I have no connection.

19. There is nothing else for me to click.

What am I doing wrong? What do I do next? 

Please post 1 step at a time and tell me what I should see and what you information you need me to supply for the follow up post.

Thanks :)

---

