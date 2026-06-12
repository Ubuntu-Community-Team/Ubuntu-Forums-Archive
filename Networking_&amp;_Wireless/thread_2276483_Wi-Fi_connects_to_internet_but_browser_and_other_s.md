---
title: "Wi-Fi connects to internet but browser and other software will not open"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by harry003 on 2015-05-02
Thank you in advance for your help!

Here is the output from wireless-info.txt:

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ printf "\n########## wireless info START ##########\n\n"



########## wireless info START ##########



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z  ###########



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/ byte:~$ ifconfig -a | sed '/^lo /,/^$/d'

eth0      Link encap:Ethernet  HWaddr fc:aa:14:55:a0:4b  

          inet addr:10.132.97.141  Bcast:10.132.97.255  Mask:255.255.255.0

          inet6 addr: 2601:0:8700:6e0:feaa:14ff:fe55:a04b/64 Scope:Global

          inet6 addr: 2601:0:8700:6e0:b1cb:35d4:c1cf:498/64 Scope:Global

          inet6 addr: fe80::feaa:14ff:fe55:a04b/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:4890 errors:0 dropped:0 overruns:0 frame:0

          TX packets:369 errors:0 dropped:846 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2089076 (2.0 MB)  TX bytes:36978 (36.9 KB)



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ printf "\n##### iwconfig ##########################\n\n"



##### iwconfig ##########################



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ iwconfig

eth0      no wireless extensions.



lo        no wireless extensions.



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ printf "\n##### route #############################\n\n"



##### route #############################



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

0.0.0.0         10.132.97.99    0.0.0.0         UG    0      0
        0 eth0

10.132.97.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ printf "\n##### resolv.conf #######################\n\n"



##### resolv.conf #######################



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ grep -v '^#' /etc/resolv.conf

nameserver 127.0.1.1

search hsd1.ga.comcast.net

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ printf "\n##### NetworkManager info ###############\n\n"



##### NetworkManager info ###############



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ if [ -x /usr/bin/nm-tool ]; then

> 

>     nm-tool

> 

> else

> 

>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0 ]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ printf "\n##### NetworkManager.conf ###############\n\n"



##### NetworkManager.conf ###############



#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf

[main]

plugins=ifupdown,keyfile,ofono

dns=dnsmasq



[ifupdown]

managed=false

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ 

#]0;aaron@asm-gigabyte: ~#aaron@asm-gigabyte:~$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; the n@asm-gigabyte:~$ if [ -n "$SUDO" ]; then

> 

>     trap "" 2 3

> 

>     IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan 2>&1) && SUDOSUCCESS="yes" ||

---

### Post by harry003 on 2015-05-02
Since 54 people have already viewed this in less than 2 hours, there must be some serious interest in it.

Here is the beginning part that was posted in another thread, just so you have some background:


I am returning after a few years with a fresh install of 14.04 on a  Gigabyte AM3+ motherboard with onboard LAN, for/with my teenage son.

The ethernet connects and I get the up/down arrow symbol, but when I attempt to open Firefox, it hangs. 

Same when I attempt to do something like "apt-get update"

Not only that, but a Tendo USB wi-fi dongle will "sometimes" connect  too, and it always sees the wireless network in my home whether it  successfully connects to it or not.

This represents several iterations of various attempts at  disabling/enabling, re-booting, hot-plugging, etc. We have also  completely re-installed Ubuntu itself.
The evidence leads me to believe that this is not a hardware or OS problem but rather a specific Firefox problem. 

Is there any way to download only the Firefox software program on  another computer and install it via flash drive onto the new computer?

Thank you very much in advance.

---

### Post by wildmanne39 on 2015-05-03
Please run the script again and read how to post it in that link, I am not sure what you posted but it was not the output of the script.
Thanks

---

### Post by harry003 on 2015-05-03
I really appreciate your help. All this stuff that takes seconds online is a huge kludge on a sneaker net.

The script was downloaded to a flash drive on another computer, copied and pasted into a terminal, and we hit "Enter"

"wireless-info.txt" was then generated, and I copied and pasted that text into my post, using the other computer.

I have attached the actual .txt file here, in case that can help.

My son will be available in a little while, and we will return to the process.

Just to be clear, can the body of the text of the script file be run as-is, or do I code the "intro" part: 

```
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info
```

(shown in the link) first, and then add the long part?

Thank you.

---

