---
title: "Wired network randomly disconnects"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by toodh on 2015-03-24
My wired Ethernet internet connection works fine for maybe an hour and then disconnects. If I go to the Network manager and disable and then re-enable networking, then it the internet connection works again for a while.

I did a lot of research but none of the posts describes the same problem. I am running Kubuntu 12.04 LTS. Here is the output of some commands when the connection is down, but I dont understand much of it. Note in particular the errors in dmesg.

uname -a
```
 Linux moria 3.2.0-77-generic #114-Ubuntu SMP Tue Mar 10 17:26:03 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux 
```

lspci -nnk | grep -iA2 net
```

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
        Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
        Kernel driver in use: r8169

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr c8:60:00:6b:21:d2  
          inet addr:82.130.121.153  Bcast:82.130.121.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fe6b:21d2/64 Scope:Link
          inet6 addr: 2001:67c:10ec:3c91:8000::1046/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1885590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3357414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:664945101 (664.9 MB)  TX bytes:3761377899 (3.7 GB)
          Interrupt:58 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6356355 (6.3 MB)  TX bytes:6356355 (6.3 MB)

```

lsmod
```

Module                  Size  Used by
cdc_acm                26857  0 
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  2 
cifs                  287412  4 
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             25670  0 
vboxnetflt             23478  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
snd_hda_codec_hdmi     32530  4 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bluetooth             180113  10 bnep,rfcomm
nfsd                  282215  2 
nfs                   436999  0 
lockd                  90326  2 nfsd,nfs
fscache                61529  1 nfs
auth_rpcgss            53380  2 nfsd,nfs
nfs_acl                12883  2 nfsd,nfs
binfmt_misc            17540  1 
sunrpc                255272  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
nvidia              11359705  41 
snd_hda_codec_realtek   224261  1 
v4l2_compat_ioctl32    17128  1 videodev
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_usb_audio         123020  1 
snd_usbmidi_lib        29476  1 snd_usb_audio
joydev                 17693  0 
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  2 snd_usb_audio,snd_hda_codec
psmouse                98133  0 
serio_raw              13211  0 
snd_pcm                97275  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79081  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
mei                    41616  0 
wmi                    19256  1 asus_wmi
shpchp                 37201  0 
hwmon_vid              12827  0 
coretemp               13554  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_microsoft          12888  0 
usbhid                 47238  0 
hid                    99883  2 hid_microsoft,usbhid
usb_storage            49198  0 
video                  19651  0 
r8169                  62190  0 

```


tail -n 20 /var/log/dmesg
```

[    4.707253] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    4.740186] type=1400 audit(1426774336.190:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1343 comm="apparmor_parser"
[    4.740308] type=1400 audit(1426774336.190:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=1343 comm="apparmor_parser"
[    4.740409] type=1400 audit(1426774336.190:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1347 comm="apparmor_parser"
[    4.742847] Bluetooth: Core ver 2.16
[    4.742857] NET: Registered protocol family 31
[    4.742857] Bluetooth: HCI device and connection manager initialized
[    4.742859] Bluetooth: HCI socket layer initialized
[    4.742859] Bluetooth: L2CAP socket layer initialized
[    4.742862] Bluetooth: SCO socket layer initialized
[    4.743652] Bluetooth: RFCOMM TTY layer initialized
[    4.743654] Bluetooth: RFCOMM socket layer initialized
[    4.743655] Bluetooth: RFCOMM ver 1.11
[    4.744680] ppdev: user-space parallel port driver
[    4.790160] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.790163] Bluetooth: BNEP filters: protocol multicast
[    4.906957] r8169 0000:05:00.0: eth0: link down
[    4.906963] r8169 0000:05:00.0: eth0: link down
[    4.907581] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.907724] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:6b:21:d2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:58 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff

```

---

### Post by toodh on 2015-03-26
No answer so far... please help! I forgot to say that the system has worked perfectly fine for the last 1.5 years and the network problem just appeard about 2 weeks ago. This is my main work machine, so this network problem has a real impact on my work productivity...

---

### Post by ian77 on 2015-03-26
The logs report the ethernet link going down.

So it could either be an issue with the physical cable, the network card (at either end) or the negotiation.

The ifconfig stats for your connection show no errors, which is good. 
The other side of the link may be dropping out. I assume it goes to a router or switch? What are the port statistics for that device? does it show physical link errors, input drops, CRC errors etc? If so then you probably have a bad cable. So I would definately check the other side of the link too.

Does the physical link activity light actually go out on both sides?

---

### Post by toodh on 2015-03-27
I had our IT support check the connection, and everything outside of my PC seems to work perfectly fine (cable, etc). The physical link activity lights (one yellow and one green) on my PC are on even when the connection is down. So what now?

---

### Post by praseodym on 2015-03-27
Change the driver via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by toodh on 2015-03-30
I will try as soon as I am back and have access to the machine, and post the results here.

---

