---
title: "Ubunut 9.10 ethernet stopped working"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by chaddiesel on 2010-07-07
I have an ethernet port on my motherboard that will not work with ubuntu. When I boot in windows xp it works no problem. This problem started out after moving my desk (which should have nothing to do with things). It was intermittent at first and I got the wired connection back once just by restarting and logging out a few times.

I cannot ping the router. But, I know that the router and cable work fine with windows. 

Any suggestions?

---

### Post by dineshs on 2010-07-08
Does ```
ifconfig -a
``` give a valid IP?
Did you try```
sudo dhclient eth0
```

---

### Post by jtarin on 2010-07-08
Post your results from the command in a terminal ```
lspci
```
Then the command in a terminal ```
lsmod
```

---

### Post by chaddiesel on 2010-07-09
lspci

```
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1) 
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a2) 
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1) 
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1) 
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1) 
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1) 
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1) 
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1) 
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1) 
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a1) 
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1) 
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) 
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) 
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10) 
04:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1) 

```

lsmod:

```
Module                  Size  Used by 
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          27016  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               7200  1 snd_hda_codec 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter 
x_tables               16544  1 ip_tables 
nvidia               9586440  38 
ppdev                   6688  0 
lp                      8964  0 
parport_pc             31940  1 
agpgart                34988  1 nvidia 
parport                35340  3 ppdev,lp,parport_pc 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi 
psmouse                57332  0 
serio_raw               5280  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              22276  2 snd_pcm,snd_seq 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
k8temp                  4188  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               7264  1 snd 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm 
i2c_nforce2             6784  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45 
usbhid                 38208  0 
r8169                  32160  0 
mii                     5212  1 r8169 
floppy                 54916  0 

```

---

### Post by chaddiesel on 2010-07-09
> **dineshs said:**
> Does ```
ifconfig -a
``` give a valid IP?
Did you try```
sudo dhclient eth0
```


iconfig -a:

did not give an IP

sudo dhclient eth0:

timed out without any results

---

### Post by jtarin on 2010-07-09
Your card is recognized and the module is loaded for it so.....
Find out if Network Manager is running with:```
ps aux | grep -i 
```

[Have you read the documentation on Network Manager?]("https://help.ubuntu.com/community/NetworkManager0.7")

---

### Post by chaddiesel on 2010-08-04
Sorry to post so late.... I just got married and life is hectic.

I cannot get that command to work. 

>  ps aux 

will spit out code but the whole thing wont

---

### Post by chaddiesel on 2010-08-04
okay... just read all of the lines from, ps aux , STAT  on Network manager is Ss.


Any ideas?

---

### Post by jtarin on 2010-08-05
Try the command```
sudo ifup eth0
``` then return to the command ```
ifconfig -a
``` and see if you get an IP.

---