### Post by wildmanne39 on 2015-05-03
The command you posted is meant to be run all at once but it is for a computer with an internet connections, it will download the script and then run it creating the file in your home folder. It is different when you have to copy to a flash drive then put it on your ubuntu computer. You need to put the script on your desktop then right click and make the file executable then you can run the file with the run dialogue hopefully I say that because my run dialogue is broken in 14.04. You should be able to open the run dialogue by holding down the ALT+F2 key.

---

### Post by wildmanne39 on 2015-05-03
Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by harry003 on 2015-05-03
Thanks, Wild Man! Here is what we got:

```
aaron@asm-gigabyte:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
Linux asm-gigabyte 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
aaron@asm-gigabyte:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
aaron@asm-gigabyte:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 005 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
aaron@asm-gigabyte:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

aaron@asm-gigabyte:~$ rfkill list all
aaron@asm-gigabyte:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
uas                    23159  0 
usb_storage            66545  1 uas
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
kvm_amd                60328  0 
kvm                   452043  1 kvm_amd
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  0 
snd_hda_codec_via      31956  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_via
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_hda_codec_hdmi     47548  1 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
radeon               1408739  3 
snd_hda_intel          30469  5 
snd_hda_controller     31056  1 snd_hda_intel
edac_core              56549  0 
snd_hda_codec         139682  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
serio_raw              13483  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
k10temp                13144  0 
snd_rawmidi            30876  1 snd_seq_midi
fam15h_power           13142  0 
edac_mce_amd           22578  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
sp5100_tco             13999  0 
snd                    79468  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ttm                    85314  1 radeon
i2c_piix4              22166  0 
drm_kms_helper         61574  1 radeon
soundcore              15047  2 snd,snd_hda_codec
drm                   311018  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
shpchp                 37047  0 
tpm_infineon           17131  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13053  0 
ahci                   34062  2 
r8169                  71694  0 
pata_atiixp            13279  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
aaron@asm-gigabyte:~$ 


```

---

### Post by harry003 on 2015-05-03
I have the installation DVD that came with the motherboard.

Under the Windows OS, there are various drivers and installers that take care of these problems, but I do not see anything there that might run under Linux.

Is there any chance that there is a solution to be found? And how would I find it?

Thanks!

---

### Post by wildmanne39 on 2015-05-03
I do not see a wireless device, only the ethernet. 
Your windows drivers really do not do us any good for linux.
Go into your bios and make sure your wireless is on, some bios have a setting for wireless. If it is a standard bios you can reset it and see if your device is seen then.

There is not anything we can do if the device is not showing up.

Is your wifi an internal device?
Thanks

---

### Post by harry003 on 2015-05-03
I have a wireless USB dongle, actually 2 of them, both Tenda brands.

For now I am just trying to hard-wire via ethernet cable just to try to get SOMETHING going.

My concept is that if I can ever just get online, even once, then I can run updates and whatnot and that will bring in whatever it is that is missing.

My thread title should have read "Wi-Fi and/or ethernet connects but browser and apt-get will not open"

---

### Post by wildmanne39 on 2015-05-03
I was looking for wifi devices, if you plug one in then post those commands again we can trouble shoot it.

I really do not work with wired issues but the issue with yours is that it is using the wrong driver but I do not know no way to fix that without an internet connection. You are actually connected with your wired but because it is the wrong driver it is very slow, I have seen on person download the driver needed and install it with that wrong driver but it would be very slow if it worked at all.

So let's look at your wifi first.

---

### Post by harry003 on 2015-05-06
> **Wild Man said:**
> 

You are actually connected with your wired but because it is the wrong driver



Well, yes and no.

According to the icon at the top. With the hard wire, I am on perhaps 20%-30% of the time. With the USB dongle, it will show connection occasionally for a brief period, but always collapses when I actually try to do something.

Here is the output with the ethernet unplugged and the W522U dongle in a USB port:

*    *    *    *    *    *
   aaron@asm-gigabyte:~$ cat /etc/lsb-release;
uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
Linux asm-gigabyte 3.16.0-30-generic
#40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64
x86_64 GNU/Linux
aaron@asm-gigabyte:~$ lspci -nnk | grep -iA2
net
03:00.0 Ethernet controller [0200]: Realtek
Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit
Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd
Motherboard [1458:e000]
	Kernel driver in use: r8169
