---
title: "more Wlan blues"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Schiaparelli on 2010-04-18
Hi all

totally new to ubuntu. just bought a new wireless card as couldnt get wireless dongle to work.

I've got the driver installed for it via ndiswrapper 1.55. when I run 'sudo iwlist scanning' I do detect the wireless network I'm looking to connect to - so clearly this means the card works... (at least that's what I hope)

ifconfig doesnt list wlan1 (only eth0 and lo).
iwconfig lists the wlan0, with mode: managed but ESSID: off/any and Access Point: Not-Associated.
lshw -C network gives me my first clue: network: 0 DISABLED. 

When I go to system > administration > windows wireless drivers or network in both cases the Wireless connection is unticked. making a change to properties and ticking this causes it to temporarily grey things out while it (I guess) configures. But then it unticks this box again.

any help would be greatly appreciated... alternatively if you're all as puzzled as me I guess I have two options - reinstall ubuntu 9.10 and hope that does something, or can someone tell me a wireless card that works out the box (I can always take this D-link card back!)

---

### Post by 3rdalbum on 2010-04-18
If you were buying a wireless card, why didn't you buy one that you knew would work natively in Linux?

Before taking it back, try removing Ndiswrapper (blacklist it - add the words "blacklist ndiswrapper" to /etc/modprobe.d/blacklist.conf), reboot and see if there's a native Linux driver that will take control of the card.

---

### Post by anewguy on 2010-04-18
If your wireless driver is working as you say it is, and you can see your SSID being broadcast by the router as you say via sudo iwlist scanning, then your wireless adapter and driver are working.  Have you:

- checked in network manager to be sure "enable wireless" is checked?
- tried connecting to the network you see (hopefully your own)?

Dave ;)

---

### Post by coffeecat on 2010-04-18
> **Schiaparelli said:**
> (I can always take this D-link card back!)

Which D-Link card and what does..

```
lspci
```... tell us about the wireless chipset in the card? Perhaps it does work out of the box and ndiswrapper is a distraction. Let's see.

---

### Post by Schiaparelli on 2010-04-18
3rdalbum: well being new I just assumed any card would work under linux (seems to have been a rather fatal mistake)... tried blacklisting ndiswrapper...but the hardware thingy is only finding video card drivers... not sure how to make it look for wireless cards...

anewguy - yep thanks - checked for that - it's all checked... with the ndiswrapper changes (although I'm not sure I've actualy changed anything) running iwconfig gives me the correct EDDIS and AP.... so everything is working.... but my router can't see the machine.... running lshw -C network now just says network:0 - it no longer says disabled... so for some reason I'm closer heh.

---

### Post by Schiaparelli on 2010-04-18
Hi coffeecat - its a D-link DWA-520. I looked on the ndiswrapper list of supported cards and I don't see it there (but then no DWA cards are there) so I figured it's just a naming change (which sometimes happens with cards in Africa). 

using lspci gives me - 00:0d.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

---

### Post by Schiaparelli on 2010-04-18
I ran dmesg:

```
[   21.334494] ndiswrapper: using IRQ 17
[   21.538119] wlan0: ethernet device 00:24:01:0d:d2:4d using serialized NDIS driver: neta3ab, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0013.5.conf
[   21.549681] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   21.557384] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   21.557392] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   21.557402]   alloc irq_desc for 22 on node -1
[   21.557405]   alloc kstat_irqs on node -1
[   21.557419] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   21.557799] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   22.089736] usbcore: registered new interface driver ndiswrapper
[   22.167019] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   22.167112] udev: renamed network interface wlan0 to wlan1
[   22.324970] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   23.631635] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   23.631664] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   23.631769] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   29.247737] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   29.266804] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   39.416052] wlan1: no IPv6 routers present
[   40.002063] UDF-fs: No VRS found
[   40.002074] UDF-fs: No partition found (1)
[   40.064066] ISO 9660 Extensions: Microsoft Joliet Level 3
[   40.068375] ISOFS: changing to secondary root
[  305.148854] ndiswrapper (iw_set_auth:1602): invalid cmd 12

```as you can see I've got some sort of invalid cmd 12 with ndiswrapper, but it seems to have worked if I look at lshw -C network

