---
title: "no network connection both ethernet and WiFi"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by jlh68 on 2014-03-12
My netbook (AcerOne 750) after using Boot-Repair is having trouble connecting to the internet.  The panel icon shows WiFi connected or it shows Ethernet connected, but I cannot get any applications to connect with the internet (Firefox, Thunderbird, and Logitec Harmony Remote Software).  My wife's Kindle is connected without problem and this computer is Ethernet connected so I am pretty sure it is in the laptop.

I do not know where to start in finding out what has happened. I have shut the computer doen and rebooted it several times, I have turned off the computer WiFi and turnned it back on and the WiFi will connect and show it is connected with about 58Mb/s speed, but the apps will not reconize the Wifi or Ethernet.

---

### Post by praseodym on 2014-03-12
Please show the terminal outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
rfkill list
```

---

### Post by Iowan on 2014-03-12
Check (from a terminal) **ifconfig -a** to see if either interface has an IP address. 
If it does, can you **ping** the router? 
If so, can you **ping** the internet (try 8.8.8.8)?

---

### Post by jlh68 on 2014-03-12
Here is my laptop output.
```
john@Nighthawk:~$ uname -a 
Linux Nighthawk 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
``````
 
john@Nighthawk:~$ lspci -nnk | grep -iA2 net 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 
	Subsystem: Acer Incorporated [ALI] Device [1025:0740] 
	Kernel driver in use: r8169 
-- 
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01) 
	Subsystem: Foxconn International, Inc. Device [105b:e047] 
	Kernel driver in use: ath9k 
```
```
john@Nighthawk:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 002 Device 002: ID 064e:d251 Suyin Corp. 
```
```
john@Nighthawk:~$ lsmod 
Module                  Size  Used by 
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180113  10 rfcomm,bnep 
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32530  1 
binfmt_misc            17540  1 
wl                   3074895  0 
acer_wmi               28418  0 
snd_hda_intel          33719  5 
uvcvideo               72627  0 
joydev                 17693  0 
sparse_keymap          13890  1 acer_wmi 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel 
videodev               98259  1 uvcvideo 
v4l2_compat_ioctl32    17128  1 videodev 
psmouse                97519  0 
serio_raw              13211  0 
k10temp                13166  0 
i2c_piix4              13301  0 
lib80211               14381  1 wl 
arc4                   12529  2 
snd_hwdep              17764  1 snd_hda_codec 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
ath9k                 132428  0 
snd_timer              29990  2 snd_pcm,snd_seq 
mac80211              506862  1 ath9k 
radeon                808783  3 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
ath9k_common           14053  1 ath9k 
wmi                    19256  1 acer_wmi 
video                  19651  0 
snd                    79041  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
ath9k_hw              411239  2 ath9k,ath9k_common 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw 
cfg80211              205774  4 wl,ath9k,mac80211,ath 
ttm                    76949  1 radeon 
drm_kms_helper         46978  1 radeon 
mac_hid                13253  0 
drm                   241971  5 radeon,ttm,drm_kms_helper 
soundcore              15091  1 snd 
i2c_algo_bit           13423  1 radeon 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp 
r8169                  62190  0 
```
```
john@Nighthawk:~$ lwconfig 
The program 'lwconfig' is currently not installed.  You can install it by typing: 
sudo apt-get install likewise-open 
```
```
john@Nighthawk:~$ ifconfig -a 
eth2      Link encap:Ethernet  HWaddr 04:7d:7b:9d:f6:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:29437 (29.4 KB)  TX bytes:41857 (41.8 KB) 
          Interrupt:44 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:13399 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:13399 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1100135 (1.1 MB)  TX bytes:1100135 (1.1 MB) 

wlan2     Link encap:Ethernet  HWaddr 08:ed:b9:3f:0d:aa  
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::aed:b9ff:fe3f:daa/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1758 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:329 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:515998 (515.9 KB)  TX bytes:68732 (68.7 KB)
``` 

```
john@Nighthawk:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1 
search ntelos.net 
```
```
john@Nighthawk:~$ rfkill list 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
john@Nighthawk:~$ 
```

---

### Post by Iowan on 2014-03-12
Curious why the interfaces acquired a "2" designation.
The **resolv.conf** doesn't seem quite right, either...

---

### Post by Hadaka on 2014-03-12
Hi, it looks like you someow got the broadcom wl
driver stuffed in there. Let's get rid of that and see
if we can also wake up the ath9k..the correct driver.
please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe ath9k

```
i also noticed you have eth2 and wlan2, s let's clean that up as well,
please do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
thanks
BOOT and report back good news..