aaron@asm-gigabyte:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6364 Alcor Micro
Corp. AU6477 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0053 Microsoft Corp.
Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux
Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub
aaron@asm-gigabyte:~$ iwconfig
eth0      no wireless extensions.
 lo        no wireless extensions.
 aaron@asm-gigabyte:~$ rfkill list all
aaron@asm-gigabyte:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
uas                    23159  0 
usb_storage            66545  1 uas
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2
hid_generic,usbhid
kvm_amd                60328  0 
kvm                   452043  1 kvm_amd
radeon               1408739  3 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
snd_hda_codec_via      31956  1 
snd_hda_codec_generic    68937  1
snd_hda_codec_via
aesni_intel           152552  0 
snd_hda_codec_hdmi     47548  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3
ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          30469  5 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5
snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
serio_raw              13483  0 
fam15h_power           13142  0 
k10temp                13144  0 
edac_core              56549  0 
snd_pcm               104112  4
snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
edac_mce_amd           22578  0 
snd_seq_midi           13564  0 
sp5100_tco             13999  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_piix4              22166  0 
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2
snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3
snd_seq,snd_rawmidi,snd_seq_midi
ttm                    85314  1 radeon
snd_timer              29562  2 snd_pcm,snd_seq
drm_kms_helper         61574  1 radeon
snd                    79468  21
snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   311018  6
ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
soundcore              15047  2
snd,snd_hda_codec
shpchp                 37047  0 
tpm_infineon           17131  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3
lp,ppdev,parport_pc
pata_acpi              13053  0 
ahci                   34062  2 
pata_atiixp            13279  0 
libahci                32424  1 ahci
r8169                  71694  0 
mii                    13934  1 r8169
 

I do appreciate your help very much. Aaron is 15 and I have helped him build this computer. It will be a satisfying learning experience if we successfully complete it!

---

### Post by wildmanne39 on 2015-05-06
With the usb adapter plugged in please run:
```
lsusb
```
and post the output here, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated    [code] paste here [ /code] tags.

---

### Post by harry003 on 2015-05-09
Here is the output of lsusb:

```
aaron@asm-gigabyte:~$ lsusb
Bus 003 Device 002: ID 148f:3572 Ralink Technology, Corp. RT3572 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 005 Device 002: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
aaron@asm-gigabyte:~$ 


```

---

### Post by wildmanne39 on 2015-05-09
Your device looks like it is supported in 14.04 maybe the driver did not get installed because you did not have an internet connection when you installed ubuuntu, if it get it to load it usually requires  little work to get it to work properly.

Please do:
```
sudo modprobe rt2800usb
```
then post the output of:
```
modinfo rt2800usb
```
wrap it up in code tags.
Thanks

---

### Post by harry003 on 2015-05-09
This procedure seemed to make the USB connections get weird. Is that because I accidentally ran the second one as sudo?


```
   aaron@asm-gigabyte:~$ sudo modprobe rt2800usb 
[sudo] password for aaron: 
aaron@asm-gigabyte:~$ sudo modprobe rt2800usb 
aaron@asm-gigabyte:~$ sudo modinfo rt2800usb 
filename:      
/lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL 
firmware:       rt2870.bin 
description:    Ralink RT2800 USB Wireless LAN
driver. 
version:        2.3.0 
author:         http://rt2x00.serialmonkey.com 
srcversion:     AA4336C224E35E523F23134 
alias:         
usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0254d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0078d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p006Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0069d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2019pAB29d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v06F8pE036d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p0602d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p0600d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3401d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3400d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3399d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p17A7d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v20F4p724Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C21d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p0253d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p0241d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C23d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C22d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C20d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p17E8d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0586p3421d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p006Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p006Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0067d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp3573d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2019pED19d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0846p9019d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0846p9013d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0846p9012d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p016Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13B1p003Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04BBp094Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0021d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0020d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v7392p7733d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C1Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148FpF301d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp1103d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p17ADd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p17BCd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1B75p7733d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p0170d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0165d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0163d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0324d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0164d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1B75pA200d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v2001p3317d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p01A8d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*in* 
alias:         
usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*in* 
depends:        rt2x00lib,rt2800lib,rt2x00usb 
intree:         Y 
vermagic:       3.16.0-30-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key 
sig_key:       
7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE 
sig_hashalgo:   sha512 
parm:           nohwcrypt:Disable hardware
encryption. (bool) 
aaron@asm-gigabyte:~$ h 


```

---

### Post by wildmanne39 on 2015-05-09
No, I doubt it. Please post the out come of:
```
modinfo rt2800usb | grep 148f
```
Make sure wireless is enabled in netwok manager at the top right of the screen.

