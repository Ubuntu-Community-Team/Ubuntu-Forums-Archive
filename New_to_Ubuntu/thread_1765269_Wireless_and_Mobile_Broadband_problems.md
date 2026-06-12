---
title: "Wireless and Mobile Broadband problems"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by ptrsdwski on 2011-05-22
I'm completely new with Linux, just installed it yesterday, and I'm looking to have some fun with it, but problem is, I can't get the wireless or the mobile broadband to auto register with the network tab. I plug my Droid in and it doesn't recognize it, and I can't get the wireless tab to show up either. Like I said, I'm completely new with this, but I am proficient with windows. I'm running Ubuntu 11.04, It's on a Compaq Presario C500 I believe, and any other information I'd be more than willing to provide. Can anyone help me to download the right drivers and such to get this to work?

---

### Post by fritz269 on 2011-05-22
I use a Garmin Garminfone and I have to go into the settings of the phone and allow connection sharing on the phone. Also, when I plug in my phone it prompts me to see if I want to share files or Internet connection, otherwise I cannot see the phone on my computer. Use the slide down menu, on the top where you get notifications, on the phone and slide down and see if it gives you those prompts. If it does, just press it and it should work. Hope this helps.

---

### Post by charlie_b on 2011-05-22
What kind of mobile broadband do you have?

---

### Post by fritz269 on 2011-05-22
3g through a Simple Mobile that runs on T-Mobiles network

---

### Post by ptrsdwski on 2011-05-22
I'm more focused on trying to get the wireless to work. Do either of you know any specific problems with the wireless capabilities on this laptop? It's an older one, got it a couple of years back. It works just fine with ethernet plugged straight in, but wireless doesn't even come up as an option. Any ideas? I'm gonna go through the HP website and see if there is any drivers there.

---

### Post by josephmills on 2011-05-22
Hi there could we look at some hardware? please open your terminal (ctrl+alt+t) then type in ```
lspci -nn
``` and then ```
rfkill list all
``` then paste that here thanks Oh and Welcome to Ubuntu Forums

---

### Post by ptrsdwski on 2011-05-22
peter@Cassiopeia:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
peter@Cassiopeia:~$ ^C
peter@Cassiopeia:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
Thanks buddy, I'm gonna go check out those other pages now.

---

### Post by josephmills on 2011-05-22
could we see ```
lsmod | grep b43 
``` and ```
dmesg | grep b43
``` thanks hope you find my signature funny :popcorn: also if it gives nothing just say so

---

### Post by ptrsdwski on 2011-05-22
dec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     13349  0 
i915                  450944  3 
psmouse                73312  0 
drm_kms_helper         40745  1 i915
soundcore              12600  1 snd
parport                36746  3 parport_pc,ppdev,lp
hp_wmi                 13418  0 
serio_raw              12990  0 
drm                   180037  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lib80211               14570  1 wl
sparse_keymap          13666  1 hp_wmi
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  2 
8139too                23208  0 
8139cp                 22497  0 
libahci                25548  1 ahci
I got the first one, but the other three didn't bring anything up. You just type them in exactly how you put em?

---

### Post by josephmills on 2011-05-22
please open your terminal and type in ```
sudo apt-get install b43-fwcutter 
``` then ```
sudo apt-get install firmware-b43-installer 
``` then ```
sudo apt-get install bcmwl-kernel-source
``` then reboot do you have wireless? if not post back if you get any errors then just post and tell us thanks 
```
lsmod | grep b43
``` ```
dmesg | grep b43 
``` getting close

---

### Post by ptrsdwski on 2011-05-23
Perfect! Worked on the wireless! Thank you so much. Now, for future reference, what exactly did we do? I wanna learn all of this stuff so that I can help out on here as well.

---

### Post by josephmills on 2011-05-23
> **ptrsdwski said:**
> Perfect! Worked on the wireless! Thank you so much. Now, for future reference, what exactly did we do? I wanna learn all of this stuff so that I can help out on here as well.

I wrote this a while ago it will tell all that we did Glad that you got it working please see post #44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

do you want to get the phone to work also ?  If so plug in the phone then do a ```
dmesg 
``` and copy the last 25 lines and let us see them thanks

---

### Post by reepjyoti on 2011-06-19
sir, i am having problems in using my Photon Plus Mobile broadband service in ubuntu 2.7 UE. My model is huawei EC 152. i have made some changes in some files and am able to use it. but my problem is that i can use it only by luck, only when the photon is detected automatically by my system. if its not detected i have to restart my system 2-3 times so that it is again detected automatically. please help.

---

