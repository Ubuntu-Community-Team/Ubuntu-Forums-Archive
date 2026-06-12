---
title: "D-Link Wireless N Nano USB Adapter DWA-131"
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by techanimelover on 2014-01-19
Can anybody help me getting a D Link Wireless N Nano USB Adapter DWA-131 to work under Ubuntu?
TIA

---

### Post by praseodym on 2014-01-19
Please open a terminal with CTRL+ALT+T and show the output of

```
lsusb

```
with the stick plugged in. Does LAN work?

---

### Post by techanimelover on 2014-01-19
i am on online wth the lan right now

thegroup@thegroup-Pavilion-zv5000-PF126UA-ABL:~$ lsusb
\Bus 001 Device 002: ID 2001:330d D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by praseodym on 2014-01-20
Which Ubuntu version is it?

---

### Post by techanimelover on 2014-01-20
Ubuntu 12.04.4 LTS

---

### Post by praseodym on 2014-01-21
Update the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by techanimelover on 2014-01-21
when is used the code and it finished  i rebooted the computer did not restart correctly and i had to power it off manually 
when i finally got it back up the dongle still did not work

---

### Post by praseodym on 2014-01-22
Check now
```

lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by techanimelover on 2014-01-22
it said no wireless extentions

---

### Post by praseodym on 2014-01-24
Please show the outputs, if possible

---

### Post by techanimelover on 2014-01-24
how do i do that? sorry i am a newbie

---

### Post by praseodym on 2014-01-25
Like you did for "lsusb" in the beginning

---

### Post by connor-jolley1980 on 2014-04-05
> **praseodym said:**
> Please show the outputs, if possible

Hi.

I am having a similar issue. My internal Qualcomm device doesn't work so I bought the DWA-131.

LAN works with USB adapter plugged in, no light on the adapter

Here is the lsusb - using v. 13.10

```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 13d3:5188 IMC Networks 
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 2001:330d D-Link Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I used your first code for installing the drivers, it did a lot of install stuff, rebooted, dongle still isn't working.

I did the second code and this is the output

```
Module                  Size  Used by
nls_utf8               12557  1 
udf                    89685  1 
crc_itu_t              12707  1 udf
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  0 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
snd_hda_codec_hdmi     41154  1 
snd_hda_codec_realtek    56475  1 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431754  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
acer_wmi               32522  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  2 acer_wmi,asus_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
snd_hda_intel          52267  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
arc4                   12608  2 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath9k                 155907  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
microcode              23656  0 
mac80211              597268  1 ath9k
psmouse                97655  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
serio_raw              13413  0 
cfg80211              480503  3 ath,ath9k,mac80211
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
nouveau               943749  0 
i915                  661339  5 
mxm_wmi                13021  1 nouveau
ttm                    84169  1 nouveau
drm_kms_helper         52710  2 i915,nouveau
video                  19318  4 i915,acer_wmi,nouveau,asus_wmi
wmi                    19070  4 acer_wmi,mxm_wmi,nouveau,asus_wmi
mac_hid                13205  0 
drm                   297056  6 ttm,i915,drm_kms_helper,nouveau
mei_me                 18421  0 
mei                    77782  1 mei_me
soundcore              12680  1 snd
i2c_algo_bit           13413  2 i915,nouveau
hid_logitech_dj        18581  0 
usbhid                 53014  0 
hid                   101762  3 usbhid,hid_logitech_dj
ahci                   25819  3 
alx                    32452  0 
libahci                32009  1 ahci
mdio                   13807  1 alx
connor@connor:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
connor@connor:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 74:d0:2b:e7:1f:8c  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76d0:2bff:fee7:1f8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14916 (14.9 KB)  TX bytes:14916 (14.9 KB)

wlan0     Link encap:Ethernet  HWaddr 24:fd:52:79:9c:53  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by praseodym on 2014-04-06
Hi,

the driver DEB-package is for 13.04, uninstall it and install the right one:
```

sudo apt-get remove --purge rtl8192cu-tjp-dkms_1.6_all.deb
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Additionally, deactivate the hardware encryption of the driver for the internal Atheros card:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Reboot.

---

### Post by connor-jolley1980 on 2014-04-06
Thanks.

I am using 13.10 though. Does that matter? Should I go and install 12 again? I only upgraded because I couldn't get the Atheros device working using 12.

When I do the first line this is the output:

```
connor@connor:~$ sudo apt-get remove --purge rtl8192cu-tjp-dkms_1.6_all.deb
[sudo] password for connor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtl8192cu-tjp-dkms_1.6_all.deb
E: Couldn't find any package by regex 'rtl8192cu-tjp-dkms_1.6_all.deb'
```

---

### Post by connor-jolley1980 on 2014-04-06
I'm actually much more interested in getting the Atheros to work, it's the internal device in my laptop.

When I go to network settings I cannot turn wireless on, it switches on for a second then just switches off again.

When I use your code this is the output:

```
connor@connor:~$ echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
[sudo] password for connor: 
Sorry, try again.
[sudo] password for connor: 
options ath9k nohwcrypt=1
connor@connor:~$ sudo modprobe -rfv ath9k
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
connor@connor:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.11.0-19-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-19-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1 nohwcrypt=1 
connor@connor:~$ 


```

When I reboot I still can't tuen the wireless on

Currently I am connecting my phone to the network then tethering it to my laptop via USB

---

### Post by praseodym on 2014-04-06
Sorry, it needs to be
```

sudo apt-get remove --purge rtl8192cu-tjp-dkms
```
For your ASUS in general:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
Reboot.

---

### Post by connor-jolley1980 on 2014-04-11
Atheros problem was solved by someone on Ask Ubuntu:

Enter the following, line by line:

```
sudo modprobe -r acer-wmi
cd /etc/modprobe.d
sudo nano blacklist.conf
```

  Then add ```
blacklist acer-wmi
``` as a new line at the end of the file.

IT WORKED!!!! W000000000!!!!!

---

