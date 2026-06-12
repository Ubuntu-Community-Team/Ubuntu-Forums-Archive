---
title: "New build, 14.04 and ethernet does not work"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by sebastien3 on 2014-10-12
So after having run Ubuntu for the past 6 years I decided it was time to upgrade my computer. I assembled a new system and installled 14.04. Everything worked great except one major problem. Ethernet is not working.

I need  some help here, I am more a end user, my skill level is minimal at best. I am trying to connect to my internet modem direct. If I plug the ethernet cable into my windoze laptop it works, but plug it into my ubuntu computer and it does not. Wireless is working fine, I'm hotspotting the phone as we speak to be able to post this. Is anyone able to help me, or point me in the right direction?

Thank you, any help is greatly appreciated.

---

### Post by praseodym on 2014-10-12
Please show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by sebastien3 on 2014-10-13
> **praseodym said:**
> Please show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/resolv.conf
```

**lspci -nnk | grep -iA2 net**

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Device [7470:3468]
``` 

and

**lsmod**

```
Module                  Size  Used by
r8188eu               814658  0 
asix                   38914  0 
usbnet                 43913  1 asix
mii                    13934  2 asix,usbnet
cfg80211              484040  0 
joydev                 17381  0 
hid_logitech_dj        18581  0 
usbhid                 52659  0 
hid                   106148  5 usbhid,hid_logitech_dj
usb_storage            62209  0 
usblp                  22891  0 
snd_hda_codec_realtek    65580  1 
snd_hda_codec_hdmi     46368  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
nls_iso8859_1          12713  1 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143109  0 
kvm                   451552  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
acpi_pad               17926  0 
mac_hid                13205  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i915                  783805  5 
serio_raw              13462  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
video                  19476  1 i915
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         55071  1 i915
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
drm                   303102  4 i915,drm_kms_helper
parport_pc             32701  1 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 i915
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mei_me                 18627  0 
mei                    82276  1 mei_me
soundcore              12680  1 snd
psmouse               106678  0 
ahci                   25819  3 
libahci                32716  1 ahci
```

and
[B]
ifconfig -a[/B]

```
eth2      Link encap:Ethernet  HWaddr 00:50:b6:6b:59:0a  
          inet6 addr: fe80::250:b6ff:fe6b:590a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79283 (79.2 KB)  TX bytes:144311 (144.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3619 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440947 (440.9 KB)  TX bytes:440947 (440.9 KB)

wlan0     Link encap:Ethernet  HWaddr c0:4a:00:22:2d:4b  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c24a:ff:fe22:2d4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5754 errors:0 dropped:147 overruns:0 frame:0
          TX packets:5686 errors:0 dropped:17 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3952066 (3.9 MB)  TX bytes:831455 (831.4 KB)
```

and 

[B]cat /etc/resolv.conf
[/B]
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```

I hope this helps. At the moment I have the built in integrated network adapter, and pcie adapter (same chipset, had it handy to try out) and usb adapter, which is what I most recently have tried plugging into. For now I am still only able to use wireless via a usb wireless adapter. Thank you for taking the time to help me out, it is much appreciated!

---

### Post by praseodym on 2014-10-14
Install the latest driver via wireless:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

