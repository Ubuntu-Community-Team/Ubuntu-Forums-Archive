---
title: "Ethernet problem in 14.04"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by TN76xw7 on 2014-05-25
Hi! I'm facing internet problems in Ubuntu 14.04 in my desktop. I've Windows 8 and Ubuntu 14.04 dual booted. My Ethernet port is [COLOR=#333333][FONT=Segoe UI][/FONT][/COLOR][FONT=Segoe UI]Realtek 8112L Gigabit LAN.[/FONT][COLOR=#333333][FONT=Segoe UI]

My internet works perfectly fine in Windows 8. It connects as a WAN Miniport (PPPOE). But I'm not able to connect Ubuntu.

I tried connecting as DSL connection but failed. I tried to connect as Ethernet connection but it just asks for my Ethernet password a few seconds later repeatedly. I authenticate but doesn't connect :(

I didn't try ethernet on 12.04LTS.  I upgraded from 12.04LTS to 14.04LTS. I'm wondering if I'd lost any drivers.

Any help?

Thanks![/FONT][/COLOR]

---

### Post by praseodym on 2014-05-25
Hi,

please show these outputs:
```
uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by TN76xw7 on 2014-05-28
Thank you very much [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497") for your reply!

Fortunately, I've solved the problem. I changed from Ethernet to DSL Connection and everything worked out fine!

Still, posting the results so that others might get benefitted.

```
mishkat@mishkat-Ubuntu14LTS:~$ uname -a
Linux mishkat-Ubuntu14LTS 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
mishkat@mishkat-Ubuntu14LTS:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169
mishkat@mishkat-Ubuntu14LTS:~$ lsmod
Module                  Size  Used by
pppoe                  17873  2 
pppox                  13342  1 pppoe
nls_utf8               12557  1 
isofs                  39835  1 
bnep                   19624  2 
snd_hda_codec_hdmi     46207  1 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
joydev                 17381  0 
gpio_ich               13476  0 
snd_hda_codec_via      27860  1 
intel_powerclamp       14705  0 
snd_seq_midi           13324  0 
coretemp               13435  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm_intel             143060  0 
snd_hda_intel          52355  5 
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
kvm                   451511  1 kvm_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse               102222  0 
radeon               1514165  3 
serio_raw              13462  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ttm                    85115  1 radeon
lpc_ich                21080  0 
drm_kms_helper         52758  1 radeon
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   302817  5 ttm,drm_kms_helper,radeon
mei_me                 18627  0 
soundcore              12680  1 snd
mei                    82274  1 mei_me
i2c_algo_bit           13413  1 radeon
asus_atk0110           18657  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
r8169                  67581  0 
mii                    13934  1 r8169
mishkat@mishkat-Ubuntu14LTS:~$ ifcoonfig -a
No command 'ifcoonfig' found, did you mean:
 Command 'ifconfig' from package 'net-tools' (main)
ifcoonfig: command not found
mishkat@mishkat-Ubuntu14LTS:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f4:6d:04:76:a5:4f  
          inet6 addr: fe80::f66d:4ff:fe76:a54f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237498 errors:0 dropped:7 overruns:0 frame:0
          TX packets:169559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:306553768 (306.5 MB)  TX bytes:23023091 (23.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:898761 (898.7 KB)  TX bytes:898761 (898.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.100.215  P-t-P:192.168.100.1  Mask:255.255.255.255
          inet6 addr: fe80::5974:db72:8477:d633/10 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:228579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:300773980 (300.7 MB)  TX bytes:19274779 (19.2 MB)

mishkat@mishkat-Ubuntu14LTS:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


```

---

