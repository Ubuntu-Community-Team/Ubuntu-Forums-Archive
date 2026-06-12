---
title: "no wireless card detected wubi unbuntu 9.1 - help!"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by annoluce on 2010-03-19
this is driving me absolutely insane.
this is the first time i've used linux, i've got windows xp sp3 and i'm running wubi 9.1 on my eeepc (so no cd drive), i don't want to lose xp and just want linux for occasional use so i don't want to do a proper install, would my wireless card work out the box with a usb boot version of ubuntu? 


Trying to get the computer to recognise my atheros ar9825 card.  
tried looking for hardware drivers, said no drivers to be found
tried looking in synaptic package manager, no atheros, no wireless

another way told me to go to synaptic package manager and install ndisgtk, and then download xp drivers, ndisgtk isn't there. 

Any recommendations of how to get wireless working? The simpler the better.

---

### Post by annoluce on 2010-03-19
well it is there when i so lshw at least...

---

### Post by akikumar on 2010-04-14
I posted it some where in Ubuntu Forum again posting here

Nothing is working for me, first try to connect wireless at home then shove the cable in from modem but nothing at all happen

My driver is ar9285

Below is few details Only copying the error part..My system is HP DV 4 PAVALLION

I have another lap top through which i can download all the packages...its a wireless connection..so i downloaded compact wireless and others as told by people but nothing is working fr me


Tried compact wireless



```
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h: In function ‘drv_prepare_multicast’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h:92: warning: passing argument 2 of ‘local->ops->prepare_multicast’ from incompatible pointer type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h:94: error: dereferencing pointer to incomplete type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c: In function ‘__check_ieee80211_disable_40mhz_24ghz’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c:37: warning: return from incompatible pointer type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c: In function ‘ieee80211_alloc_hw’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c:394: error: implicit declaration of function ‘__hw_addr_init’ 
make[3]: *** [/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.o] Error 1 
make[2]: *** [/home/akshay/compat-wireless-2010-04-13/net/mac80211] Error 2 
make[1]: *** [_module_/home/akshay/compat-wireless-2010-04-13] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make: *** [modules] Error 2 


```
After that tried madfi

make

```
/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath/if_ath_pci.c:203: error: 'struct net_device' has no member named 'owner' 
make[3]: *** [/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath/if_ath_pci.o] Error 1 
make[2]: *** [/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath] Error 2 
make[1]: *** [_module_/home/akshay/Desktop/aKI/madwifi-0.9.3.2] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make: *** [modules] Error 2 
```

Here is what i see

```
lspci -v
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01) 
Subsystem: Hewlett-Packard Company Device 303f 
Flags: bus master, fast devsel, latency 0, IRQ 10 
Memory at d6400000 (64-bit, non-prefetchable) [size=64K] 
Capabilities: <access denied> 

ifconfig
eth0 Link encap:Ethernet HWaddr 00:26:22:bf:9d:51 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:192582150 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:245 Base address:0xe000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:92 errors:0 dropped:0 overruns:0 frame:0 
TX packets:92 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:7280 (7.2 KB) TX bytes:7280 (7.2 KB) 

eth0 Link encap:Ethernet HWaddr 00:26:22:bf:9d:51 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:192582150 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:245 Base address:0xe000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:92 errors:0 dropped:0 overruns:0 frame:0 
TX packets:92 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:7280 (7.2 KB) TX bytes:7280 (7.2 KB) 

eth0 Link encap:Ethernet HWaddr 00:26:22:bf:9d:51 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:192582150 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:245 Base address:0xe000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:92 errors:0 dropped:0 overruns:0 frame:0 
TX packets:92 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:7280 (7.2 KB) TX bytes:7280 (7.2 KB) 

akshay@akshay:~$ iwconfig 
lo no wireless extensions. 

eth0 no wireless extensions. 

pan0 no wireless extensions. 
```

```
akshay@akshay:~$ lsmod 
Module Size Used by 
nls_iso8859_1 12032 1 
nls_cp437 13696 1 
vfat 18816 1 
fat 58272 1 vfat 
binfmt_misc 16776 1 
ppdev 15620 0 
bridge 56340 0 
stp 10500 1 bridge 
bnep 20224 2 
input_polldev 11912 0 
lp 17156 0 
parport 42220 2 ppdev,lp 
snd_hda_intel 435636 3 
snd_pcm_oss 46336 0 
snd_mixer_oss 22656 1 snd_pcm_oss 
snd_pcm 82948 2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy 10756 0 
snd_seq_oss 37760 0 
snd_seq_midi 14336 0 
snd_rawmidi 29696 1 snd_seq_midi 
snd_seq_midi_event 15104 2 snd_seq_oss,snd_seq_midi 
snd_seq 56880 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event 
uvcvideo 63240 0 
snd_timer 29704 2 snd_pcm,snd_seq 
psmouse 61972 0 
snd_seq_device 14988 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq 
compat_ioctl32 9344 1 uvcvideo 
serio_raw 13316 0 
videodev 41600 1 uvcvideo 
snd 62628 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_de vice 
pcspkr 10496 0 
v4l1_compat 21764 2 uvcvideo,videodev 
soundcore 15200 1 snd 
sdhci_pci 15232 0 
sdhci 23940 1 sdhci_pci 
snd_page_alloc 16904 2 snd_hda_intel,snd_pcm 
leds_hp_disk 10756 0 
led_class 12036 1 leds_hp_disk 
joydev 18368 0 
video 25360 0 
lis3lv02d 17848 0 
output 11008 1 video 
usb_storage 82880 1 
r8169 40836 0 
mii 13312 1 r8169 
fbcon 46112 0 
tileblit 10752 1 fbcon 
font 16384 1 fbcon 
bitblit 13824 1 fbcon 
softcursor 9984 1 bitblit 

```

finally shoving the cable in to use some apt get remedies here but
AFTER CONNECTING IT TO Motorola cable modem 

```
ifconfig 
eth0 Link encap:Ethernet HWaddr 00:26:22:bf:9d:51 
inet6 addr: fe80::226:22ff:febf:9d51/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:184549365 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:245 Base address:0xe000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B) #[CODE]
```
[/CODE]

in the connection manager it is showing
autoeth0 but nothing after some time it pops up no wired connection
:confused:

---

