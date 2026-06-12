---
title: "Wired internet on Intell NUC Kit D34010WYK intermittently unable to access network"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by fenkod on 2015-07-22
I have Ubuntu 14.04 installed on a [Intel NUC D34010WYK]("http://www.intel.com/content/www/us/en/nuc/nuc-kit-d34010wyk.html") with an Intel Ethernet Gigabit controller. Throughout the week, the install will occasionally act as though it can not access the internet, despite the connection still showing link when looking at the network port on the NUC and the switch nearby.

The ethernet controller information is:

```

[COLOR=#111111][FONT=Consolas][FONT=courier new]> lspci | awk '/net/ {print $1}' | xargs -i% lspci -ks %[/FONT]
[/FONT][/COLOR]00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I218-V (rev 04)
    Subsystem: Intel Corporation Device 2054
    Kernel driver in use: e1000e

```

```

ifconfig
eth0      Link encap:Ethernet  HWaddr c0:3f:d5:6b:3e:4a  
          inet addr:10.0.100.20  Bcast:10.0.100.255  Mask:255.255.255.0
          inet6 addr: fe80::c23f:d5ff:fe6b:3e4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4177412 errors:0 dropped:2 overruns:0 frame:0
          TX packets:3154333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6001422953 (6.0 GB)  TX bytes:1799429989 (1.7 GB)
          Interrupt:20 Memory:f7c00000-f7c20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:311812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:223815664 (223.8 MB)  TX bytes:223815664 (223.8 MB)

```

Looking at dmesg, all I ever seem to see is:

```

[Wed Jul 22 10:08:24 2015] CIFS VFS: Server disk.local has not responded in 120 seconds. Reconnecting...

```

Based on another similar thread, I have run the following commands and will post their output:

```

> lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04d9:1605 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 062a:0252 Creative Labs Emerge Uni-retractable Laser Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

> lsmod
Module                  Size  Used by
des_generic            21163  0 
md4                    12523  0 
nls_utf8               12493  1 
cifs                  410382  2 
fscache                56756  1 cifs
snd_hda_codec_hdmi     45440  1 
snd_hda_codec_realtek    59297  1 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
intel_rapl             18301  0 
x86_pkg_temp_thermal    13845  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm_intel             132651  0 
kvm                   388277  1 kvm_intel
crc32_pclmul           12967  0 
aesni_intel            18156  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
snd_hda_intel          42794  5 
snd_rawmidi            25135  1 snd_seq_midi
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
snd_hda_codec         168221  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
i915                  710018  5 
mac_hid                13037  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
nuvoton_cir            17482  0 
drm_kms_helper         48868  1 i915
rc_core                26724  1 nuvoton_cir
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_timer              28584  2 snd_pcm,snd_seq
mei_me                 18195  0 
drm                   244037  4 i915,drm_kms_helper
video                  18903  1 i915
parport_pc             31981  1 
lpc_ich                16864  0 
ppdev                  17391  0 
mei                    66737  1 mei_me
snd                    60939  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
lp                     13299  0 
i2c_algo_bit           13197  1 i915
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
ahci                   25643  2 
e1000e                223034  0 
libahci                27214  1 ahci
usbhid                 47070  0 
ptp                    18445  1 e1000e
hid                    87604  2 hid_generic,usbhid
pps_core               18799  1 ptp

```

```

> cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

```

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```

> cat /var/lib/NetworkManager/NetworkManager.state 
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

Unfortunately, that's about the only thing I've been able to find that even hints at the problem I'm experiencing. I'm new to Ubuntu and Linux and I've been struggling finding where I should even look to identify the problem. I would really appreciate hints as to what I should look into to find my actual issue.

Please note that if I unplug and replug the ethernet cord, the wired connection connects to the network and the internet like nothing happened.

---

### Post by chili555 on 2015-07-23
I have a NUC as well and found that several minor quirks were fixed when I updated the BIOS to the latest. I urge you to do the same.

 There are several things you might try. The probable solution that seems to work often, but not always, is to disable gigabit speeds. You can try temporarily with```
sudo ethtool --change eth0 speed 100 autoneg off
```
If this is helpful, we will drop the parameters into rc.local to make them persistent.

---

### Post by fenkod on 2015-07-23
Fortunately (unfortunately), the issue has yet to recur. However, I have finished updating the bios to the latest version, so I'll let you know.

---

### Post by fenkod on 2015-07-25
Sometime during the night, the network dropped again. I tried to ping the router when it was exhibiting the problem and saw this:

```

> ping 10.0.100.1
connect: Network is unreachable

```

The link lights were still on and green. As soon as I unplugged and re-plugged the ethernet cord, everything was working as expected,

I'm going to try the ethernet limiting suggestion above.

---

