---
title: "Cant connect to internet"
date: 2017-08-16
forum: Networking &amp; Wireless
---

### Post by warmango on 2017-08-16
When using ubuntu17
I try to connect to unsecured WIFI (My house) it shows im connectedbut when i try to go online, it doesnt load anything, any ideas? im using a laptop right now with a Win10 Ubuntu dualboot

---

### Post by &amp;KyT$0P# on 2017-08-16
Do you use a USB Wi-Fi adapter?  If so, see [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513").

---

### Post by warmango on 2017-08-16
Nope, i use the Laptops built in Wifi receiver, which works fine for Windows

---

### Post by genericvii143 on 2017-08-16
Greetings... first wrong  section  but however can you put in the terminal   "ifcofing" and "iwconfig"  also "rfkill list"   and post the result also give us more information about your PC. Open the Driver Manager and show us what is it says. 

Cheers.

---

### Post by wildmanne39 on 2017-08-16
*Thread moved to **Networking & Wireless**.*

Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by Andreyshel on 2017-08-17
> [COLOR=#000000]but when i try to go online, it doesnt load anything, [/COLOR]
Can you use ping?
try to run

ping 8.8.8.8
and then

ping [www.google.com](www.google.com)  

in the terminal

Thanks.

---

### Post by warmango on 2017-08-19
When i run Ping 8.8.8.8 and Ping [www.google.com](www.google.com), i get this 

```
zach@zach-Satellite-L955:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=77.9 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=52.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=564 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=58 time=385 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=58 time=45.3 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=58 time=126 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=58 time=44.8 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=58 time=52.0 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=58 time=155 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=58 time=51.7 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=58 time=45.1 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=58 time=681 ms
64 bytes from 8.8.8.8: icmp_seq=16 ttl=58 time=53.2 ms
64 bytes from 8.8.8.8: icmp_seq=17 ttl=58 time=45.6 ms
64 bytes from 8.8.8.8: icmp_seq=18 ttl=58 time=184 ms
```
((Continues like this forever))


zach@zach-Satellite-L955:~$ ping [www.google.com](www.google.com)


ping: [www.google.com:](www.google.com:) Name or service not known

---

### Post by wildmanne39 on 2017-08-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by warmango on 2017-08-19
Oh sorry, heres me running the other commands 

```
  zach@zach-Satellite-L955:~$ ifcofingifcofing: command not found
zach@zach-Satellite-L955:~$ iwconfig
enp1s0    no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:"dlink"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: D8:FE:E3:80:58:3A   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


zach@zach-Satellite-L955:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
zach@zach-Satellite-L955:~$ 
```

and i thank you for moving this thread over to the correct area

---

### Post by wildmanne39 on 2017-08-19
Your welcome, please read post 5.

Thanks

---

### Post by Andreyshel on 2017-08-20
> [COLOR=#000000]When i run Ping 8.8.8.8 and Ping [/COLOR][www.google.com]("http://www.google.com/")[COLOR=#000000], i get this [/COLOR]
Please, show the contents of /etc/resolv.conf file(while you are connected).
Command to do that is:
cat /etc/resolv.conf

---

### Post by warmango on 2017-08-20
Oh, just noticed the second page, i am unable to use a wired connection as i own no Ethernet cables and my router is a cluster**** of wires and postioning, i only touch it when it needs to be fixed

---

### Post by wildmanne39 on 2017-08-20
Can you tether your cell phone through an usb port? I have done it the connections are very fast that way.

---

### Post by warmango on 2017-08-20
I have a Cricket Wireless ZTE Sonata 3, I do not have tethering, The only tether i have is EasyTether but i never got that to work on Ubuntu. and i can only access UNSECURED links, which the Repository is secured

If it can be packaged i can throw it onto USB then boot into ubuntu and install it

---

### Post by wildmanne39 on 2017-08-20
We will skip the wireless script and do it old school.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by warmango on 2017-08-20
Okay, give me a moment

```
zach@zach-Satellite-L955:~$ cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu 17.04"
Linux zach-Satellite-L955 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
zach@zach-Satellite-L955:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Toshiba America Info Systems AR8162 Fast Ethernet [1179:ff1e]
	Kernel driver in use: alx
	Kernel modules: alx
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8212]
	Kernel driver in use: rtl8192ce
zach@zach-Satellite-L955:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a43 Importek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0781:5575 SanDisk Corp. 
Bus 003 Device 002: ID 276d:1160  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
zach@zach-Satellite-L955:~$ iwconfig
wlp2s0    IEEE 802.11  ESSID:"dlink"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: D8:FE:E3:80:58:3A   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


enp1s0    no wireless extensions.


zach@zach-Satellite-L955:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
zach@zach-Satellite-L955:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
uas                    24576  0
usb_storage            69632  2 uas
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  3
intel_rapl             20480  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
intel_cstate           20480  0
snd_seq_midi           16384  0
intel_rapl_perf        16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
arc4                   16384  2
input_leds             16384  0
joydev                 20480  0
serio_raw              16384  0
rtl8192ce              57344  0
rtl_pci                28672  1 rtl8192ce
rtl8192c_common        49152  1 rtl8192ce
rtlwifi                73728  3 rtl_pci,rtl8192ce,rtl8192c_common
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              782336  3 rtl_pci,rtl8192ce,rtlwifi
snd_timer              32768  2 snd_seq,snd_pcm
lpc_ich                24576  0
cfg80211              602112  2 mac80211,rtlwifi
mei_me                 40960  0
toshiba_acpi           45056  0
snd                    77824  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
sparse_keymap          16384  1 toshiba_acpi
soundcore              16384  1 snd
mei                   102400  1 mei_me
shpchp                 36864  0
industrialio           69632  1 toshiba_acpi
toshiba_bluetooth      16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   114688  2 hid_generic,usbhid
i915                 1449984  92
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
psmouse               139264  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  1
drm                   352256  11 i915,drm_kms_helper
libahci                32768  1 ahci
alx                    45056  0
mdio                   16384  1 alx
video                  40960  2 toshiba_acpi,i915
wmi                    16384  1 toshiba_acpi
fjes                   73728  0
zach@zach-Satellite-L955:~$ 
```

Here is EVRY thing i get back

I trust the comunity more than i trust windows for their own stuff

---

### Post by wildmanne39 on 2017-08-20
Need to open the NetworkManager file with your text editor because there is a bug in 17.04 network manager:
  
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot

Thanks

---

### Post by warmango on 2017-08-20
alright thanks, ill do it in a bit, away from home shopping

---

### Post by warmango on 2017-08-20
Okay, that DID NOT work, i am connected to the wifi like usual, but no webpage will load

screen shot
[https://drive.google.com/open?id=0B_WG7MyjS7QwcVFDbzg3QTRNMG8](https://drive.google.com/open?id=0B_WG7MyjS7QwcVFDbzg3QTRNMG8)

---

### Post by &amp;KyT$0P# on 2017-08-20
If you click the Wi-Fi icon in upper right of your screenshot and go to "Connection information", what does it show for DNS?

Also please post the output of the following commands -
```
ls -la /etc/resolv.conf
cat /etc/resolv.conf
```

---

### Post by warmango on 2017-08-21
give me a moment

---

### Post by warmango on 2017-08-21
```
zach@zach-Satellite-L955:~$ ls -la /etc/resolv.conf
 lrwxrwxrwx 1 root root 29 Aug 21  2017 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
 zach@zach-Satellite-L955:~$ cat /etc/resolv.conf
 # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
 #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
 # 127.0.0.53 is the systemd-resolved stub resolver.
 # run "systemd-resolve --status" to see details about the actual nameservers.
 
 
 nameserver 127.0.0.53

```
DNS is 10.0.0.1
I even tried installing an older version, same error. Found out thagt the AirDroid App could enable a free hotspot, if slow, it works so running APT-GET Update

---

### Post by &amp;KyT$0P# on 2017-08-22
So far so good.  Now please post the output of these commands -
```
cat /etc/systemd/resolved.conf
systemd-resolve --status
```

---

### Post by warmango on 2017-08-22
```
zach@zach-Satellite-L955:~$ cat /etc/systemd/resolved.conf#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details


[Resolve]
#DNS=
#FallbackDNS=8.8.8.8 8.8.4.4 2001:4860:4860::8888 2001:4860:4860::8844
#Domains=
#LLMNR=yes
#DNSSEC=allow-downgrade
#Cache=yes
#DNSStubListener=udp

zach@zach-Satellite-L955:~$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal

```

This is what it says on my home n
network, for some reason i only have this problem on My HOME network

---

### Post by &amp;KyT$0P# on 2017-08-22
Do you have NetworkManager set to use dnsmasq for DNS?  If so see [this thread]("https://ubuntuforums.org/showthread.php?t=2359238") to get that working in 17.04.

---