---

### Post by jlh68 on 2014-03-13
Did suggestions, rebooted and bad news, still no connections. Below are the listings after changes:
```
john@Nighthawk:~$ lspci -nnk | grep -iA2 net 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 
	Subsystem: Acer Incorporated [ALI] Device [1025:0740] 
	Kernel driver in use: r8169 
-- 
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01) 
	Subsystem: Foxconn International, Inc. Device [105b:e047] 
	Kernel driver in use: ath9k 
```
```
john@Nighthawk:~$ lsmod 
Module                  Size  Used by 
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep 
ppdev                  17113  0 
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32530  1 
binfmt_misc            17540  1 
snd_hda_intel          33719  5 
acer_wmi               28418  0 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel 
joydev                 17693  0 
sparse_keymap          13890  1 acer_wmi 
snd_hwdep              17764  1 snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
uvcvideo               72627  0 
arc4                   12529  2 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_timer              29990  2 snd_seq,snd_pcm 
videodev               98259  1 uvcvideo 
psmouse                97519  0 
v4l2_compat_ioctl32    17128  1 videodev 
serio_raw              13211  0 
ath9k                 132428  0 
k10temp                13166  0 
i2c_piix4              13301  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
mac80211              506862  1 ath9k 
radeon                808783  3 
ath9k_common           14053  1 ath9k 
ath9k_hw              411239  2 ath9k,ath9k_common 
snd                    79041  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_timer,snd_seq_device 
ttm                    76949  1 radeon 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw 
drm_kms_helper         46978  1 radeon 
cfg80211              205774  3 ath9k,mac80211,ath 
drm                   241971  5 radeon,ttm,drm_kms_helper 
soundcore              15091  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
i2c_algo_bit           13423  1 radeon 
wmi                    19256  1 acer_wmi 
video                  19651  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp 
r8169                  62190  0 
```

```
john@Nighthawk:~$ lwconfig -a 
The program 'lwconfig' is currently not installed.  You can install it by typing: 
sudo apt-get install likewise-open 
```

```
john@Nighthawk:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1 
search ntelos.net 
```

```
john@Nighthawk:~$ rfkill list 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
```
I hope the above will help. 

I have my Home partition backed up.  If I knew which file of it to restore maybe some would be the ones that make the Ethernet and WiFi connections work.

---

### Post by Hadaka on 2014-03-13
ok makeing progress,the wl is gone.please do..
click the network mgr. icon...make sure all are ENABLE
then do..
```
sudo iwlist wlan0 scan
```
```
sudo modprobe -rfv acer_wmi
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1
```
thanks.

---

### Post by praseodym on 2014-03-13
Remove any connections in "cable", "wirless" and "DSL" and reboot. Then setup Wifi again

---

### Post by jlh68 on 2014-03-13
made code changes recommended by **Hadaka**, then did what **praseodym** sugessted.  Did this twice, without success.

```
john@Nighthawk:~$ sudo iwlist wlan0 scan 
[sudo] password for john: 
wlan0     Scan completed : 
          Cell 01 - Address: 68:7F:74:4D:36:C3 
                    Channel:9 
                    Frequency:2.452 GHz (Channel 9) 
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on 
                    ESSID:"KangarooJump" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000001124d12388 
                    Extra: Last beacon: 380ms ago 
                    IE: Unknown: 000C4B616E6761726F6F4A756D70 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030109 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1609080400000000000000000000000000000000000000 
                    IE: Unknown: DD670050F204104A00011010440001021041000100103B00010310470010B5B07B68B39336F9988932F1B14E139A102100074C696E6B737973102300034D3130102400063132333435361042000234321054000800060050F2040001101100034D3130100800020084 
                    IE: Unknown: DD090010180202F0050000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3409080400000000000000000000000000000000000000 
          Cell 02 - Address: 00:1D:D1:5B:61:30 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on 
                    ESSID:"HOME-6132" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
```

```
john@Nighthawk:~$ sudo modprobe -rfv acer_wmi 
rmmod /lib/modules/3.2.0-60-generic/kernel/drivers/platform/x86/acer-wmi.ko 
rmmod /lib/modules/3.2.0-60-generic/kernel/drivers/platform/x86/wmi.ko 
rmmod /lib/modules/3.2.0-60-generic/kernel/drivers/input/sparse-keymap.ko 

john@Nighthawk:~$ sudo modprobe -rfv ath9k 
rmmod /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
rmmod /lib/modules/3.2.0-60-generic/kernel/net/mac80211/mac80211.ko 
rmmod /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
rmmod /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
rmmod /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/ath/ath.ko 
rmmod /lib/modules/3.2.0-60-generic/kernel/net/wireless/cfg80211.ko 

```

