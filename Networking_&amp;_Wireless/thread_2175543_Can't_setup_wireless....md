---
title: "Can't setup wireless..."
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by sam18 on 2013-09-19
Hi, my laptop Specs:
-Dell Inspiron 1545
-Ubuntu 12.4
-Dell Wireless 1397 WLAN Mini-card


I have tried installing various wireless drivers, I've had people try to set it up for me....I've tried to install Broadcom and I didn't really know what I was doing, I tried to install a driver and I just got errors, I type my details of my wireless network in the network manager and just nothing happens...I don't know if it scans for it automatically or what, I don't know how to connect to it, I also tried WifiRadar after someone suggested it, I type my details of my network into that and click connect, and it simply does nothing, I can only connect to my network via wired with an Ethernet. 

Could someone who knows what they are doing give me some help and try and sort this out for me, step-by-step would be much appreciated as I'm new to Ubuntu, thanks.


-Sam.

---

### Post by Hadaka on 2013-09-19
Hi, please open a terminal ctrl/alt/t
then Copy and enter the following commands..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list
```
post the output
thanks.

---

### Post by sam18 on 2013-09-26
Sorry for late reply, here's the output:

```
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
    Kernel modules: sky2
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel modules: ssb
sam@sam-Inspiron-1545:~$ lsmod
Module                  Size  Used by
snd_hda_codec_idt      71153  1 
joydev                 17613  0 
snd_hda_intel          44339  3 
snd_hda_codec         141761  2 snd_hda_codec_idt,snd_hda_intel
uvcvideo               82214  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  2 snd_hda_intel,snd_hda_codec
bnep                   18258  2 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
i915                  620419  3 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_memops       13202  1 videobuf2_vmalloc
rfcomm                 47864  0 
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
coretemp               13596  0 
bluetooth             247024  10 bnep,rfcomm
snd                    69533  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              12680  1 snd
gpio_ich               13526  0 
drm_kms_helper         49597  1 i915
microcode              23017  0 
psmouse                97873  0 
drm                   287564  4 i915,drm_kms_helper
evbug                  12661  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
i2c_algo_bit           13564  1 i915
parport_pc             28284  0 
wmi                    19256  1 dell_wmi
video                  19652  1 i915
serio_raw              13215  0 
ppdev                  17113  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                17144  0 
dell_laptop            17425  0 
dcdbas                 14449  1 dell_laptop
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech_dj        18767  0 
usbhid                 47346  1 hid_logitech_dj
hid                   105549  2 hid_logitech_dj,usbhid
ums_realtek            18256  0 
usb_storage            61749  1 ums_realtek
sky2                   62824  0 
ahci                   25879  2 
libahci                31606  1 ahci

```

---

### Post by Hadaka on 2013-09-26
Hi,please open a terminal..ctrl/alt/t
with a wired connection  enter..
```
sudo apt-get update
sudo apt get upgrade
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe b43
```
thanks.

---

### Post by akamaras2 on 2013-09-26
Dear Sam18,

I'm not an expert but think I had the same problem and managed to make some workaround.
Just in case get rid of old drivers:

```
sudo apt-get remove --purge bcmwl-kernel-source
```

Block your sky2 driver:
```
echo "blacklist sky2" >> /etc/modprobe.d/blacklist.conf
```

Then check if b43 drivers are not blacklister in /etc/modprobe.d/blacklist.conf

```
grep -e "blacklist b43"  /etc/modprobe.d/blacklist.conf
```

If you get blacklist b43, then it is blacklisted. Put # in front of the line

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Then install the drivers (if you have already installed lpphy driver skip it and install just b43-fwcutter:

```
sudo apt-get install firmware-b43-lpphy-installer
sudo apt-get install b43-fwcutter
```

And you can also do this, I don't know if it's neccessary:

```
echo "b43" >>/etc/modules
```

Restart the computer and try my miserable trick:

```
sudo iwlist scan
```

several times.

---

### Post by varunendra on 2013-09-27
This should not be needed -
> **akamaras2 said:**
> 
Block your sky2 driver:
```
echo "blacklist sky2" >> /etc/modprobe.d/blacklist.conf
```
Why do you think it needs to be blacklisted?
It is an ethernet driver and does not conflict with b43 as far as I know (and modinfo tells). Blacklisting it would disable the Ethernet interface.

---

### Post by sam18 on 2013-09-28
> **Hadaka said:**
> Hi,please open a terminal..ctrl/alt/t
with a wired connection  enter..
```
sudo apt-get update
sudo apt get upgrade
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe b43
```
thanks.

Hi, I did this and I have copied the last lines of code after it connected.


```

Fetched 4,363 kB in 33s (132 kB/s)                                             
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not connect to extras.ubuntu.com:80 (91.189.92.152). - connect (113: No route to host)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to extras.ubuntu.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by Hadaka on 2013-09-28
Hi sam18, I am a little confused by this..
"Hi, I did this and I have copied the last lines of code after it connected."
"after it conncted"
is the wireless now working?
these lines of code should be entered with the wired connection..connected to the internet.
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.

---

### Post by varunendra on 2013-09-29
Apparently it was connected -
> **sam18 said:**
> ```

Fetched **4,363 kB in 33s** (132 kB/s)

```
It seems a gateway error occurred while downloading the packages (was the connection interrupted?) -
> Could not connect to extras.ubuntu.com:80 (91.189.92.152). - connect (113: No route to host)

---

### Post by sam18 on 2013-09-29
> **Hadaka said:**
> Hi sam18, I am a little confused by this..
"Hi, I did this and I have copied the last lines of code after it connected."
"after it conncted"
is the wireless now working?
these lines of code should be entered with the wired connection..connected to the internet.
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.

Ok I did 

```
sudo apt-get update
sudo apt-get upgrade
```

and both came back succesful I think, here's the final code

```
Reading package lists... Done
sam@sam-Inspiron-1545:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```


EDIT: Available wireless networks in range now show on the dropdown list, they did not before, so i think it's fixed, I'll post back if it's not.

---

### Post by Hadaka on 2013-09-29
ok......If you are satisfied with the results please mark your thread solved.
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

### Post by sam18 on 2013-09-29
Yep all sorted now, thanks guys.

---