one other thing I found when trying to blacklist ndiswrapper is that in that same modprobe.d folder is a file called: blacklist -ath_pci.conf

this warns that "For some Atheros 5k RF MACs, the madwifi driver..." essentially messes things up, but as far as I know I'm not using the madwifi driver... at the end of this file it has a: blacklist ath_pci line...

sorry I'm just pasting stuff that I think might be useful... no real clue as to what I'm doing...

update: when I use: system > administration > network tools and I use the dropdown of network device to check out the wlan1 it has both an IPv6 and IPv4 running (under the Scope part for IPv6 it says Link, but not under the IPv4 part). under interface information it says state: active (which I presume is good) and under interface statistics I see that its transmitting information all the time... (its both sending and receiving)

I've heard that IPv6 shold be disabled but not sure how to do that.... 

When I try right click network manager and go to Edit connections... I only have ifupdown (wlan1) listed under wireless and try as I might I can't add a connection - it will let me fill in new stuff when I click add, but when I click apply it just isnt there... urgh

---

### Post by lkraemer on 2010-04-18
What version of Ubuntu are you running? 9.10 ????
9.10 uses ath9k which should work out of the box
for Atheros.  At least it works on this laptop for me.

32 Bit or 64 Bit?

You need to use the proper 32 Bit or 64 Bit Windows Drivers that
match the Ubuntu 32/64 Bit Version, when using Ndiswrapper.

To install the Windows Drivers you did something like this:
I'll assume broadcom.......just for a change.....
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```

To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```

If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```

This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```

Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Open a Terminal & Check for errors:
```

dmesg tail
lsmod

```
You may have to remove other modules depending on what lsmod shows:......example only.....
What you will REMOVE depends on what you post as output from your commands.
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```

You need to supply more information by running some more commands.
So, open a Terminal Window and use these commands to get more
information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. Use Copy & Paste....
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf     OR for versions earlier than 9.04 use:
                                       cat /etc/modprobe.d/blacklist
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.

Post the output of each command........so we have more information...

It will be your decision on what to use.......Ndiswrapper or provided Driver for your version.

Once everything is correct you can use:
```

sudo /etc/init.d/networking restart

