---
title: "wireless internet connection probs"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by ctdub on 2011-07-17
I am connected to the internet with Vista on my PC but cannot seem to 

connect from ubuntu 11.04, which I just installed. I have a wireles network 

card (Linksys Wireless-N-PCI Adapter, Model # WMP 300N) and a router(Linksys 

WRT Wireless N, Model # WRT 300 NV1).  I have tried scripts from the ubuntu 

help on the internet, so far to no avail.  Can someone please get me going?

---

### Post by ercferret18 on 2011-07-17
can you post the output of "ifconfig -a"?

---

### Post by ctdub on 2011-07-18
clarke@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:26:18:06:f5:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6320 (6.3 KB)  TX bytes:6320 (6.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:0f:06:8d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by wildmanne39 on 2011-07-18
Hi, run these commands in a terminal
```
lspci -nn
```
```
lsmod
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by ctdub on 2011-07-18
Thanks for the response.  I hope I am not in too much trouble for posting 2 similar questions, but my first post didn't appear for a while.

Here are your instructions and the results. (rfkill list All       didn't seem to work.)

wildmanne39 has just replied to a thread you have subscribed to entitled - [ubuntu] wireless internet connection probs - in the Absolute Beginner Talk forum of Ubuntu Forums.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=1806642&goto=newpost](http://ubuntuforums.org/showthread.php?t=1806642&goto=newpost)

Here is the message that has just been posted:
***************
Hi, run these commands in a terminal

Code:
---------
lspci -nn
---------

Code:
---------
lsmod
---------

Code:
---------
rfkill list All
---------
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
***************


There may also be other replies, but you will not receive any more notifications until you visit the forum again.

All the best,
Ubuntu Forums

clarke@ubuntu:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0d.0 VGA compatible controller [0300]: nVidia Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:0a.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
clarke@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93525  1 
crc_itu_t              12707  1 udf
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336693  1 
binfmt_misc            17565  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
b43                   318638  0 
snd_rawmidi            30486  1 snd_seq_midi
nouveau               682322  2 
mac80211              294370  1 b43
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178528  2 b43,mac80211
ses                    17321  0 
ttm                    76664  1 nouveau
snd_timer              29602  2 snd_pcm,snd_seq
enclosure              15217  1 ses
usblp                  18233  0 
psmouse                73535  0 
drm_kms_helper         42136  1 nouveau
serio_raw              13166  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53845  0 
drm                   227495  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13400  1 nouveau
video                  19438  1 nouveau
edac_mce_amd           23464  0 
k10temp                13119  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2            13058  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  2 
uas                    17996  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
ssb                    51945  1 b43
sata_nv                32054  1 
forcedeth              63555  0 
clarke@ubuntu:~$ rfkill list All
Bogus list argument 'All'.
clarke@ubuntu:~$

---

### Post by wildmanne39 on 2011-07-19
Hi, first before installing any drivers remove any that may already be installed by opening synaptic and type bcm into the search box and right click on any in that section that are green and choose to remove completely, then restart your system.

Now open synaptic and type bcm and install 
**firmwareb43-lpphy-installer**,[B]bcmwl-kerrnel-source
 [/B]then restart and your wireless should be working.

---

### Post by ctdub on 2011-07-19
wildmanne39,

Thanks for your response. In ubuntu 8.04 I deleted the green icons and completely deleted the one icon and associated packages (ones that are affected by deletion of the original - this is a query from ubuntu).  When I rebooted, the system no longer boots up.
In ubuntu 11.04, which I also have installed, there is no bcm, only bc, so I didn't do anything.
Any suggestions?
ctdub

---

### Post by bkratz on 2011-07-19
> **ctdub said:**
> wildmanne39,

Thanks for your response. In ubuntu 8.04 I deleted the green icons and completely deleted the one icon and associated packages (ones that are affected by deletion of the original - this is a query from ubuntu).  When I rebooted, the system no longer boots up.
In ubuntu 11.04, which I also have installed, there is no bcm, only bc, so I didn't do anything.
Any suggestions?
ctdub

note to @wildmanne39, did you perhaps transpose his network card info?

[COLOR="Red"]01:0a.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)[/COLOR]

confusing it with the 4312?

Josephmills excellent post (  [http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)  )


shows that the 4321 should utilize the

copied from the posting"

```
If you have model number
14e4:0576
14e4:4313
14e4:4315 
14e4:4328
14e4:4329
14e4:432a
14e4:432b
14e4:432c
14e4:432d 
14e4:4353
14e4:4357
14e4:4358
14e4:4359
14e4:435a
14e4:4727
14e4:a99d

then you are going to need the broadcom-sta-source + broadcom-sta-common 
```


"

@ctdub, that post should take care of you in 11.04. since 8.04 is no longer supported, I am surprised that you can even look in synaptic unless you have changed all your sources to the "old versions" repos.

---

### Post by wildmanne39 on 2011-07-19
@bkratz Thank you, I did indeed read it as 4312 and not 4321 I appreciate the save.

@ctdub I gave you the wrong information I read your card number backwards, I am very sorry for that.

I do not know why you can not boot if you just removed broadcom drivers after you typed in bcm. Maybe it has to do with your version being outdated. 

If I type bcm in 11.04 I get all the broadcom drivers.

You can use the link provided by bkratz and it should get your wireless working please come back if you need more help and if it works mark thread solved. 
Thank you

---

