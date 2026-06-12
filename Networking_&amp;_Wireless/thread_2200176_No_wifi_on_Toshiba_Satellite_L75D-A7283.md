---
title: "No wifi on Toshiba Satellite L75D-A7283"
date: 2014-01-17
forum: Networking &amp; Wireless
---

### Post by Keith_Valin on 2014-01-17
I cannot get wifi.  I have used intsalled:
```
 linux-headers-3.2.0-54-generic 
 linux-headers-3.2.0-54
```
before but now I can't get this.
Any suggestions?

---

### Post by praseodym on 2014-01-18
Please show
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```
Does LAN work?

---

### Post by Keith_Valin on 2014-01-18
```
 uname -a 
``` results in
```
Linux Linux-lapto 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux 
```
```
keithvalin@Linux-lapto:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:fa85]
    Kernel driver in use: alx
--
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181]
keithvalin@Linux-lapto:~$ lsusb
Bus 002 Device 002: ID 04f2:b3b1 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
keithvalin@Linux-lapto:~$ lsmod
Module                  Size  Used by
vesafb                 13876  1 
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
snd_hda_codec_conexant    62464  1 
snd_hda_codec_hdmi     37434  1 
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_intel          44339  5 
snd_hda_codec         141716  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
uvcvideo               82214  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
videobuf2_core         40785  1 uvcvideo
snd_rawmidi            30417  1 snd_seq_midi
videodev              130053  2 uvcvideo,videobuf2_core
kvm                   455932  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
videobuf2_vmalloc      13056  1 uvcvideo
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ghash_clmulni_intel    13259  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
aesni_intel            55495  0 
joydev                 17613  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
snd                    69533  20 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
toshiba_acpi           18774  0 
sparse_keymap          13890  1 toshiba_acpi
video                  19652  0 
wmi                    19256  1 toshiba_acpi
mac_hid                13253  0 
lp                     17799  0 
psmouse                97873  0 
i2c_piix4              13459  0 
parport                46562  3 parport_pc,ppdev,lp
serio_raw              13215  0 
fam15h_power           13166  0 
alx                    73230  0 
mdio                   13807  1 alx
microcode              23017  0 
ahci                   25879  2 
libahci                31606  1 ahci
keithvalin@Linux-lapto:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

keithvalin@Linux-lapto:~$ cat /ect/resolv.conf
cat: /ect/resolv.conf: No such file or directory
keithvalin@Linux-lapto:~$ rfkill list

```

---

### Post by Keith_Valin on 2014-01-18
No result in rfkill list

---

### Post by praseodym on 2014-01-18
Install this driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by chili555 on 2014-01-18
Are you sure that rtl8192cu covers his device? [http://ubuntuforums.org/showthread.php?t=2187780](http://ubuntuforums.org/showthread.php?t=2187780)

---

### Post by praseodym on 2014-01-18
You're right. It is the wrong driver:

```
sudo apt-get remove --purge rtl8192cu-tjp-dkms
```
Follow Chili's link!

---

### Post by Keith_Valin on 2014-01-18
I have found a driver that has worked with xubuntu and LXLE (with some packages installed), but in ubuntu none of the packages work with the driver which is [located here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE").  The driver is called RTL8188CE, but mine is an RTL8188EE (CE includes many common drivers for realtek devices).  This is a .tar.bz2 file so in order to install it you must extract it and run ```
 make 
``` and whenn that's done you run ```
 sudo make install 
``` and reboot, but whenever i run the 1st command it gives me ```
 keithvalin@Linux-lapto:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ makemake -C /lib/modules/3.8.0-35-generic/build M=/home/keithvalin/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-35-generic'
  CC [M]  /home/keithvalin/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/keithvalin/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/keithvalin/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/keithvalin/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/keithvalin/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-35-generic'
make: *** [all] Error 2

```

---

### Post by praseodym on 2014-01-18
Try the patched one:

[http://media.cdn.ubuntu-de.org/forum/attachments/38/34/5443987-rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patc.gz](http://media.cdn.ubuntu-de.org/forum/attachments/38/34/5443987-rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patc.gz)

Edit: Patches here:

[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/?highlight=rtl8188ee#post-5443987](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/?highlight=rtl8188ee#post-5443987)

last grey box

---

### Post by chili555 on 2014-01-18
Did you try my proven solution that I linked? In the link, the OP says:> Now i'm writing with my wi-fi on :P

---

### Post by Keith_Valin on 2014-01-19
Does the patched one use make and sudo make install?

---

### Post by Keith_Valin on 2014-01-19
Never mind it worked!!!  Thank you!

---

