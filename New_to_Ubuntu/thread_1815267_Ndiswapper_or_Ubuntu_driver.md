---
title: "Ndiswapper or Ubuntu driver?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by asensio on 2011-07-31
Well, I got a TP-Link TL-WN321G v2 Wireless USB adapter and the first thing I did was to install the windows drivers with ndiswrapper. Only after I realized that it should work "out of the box" (and I know it does).


I tried uninstalling ndiswrapper but then the adapter didn't work, probabily because the rt73usb driver needed was "unloaded"

How can I unload ndiswrapper and load the rt73usb module?

Thank you for your help.
Cheers

Oh! I'm running Maverick 10.10

---

### Post by sadaruwan12 on 2011-07-31
First remove the windows drivers from ndsiwrapper then use

```
$ sudo apt-get purge ndsiwrapper
```

to remove the software then restart you computer and after that plug the adapter and see if it works.

---

### Post by lkraemer on 2011-07-31
We need a bit more information to make the proper decisions on what to do.

Will you post the output of:
```
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
iwconfig

```


Depending on what is found there follow this guide:

**REMOVE WINDOWS DRIVERS:**
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


Now you need to check what was blacklisted, and undo anything you previously did......or fix it so the proper driver isn't blacklisted.

Then you can use:
```

sudo nano /etc/modprobe.d/blacklist.conf

```
and add/remove the necessary modules to blacklist.

At this point you can purge ndiswrapper with:
```

sudo apt-get purge ndsiwrapper

```


Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```


Click on the Wifi Icon in the top right toolbar and select the Network.

**Manual Choice:**
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink"

So, we just did what the previous posing stated......but, with a bit
more detail so it would be more likely to come up working, versus a quick
slam dunk.......with hope Ubuntu magically repaired itself.


lkraemer

---

### Post by asensio on 2011-08-01
Thank you both for your reply.

sadaruwan12: Thanks, but that was the first thing I tried with no luck.

lkraemer: here are the outputs

> **lshw -C network**
*-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:22:c6:b9
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 94:0c:6d:e1:85:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.56+TP-LINK,10/21/2008, 1.03.02 ip=192.168.1.76 link=yes multicast=yes wireless=IEEE 802.11g

> **lsmod**
Module                  Size  Used by
binfmt_misc             6599  1 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_multiport            1577  4 
xt_limit                1394  7 
xt_tcpudp               1927  11 
ipt_addrtype            1611  4 
xt_state                1014  7 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
ac97_bus                1014  1 snd_ac97_codec
nf_conntrack_ftp        5361  1 nf_nat_ftp
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1302  1 
snd_seq_midi            4588  0 
ip_tables              10460  1 iptable_filter
i915                  291004  3 
snd_rawmidi            17783  1 snd_seq_midi
x_tables               15921  11 ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
drm                   168054  4 i915,drm_kms_helper
parport_pc             26058  1 
ndiswrapper           184207  0 
dcdbas                  5402  0 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
joydev                  8735  0 
shpchp                 29886  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
floppy                 54311  0 
hid                    67742  1 usbhid
usb_storage            40172  0 
e1000                  97525  0 

> **ndiswrapper -l**
rt73 : driver installed
	device (148F:2573) present (alternate driver: rt2500usb)

> **cat /etc/modprobe.d/blacklist.conf**
# This file lists those modules which we don't want to be loaded by
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

> **cat /etc/modules**
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper

> **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"ThomsonE3A467"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:44:E3:A4:67   
          Bit Rate=18 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I will try this method, thanks. Hope it works...

---

### Post by asensio on 2011-08-01
I tried your method, but no luck. I guess now Ubuntu doesn't recognizes my wireless adapter. Here are some outputs after I got rid of ndiswrapper...

> **lshw -C network**
*-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:22:c6:b9
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)

**lsmod**
Module                  Size  Used by
binfmt_misc             6599  1 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_multiport            1577  4 
xt_limit                1394  7 
xt_tcpudp               1927  11 
ipt_addrtype            1611  4 
xt_state                1014  7 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
snd_intel8x0           25632  2 
nf_nat_irc              1168  0 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
nf_conntrack_irc        3348  1 nf_nat_irc
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
i915                  291004  3 
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5361  1 nf_nat_ftp
snd_seq_midi            4588  0 
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_rawmidi            17783  1 snd_seq_midi
iptable_filter          1302  1 
snd_seq_midi_event      6047  1 snd_seq_midi
ip_tables              10460  1 iptable_filter
drm_kms_helper         30200  1 i915
x_tables               15921  11 ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
ndiswrapper           184207  0 
dcdbas                  5402  0 
parport_pc             26058  1 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
joydev                  8735  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
i2c_algo_bit            5168  1 i915
shpchp                 29886  0 
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
e1000                  97525  0 
floppy                 54311  0 
hid                    67742  1 usbhid
usb_storage            40172  0 

 
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

Why is ndiswrapper in the Modules if I purged it?

---

### Post by lkraemer on 2011-08-01
First of all your wlan1 was up and connected.  You posted:
> 
wlan1 IEEE 802.11g ESSID:"ThomsonE3A467"
Mode:Managed Frequency:2.462 GHz Access Point: 00:26:44:E3:A4:67
Bit Rate=18 Mb/s Tx-Power:20 dBm Sensitivity=-121 dBm
RTS thr=2347 B Fragment thr=2346 B
Power Managementff
Link Quality:18/100 Signal level:-84 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

So, at this point you should have tried:
```

