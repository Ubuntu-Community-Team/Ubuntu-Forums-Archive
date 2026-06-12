---
title: "Sound issues"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by cuberts on 2010-04-27
Hi, I have been trying to solve my sound problem for  a while, but I cant.

So the problem is that it doesnt make any sound. 
I belive that my computer detects the sound card though. 
Please help.

---

### Post by Jon Monreal on 2010-04-27
Hello,

Could you type the following commands in the terminal (separately) and post their respective outputs here:

```
sudo lspci
```
```
sudo lsmod
```

If you need help with this, please feel free to ask.

Thanks.

---

### Post by ttshivers on 2010-04-27
I see that you have created another threat about this issue.  Maybe we can find out information about his hardware from that thread.

---

### Post by Jon Monreal on 2010-04-27
> **ttshivers said:**
> I see that you have created another threat about this issue.  Maybe we can find out information about his hardware from that thread.

Which thread is that? I see nothing in [his posts]("http://ubuntuforums.org/search.php?searchid=72350745") with hardware info, and would appreciate a link.

Thanks.

---

### Post by cuberts on 2010-04-27
> **Jon Monreal said:**
> Hello,

Could you type the following commands in the terminal (separately) and post their respective outputs here:

```
sudo lspci
```
```
sudo lsmod
```

If you need help with this, please feel free to ask.

Thanks.so when I do the first command in the terminal, this is what it comes up with:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
 
When I do the second command, this is what happens:

Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
x_tables               16544  1 ip_tables
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   6688  0 
dell_wmi                2564  0 
parport_pc             31940  1 
lp                      8964  0 
dcdbas                  7292  0 
soundcore               7264  1 snd
parport                35340  3 ppdev,parport_pc,lp
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
b44                    28652  0 
ssb                    35524  1 b44
mii                     5212  1 b44
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

I think now that should give you enough information.
Please help, and I appreciate you helping me with this issue.

---

### Post by ttshivers on 2010-04-27
[LEFT]Oh.  Sorry, I forgot to include the link.  Well here it is:  [http://ubuntuforums.org/showthread.php?t=1454478](http://ubuntuforums.org/showthread.php?t=1454478)
[/LEFT]

---

### Post by Jon Monreal on 2010-04-27
Sorry guys, I have to run for tonight. I'll look at your info tomorrow to see what to do (so no, I won't forget).

---

### Post by ttshivers on 2010-04-27
Ok.  Thank you for helping him.

---

### Post by cuberts on 2010-04-27
> **ttshivers said:**
> Ok.  Thank you for helping him.
Thank you again, and Travis, do you have any idea how I could solve this? Thanks

---

### Post by ttshivers on 2010-04-27
Not really, but I am sure that that other guy can help you.

---

### Post by cuberts on 2010-04-27
> **ttshivers said:**
> Not really, but I am sure that that other guy can help you.All right, and would he also need some information on the sound card?

---

### Post by ttshivers on 2010-04-27
I gave him the link to your other thread, which has all that information, so we don't need to give him that information again.

---

### Post by cuberts on 2010-04-27
> **ttshivers said:**
> I gave him the link to your other thread, which has all that information, so we don't need to give him that information again.all right then thanks for your help too travis

---

### Post by Jon Monreal on 2010-04-28
[This bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369631"), at least according to posters, applied at least through 9.04. Did you upgrade from Jaunty (9.04) or another previous version?

One good thing to try would be to wait for tomorrow's impending release of 10.04 Lucid Lynx, download the Live CD and test that. If that works things will be a lot easier.

---

### Post by alphacrucis2 on 2010-04-28
> **Jon Monreal said:**
> [This bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369631"), at least according to posters, applied at least through 9.04. Did you upgrade from Jaunty (9.04) or another previous version?

One good thing to try would be to wait for tomorrow's impending release of 10.04 Karmic Koala, download the Live CD and test that. If that works things will be a lot easier.

Don't you mean Lucid Lynx? Karmic Koala was 9.10.

---

### Post by mhgsys on 2010-04-28
There was a bug in 9.10 which also had a problem with my [SiS] Azalia Audio Controller

It was send to sleepmode and could not wake up.
Fixed it with;

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

change the line
```
options snd-hda-intel power_save=10 power_save_controller=N
```

into

```
options snd-hda-intel power_save=0 power_save_controller=N
```

---

### Post by Jon Monreal on 2010-04-28
> **alphacrucis2 said:**
> Don't you mean Lucid Lynx? Karmic Koala was 9.10.

Yep, sorry about that.

---

### Post by cuberts on 2010-05-02
thanks for trying to help me, and I have fixed my problem.
ttshivers fixed it.

---

### Post by ttshivers on 2010-05-03
It was actually a hardware issue not a software or driver issue.

---

### Post by cuberts on 2010-06-15
> **ttshivers said:**
> not really, but i am sure that that other guy can help you.```
this is code
```

---

