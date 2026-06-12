---
title: "Internet not working in my computer - Ubuntu 13.10"
date: 2014-01-21
forum: Networking &amp; Wireless
---

### Post by matheuspfaustino on 2014-01-21
Hello,

Thank you for attention.
I installed a copy of Ubuntu 13.10 in a partition of my computer, making a dual-boot with Windows 7 for work.
Everything worked, less the internet. My computer is connected with ethernet cable and in windows 7 I have access to internet, but not in Ubuntu.

Even Ubuntu running by CD I don't have internet, neither in installation I have.

I'm attaching a file that contain some information about my computer, maybe can help.

I think that is a driver problem.

Someone can help fix this, this never happened to me, before.

Thanks

[ATTACH]249636[/ATTACH]

---

### Post by SlidingHorn on 2014-01-21
What are the outputs of the following commands:

lspci


sudo lshw -C network

---

### Post by matheuspfaustino on 2014-01-22
Sorry for the delay. This computer is in my house.

The command lspci return:

```
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
 

 00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
 

 00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
 

 00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
 

 00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
 

 00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
 

 00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
 

 00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
 

 00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
 

 00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
 

 00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
 

 00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
 

 00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
 

 00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
 

 00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
 

 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
 

 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
 

 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
 

 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
 

 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
 

 00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
 

 02:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2)


```

And 

The command sudo lshw -C network show:

   ```
PCI (sysfs)
```

---

### Post by praseodym on 2014-01-22
The device is there:

```
 00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
```
Check the following:
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
```
Remove all profiles in "cable" and "DSL" in the network-manager applet and reboot. Check afterwards:
```
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by matheuspfaustino on 2014-01-22
> **praseodym said:**
> The device is there:

```
 00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
```
Check the following:
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
```
Remove all profiles in "cable" and "DSL" in the network-manager applet and reboot. Check afterwards:
```
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

The part of "Check the following" show me what is in the echo. Nothing more

I remove all profiles and execute the follow commmands:

lsmod
```
 
Module                  Size  Used by

nls_utf8               12557  1

isofs                  39842  1

rfcomm                 46619  0

bnep                   18140  2

snd_hda_codec_via      46478  1

kvm_amd                55604  0

kvm                   414070  1 kvm_amd

ghash_clmulni_intel    13180  0

aesni_intel            51037  0

cryptd                 20403  2 ghash_clmulni_intel,aesni_intel

aes_x86_64             17208  1 aesni_intel

ppdev                  17073  0

snd_hda_intel          33491  3

snd_hda_codec         134212  2 snd_hda_codec_via,snd_hda_intel

snd_hwdep              13602  1 snd_hda_codec

snd_pcm                96580  2 snd_hda_intel,snd_hda_codec

btusb                  18334  0

snd_seq_midi           13324  0

snd_rawmidi            30512  1 snd_seq_midi

snd_seq_midi_event     14899  1 snd_seq_midi

microcode              22803  0

psmouse                95552  0

serio_raw              13215  0

parport_pc             32688  1

bluetooth             209199  12 rfcomm,bnep,btusb

nouveau               895609  3

ttm                    83595  1 nouveau

drm_kms_helper         46784  1 nouveau

snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event

fam15h_power           13119  0

drm                   275528  5 nouveau,ttm,drm_kms_helper

i2c_algo_bit           13413  1 nouveau

mxm_wmi                12979  1 nouveau

video                  19335  1 nouveau

wmi                    19070  2 nouveau,mxm_wmi

snd_timer              29425  2 snd_pcm,snd_seq

snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq

edac_core              52451  0

edac_mce_amd           23303  0

snd                    78734  15 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

mac_hid                13205  0

k10temp                13126  0

i2c_nforce2            13013  0

lp                     17759  0

parport                46345  3 ppdev,parport_pc,lp

soundcore              15047  1 snd

snd_page_alloc         18484  2 snd_hda_intel,snd_pcm

hid_generic            12493  0

usbhid                 46947  0

hid                   100366  2 hid_generic,usbhid

uas                    17844  0

usb_storage            48838  1

forcedeth              67156  0

pata_amd               14118  0

sata_nv                31830  3  

```
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:a2:fb:6e 

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 
 
lo        Link encap:Local Loopback 

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:96 errors:0 dropped:0 overruns:0 frame:0

          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0

          RX bytes:7840 (7.8 KB)  TX bytes:7840 (7.8 KB)


```
cat /etc/network/interfaces
```
 
 
# interfaces(5) file used by ifup(8) and ifdown(8)

auto lo

#iface lo inet loopback

iface eth0 inet dhcp 

```
cat /etc/resolv.conf
```
 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)

#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 

```
route -n
```
 
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


```

---

### Post by praseodym on 2014-01-23
Open this file
```

gksudo gedit /etc/network/interfaces
```
It has to look like this
```

auto lo
iface lo inet loopback
```
Save, close the Editor and reboot. Check the nameservers again.

---

### Post by matheuspfaustino on 2014-01-25
> **praseodym said:**
> Open this file
```

gksudo gedit /etc/network/interfaces
```
It has to look like this
```

auto lo
iface lo inet loopback
```
Save, close the Editor and reboot. Check the nameservers again.


I do that and I change the file interfaces, now it is like this:
```
# interfaces(5) file used by ifup(8) and ifdown(8)

auto lo
iface lo inet loopback
#iface eth0 inet dhcp
```

For a look the nameservers I use this command "Ifconfig -a" ?
If it's, so return:

```
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:a2:fb:6e  

          inet6 addr: fe80::be5f:f4ff:fea2:fb6e/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:32216 (32.2 KB)

 
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:176 errors:0 dropped:0 overruns:0 frame:0

          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0
          RX bytes:14304 (14.3 KB)  TX bytes:14304 (14.3 KB) 

```

Thanks for attention

---

### Post by praseodym on 2014-01-25
No, 
its
```

cat /etc/resolv.conf
```
Try:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

