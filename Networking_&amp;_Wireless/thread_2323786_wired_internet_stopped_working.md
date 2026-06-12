---
title: "wired internet stopped working"
date: 2016-05-08
forum: Networking &amp; Wireless
---

### Post by TaiChiRabbit on 2016-05-08
Hello

 Unfortunately I’ve lost my wired internet connection (it has no wifi connection) on my desktop Ubuntu 16.04.  The frustrating part is that I’ve tested the cable with my laptop and it works fine (I’m using it to send this post) and when using a Live CD on my desktop the internet connection also works fine.  On my desktop browser (Firefox) I can still access other machines on the LAN, eg my router at 192.168.0.100, but get Server Not Found when I try to access internet via Firefox (Thunderbird email also not working). Not sure whether it is relevant but I downloaded an update for HP printer Device Manager on the desktop before I lost the Internet connection.

 I think I’ve tried most things: reboot router and desktop, edited the ipv6 settings on network manager (from automatic to ignore and back again). So now totally stuck and grateful for any further ideas.  I hope the outputs below are sufficient to give some clues and were done with the ethernet cable plugged in to the desktop pc.  Thank you.
 
 
 ifconfig
 ```

 eth0      Link encap:Ethernet  HWaddr 48:5b:39:d2:05:1b   
           inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
           inet6 addr: fe80::fe57:362:ab42:f755/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:11430 errors:0 dropped:0 overruns:0 frame:0
           TX packets:3534 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:3478698 (3.4 MB)  TX bytes:1373016 (1.3 MB)
 
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:86944 errors:0 dropped:0 overruns:0 frame:0
           TX packets:86944 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1  
           RX bytes:6685108 (6.6 MB)  TX bytes:6685108 (6.6 MB)
 
```
 
 
 cat /etc/network/interfaces
 ```

 # interfaces(5) file used by ifup(8) and ifdown(8)
 auto lo
 iface lo inet loopback
 
```
 
 
 sudo lshw -C network
 ```

   *-network
        description: Ethernet interface
        product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eth0
        version: 03
        serial: 48:5b:39:d2:05:1b
        size: 100Mbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.0.111 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
        resources: irq:39 ioport:d800(size=256) memory:f4fff000-f4ffffff memory:f4ff8000-f4ffbfff memory:f7cf0000-f7cfffff
 
```
 
 
 cat /etc/NetworkManager/NetworkManager.conf
 ```

 [main]
 plugins=ifupdown,keyfile,ofono
 dns=dnsmasq
 
 
 [ifupdown]
 managed=false
 
```
 
 
 cat /var/lib/NetworkManager/NetworkManager.state
 ```

 [main]
 NetworkingEnabled=true
 WirelessEnabled=true
 WWANEnabled=true
 WimaxEnabled=true
 
```

---

### Post by praseodym on 2016-05-08
Download the packages dkms and r8168-dkms, install them, blacklist r8169 and reboot

[http://packages.ubuntu.com/xenial/r8168-dkms](http://packages.ubuntu.com/xenial/r8168-dkms)

---

### Post by TaiChiRabbit on 2016-05-08
Thank you.  Ubuntu novice so need some help on the install process,

have downloaded:

dkms_2.2.0.3.orig.tar.gz
r8168_8.041.00.orig.tar.bz2


However when I try to install get following error:
```

&#65279;dkms ldtarball ~/Downloads/dkms_2.2.0.3.orig.tar.gz
Error! No valid dkms.conf in dkms_source_tree or dkms_binaries_only.
/home//Downloads/dkms_2.2.0.3.orig.tar.gz is not a valid DKMS tarball.

```

when I try to install r8168 files i get the following error 
```

Check old driver and unload it.
rmmod r8169
Build the module and install
make[2]: *** No rule to make target 'kernel/drivers/net/ethernet/realtek'. Stop.
make[1]: *** [install] Error 2
make: *** [install] Error 2

```


To "blacklist" do i just insert
```

blacklist r8169

```
to the blacklist.conf file in /etc/modprobe.d

---

### Post by praseodym on 2016-05-08
Download these:

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.041.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.041.00-1_all.deb)

Save them in "Downloads" and run
```

sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by TaiChiRabbit on 2016-05-08
...thanks  for very clear instructions, which installed smoothly, unfortunately on reboot still no internet access.

---

### Post by praseodym on 2016-05-08
Lets check:
```

lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
grep r8 /etc/modprobe.d/*
cat /etc/modules
```

---

### Post by TaiChiRabbit on 2016-05-08
lsmod
```

Module                  Size  Used by
snd_seq_dummy          16384  0
nls_iso8859_1          16384  0
nvidia_uvm            696320  0
snd_hda_codec_hdmi     53248  1
nvidia_modeset        745472  3
nvidia              10076160  60 nvidia_modeset,nvidia_uvm
coretemp               16384  0
kvm_intel             172032  0
input_leds             16384  0
snd_hda_codec_via      24576  1
snd_hda_codec_generic    77824  1 snd_hda_codec_via
kvm                   536576  1 kvm_intel
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
irqbypass              16384  1 kvm
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
serio_raw              16384  0
i7core_edac            24576  0
snd_seq                69632  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
edac_core              53248  2 i7core_edac
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   360448  3 nvidia
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                24576  0
soundcore              16384  1 snd
8250_fintek            16384  0
asus_atk0110           20480  0
binfmt_misc            20480  1
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
psmouse               126976  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
pata_acpi              16384  0
ahci                   36864  0
pata_jmicron           16384  0
uas                    24576  0
libahci                32768  1 ahci
r8168                 487424  0
usb_storage            69632  1 uas
fjes                   28672  0

```
ifconfig -a 
```

eth0      Link encap:Ethernet  HWaddr 48:5b:39:d2:05:1b  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b4e6:de4d:437b:cacb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:514848 (514.8 KB)  TX bytes:842400 (842.4 KB)
          Interrupt:39 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:27571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2107536 (2.1 MB)  TX bytes:2107536 (2.1 MB)

```
cat /etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
cat  /etc/resolv.conf
```

nothing! 

```
route -n 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

```
grep r8 /etc/modprobe.d/*
```

/etc/modprobe.d/blacklist.conf:blacklist r8169
/etc/modprobe.d/r8168-dkms.conf:# settings for r8168-dkms
/etc/modprobe.d/r8168-dkms.conf:# map the specific PCI IDs instead of blacklisting the whole r8169 module
/etc/modprobe.d/r8168-dkms.conf:alias    pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*    r8168
/etc/modprobe.d/r8168-dkms.conf:alias    pci:v000010ECd00008168sv*sd*bc*sc*i*            r8168
/etc/modprobe.d/r8168-dkms.conf:# to blacklist the whole r8169 module
/etc/modprobe.d/r8168-dkms.conf:#blacklist r8169

```
route -n 
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

```

---

### Post by praseodym on 2016-05-08
The nameservers are missing:
```

echo "nameserver 192.168.0.1" | sudo tee -a /etc/resolv.conf
```

---

### Post by TaiChiRabbit on 2016-05-08
YES!!!!!!!!!!!!
Praseodym you are an ubuntu genius, ninja and yoda rolled into one.  Thank you.

---

