---
title: "Ubuntu Server 14.04 No Connection"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by oldpilsbury on 2014-08-09
Asus A53E Series

New install of Ubuntu Server 14.04.1 64-bit. No wireless connection. No ethernet connection.
I can't find a wireless on/off switch anywhere on the computer. 3.13.0-32-generic

#/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto virbr0
iface virbr0 inet loopback

auto wlan0
iface wlan0 inet loopback

#ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1824 (1.8 KB)  TX bytes:1824 (1.8 KB)

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:9e:03:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

#ifconfig wlan0 down
no talloc stackfram at ../source3/param/loadparm.c:4864, leaking memory

#iwlist wlan0 scan
wlan0     No scan results

#iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
#lspci | grep Network 
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

#lsmod
Module                  Size  Used by
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
arc4                   12608  2 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
ath9k                 164164  0 
coretemp               13435  0 
crct10dif_pclmul       14289  0 
snd_hda_codec_hdmi     46254  1 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec_realtek    61438  1 
joydev                 17381  0 
mac80211              630653  1 ath9k
serio_raw              13462  0 
snd_hda_intel          52355  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
uvcvideo               80885  0 
snd_hwdep              13602  1 snd_hda_codec
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_core         40664  1 uvcvideo
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i915                  783805  1 
videodev              134688  2 uvcvideo,videobuf2_core
cfg80211              484040  3 ath,ath9k,mac80211
lpc_ich                21080  0 
snd_timer              29482  1 snd_pcm
drm_kms_helper         53081  1 i915
snd                    69238  7 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
soundcore              12680  1 snd
drm                   303102  2 i915,drm_kms_helper
mei_me                 18627  0 
mei                    82276  1 mei_me
i2c_algo_bit           13413  1 i915
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42348  1 lp
usb_storage            62209  0 
psmouse               106678  0 
atl1c                  46086  0 
ahci                   25819  2 
libahci                32560  1 ahci

---

### Post by chili555 on 2014-08-10
> #/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto virbr0
iface virbr0 inet loopback

auto wlan0
iface wlan0 inet loopbackFirst of all, only lo is loopback, all normal interfaces like wlan0 and eth0 are either DHCP or static.

Is this a virtual machine? What is virbr0 for?

At the minimum, you need to specify what network and what network password you want to connect to in a wireless setting. To start, I'd try this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid myroutername
wpa-psk mysecretkey
```Restart the interface, or reboot, to get the system to re-read the file:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```Did you connect? Check:```
ping -c3 8.8.8.8
ping -c3 www.google.com
```Once we have you reliably connected, let's set up a static IP address as servers should have so you can find them.

---

### Post by oldpilsbury on 2014-08-11
Thanks, the loopback was an error on my part, although I did not know about the next two lines. I'm not sure where virbr0 came from but it came up in one of the iwconfig/ifconfig commands upon install I believe. This is just a little project I put together to teach my students and fellow teachers ssh, sftp, and a few bash commands. I decided Linux Mint made more sense for our purposes. (I was going to install a desktop environment anyhow, although it would have been nice to walk my sixth graders through the process.) I shouldn't need a static ip, should I? I'm just working over a local area network.

Greetings and thanks from Honduras!

---

### Post by chili555 on 2014-08-12
>  I'm not sure where virbr0 came from but it came up in one of the iwconfig/ifconfig commands upon install I believe.What is reported now that the system is installed?```
ifconfig
```If this is a normal install to a harddrive and not any kind of virtual machine, then you won't see virbr0. [http://askubuntu.com/questions/246343/what-is-the-virbr0-interface-used-for](http://askubuntu.com/questions/246343/what-is-the-virbr0-interface-used-for)>  I shouldn't need a static ip, should I? I'm just working over a local area network.How, then, were you going to ssh or ftp to the server? By hostname?```
ssh -l user mylittleserver.local
```That has some problems of its own, especially if some of the machines are of the Windows persuasion; please see: [http://askubuntu.com/questions/144280/cannot-ssh-into-ubuntu-server-by-hostname](http://askubuntu.com/questions/144280/cannot-ssh-into-ubuntu-server-by-hostname)

Servers usually have static IPs; and by 'usually,' I mean 99.9%, more or less. It is quite simple, actually:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.120  [COLOR="#FF0000"]<-- an address outside the DHCP pool in the router or switch[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
wpa-ssid myroutername
wpa-psk mysecretkey
```Then *any* machine with an FTP client or *any* machine with ssh can reach 192.168.1.120. 

So, after you made the change I suggested, did you connect?

---

### Post by oldpilsbury on 2014-08-13
Maybe I wasn't clear. I wiped Ubuntu Server and installed Linux Mint  Cinnamon because network administration is still a little over my head,  and the server is not actually offering any services, other than file  transfers, perhaps.

```
#ifconfig
eth0      Link encap:Ethernet  HWaddr e8:03:9a:9b:31:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1213535 (1.2 MB)  TX bytes:1213535 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr e8:03:9a:84:a0:43  
          inet addr:192.168.0.115  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea03:9aff:fe84:a043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:182056604 (182.0 MB)  TX bytes:11653590 (11.6 MB)

```

I can access remotely via
ssh username@192.168.0.115
and enter password (using ifconfig or nmap to learn ip address if it changes).

I'm going to mark this thread solved. I'll consider implementing a static ip the next time I install Ubuntu Server.

Thank you.):P

---