ping www.yahoo.com -c3
ping 209.191.122.70 -c3

```
to see what was happening.  If those commands didn't work you needed to
check your DNS Server settings.

BUT......you instantly purged as previously posted instead of an orderly removal of the drivers ad ndiswrapper.
Ndiswrapper is still in your modules list because it wasn't removed as I posted.  You should have done:
```

sudo ndiswrapper -e rt73
sudo ndiswrapper -e rt2500usb

```

then did another:
```

ndiswrapper -l

```
until no drivers were displayed.  At that point you should have removed
ndiswrapper.
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing /etc/modules:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

At this point you should have purged ndiswrapper with:
```

sudo apt-get purge ndiswrapper

```

So, edit /etc/modules and remove ndiswrapper, then reboot with your USB
Dongle removed.  That will remove ndiswrapper from the lsmod display listing.

Then try:
Plug in your USB Dongle and do the following:
```

dmesg | tail
lsusb

```
Your device will be something like this:
```

Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
Now, cut and paste the following command in your Linux Terminal Window, substituting your info:
```

lsusb -v -d 058f:9720

```


**Manual Choice:**
If you know the routers essid and the correct <interface=wlan1>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig wlan1 down
sudo dhclient -r wlan1
sudo iwconfig wlan1 essid "ThomsonE3A467"
sudo iwconfig wlan1 mode Managed
sudo ifconfig wlan1 up
sudo dhclient wlan1
iwconfig

```
then try:
```

ping www.yahoo.com -c3
ping 209.191.122.70 -c3

```

Then try:
```

route
route -n
route -nee
netstat -r
ping yourgatewayIPaddress

```
and post the results of the last 7 commands if it doesn't work.

lk

---

### Post by asensio on 2011-08-03
Thank you, lkraemer. Using your new guide:

> **dmesg | tail**
[   30.512220] EXT4-fs (sdb1): re-mounted. Opts: commit=0
[   32.582404] render error detected, EIR: 0x00000010
[   32.582418] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[   32.582456] render error detected, EIR: 0x00000010
[   66.404574] usb 1-3: new high speed USB device using ehci_hcd and address 4
[   66.722965] Disabling lock debugging due to kernel taint
[   66.734912] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   66.737231] usbcore: registered new interface driver ndiswrapper
[  211.622603] usb 1-3: USB disconnect, address 4
[  224.488040] usb 1-3: new high speed USB device using ehci_hcd and address 5

ndiswrapper keeps loaded???? but, but....

**this is my /etc/modules**
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


> **lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 002: ID 13fd:2040 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**lsusb -v -d 148f:2573**
Bus 001 Device 005: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2573 RT2501/RT2573 Wireless Adapter
  bcdDevice            0.01
  iManufacturer           1 Ralink
  iProduct                2 54M.USB.......
  iSerial                 3 12345
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

**sudo ifconfig wan1 down**
wan1: ERRO enquanto obtinha as opções de interface: Dispositivo inexistente

**sudo dhclient -r wan1**
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Bind socket to interface: No such device

**sudo iwconfig wan1 essid "ThomsonE3A467"**
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wan1 ; No such device.

**sudo iwconfig wan1 mode Managed**
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wan1 ; No such device.

**sudo ifconfig wan1 up**
wan1: ERRO enquanto obtinha as opções de interface: Dispositivo inexistente

**sudo dhclient wan1**
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
wan1: ERROR while getting interface flags: No such device
wan1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

**ping [www.yahoo.com](www.yahoo.com) -c3**
ping: unknown host [www.yahoo.com](www.yahoo.com)

**ping 209.191.122.70 -c3**
connect: Network is unreachable

**route**
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface

**route -n**
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface

**route -nee**
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen     Opções Métrica Ref   Uso Iface    MSS   Janela irtt

**netstat -r**
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções   MSS Janela  irtt Iface

**ping 192.168.1.254**
connect: Network is unreachable


I guess it's better that I keep ndiswrapper...

---

### Post by lkraemer on 2011-08-03
OOPS....I had a typo.....I had wan1 and it should be wlan1.

Try those commands again.  Just make sure wlan1 is correct.


Why don't you boot from the LiveCD, and when everything is up,
then plug in your USB device, and then see if it is recognized 
and is functional?  That would be an easy test.

Then you could use lsmod and dmesg | tail for more information.

lk

---