```
Or reboot.

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below, if you want to do it manually:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

lk

---

### Post by coffeecat on 2010-04-18
> **Schiaparelli said:**
> Hi coffeecat - its a D-link DWA-520. I looked on the ndiswrapper list of supported cards and I don't see it there (but then no DWA cards are there) so I figured it's just a naming change (which sometimes happens with cards in Africa). 

using lspci gives me - 00:0d.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

AR5001X should work out of the box with recent versions of Ubuntu. You don't need ndiswrapper. All you do is to click on the Network Manager applet (near top right), click on your network name, type in your passkey where prompted, and surf away. It's easier than with Vista - honest!

However, if you've installed ndiswrapper, this will interfere with the native driver. Others have told you what to do with ndiswrapper. (I could make a few suggestions. :wink:)

---

### Post by Schiaparelli on 2010-04-18
hi lkraemer - thanks for your offer to help :)

lspci:

> 00:0d.0 Ethernet controller: Atheros Communications Inc. Atheros  AR5001X+ Wireless Network Adapter (rev 01)

lshw -C network:

> WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: wlan1
       version: 01
       serial: 00:24:01:0d:d2:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neta3ab driverversion=1.55+D-Link,05/28/2007,5.3.0.46 ip=192.168.5.81 latency=128 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:eb000000-eb00ffff
lsmod:

> Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52768  1 
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
snd_via82xx            23576  2 
snd_ac97_codec        101216  1 snd_via82xx
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6940  1 snd_via82xx
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  2 snd_mpu401_uart,snd_seq_midi
nvidia               9586440  36 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ns558                   5404  0 
gameport               11368  3 snd_via82xx,ns558
parport_pc             31940  1 
snd                    59204  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
shpchp                 32272  0 
ndiswrapper           185532  0 
i2c_viapro              7344  0 
via_ircc               24016  0 
irda                  189564  1 via_ircc
crc_ccitt               1852  1 irda
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
via_rhine              22212  0 
mii                     5212  1 via_rhine
ndiswrapper -l:

> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
neta3ab : driver installed
    device (168C:0013) present (alternate driver: ath5k)
cat /etc/modprobe.d/blacklist.conf
> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist ath_pci
blacklist ath_hal
#blacklist ndiswrapper
iwconfig:

> wlan1     IEEE 802.11g  ESSID:"hiro"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:FE:A3:D2   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



when I run dmesg, two things (to my mind) stand out:

ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
wlan1: no IPv6 routers present

when I look at System > administration > Network tools and I select the netwrok device (wireless interface (wlan1) I get both ipv6 and ipv4 coming up, with LINK listed under scope for ipv6 but not ipv4. Judging by the dmesg I was thinking that perhaps there's a problem there?

I was reading in another post about how to disable ipv6 by editing /etc/modprobe.d/aliases but I don't appear to have this file!

---

### Post by Schiaparelli on 2010-04-18
coffeecat: perhaps I should just reinstall? I'm not sure how to get it to find a hardware driver - and I think I've blacklisted those to get the ndiswrapper working.... (see above). when I try look for hardware it jsut finds the nvidia proprietary drivers - not sure how to make it look for MORE drivers...?

---

### Post by lkraemer on 2010-04-18
Well, your posting shows you are connected:
wlan1 IEEE 802.11g ESSID:"hiro"
Mode:Managed Frequency:2.462 GHz Access Point: 00:18:4D:FE:A32
Bit Rate=108 Mb/s
Power Managementff
Link Quality:85/100 Signal level:-41 dBm Noise level:-96 dBm

Left Click on Firefox in the top menu and open a session.  Then click
on FILE, in the Left Corner and make sure there is no TICK MARK in
the WORK OFFLINE Box.

You should be able to surf.


Your Windows driver is loaded, but ath5k is alternate.  You can try to remove ath5k
by adding it to the blacklist file, and then rebooting.  That may get you
to a working system.  It is worth a try, even though ath5k isn't listed in
the loaded modules.

What version of Ubuntu?  9.10 ????

RE-READ MY FIRST POSTING, as I've added lots of updates.

lk

---

### Post by coffeecat on 2010-04-18
> **Schiaparelli said:**
> I'm not sure how to get it to find a hardware driver

You don't have to. So long as you haven't blacklisted a Linux driver, it gets autodetected and autoloaded as and when it's needed. Forgive me for saying this, but you're making things far too complicated by thinking in Windows ways.

> **Schiaparelli said:**
>  - and I think I've blacklisted those to get the ndiswrapper working....

Well - unblacklist them then! :wink: You know what you did - just reverse what you did.

> **Schiaparelli said:**
> when I try look for hardware it jsut finds the nvidia proprietary drivers - not sure how to make it look for MORE drivers...?

The Hardware Drivers utility is for proprietary drivers that cannot be included in a default install - which includes the nvidia proprietary driver. The only proprietary wireless driver that Hardware Drivers is used for (afaik) is the Broadcom one - which is irrelevant to your situation. The ath5k driver which comes in the box for your wireless chipset is an open source one. To repeat myself: so long as you haven't blacklisted it, it will be loaded automagically for you.

---

### Post by lkraemer on 2010-04-18
What happens if you try:
```

sudo ifconfig wlan0 down
sudo ifconfig wlan1 down
sudo dhclient -r wlan0
sudo dhclient -r wlan1
sudo iwconfig wlan1 essid "hiro"
sudo iwconfig wlan1 mode Managed
sudo ifconfig wlan1 up
sudo dhclient wlan1
ifconfig
iwconfig

```

lk

---

### Post by Schiaparelli on 2010-04-18
lkraemer: tried that - and it actually connected for a few seconds! tried another google search a few mins later and nada - but at least I knew that the card COULD work.... I realised I'd just borked the settings. so bit the bullet, reinstalled...stayed far away from ndiswrapper and whamo...20 seconds after I'd reinstalled I was connected...

so thanks all for your help - that's now 3 out of 5 pc's in this house running linux.... 2 to go ;)

---

