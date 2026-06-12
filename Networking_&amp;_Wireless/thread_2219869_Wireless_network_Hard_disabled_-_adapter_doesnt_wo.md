---
title: "Wireless network Hard disabled - adapter doesnt work - acer"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by spiderDuck on 2014-04-25
[COLOR=#333333][FONT=Ubuntu]Hello everybody. I have been trying to solve this problem for over a year now.
I have an Acer Travelmate 290 which runs only Ubuntu. I cannot connect with wireless.
The laptop has a switch to turn on and off the wireless. I have, of course, turned it on. I have opened up the case and changed the wireless card. Nothing. I have checked the BIOS. Nothing. I have tried commands like "rfkill [whatever]". Nothing.
As a last resort, I bought a wireless usb adapter, namely "Edimax EW-7811Un". I have installed it but again the Network Manager says it is hard disabled, although the "rfkill list" says it isn't. I hope someone can help.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]PS: I am not a Linux expert but I am also not a total noob. I have used Ubuntu for some time and I really want to keep using.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]here are the results of some commands I think are useful:
[/FONT][/COLOR]
```
**[COLOR=#333333][FONT=Ubuntu]anthony@myLaptop:~$ sudo lshw -businfo[/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]
Bus info Device Class Description
========================================================
                              system Portable Computer
                              bus CL50
                              memory 84KiB BIOS
cpu@0 processor Intel(R) Pentium(R) M processor 150
                              memory 32KiB L1 cache
                              memory 1MiB L2 cache
                              memory System Memory
                              memory 256MiB DIMM DRAM EDO 1 MHz (1000.0
                              memory 512MiB DIMM DRAM EDO 1 MHz (1000.0
                              memory Video Memory
                              memory 512MiB FLASH Non-volatile
                              memory
                              memory
pci@0000:00:00.0 bridge 82855PM Processor to I/O Controller
pci@0000:00:01.0 bridge 82855PM Processor to AGP Controller
pci@0000:01:00.0 display RV350/M10 [Mobility Radeon 9600 PRO
pci@0000:00:1d.0 bus 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M
pci@0000:00:1d.1 bus 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M
pci@0000:00:1d.2 bus 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M
pci@0000:00:1d.7 bus 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI
pci@0000:00:1e.0 bridge 82801 Mobile PCI Bridge
pci@0000:02:00.0 bus VT6306/7/8 [Fire II(M)] IEEE 1394 O
pci@0000:02:01.0 eth0 network RTL-8139/8139C/8139C+
pci@0000:02:02.0 eth1 network PRO/Wireless 2200BG [Calexico2] Net
pci@0000:02:03.0 bridge CB1410 Cardbus Controller
pci@0000:00:1f.0 bridge 82801DBM (ICH4-M) LPC Interface Bri
pci@0000:00:1f.1 scsi0 storage 82801DBM (ICH4-M) IDE Controller
scsi@0:0.0.0 /dev/sda disk 40GB IC25N040ATMR04-0
scsi@0:0.0.0,1 /dev/sda1 volume 9536MiB EXT4 volume
scsi@0:0.0.0,2 /dev/sda2 volume 27GiB Extended partition
                  /dev/sda5 volume 3814MiB Linux swap / Solaris partit
                  /dev/sda6 volume 24GiB Linux filesystem partition
scsi@1:0.0.0 /dev/cdrom disk CDRW/DVD SBW242C
pci@0000:00:1f.3 bus 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M
pci@0000:00:1f.5 multimedia 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M
pci@0000:00:1f.6 communication 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M
                              power
usb@1:6 wlan0 network Wireless interface[/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]```
**anthony@myLaptop:~$ sudo lshw -C network**
[sudo] password for anthony:
```[/FONT][/COLOR]```

[COLOR=#333333][FONT=Ubuntu]  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:17:1d:40
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.10.3 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:8d:2a:cb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:d0000000-d0000fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan0
       serial: 80:1f:02:e2:52:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-60-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn[/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]```
**anthony@myLaptop:~$ lspci**
```[/FONT][/COLOR]```

[COLOR=#333333][FONT=Ubuntu]00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350/M10 [Mobility Radeon 9600 PRO Turbo]
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:03.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)[/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]```
**anthony@myLaptop:~$ sudo lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 002: ID 13ee:0001 MosArt
```
[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]```
**anthony@myLaptop:~$ sudo lsmod**
Module Size Used by
xt_limit 12541 8
xt_tcpudp 12531 7
ipt_LOG 12783 8
ipt_MASQUERADE 12663 0
xt_DSCP 12549 0
ipt_REJECT 12512 1
nf_conntrack_irc 13138 0
nf_conntrack_ftp 13183 0
xt_state 12514 6
arc4 12473 2
rtl8192cu 97717 0
rtl8192c_common 69519 1 rtl8192cu
rtlwifi 95855 1 rtl8192cu
iptable_nat 13016 0
nf_nat 24959 2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4 19084 9 iptable_nat,nf_nat
nf_conntrack 73847 7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4 12649 1 nf_conntrack_ipv4
mac80211 436493 3 rtl8192cu,rtl8192c_common,rtlwifi
iptable_mangle 12646 0
iptable_filter 12706 1
ip_tables 18106 3 iptable_nat,iptable_mangle,iptable_filter
x_tables 22011 11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
bnep 17830 2
bluetooth 158447 7 bnep
joydev 17393 0
snd_intel8x0 33455 2
snd_ac97_codec 110213 1 snd_intel8x0
ac97_bus 12642 1 snd_ac97_codec
ppdev 12849 0
snd_pcm 80916 2 snd_intel8x0,snd_ac97_codec
binfmt_misc 17292 1
snd_seq_midi 13132 0
pcmcia 39826 0
snd_rawmidi 25424 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
radeon 738089 3
snd_seq 51592 2 snd_seq_midi,snd_seq_midi_event
snd_timer 28931 2 snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200 146210 0
snd 62218 11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm 65344 1 radeon
libipw 46732 1 ipw2200
psmouse 96744 0
cfg80211 178877 4 rtlwifi,mac80211,ipw2200,libipw
drm_kms_helper 45466 1 radeon
drm 197641 5 radeon,ttm,drm_kms_helper
soundcore 14635 1 snd
yenta_socket 27428 0
pcmcia_rsrc 18367 1 yenta_socket
serio_raw 13027 0
snd_page_alloc 14115 2 snd_intel8x0,snd_pcm
pcmcia_core 21511 3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211 14040 2 ipw2200,libipw
irda 185517 0
parport_pc 32114 1
i2c_algo_bit 13199 1 radeon
crc_ccitt 12627 1 irda
mac_hid 13077 0
shpchp 32265 0
lp 17455 0
parport 40930 3 ppdev,parport_pc,lp
usbhid 41937 0
hid 81731 1 usbhid
firewire_ohci 40180 0
8139too 23283 0
8139cp 26688 0
firewire_core 56940 1 firewire_ohci
crc_itu_t 12627 1 firewire_core
```
[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]```
**anthony@myLaptop:~$ rfkill list all**
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
1: phy1: Wireless LAN
 Soft blocked: no
 Hard blocked: no
```
[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]```
**anthony@myLaptop:~$ sudo iwconfig**
lo no wireless extensions.
```[/FONT][/COLOR]```

[COLOR=#333333][FONT=Ubuntu]eth1 IEEE 802.11bg ESSID off/any
          Mode:Managed Channel:0 Access Point: Not-Associated
          Bit Rate:0 kb/s Tx-Power=off Sensitivity=8/0
          Retry limit:7 RTS thr:off Fragment thr:off
          Encryption key:off[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
          Power Management:on
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]wlan0 IEEE 802.11bgn ESSID:off/any
          Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm
          Retry long limit:7 RTS thr=2347 B Fragment thr:off
          Encryption key:off
          Power Management:on [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eth0 no wireless extensions[/FONT][/COLOR]
```

---

### Post by varunendra on 2014-04-27
Please post the outputs of -
```
egrep -v '^#|^$' /etc/modprobe.d/blacklist.conf
grep wmi /etc/modprobe.d/*
```

---

### Post by spiderDuck on 2014-05-02
Here you go: (and sorry for the delay in my answer)

**egrep -v '^#|^$' /etc/modprobe.d/blacklist.conf**

```
[COLOR=#222222][FONT=Verdana]anthony@myLaptop:~$ egrep -v '^#|^$' /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
```


and **[COLOR=#000000][FONT=Ubuntu Mono]grep wmi /etc/modprobe.d/*[/FONT][/COLOR]**
```
grep wmi /etc/modprobe.d/*
/etc/modprobe.d/alsa-base.conf:install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
```

---

### Post by spiderDuck on 2014-05-02
And some more commands that might be useful:

**anthony@myLaptop:~$ dmesg | tail**
```
[   31.136096] ipw2200: Failed to send POWER_MODE: Command timed out.
[   31.678892] init: plymouth-stop pre-start process (1522) terminated with status 1
[   33.156081] ACPI: EC: GPE storm detected, transactions will use polling mode
[   35.392051] ipw2200: Failed to send POWER_MODE: Command timed out.
[   39.680033] eth0: no IPv6 routers present
[  122.176046] eth0: no IPv6 routers present
[ 2932.370282] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[ 2932.372847] watchdog: failed to be enabled on some cpus
[ 2933.560227] ipw2200: Failed to send POWER_MODE: Command timed out.
[ 3524.101845] usbcore: registered new interface driver rt2800usb
```


**anthony@myLaptop:~$ lsmod | grep rt2**

```
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48923  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  6 rt2800lib,rt2x00usb,rt2x00lib,rtl8192cu,rtl8192c_common,rtlwifi
crc_ccitt              12627  2 rt2800lib,irda
cfg80211              178877  5 rt2x00lib,rtlwifi,mac80211,ipw2200,libipw
```

---

### Post by spiderDuck on 2014-05-11
OK. Update:

    I tried reinstalling the adapter with this driver I found: RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911
It had a "install.sh" file in it. So I did:
```

                                                      cd Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911
                                                      sudo su
                                                      [COLOR=#000000][FONT=Ubuntu Mono]chmod +x install.sh
[/FONT][/COLOR]                                                      [COLOR=#000000][FONT=Ubuntu Mono]./install.sh
```

All went well, until:
[/FONT][/COLOR]```
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-61-generic'
##################################################
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-61-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-61-generic
##################################################
The Setup Script is completed !
##################################################
```

So, then I tried:
                       [COLOR=#000000][FONT=Ubuntu Mono]modprobe 8192cu
But:
[/FONT][/COLOR]```
FATAL: Error inserting 8192cu (/lib/modules/3.2.0-61-generic/kernel/drivers/net/wireless/8192cu.ko): Device or resource busy
```


Any ideas?  :confused:

---

### Post by chili555 on 2014-05-16
First, I'd blacklist ipw2200 and see how it goes. If that doesn't help, we'll take a few more steps:```
sudo -i 
echo "blacklist ipw2200"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us see:```
rfkill list all
lsmod | grep 8192
```Thanks.

---

### Post by spiderDuck on 2014-05-18
> **chili555 said:**
> First, I'd blacklist ipw2200 and see how it goes. If that doesn't help, we'll take a few more steps:```
sudo -i 
echo "blacklist ipw2200"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us see:```
rfkill list all
lsmod | grep 8192
```Thanks.


WOW! It works! Chili555 I am forever grateful! I love Ubuntu!

    Now on a more serious note:
First of all, here are the results:
```
anthony@myLaptop:~$ rfkill list all0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

and 

```
anthony@myLaptop:~$ lsmod |grep 8192
rtl8192cu              97717  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95855  1 rtl8192cu
mac80211              436493  3 rtl8192cu,rtl8192c_common,rtlwifi
```


Secondly, would you be so kind as to explain what exactly happened? To my understanding we blacklisted a module that was preventing another module from working. Correct?

Thirdly, the fact that we (well, you!) got my usb-adapter working does not explain why my laptop's internal "Intel PRO/Wireless 2200BG" was not working (and, actually, is still not working. We just got rid of it). Maybe the hardware switch (on the side of my laptop) is broken. Maybe I could solder the connections on the motherboard and make the wifi be always on. I want to remind you that my first move to try and fix the problem was to replace the original wifi card inside my laptop with a new one.

Again, thank you very much. I will wait a couple of days to test it out before I mark the topic as solved.

---

### Post by chili555 on 2014-05-18
> To my understanding we blacklisted a module that was preventing another module from working. Correct?Correct. The two wireless drivers were competing for networking domination and world supremacy! Probably, and more likely, their 80211 stacks were conflicting.

As to why your internal didn't work, that's a different question that we could investigate and maybe or maybe not solve. A steady hand on the soldering iron may be helpful.

Over the years, I have seen dozens of cases of 'my internal doesn't work (at all or well enough) and so I replaced it with a USB' and have had a little luck troubleshooting the internal and a lot of luck getting the USB working so I stick with what works. If you'd like to revert to the internal, I am very willing to help. On the other hand, you have a working wireless now and those mp3s, emails and Youtube videos are waiting!

---

### Post by spiderDuck on 2014-05-24
The solution has been working great for so long, so I'm gonna mark this topic as SOLVED.

I guess you are correct, I am content with my wifi working again; it is unnecessary  to get into more trouble.

However, if I decide to give it a shot with the internal wifi in the future, I will start a new topic.

Again, thank you so much for the help, and a big "Bravo" to the Ubuntu Community!


Kind Regards,
Antony

---

### Post by mark142 on 2014-06-11
> **chili555 said:**
> '''As to why your internal didn't work, that's a different question that we could investigate and maybe or maybe not solve. A steady hand on the soldering iron may be helpful.

 If you'd like to revert to the internal, I am very willing to help. On the other hand, you have a working wireless now and those mp3s, emails and Youtube videos are waiting!

I have a similar internal card [COLOR=#000000]"Intel PRO/Wireless 2200BG" [/COLOR]on an old Acer Travelmate 2200. The way I have been able to gain functionality was a simple ndiswrapper. [possibly not the best solution but it works well] The issue I am having would be in fact a hardware disabled issue. I am refurbishing this via Linux (Debian rather then Ubuntu as the Xubuntu and Mint installers seemingly take issue with the network hardware and made it more difficult then I cared to endure for installation... so may be some differences.) This is for a less tech savvy windows convert. So, I am running XFCE over LightDM and solutions are simple as possible gui front end.
I am able to get the wireless working flawlessly by turning on the wireless (external hardware button) after boot. The issue is that after eachboot I have to uninstall/re-install the i2200 ndiswrapper [via ndisgtk] and then reconnect wireless [via wicd-client]. I am unable to find a way to get wireless hardware to turn on by default on boot

I am hoping to find a simple work around such as a script I could make executable that would uninstall/re-install drivers via ndiswrapper and auto connect wireless via wicd or other. The idea is a one click my wife can use to get connected to a wireless I have setup. 
something like: 
ndiswrapper -r i2200 && ndiswrapper -i /opt/A820/Winxp/i2200.inf && wicd essid mynetwork key mypassphrase

I'm not good with scripts and things but can follow direction and fumble through learning as I go. I've not had the chance to try the above script and do not feel overly confident it would be correct. If it were or if there is a script that would work are you able to  just +x a text file holding the script to make it executable and give it a 'pretty' little icon so my wife recognizes it as a wireless connect button?

"A steady hand on the soldering iron may be helpful." probably would hold true but where I am not too afraid to rip apart machines I am not willing to risk killing this thing as it is currently what I have to make her happily FB and email away, etc.

I apologize in advance for the length and if I am displaying my ignorance.

---

### Post by chili555 on 2014-06-12
When you boot from scratch, is ndiswrapper loaded?```
lsmod | grep ndis
```Does it all work as expected if you simply load it?```
sudo modprobe ndiswrapper
```

---