Still no connection.

---

### Post by Hadaka on 2014-03-13
Hi,you need to check all your network settings and
also log into the modem.change TKIP to aes-wpa2
or anything other than TKIP.
check your password and all your settings..carefullly, the scan
shows its working..it may just be the tkip or password..you are close !

---

### Post by jlh68 on 2014-03-13
How do I log into the modem? Or did you mean the WiFi Router?  Same Question how do I get access to the WiFi router.  I tried 198.168.1.1 which was the Cisco Valet connection web page and it is not found by my desktop computer.  Everything I read about my router is for Windows or Mac, no Linux connection instuctions.  When will these manufacturers learn that there are mor OS than Windows and Mac?

I have a Cisco Valet (Linksys) router.  Not sure of the  model, I think it is an M10.  The model number is on the bottom and the unit is screwed to the shelf it sits on (so it won't fall on the floor).

---

### Post by jlh68 on 2014-03-13
I meant 192.168.1.1 which came right out of the manual.

---

### Post by Hadaka on 2014-03-13
yup....192.168.1.1 ..type that in at your browser, that connets to the modem
one there it will ask for usenamer and password...if you have never set it...
it will be simple to look up..or we can reset it eaisly....normal user is admin
password...admin....or admn...12334   or admin admin password  post back
if you have a problem getting into the modem.

---

### Post by Bashing-om on 2014-03-13
jlh68; Hi !

Allow me to fill in for a moment.
Try this to get the IP assignment of your router:
```

route -n

```
The entry under "gateway" is the address you want.

so in your browser's address bar enter only that IP ( say, 192.168.0.1).
This should give you access to your router to check/re-configure things.

My little bit to try and help

---

### Post by jlh68 on 2014-03-13
Thanks **Bashing-om** for the tip.  I found my access is 192.168.2.1. That got me to the online setup. I searched it all for the TKIP to change to aes-wpa2 but did not fine it there.  I went through several layers of screens both horizontal and vertical menu items.

---

### Post by Bashing-om on 2014-03-13
jlh68; Hey,

I also have a Cisco router, and I find that setting under wireless -> wireless security -> WPA algorithms .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by jlh68 on 2014-03-13
Mine must be the home version as it does not have that menu item. See the screenshot, that is what I have and the blacked out is the passphrase.

---

### Post by Bashing-om on 2014-03-13
jlh68; Welp. 

You are at the same place as I, different models. I have several options in that screen that are not present in yours.

Sorry to have got your hopes up - but not a total loss as I did learn a bit - .

I am back to my lurking mode 'till I think I can add something .

[INDENT][INDENT]'till I can shine a light
[/INDENT][/INDENT]

---

### Post by Hadaka on 2014-03-14
Hi, I looked your cicso m10 router up online
to change the tkip setteng to wpa-2/aes is under encryption
..i "think" the page you posted is the correct page..try clicking the
up/down arrows above your password and see if that changes..it says
wpa-wpa-2 mxed right now...see if you can get to wpa-2/aes....wpa-2/ccmp
either one.
thanks

---

### Post by jlh68 on 2014-03-14
Choices are:[LIST]
[*]WPA/WPA2 mixed-mode
[*]WPA2 Personal
[*]WPA Personal
[*]WEP
[*]RADIUS
[*]Diabled
[*]
[/LIST]

---

### Post by jlh68 on 2014-03-14
Here is the definition (from my Cisco router) of WPA/WPA2 Mixed-Mode:
> WPA/WPA2 Mixed Mode 	

WPA/WPA2 mixed-mode supports two encryption methods at the same time: WPA2-Personal with AES encryption, and WPA-Personal with TKIP encryption, with a shared dynamic encryption key.

Passphrase. Enter a Passphrase of 8-63 characters.

WPA2 Personal is the following
> WPA2 Personal 	

WPA2-Personal supports only AES encryption.

Passphrase. Enter a Passphrase of 8-63 characters.

So I changed it to WPA2 Personal, and rebooted netbook and it still would not connect.  I was thinking about restoring my "Home" partition with my backup and see if that would get me back in business.  Any thoughts to that? Or should we continue on working this out.  I am learning from it, so it is not a lost cause.

---

### Post by Hadaka on 2014-03-14
GOOD JOB !!  only thing left to do in the router iis change the channel to 1 or 11
then..yeah..not going to break anything..restore your home file .
also are you able to connect with the ethernet cable?

---

### Post by jlh68 on 2014-03-16
Today I restored my "home" partition from an external HD.  Bad news, still no connectivity.  It appears that the WiFi is working, but will not allow the computer to communicate on the WiFi channel. The Ethernet connection also does not connect.

---

### Post by Hadaka on 2014-03-16
try this...please do..
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo modprobe ath9k
```
BOOT
got wireless?

---

### Post by jlh68 on 2014-03-19
I followed your instructions, still no connection.

Here is some information:  I am using the subject netbook to write this, but I am using a USB live Unbutnu12.04LTS.  At this point I am reluctant to reinstall the OS, as I was really waiting to install 14.04LTS next month.  Maybe I caould get the info from this OS and compare it to the onboard OS to see what is different?

What do you think of that plan?

---

### Post by Hadaka on 2014-03-19
HI, trying to set up wireless and other driver driven devices can
be diffiult with the set up you are trying, USB/LIVE/TRY ME.
I am still surprised at least the wired ethernet connection is
not working. I suspect you will have tweaking to do as well
with 14.04 but seems to be the norm now. You decide, I will
happy to continue woking this,or you can mark it solved and await 14.04
which you can load now if you like. Just because the official release date
is april..doesnt mean it will be bug free.

---

### Post by jlh68 on 2014-03-19
I hope you did not misunderstand me, using the USB live, I had no problem with connecting on WiFi.  I have not tried Ethernet, but I expect it works also.  So my installed OS is missing something that the live OS has.  

I am going to open a terminal and ask the same questions as you-all had me to do from the start and I will report the differences back to this forum.  Lets see if that action willl uncover something that will help us.

Thanks for your help.  I believe getting it to work in 12.04LTS is achievabe.

---

### Post by Hadaka on 2014-03-19
it "may" still have a piece of the wl driver stuck in there
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf wl
sudo modprobe -v ath9k
```
do each command even if you get an error message
then post the output of..
```
lsmod
```
thanks.
p.s.  ignore any offering of a proprietary driver...or any driver

---

### Post by jlh68 on 2014-03-19
Here is the USB (ubuntu@ubuntu) code versus the resident OS code (john@nighthawk)


```
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:0740]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e047]
	Kernel driver in use: ath9k
ubuntu@ubuntu:~$ 



john@Nighthawk:~$ lspci -nnk | grep -iA2 net 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 
        Subsystem: Acer Incorporated [ALI] Device [1025:0740] 
        Kernel driver in use: r8169 
-- 
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01) 
        Subsystem: Foxconn International, Inc. Device [105b:e047] 
        Kernel driver in use: ath9k
```

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23126  0 
kvm                   422160  0 
snd_hda_codec_realtek    79756  1 
snd_hda_codec_hdmi     32476  1 
acer_wmi               32845  0 
snd_hda_intel          34117  5 
joydev                 17694  0 
sparse_keymap          13891  1 acer_wmi
snd_hda_codec         135141  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
arc4                   12530  2 
ath9k                 133133  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              555198  1 ath9k
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
dm_multipath           23306  0 
scsi_dh                14589  1 dm_multipath
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
ath9k_common           14054  1 ath9k
videodev              125126  2 uvcvideo,videobuf2_core
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              399665  2 ath9k,ath9k_common
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_timer              29990  2 snd_pcm,snd_seq
microcode              23030  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
psmouse               102075  0 
cfg80211              208382  3 ath9k,mac80211,ath
snd                    83674  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13216  0 
i2c_piix4              13302  0 
k10temp                13174  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mac_hid                13254  0 
parport_pc             32867  0 
rfcomm                 47562  0 
bnep                   18240  2 
ppdev                  17114  0 
bluetooth             211812  10 rfcomm,bnep
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
squashfs               36801  1 
overlayfs              28353  1 
nls_iso8859_1          12714  1 
dm_raid45              78156  0 
xor                    17153  1 dm_raid45
dm_mirror              22204  0 
dm_region_hash         20962  1 dm_mirror
dm_log                 18565  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 781017  0 
zlib_deflate           27140  1 btrfs
libcrc32c              12645  1 btrfs
radeon                912794  3 
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
r8169                  62766  0 
drm                   290344  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  1 radeon
wmi                    19257  1 acer_wmi
video                  19598  1 acer_wmi
usb_storage            49288  1 

john@Nighthawk:~$ lsmod 
Module                  Size  Used by 
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep 
ppdev                  17113  0 
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32530  1 
binfmt_misc            17540  1 
snd_hda_intel          33719  5 
acer_wmi               28418  0 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel 
joydev                 17693  0 
sparse_keymap          13890  1 acer_wmi 
snd_hwdep              17764  1 snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
uvcvideo               72627  0 
arc4                   12529  2 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_timer              29990  2 snd_seq,snd_pcm 
videodev               98259  1 uvcvideo 
psmouse                97519  0 
v4l2_compat_ioctl32    17128  1 videodev 
serio_raw              13211  0 
ath9k                 132428  0 
k10temp                13166  0 
i2c_piix4              13301  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
mac80211              506862  1 ath9k 
radeon                808783  3 
ath9k_common           14053  1 ath9k 
ath9k_hw              411239  2 ath9k,ath9k_common 
snd                    79041  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_timer,snd_seq_device 
ttm                    76949  1 radeon 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw 
drm_kms_helper         46978  1 radeon 
cfg80211              205774  3 ath9k,mac80211,ath 
drm                   241971  5 radeon,ttm,drm_kms_helper 
soundcore              15091  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
i2c_algo_bit           13423  1 radeon 
wmi                    19256  1 acer_wmi 
video                  19651  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp 
r8169                  62190  0]
```

```
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 04:7d:7b:9d:f6:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:199919 (199.9 KB)  TX bytes:199919 (199.9 KB)

