---
title: "Network Manager not allowing to disconnect or edit connections."
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by kagashe on 2015-02-23
I am using Ubuntu 12.04 on my HP ProBook 4410s Laptop. Since last update the Disconnect and Edit connections options in the Network Manager are greyed so I can't use them.

Kamalakar

---

### Post by Hadaka on 2015-02-23
Hi, please do..
```
sudo  apt-get update
sudo apt-get upgrade
```
```
sudo service network-manager stop
sudo service network-manager restart
```
please do and post...
```
cat /etc/network/interfaces
cat /etc/Network/NetworkManager
cat /etc/NetworkManager/NetworkManager.conf
```
thanks

---

### Post by kagashe on 2015-02-23
```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
#auto wlan0
#iface wlan0 inet static
#address 10.10.0.1
#netmask 255.255.255.0

$ cat /etc/Network/NetworkManager
cat: /etc/Network/NetworkManager: No such file or directory

$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

Kamalakar

---

### Post by Hadaka on 2015-02-23
Thanks...please post the output of..
```
rfkill list all
lsmod
```

---

### Post by kagashe on 2015-02-23
```
$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: hp-gps: GPS
	Soft blocked: yes
	Hard blocked: yes

```

```
$ lsmod
Module                  Size  Used by
ppp_deflate            12878  0 
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12627  1 ppp_async
option                 38241  1 
usb_wwan               19762  1 option
usbserial              39125  5 option,usb_wwan
usb_storage            48754  0 
pci_stub               12550  1 
vboxpci                22910  0 
vboxnetadp             25616  0 
vboxnetflt             27270  0 
vboxdrv               299668  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   19107  2 
rfcomm                 59026  0 
bluetooth             356727  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  17423  0 
binfmt_misc            13172  1 
snd_hda_codec_hdmi     45939  1 
snd_hda_codec_analog    14537  1 
uvcvideo               72275  0 
videobuf2_core         39510  1 uvcvideo
videodev              108952  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
snd_hda_intel          43462  3 
snd_hda_codec         169779  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
arc4                   12509  2 
snd_hwdep              13276  1 snd_hda_codec
iwldvm                221597  0 
snd_pcm                90501  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              564463  1 iwldvm
snd_seq_midi           13132  0 
i915                  733300  2 
snd_rawmidi            25198  1 snd_seq_midi
joydev                 17299  0 
coretemp               13352  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         49282  1 i915
iwlwifi               161530  1 iwldvm
snd_timer              28971  2 snd_pcm,snd_seq
psmouse                97606  0 
drm                   249595  3 i915,drm_kms_helper
hp_accel               25756  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
lis3lv02d              19600  1 hp_accel
hp_wmi                 17834  0 
sparse_keymap          13658  1 hp_wmi
serio_raw              13230  0 
snd                    61383  17 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
kvm                   400703  0 
cfg80211              423921  3 iwldvm,mac80211,iwlwifi
soundcore              12600  1 snd
mac_hid                13077  0 
lpc_ich                16987  0 
input_polldev          13648  1 lis3lv02d
i2c_algo_bit           13316  1 i915
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
video                  19330  1 i915
wmi                    18827  1 hp_wmi
shpchp                 32265  0 
lp                     13359  0 
parport                40945  3 parport_pc,ppdev,lp
ahci                   25703  1 
libahci                31395  1 ahci
sky2                   53656  0 

```

Kamalakar

---

### Post by Hadaka on 2015-02-23
hi, please do..
```
rfkill unblok all
echo "blacklist hp-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
also see if you have a keyboard on/off switch
experiment with that and run
```
rfkill list all
```
to see if there are changes
thanks.

---

### Post by houstonbofh on 2015-03-01
I have a "Me too" on this one.  Both my desktop and a VM inside that desktop on 12.04.  It used to work, but I suspect an update broke it.  This is a problem since the VPN password changed, but I can't change it.  Nor can I add new ones...

---

### Post by houstonbofh on 2015-03-01
lee@dev01:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

lee@dev01:~$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
lee@dev01:~$ 


Hardware is different on my real desktop vs the KVM emulated one, so that does not count.

---

### Post by houstonbofh on 2015-03-03
I did a lot more digging, and it seems that the update of network-manager-gnome from 0.9.4.1-0ubuntu2.3 to 0.9.4.1-0ubuntu2.4 caused this issue.  I bugged it here. [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1427800](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1427800)

To work around you have to go into synaptic and force version back on network-manager-gnome libnm-gtk0 libnm-gtk-common and unity-greeter, and you should be OK.  Also subscribe to the bug and watch for real fixes.  Additionally, finding network-manager-gnome libnm-gtk0 libnm-gtk-common in version 0.9.4.1-0ubuntu2.3 would also work without needing you to roll back unity-greeter.

---

### Post by houstonbofh on 2015-03-04
Mine was a dupe.  Master bug report is here.  [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1424119](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1424119)

---

### Post by mikewhatever on 2015-03-11
Does anyone know how to disable/remove the new network manager from lightdm? That is a new feature, and I suspect it might be related to the permission problem.

---

