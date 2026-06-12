---
title: "Removed Wine 1.8 and broke my install and WiFi"
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by steven-misshula on 2015-12-22
Hi All,

A few days ago I removed Wine 1.8 from my Toshiba Satellite - this broke my install where I had an ldap / dpkg error.

I just got that resolved, but now I'm still without wifi.

Using the GUI for Networking, I can turn, "Airplane Mode" off, which should enable wifi -- but does NOT... grrr.

Looking around I found the following page 
[http://askubuntu.com/questions/294257/connect-to-wifi-network-through-ubuntu-terminal](http://askubuntu.com/questions/294257/connect-to-wifi-network-through-ubuntu-terminal) 
[B]
From Step #2[/B]
command:

```
ifconfig wlan0
```

gets me:
```

wlan0     Link encap:Ethernet  HWaddr 4c:ed:de:93:76:66  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

[B]And from Step #3

[/B]```

iwconfig wlan0 essid name key password
```

of course using correct name and password....  ;-)

OUTPUT:

```

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
```


Any thoughts?

Many thanks in advance.

Steve

---

### Post by praseodym on 2015-12-23
Please run the wireless-script from the sticky-thread and show the outputs

---

### Post by steven-misshula on 2015-12-23
Hi Praseodym,

Thanks for the response.

I'm at work right now and don't have the machine in question with me... but...
> 
the wireless-script from the sticky-thread

I'm not sure what that means...I searched and found:

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

Is that what you mean?

Best,
Steve

---

### Post by steven-misshula on 2015-12-23
I forgot to mention, I have run the following:

```
sudo apt-get update
sudo apt-get dist-upgrade
```
And to no avail...  :-(

As well as:

```
 sudo apt-get --fix-broken install
``` ```
 	 	 sudo apt-get -f install 

``````
 sudo apt-get clean 


```

---

### Post by praseodym on 2015-12-23
Yes, that script

---

### Post by steven-misshula on 2015-12-23
OK....

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info 
```

Yields the following output:

```
--2015-12-23 21:36:13--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.252.128
Connecting to github.com (github.com)|192.30.252.128|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2015-12-23 21:36:14--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 23.235.39.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|23.235.39.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2015-12-23 21:36:14--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Reusing existing connection to raw.githubusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[=====================>]  15.50K  --.-KB/s   in 0s     

2015-12-23 21:36:14 (52.0 MB/s) - ‘wireless-info’ saved [15868/15868]


Results saved in "/home/estelle/wireless-info.txt".

Results also archived in "/home/estelle/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

```[ATTACH]266342[/ATTACH]

---

### Post by Vladlenin5000 on 2015-12-24
It's the contents of the generated 'wireless-info.txt' that are needed to start troubleshooting. You can either attach the file or copy its contents in a new post.

---

### Post by praseodym on 2015-12-24
Can you reset your BIOS to default settings? Please show

```
lsmod

```
completely

---

### Post by steven-misshula on 2015-12-24
```

lsmod
```

Yields the following:

```



Module                  Size  Used by
nvram                  16384  0
msr                    16384  0
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  1
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_conntrack_ipv4      16384  1
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack          106496  4 nf_nat,nf_nat_ipv4,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
xt_tcpudp              16384  5
bridge                114688  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  6 xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,iptable_filter,iptable_mangle
binfmt_misc            20480  1
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
arc4                   16384  2
rtl8192ce              57344  0
rtl_pci                28672  1 rtl8192ce
intel_rapl             20480  0
rtl8192c_common        53248  1 rtl8192ce
iosf_mbi               16384  1 intel_rapl
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
rtlwifi                77824  3 rtl_pci,rtl8192c_common,rtl8192ce
mac80211              733184  3 rtl_pci,rtlwifi,rtl8192ce
snd_hda_intel          36864  3
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
coretemp               16384  0
snd_hda_core           65536  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
crct10dif_pclmul       16384  0
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
cfg80211              548864  2 mac80211,rtlwifi
crc32_pclmul           16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
cryptd                 20480  0
snd                    81920  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
input_leds             16384  0
soundcore              16384  1 snd
mei_me                 32768  0
joydev                 20480  0
serio_raw              16384  0
mei                    98304  1 mei_me
sparse_keymap          16384  0
shpchp                 36864  0
toshiba_bluetooth      16384  0
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
ums_realtek            20480  0
uas                    24576  0
usb_storage            69632  2 uas,ums_realtek
i915                 1130496  3
psmouse               126976  0
ahci                   36864  2
libahci                32768  1 ahci
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
r8169                  81920  0
mii                    16384  1 r8169
drm                   356352  5 i915,drm_kms_helper
wmi                    20480  0
video                  36864  1 i915


```

---

### Post by praseodym on 2015-12-24
Please check
```

sudo modprobe -v toshiba_acpi
sudo rfkill unblock all
```

---

### Post by steven-misshula on 2015-12-24
and....

```

sudo modprobe -v toshiba_acpi
sudo rfkill unblock all
```



Gets me the following:

```

modprobe: ERROR: could not insert 'toshiba_acpi': No such device


```

---

### Post by steven-misshula on 2015-12-24
Hi - sorry for this...

this is resolved.  I spoke with someone who pointed out that this was hardware blocked...i.e. - Function key and F8 key unlocked and ta da....

Merry Christmas! :o

---