wlan0     Link encap:Ethernet  HWaddr 08:ed:b9:3f:0d:aa  
          inet addr:192.168.2.122  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::aed:b9ff:fe3f:daa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13112138 (13.1 MB)  TX bytes:1302794 (1.3 MB)


john@Nighthawk:~$ lwconfig -a 
The program 'lwconfig' is currently not installed.  You can install it by typing: 
sudo apt-get install likewise-open
```

```
ubuntu@ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search ntelos.net

john@Nighthawk:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1 
search ntelos.net
```

```
ubuntu@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ubuntu@ubuntu:~$ 

john@Nighthawk:~$ rfkill list 
0: phy0: Wireless LAN 
        Soft blocked: no 
        Hard blocked: no 
1: acer-wireless: Wireless LAN 
        Soft blocked: no 
        Hard blocked: no
```

---

### Post by praseodym on 2014-03-19
Check the differences in both /etc/resolv.conf files. From the "john" computer:
```

sudo apt-get remove --purge resolvconf
sudo reboot
```

---

### Post by jlh68 on 2014-03-19
```
john@Nighthawk:~$ sudo apt-get remove --purge bcmwl-kernel-source 
[sudo] password for john: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Unable to locate package bcmwl-kernel-source 
john@Nighthawk:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf 
rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory 
john@Nighthawk:~$ sudo modprobe -rf wl 
FATAL: Module wl not found. 
john@Nighthawk:~$ sudo modprobe -v ath9k 
john@Nighthawk:~$ lsmod 
Module                  Size  Used by 
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
bluetooth             180113  10 rfcomm,bnep 
ppdev                  17113  0 
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32530  1 
binfmt_misc            17540  1 
acer_wmi               28418  0 
snd_hda_intel          33719  5 
uvcvideo               72627  0 
joydev                 17693  0 
sparse_keymap          13890  1 acer_wmi 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel 
arc4                   12529  2 
videodev               98259  1 uvcvideo 
v4l2_compat_ioctl32    17128  1 videodev 
psmouse                97519  0 
serio_raw              13211  0 
k10temp                13166  0 
i2c_piix4              13301  0 
snd_hwdep              17764  1 snd_hda_codec 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              29990  2 snd_pcm,snd_seq 
video                  19651  0 
ath9k                 132428  0 
radeon                808783  3 
wmi                    19256  1 acer_wmi 
mac80211              506862  1 ath9k 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
ath9k_common           14053  1 ath9k 
ath9k_hw              411239  2 ath9k,ath9k_common 
```

---

### Post by jlh68 on 2014-03-20
Out of the blue I remembered that the subject hard drive ("Nighthawk") came out of my dead Laptop which uses a Broadcom wifi/ethernet board.  When I swapped it with the Hd that came in the 750 Netbook ("Osprey"), the wifi worked (the Hd that came with the 750 netbook the WiFi did not work, but does now).  The "Nighthawk" HD WiFi worked upon initial installation and up to my recent operation using Boot-Repair-Disk (USB flash drive).  Since that boot repair I have had connection problems.

I provide the above to help in trouble shooting.  The next problem will be when I repair my Laptop and put "Nighthawk" back in it.  I will then have to set up broadcom. I will worry about that later.

---