---

### Post by harry003 on 2015-05-09
> **Wild Man said:**
> No, I doubt it. Please post the out come of:
```
modinfo rt2800usb | grep 148f
```
Make sure wireless is enabled in netwok manager at the top right of the screen.

Wireless is enabled.

modinfo rt2800usb | grep 148f 

did not return anything, but did not give an error message, either

---

### Post by wildmanne39 on 2015-05-09
I think we are going to have to compile the driver, can you take the computer to a friends house with internet?

---

### Post by wildmanne39 on 2015-05-09
Please run the command like this:
```
modinfo rt2800usb | grep 148F
```
The f needed to capitalized.
Post the out put from the following commands as well:
```
lsusb
nm-tool
sudo iwlist scan
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wlan -e wpa | tail -n25
```
make sure the driver is still loaded that means if you rebooted you may have to load the driver again and the usb adapter needs to be plugged in before running the commands.
Thanks

---

### Post by harry003 on 2015-05-12
Rummaging through my old parts box, I found a Linksys PCI ethernet adapter from about 10 years ago and installed it.
When I connected the ethernet cable, it was recognized instantly and I was able to get on-line, although the connection seems very flaky and slow.

Here is the result you asked for earlier:

```
aaron@asm-gigabyte:~$ modinfo rt2800usb | grep 148F
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*in*
aaron@asm-gigabyte:~$ lsusb
Bus 003 Device 002: ID 148f:3572 Ralink Technology, Corp. RT3572 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
aaron@asm-gigabyte:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        C8:3A:35:C7:CC:DC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            tulip
  State:             connected
  Default:           yes
  HW Address:        00:0C:41:21:D2:D6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.132.97.116
    Prefix:          24 (255.255.255.0)
    Gateway:         10.132.97.99

    DNS:             10.132.97.99

  IPv6 Settings:
    Address:         2601:0:8700:6e0:5052:98fe:5789:bb3a
    Prefix:          64
    Gateway:         fe80::cad7:19ff:fe4f:3cce

    Address:         2601:0:8700:6e0:20c:41ff:fe21:d2d6
    Prefix:          64
    Gateway:         fe80::cad7:19ff:fe4f:3cce

    Address:         fe80::20c:41ff:fe21:d2d6
    Prefix:          64
    Gateway:         fe80::cad7:19ff:fe4f:3cce

    DNS:             2601:0:8700:6e0:cad7:19ff:fe4f:3cce


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        FC:AA:14:55:A0:4B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


aaron@asm-gigabyte:~$ sudo iwlist scan
[sudo] password for aaron: 
eth0      Interface doesn't support scanning.

wlan0     No scan results

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

aaron@asm-gigabyte:~$ sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa | tail -n25
May 12 13:00:08 asm-gigabyte kernel: [ 1261.423387] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.423765] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.424139] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.424511] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.424887] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.425261] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.425639] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.426012] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.426386] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.426759] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.427134] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.427509] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.427885] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.428259] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.428638] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.481865] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.569684] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1130 with error -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.607160] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1134 with error -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.644636] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1138 with error -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.682111] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.719589] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -32
May 12 13:00:08 asm-gigabyte kernel: [ 1261.889606] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1130 with error -32
May 12 13:00:08 asm-gigabyte kernel: [ 1262.041509] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -32
May 12 13:00:09 asm-gigabyte kernel: [ 1263.024271] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -32
May 12 13:00:11 asm-gigabyte kernel: [ 1264.316335] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0438 with error -32
aaron@asm-gigabyte:~$ 


```

Thanks for your continuing help.

My son and I are working on this off and on every few days in between schoolwork, etc.

---

### Post by wildmanne39 on 2015-05-12
The driver loaded is suppose to drive your device but there are errors, so we will try an updated driver.

Download the file below to your desktop:
Right click it and select Extract Here. Now open a terminal and do:
```
sudo apt-get install build-essential linux-headers-generic
cd ~/Desktop/backports-4.1-rc1-1
make defconfig-wifi
make
sudo make install
```
Watch for error, this may take a few minutes.
Reboot with usb ethernet unplugged, if it does not connect then plug ethernet in and run the wireless script and post the file create, that will tell us what is going on with your device and network.
[https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1-rc1/backports-4.1-rc1-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1-rc1/backports-4.1-rc1-1.tar.gz)

---

