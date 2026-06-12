---
title: "Atheros AR9285 Wireless in Linux Lite"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by DRW05 on 2014-03-09
This wireless card is not recognized in Linux Lite.

I have found fixes such as the following: [http://askubuntu.com/questions/75969/ar9285-wifi-on-lenovo-z570-not-enabled/77372#77372](http://askubuntu.com/questions/75969/ar9285-wifi-on-lenovo-z570-not-enabled/77372#77372)

Is someone willing to walk me through the steps of executing these instructions? I am brand new to linux.

Any help would be appreciated!

---

### Post by Ubi_one_2014 on 2014-03-10
since you are new to linux, i recommend this, instaed your offer

[http://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver](http://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver)

workaround:
```
[FONT=Ubuntu Mono]echo "options ath9k nohwcrypt=1" | sudo tee  /etc/modprobe.d/ath9k.conf[/FONT]
sudo modprobe -rfv ath9k
 [FONT=Ubuntu Mono]sudo modprobe -v ath9k[/FONT]
```

open a terminal, and copy/paste the 3 lines , one by one, into the terminal
so first line one, followed by enter, line 2 , followed by enter

---

### Post by DRW05 on 2014-03-10
Thanks for assisting.

I input the three lines and did a reboot. Doesn't seem to have any effect, anything else I should do after?

---

### Post by varunendra on 2014-03-10
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by DRW05 on 2014-03-10
Thanks for your assistance.

Here is the report it generated for me:

```


*************** info trace ***************


***** uname -a *****


Linux eeePC 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:08:04 UTC 2013 i686 athlon i386 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Linux Lite 1.0.8
Release:    12.04
Codename:    precise


***** lspci *****


01:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
--
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
    Kernel driver in use: atl1c


***** lsusb *****


Bus 002 Device 002: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


***** iw reg get *****




***** route -n *****


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 eth0
192.168.3.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


***** lsmod *****


ath9k                 136512  0 
mac80211              541819  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              406597  2 ath9k,ath9k_common
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
cfg80211              453919  3 ath9k,mac80211,ath


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.3.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.1


    DNS:             192.168.3.1




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
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


***** modinfo *****


filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DD97D617F7C24BA9D111D21
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)


filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0078E2DDCA5F8B073A36467
depends:        ath
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   13.558603] ath: phy0: ASPM enabled: 0x42
[   13.558616] ath: EEPROM regdomain: 0x60
[   13.558620] ath: EEPROM indicates we should expect a direct regpair map
[   13.558626] ath: Country alpha2 being used: 00
[   13.558630] ath: Regpair used: 0x60
[   14.140645] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140100)
[   20.778280] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************
```

---

### Post by varunendra on 2014-03-10
> **DRW05 said:**
> ```
***** rfkill *****

0: phy0: Wireless LAN
    [B]Soft blocked: [COLOR="#FF0000"]yes[/COLOR]
    Hard blocked: [COLOR="#FF0000"]yes[/COLOR][/B]
1: asus-wlan: Wireless LAN
   ** Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
    Hard blocked: no
```

As you can see above, your wireless is both hard and soft blocked. Means it is turned off by both hardware switch and by your Network Manager.

Please turn it on Physically by Fn+F2 key combination, which I assume is the combination to turn WiFi on/of for all Asus models. If that combination does not seem to work, please check out the suggestions in this thread to verify if you have the same bug : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

Check the block state with "rfkill list" command. Make sure both hard and soft block states are "no". If the hardblock is gone, but the soft block still remains, please make sure that "Enable Wireless" option in Network Manager menu is enabled (has a tick mark beside it). If it is already enabled, and still the interface appears as soft-blocked, please try -
```
rfkill unblock all
```

Try these, and let us know the result.

---

### Post by DRW05 on 2014-03-10
Ok, thank you.

Firstly, my Asus has a wifi hardware switch. I think there is something strange going on with it.

When I turn hit the hardware switch such that the system tray says "wireless is disabled by hardware switch" I actually get this output from **rfkill list all**:
```

0: phy0: Wireless LAN    
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

However, when I hit the switch again such that the tray only says "wireless is disabled" (no mention of hardware switch), my **rfkill list all** returns this:
```

0: phy0: Wireless LAN    
    Soft blocked: yes
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

And actually, when I right click and tick Enable Wireless, this actually has the effect of switching the hardware switch to 'OFF' so that nothing can be done with the wireless. I have to hit the hardware switch again.

So it appears the hardware switch might be set up backwards, or something?


Regarding the bug:
I followed the steps listed, but I can't tell if I have the bug or not. I'll post my results of the 4 steps here:

1) [COLOR=#000000]Check if a driver is available for the card
[/COLOR]```
01:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k

```
[COLOR=#800000]Is there a module name in front of it? >[/COLOR]**Yes.**

2) [COLOR=#000000]Check if the driver is loaded and if "asus_nb_wmi" driver is also in use :[/COLOR]
```
asus_wmi               23821  1 eeepc_wmisparse_keymap          13658  1 asus_wmi
ath9k                 136512  0 
mac80211              541819  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              406597  2 ath9k,ath9k_common
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
cfg80211              453919  3 ath9k,mac80211,ath
wmi                    18744  1 asus_wmi
video                  19116  1 asus_wmi



```
[COLOR=#800000]Do you see the driver for your card, and "asus_nb_wmi" both in the above output? >[/COLOR]**Not sure, I don't see **[COLOR=#800000]"asus_nb_wmi".[/COLOR]

3) [COLOR=#000000]Check the "Hard blocked" state of wifi [/COLOR]
```
0: phy0: Wireless LAN    
    Soft blocked: yes
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```
[COLOR=#800000]Does it show as "Hard blocked: yes" ? >[/COLOR]**This is the return when hardware switch should be "on". See above.**

4) Suspend the notebook.
[COLOR=#800000]Does the wireless become active now? [/COLOR][COLOR=#800000]>[/COLOR][B]No change.


[/B]And finally, when I try **rfkill unblock all**:
```
Can't open RFKILL control device: Permission denied

```

---

### Post by varunendra on 2014-03-10
The same combination controls both the wireless and bluetooth, so the switch state Vs LED state (Vs. rfkill list state) can get confusing sometime.

The "asus-wlan" interface is usually the LED. The "phy0" interface is usually the actual wireless card. And none of your outputs show phy hard block as "no". Putting simply, we need all four in the output of rfkill to appear as "no" (not blocked).

Not having the asus_nb_wmi driver is a bit unexpected, although not too surprising.

Regarding the rfkill command error in the last, please try the same with 'sudo' -
```
sudo rfkill unblock all
```
Then check again -
```
rfkill list
```
Remember - we need all four block states to be at "no".

If that (plus your experiments with the hardware switch/Network Manager option) can't get us to that state, please post back the full outputs of -
```
lsmod
grep [[:alnum:]] /sys/module/{asus*,eeepc*,wmi}/parameters/*
```

---

### Post by DRW05 on 2014-03-10
Thank you for your explanation.

After running **sudo rfkill unblock all**, my result for **rfkill list **is unchanged from before.

Output of **lsmod**:
```

Module                  Size  Used byrfcomm                 38400  4 
bnep                   17852  2 
parport_pc             27612  0 
bluetooth             211552  10 rfcomm,bnep
ppdev                  12849  0 
eeepc_wmi              12983  0 
asus_wmi               23821  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
dm_multipath           22754  0 
scsi_dh                14418  1 dm_multipath
kvm_amd                54759  0 
uvcvideo               72250  0 
arc4                   12509  2 
videobuf2_core         39385  1 uvcvideo
videodev               96131  2 uvcvideo,videobuf2_core
kvm                   384557  1 kvm_amd
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
ath9k                 136512  0 
joydev                 17329  0 
snd_hda_codec_realtek    65042  1 
microcode              18433  0 
mac80211              541819  1 ath9k
snd_hda_codec_hdmi     36612  1 
snd_hda_intel          38819  5 
snd_hda_codec         118650  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
psmouse                82769  0 
snd_hwdep              13276  1 snd_hda_codec
ath9k_common           13781  1 ath9k
sp5100_tco             13558  0 
serio_raw              13031  0 
snd_seq_midi           13132  0 
i2c_piix4              13227  0 
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
k10temp                12997  0 
ath9k_hw              406597  2 ath9k,ath9k_common
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              453919  3 ath9k,mac80211,ath
snd                    57014  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76440  0 
xor                    26062  1 dm_raid45
dm_mirror              21817  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18164  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 795833  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
hid_generic            12484  0 
usbhid                 46125  0 
hid                    87362  2 hid_generic,usbhid
radeon                892497  2 
ttm                    72088  1 radeon
drm_kms_helper         47749  1 radeon
ahci                   25631  2 
drm                   233935  4 radeon,ttm,drm_kms_helper
atl1c                  41017  0 
libahci                26336  1 ahci
i2c_algo_bit           13316  1 radeon
wmi                    18744  1 asus_wmi
video                  19116  1 asus_wmi
zram                   18207  1 



```

Output of **[COLOR=#000000][FONT=Ubuntu Mono]grep [[:alnum:]] /sys/module/{asus*,eeepc*,wmi}/parameters/*[/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]:
[/FONT][/COLOR]```


grep: /sys/module/asus*/parameters/*: No such file or directory/sys/module/eeepc_wmi/parameters/hotplug_wireless:N
/sys/module/wmi/parameters/debug_dump_wdg:N
/sys/module/wmi/parameters/debug_event:N


```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by varunendra on 2014-03-10
Please try a parameter with eeepc_wmi driver -
```
echo "options eeepc_wmi hotplug_wireless=Y" | sudo tee /etc/modprobe.d/eeepc_wmi.conf
```
Reboot for the parameter to take effect.

Check rfkill list again. Try the hardware switch if required. Better or worse ?

---

### Post by DRW05 on 2014-03-10
Sorry, is that a one or two line command?

---

### Post by varunendra on 2014-03-10
A single line command, you may copy paste using your mouse pointer.

It is actually a combination of two commands. The 'Pipe' (|) symbol is on the same key as backslash (\) on my US-104 style keypad.

---

### Post by DRW05 on 2014-03-10
Thanks for your attention in helping me.

I input the last command and rebooted but I seem to have a new problem. The machine isn't booting into Linux at all now. The BIOS appears to be getting stuck. The text onscreen refers to Atheros. I don't have the exact text now but I will copy it later when I go home. I'll try to experiment with the BIOS to boot back into Linux again.

---

### Post by varunendra on 2014-03-10
Are you sure it is BIOS screen not Ubuntu boot screen? If it is Ubuntu, can you try booting into "(recovery mode)" (press a key as soon as Ubuntu starts to boot if you don't get grub menu by default).

And do you have a Live CD/USB to be able to boot into Live mode if required?

---

### Post by DRW05 on 2014-03-10
I'm not certain. I will verify and post back here later when I have access to the machine (I'm working now).

I have the USB but will have to load the bootable .iso again.

---

### Post by DRW05 on 2014-03-11
I think this is the BIOS screen not Ubuntu/Linux Lite.

It says the following (somewhat simplified by me):

```

Intel UNDI, PXE-2.0 (build 083)
Copyright .... Intel Corp

For Atheros PCIE Ethernet Controller v2.0.2.2(03/31/10)

CLIENT MAC ADDR: <my MAC address here>
GUID: <string of numbers here>
PXE-E53: No boot filename received.

PXE-M0F: Exiting Intel PXE ROM.

Missing operating system.

Reboot and Select proper Boot device
or Insert Boot Media and press a key

```

---

### Post by varunendra on 2014-03-11
> **DRW05 said:**
> ```

Missing operating system.

Reboot and Select proper Boot device
or Insert Boot Media and press a key

```
That looks like a hardware or BIOS configuration problem to me, certainly not Ubuntu related.

Please go into your BIOS and see if the hard disk is detected at all. If it is, make sure it is included in the "Boot Devices" or "Boot Order" menu (preferably the first boot device, but that shouldn't be necessary).

Whatever caused it, it is certainly not the parameter that we tried with the eeepc_wmi driver. Because anything configuration related will come into play when the OS starts booting first. While here, either the entire hard disk is missing, or the boot-record on it.

If the Hard disk appears in BIOS, and is set properly in the Boot Order, then it is now a different problem (booting related) and you must have an alternative boot device (preferably a Live bootable usb) to fix it first.

---

### Post by DRW05 on 2014-03-12
Ok, I can boot into Linux again. I am not sure what happened. Interestingly, in my BIOS list of boot devices, there is an option for the Atheros network card in addition to my hard drive. I think it was a problem with that getting hung up for some reason. (Currently it is set in front of my hard drive in the Boot Order because that's how it was by default previously with Windows, I think).

Anyway, I rebooted and tried the last command again. No change to my **rfkill list** results, with switch on and off.

---

### Post by varunendra on 2014-03-12
> **DRW05 said:**
> Anyway, I rebooted and tried the last command again. No change to my **rfkill list** results, with switch on and off.

I would like to see the current output of -
```
 grep [[:alnum:]] /sys/module/{asus*,eeepc*,wmi}/parameters/*
```

This card that you have is certainly not a problem. I have the very same card (running problem free on kernel 3.2..) and have seen hundreds of threads where it sometimes does have speed or connectivity problems with kernel 3.8 to 3.11, but certainly not hard-block problem.

So I strongly suspect it to be a BIOS or ACPI related problem. As such, have you tried resetting the BIOS yet?

---

### Post by DRW05 on 2014-03-14
> **varunendra said:**
> As such, have you tried resetting the BIOS yet?

This fixed it.

(Possibly in conjunction with some of the other things we've been doing, but I'm not certain).

Thank you for your help. Sorry to take your time troubleshooting. I hadn't seen any suggestion to reset the BIOS until now. I apologize if it's common knowledge to reset the BIOS upon installing Linux but I was unaware.

I'll mark this as fixed.

---

### Post by varunendra on 2014-03-14
You're welcome!

Not suggesting BIOS reset earlier was entirely my fault, probably I was addressing too many threads at once.. :)

---

