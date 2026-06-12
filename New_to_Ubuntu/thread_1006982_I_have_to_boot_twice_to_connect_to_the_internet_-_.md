---
title: "I have to boot twice to connect to the internet - what's gone wrong?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-12-09
Since I did a fresh install of 8.04 (an update from 7.04) on it's own partition, created a separate /home partition and then copied my old /home files onto the new partition ............ I have recently had to boot my pc twice to connect to the internet. I'm using wi-fi which always worked perfectly with my beloved 7.04.

I don't get it.

---

### Post by nhasian on 2008-12-10
my wifi was a little quirky under 8.04 as well.  connection getting dropped, having to reboot to reconnect, etc.  Ubuntu 8.10 has much better wifi support.  Since i've upgraded to 8.10 i've been much happier.  no more dropped wifi signal for me :)

---

### Post by tahitiwibble on 2009-01-28
I was very unhappy with 8.04 and wi-fi ............ no longer, I changed my modem/router from a totally worthless Belkin piece of crap to a Netgear unit and it's like night and day. I have also "tuned up" Firefox and really can't complain any more about the speed of my connection.

However I still sometimes have to boot up twice to connect to the net .... and web page loading seems to "stall" sometimes.

I feel there might be just one more small step to take to rectify having to boot up twice. Does anyone have an idea?

Thanks guys.

---

### Post by tahitiwibble on 2009-01-29
When I boot up and look in "Network Setting", sometimes the wireless connection box is there and sometimes not. Is it really 8.04 which is not up to scratch or just a minor config problem?

---

### Post by x33a on 2009-01-29
instead of restarting the computer, try

sudo /etc/init.d/networking restart

---

### Post by tahitiwibble on 2009-01-30
> **x33a said:**
> instead of restarting the computer, try

sudo /etc/init.d/networking restart

x33a, thanks for the suggestion. I just tried it this morning (I only have this problem after a long night's computer inactivity) and this is the message I got back:

```
dad@dad-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for dad: 
 * Reconfiguring network interfaces...
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```

All very strange

---

### Post by bodhi.zazen on 2009-01-30
I had extreme problems with wifi on 8.04 and did everything.

After almost a month I tried wicd -> problem solved

wicd replaces network manager and is easily installed :

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

network manager works on 8.10.

have not tried it on 9.04 as I think X  with nvidia cards is not working, although I have not checked.

---

### Post by tahitiwibble on 2009-01-30
bodhi.zazen, thank you for that. I will have to wait till my computer has been switched off for a night before being able to test wicd. I will let you know.

Would you advise to uninstall Network Manager? *edit* hmmmm, during installation of wicd, network manager was supposedly removed ......... but it's still there!?

---

### Post by bodhi.zazen on 2009-01-30
network manager should have been removed, if you can try to reboot.

---

### Post by avtolle on 2009-01-30
Installing wicd does remove Network Manager; however, the icon is (was?) left behind. Restarting  X (ctrl+alt+backspace) took care of the problem for me. Also, just in case, check the System>Preferences>Sessions file to be sure the daemon is not activated; IIRC, wicd installation removed it totally and replaced it with the wicd icon.

On 8.10, NM seems to do well, and provides support for a few things that wicd doesn't at this point. So, if you need the extras, stay with NM; otherwise, if you are like me, change to wicd (I just like it better).

---

### Post by tahitiwibble on 2009-01-30
Can't get rid of NM at all .......... should I sudo apt-get remove?

---

### Post by tahitiwibble on 2009-01-31
Good morning.

After the first boot-up of the day I have the same problem even after having installed widc, which is running parallel to NM. NM is still there! Should/can I safely uninstall this?

---

### Post by ugm6hr on 2009-01-31
This is very strange.

Did you install Wicd from their Ubuntu repository?

If so, it should automatically remove network-manager-gnome and network-manager (the system tray icon with drop-down SSIDs).  The Network Monitor (or Network Settings / Manual config) will remain.

However, while I have used Wicd for some chipsets which misbehave under NM, most wifi should be fine with NM since Hardy.

More concerning is that you get an "interface not found" error.  I suspect this might be a hardware issue with eth1.

Show us the results of these (when wifi works, and when it doesn't):
```
cat /etc/network/interfaces
ifconfig
lshw -class network
```

---

### Post by tahitiwibble on 2009-01-31
> **ugm6hr said:**
> This is very strange.

Did you install Wicd from their Ubuntu repository?

If so, it should automatically remove network-manager-gnome and network-manager (the system tray icon with drop-down SSIDs).  The Network Monitor (or Network Settings / Manual config) will remain.

However, while I have used Wicd for some chipsets which misbehave under NM, most wifi should be fine with NM since Hardy.

More concerning is that you get an "interface not found" error.  I suspect this might be a hardware issue with eth1.

Show us the results of these (when wifi works, and when it doesn't):
```
cat /etc/network/interfaces
ifconfig
lshw -class network
```

Hello ugm6hr .... 

1/ I followed the installation instructions on the [wicd website]("http://wicd.sourceforge.net/download.php").

2/ "The Network Monitor (or Network Settings / Manual config) will remain." Upon reflection I think this **may** be the case. How can I be sure?

3/ Re. "when wifi works"

```
dad@dad-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid NETGEAR



iface eth0 inet dhcp
```

```
dad@dad-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:44:04:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:11:50:b1:7c:1b  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:feb1:7c1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18310 errors:293 dropped:11 overruns:0 frame:277
          TX packets:18529 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13141081 (12.5 MB)  TX bytes:2517103 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:455948 (445.2 KB)  TX bytes:455948 (445.2 KB)

dad@dad-desktop:~$
``` 

```
dad@dad-desktop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:e0:4d:44:04:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:11:50:b1:7c:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.5 multicast=yes wireless=IEEE 802.11b/g
dad@dad-desktop:~$ 
```

4/ Re."and when it doesn't" ...... I will have to wait till tomorrow morning when the computer is cold, after a long period of shut down.

---

### Post by ugm6hr on 2009-01-31
1. You can try simulating an installation of NM to ensure it has gone (it will tell you it needs to remove Wicd etc - don't worry, the "-s" means it won't actually do anything), or check for network-manager-gnome in Synaptic.
```
sudo apt-get install -s network-manager-gnome
```

2. See the troubleshooting advice at the top of the Wicd page you linked to re: /etc/network/interfaces

3. What wifi card are you using?  Unusually, lshw lists no driver at all. Post output from:
```
lspci
lsusb
```

---

### Post by tahitiwibble on 2009-01-31
1/ Terminal says that I do not have NM installed yet and wants to remove wicd.

2/ Hmmm ....... I should have paid more attention. Here is the result:

"auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid NETGEAR



iface eth0 inet dhcp



auto eth1"

3/ I am using a Belkin USB "stick".

```
dad@dad-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP [VIA P4M890 Chipset] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
dad@dad-desktop:~$ lsusb
Bus 005 Device 006: ID 0bda:0151 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 050d:705c Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:0a01 Logitech, Inc. Logitech USB Headset
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c30a Logitech, Inc. 
Bus 002 Device 002: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

---

### Post by ugm6hr on 2009-01-31
You have already posted contents of /etc/network/interfaces!  Follow the advice on the Wicd downloads page to remove the unnecssary lines.

You have Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver) USB stick (or perhaps v4001):
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

There appears to be competing evidence as to which driver is required for this device.

When wifi is working - post output from:
```
lsmod
```

---

### Post by tahitiwibble on 2009-01-31
This is becoming intriguing.

I modified the /etc/network/interfaces file as instructed.

I just rebooted and had no connection so using wicd did a manual "connect" ...... all systems "go". However I still have the Network Settings icon in my panel, and subsequently the program, which tells me neither wireless nor cabled nor point to point networks are connected.

Thank you for the time you're according me ugm6hr

```
dad@dad-desktop:~$ lsmod
Module                  Size  Used by
af_packet              23812  2 
binfmt_misc            12808  1 
via                    43648  2 
drm                    82452  3 via
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ipv6                  267908  14 
ppdev                  10372  0 
acpi_cpufreq           10796  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
parport_pc             36260  1 
evdev                  13056  5 
parport                37832  3 ppdev,lp,parport_pc
snd_hda_intel         346136  3 
usb_storage            73792  0 
zd1211rw               56964  0 
libusual               19236  1 usb_storage
ieee80211softmac       30976  1 zd1211rw
snd_usb_audio          83936  1 
snd_seq_dummy           4868  0 
ieee80211              35528  2 zd1211rw,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10500  2 snd_hda_intel,snd_usb_audio
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
usbhid                 32128  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
hid                    38784  1 usbhid
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_hda_intel,snd_usb_audio,snd_seq_dummy,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_usb_lib,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro              9876  0 
soundcore               8800  1 snd
i2c_core               24832  1 i2c_viapro
button                  9232  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
via_agp                11136  1 
agpgart                34760  2 drm,via_agp
ext3                  136840  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  4 
cdrom                  37408  1 sr_mod
pata_via               13316  3 
sata_via               12420  0 
ata_generic             8324  0 
floppy                 59588  0 
ehci_hcd               37900  0 
via_rhine              26632  0 
mii                     6400  1 via_rhine
pata_acpi               8320  0 
uhci_hcd               27024  0 
libata                159600  4 pata_via,sata_via,ata_generic,pata_acpi
usbcore               146412  9 usb_storage,zd1211rw,libusual,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36488  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3
```

---

### Post by ugm6hr on 2009-01-31
You can disregard Network Monitor.  Why is it on your panel?  Did you put a shortcut there yourself?  It is usually restricted to the System -> Administration menu.

lsmod shows "zd1211rw" as being loaded.

Wicd also has an "automatically connect to this network" option - have you ticked that?

If it isn't as simple as that, I wonder whether the problem is that the driver doesn't always load.  Or maybe another driver loads instead and interferes.

When you reboot with no connection - try
```
lsmod | grep zd1211
```

If there is no return, then the driver is not automatically loading at boot, and Wicd is obviously starting it "manually".  To fix this, you could manually add "zd1211rw" to /etc/modules with:
```
sudo echo zd1211rw >> /etc/modules
```

Hopefully, one of those will solve the problem.

---

### Post by tahitiwibble on 2009-01-31
I get the feeling that the problem may have been solved. :)

Yes I did put the shortcut there myself. The command points to "network-admin". The program appears to be totally inoperative.

I'll see what happens tomorrow morning and act accordingly.

**Many** thanks again. :)

---

### Post by ugm6hr on 2009-01-31
> **tahitiwibble said:**
> Yes I did put the shortcut there myself. The command points to "network-admin". The program appears to be totally inoperative.

Wicd essentially replaces this.  But it is integrated into Gnome - so I wouldn't uninstall.

Feel free to remove from panel (and even menu) if you want.

Glad it *appears* things are better.  Hopefully they will remain so in the morning!

And you are welcome :)

---

