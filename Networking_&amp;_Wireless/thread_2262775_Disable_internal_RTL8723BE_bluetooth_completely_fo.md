---
title: "Disable internal RTL8723BE bluetooth completely for USB adapter"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by afriendcalledben on 2015-01-27
Hi, 

I have a Lenevo Flex 2 15 Pro running Ubuntu 14.04. It has an internal Realtek RTL8723BE Wifi / Bluetooth module that doesn't work too great with Ubuntu it seems.

I want the bluetooth to work well and at a long disance so I bought a IOGEAR GBU321 Long Range Bluetooth USB adaptor. However, I can't seem to be able to disable the internal module so that the USB adapter can become the default. When I try to connect devices, they connect automatically to the Realtek (hci0) and not the IOGear (hci1) and then lose the connection or don't function correctly.

Here's what I've tried:

[LIST]
[*]Gone into the BIOS to attempt to disable the module. BIOS is too basic and option is not in Power Management.
[*]Used "sudo hciconfig hci0 down" to attempt to diable the module within Ubuntu. This disables the USB adaptor as well.
[*]Attempted to revive only the USB adaptor with "sudo rfkill unblock all" and then "sudo hciconfig hci1 up"
[/LIST]

That last method worked once for about 20 seconds because the internal took a moment to come back up. The devices worked perfectly but as soon as it came back it booted the devices off hci1 and took over :(

Sorry for the long explanation. Any help or advice on this matter would really genuinely be appreciated.

N.B. I'm trying to pair PS Move controllers in order to play JS Joust from Sportsfriends

---

### Post by jeremy31 on 2015-01-27
Can you post the results from ```
lsmod | grep bluetooth
```

---

### Post by afriendcalledben on 2015-01-27
Ah, this is embarrassing. I've just realised I didn't bring the adaptor in with me. Pretty stupid of me.
But thank you for your quick reply. I'll post the results as soon as I can go grab it.

---

### Post by jeremy31 on 2015-01-27
> **afriendcalledben said:**
> Ah, this is embarrassing. I've just realised I didn't bring the adaptor in with me. Pretty stupid of me.
But thank you for your quick reply. I'll post the results as soon as I can go grab it.

I just need to see what modules load for the realtek

---

### Post by afriendcalledben on 2015-01-27
Ah I see, here you go:

```
bluetooth             391136  22 bnep,btusb,rfcomm

```

Thanks.

---

### Post by jeremy31 on 2015-01-27
> **afriendcalledben said:**
> Ah I see, here you go:

```
bluetooth             391136  22 bnep,btusb,rfcomm

```

Thanks.

Post the full list ```
lsmod
```
Usually the bluetooth doesn't work at all with the 8723

---

### Post by afriendcalledben on 2015-01-27
Yeah, that seems to be the case. I'd wrench it out of my laptop if I could. Here's the full response:

```
Module                  Size  Used by
ctr                    13049  3 
ccm                    17773  3 
bnep                   19624  2 
rfcomm                 69160  12 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
uvcvideo               80885  0 
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   455835  0 
arc4                   12608  2 
videobuf2_vmalloc      13216  1 uvcvideo
snd_hwdep              13602  1 snd_hda_codec
rtl8723be             139164  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nouveau              1097199  1 
videodev              134688  2 uvcvideo,videobuf2_core
crct10dif_pclmul       14289  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
btcoexist             183378  1 rtl8723be
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  6 
snd_seq_midi           13324  0 
aes_x86_64             17131  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
lrw                    13286  1 aesni_intel
snd_rawmidi            30144  1 snd_seq_midi
gf128mul               14951  1 lrw
rtl_pci                39740  1 rtl8723be
glue_helper            13990  1 aesni_intel
rtlwifi               121320  3 btcoexist,rtl_pci,rtl8723be
mac80211              630669  3 rtl_pci,rtlwifi,rtl8723be
ablk_helper            13597  1 aesni_intel
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
i915                  784207  5 
ttm                    85150  1 nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
drm_kms_helper         55071  2 i915,nouveau
btusb                  32412  0 
parport_pc             32701  0 
drm                   303102  7 ttm,i915,drm_kms_helper,nouveau
bluetooth             391136  22 bnep,btusb,rfcomm
joydev                 17381  0 
serio_raw              13462  0 
mei_me                 18627  0 
video                  19476  2 i915,nouveau
ppdev                  17671  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ideapad_laptop         18216  0 
wmi                    19177  2 mxm_wmi,nouveau
mei                    82276  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
lpc_ich                21080  0 
soundcore              12680  1 snd
lp                     17759  0 
sparse_keymap          13948  1 ideapad_laptop
parport                42348  3 lp,ppdev,parport_pc
hid_multitouch         17407  0 
mac_hid                13205  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  3 hid_multitouch,hid_generic,usbhid
psmouse               106714  0 
ahci                   25819  3 
libahci                32716  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169

```

---

### Post by afriendcalledben on 2015-01-27
Sorry to be clear, it appears to work in that it appears as a device and you can block it, up and down it etc.

It just can't actually make and hold a connection.

---

### Post by jeremy31 on 2015-01-27
Post the results from ```
lsusb
```
there might be a couple different ways to do this
have you tried ```
rfkill list all
``` and used the number for hci0 to block it with ```
rfkill block 
``` followed by the number?
and ```
uname -a
```

---

### Post by afriendcalledben on 2015-01-27
Hi Jeremy,

lsusb returns:

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 03eb:8a1b Atmel Corp. 
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 5986:0652 Acer, Inc 
Bus 001 Device 002: ID 045e:07b1 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

uname -a returns:
```
Linux afcb-ubuntu 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Just so you know, I haven't got hold of the adaptor yet, in case it's needed at this point.

I have tried the rfkill block method. Unfortunately, where 0 is the itnernal module and 1 is the external adapter, if I do:

```
rfkill block 0
```

... it soft blocks them both and if I then do:

```
rfkill unblock 1
```

... they both come back up. They seem linked somehow which makes no sense to me.

---

### Post by jeremy31 on 2015-01-27
It might be another 8 hours before I am able to do much more than try this ```
echo "install btusb /sbin/modprobe --ignore-install btusb && echo '0bda b728' > /sys/bus/usb/drivers/btusb/remove_id && hciconfig hci0 down" | sudo tee /etc/modprobe.d/bcmbtusb.conf
```
and see if rfkill shows bluetooth after a reboot with just the realtek.  I hope it works but have doubts as it is too simple.  I have a GBU321, GBU421, and a GBU521 and they work nicely, although I had to change the btusb module to get the 521 functioning

---

### Post by afriendcalledben on 2015-01-27
Hi Jeremy, 

So I did that and restarted and now rfkill list all doesn't show the hci0 bluetooth which is great. The only problem now is that it also doesn't recognise the usb adaptor either. 

I ran lsusb and got:
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 03eb:8a1b Atmel Corp. 
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 013: ID 0a5c:2148 Broadcom Corp. BCM92046DG-CL1ROM Bluetooth 2.1 Adapter
Bus 001 Device 012: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 001 Device 011: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 010: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 5986:0652 Acer, Inc 
Bus 001 Device 002: ID 045e:07b1 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

hciconfig -a returns nothing.

Thanks for your help so far.

---

### Post by jeremy31 on 2015-01-27
Ok, ```
sudo rm /etc/modprobe.d/bcmbtusb.conf
``````
sudo modprobe -r btusb
``````
sudo modprobe btusb
``` and it should be back to the way it was
Actually try this```
echo "install btusb /sbin/modprobe --ignore-install btusb && echo '0bda b728' > /sys/bus/usb/drivers/btusb/remove_id" | sudo tee /etc/modprobe.d/bcmbtusb.conf
``````
sudo modprobe -r btusb
``````
sudo modprobe btusb
```

---

### Post by jeremy31 on 2015-01-27
If that didn't work ```
sudo rm /etc/modprobe.d/bcmbtusb.conf
```
Copy this file to /home [https://www.dropbox.com/s/0gpuq5z7j2oabat/benbtusb.ko?dl=0](https://www.dropbox.com/s/0gpuq5z7j2oabat/benbtusb.ko?dl=0)
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r btusb && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp benbtusb.ko  /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Then ```
sudo modprobe -v btusb
``` and if you find after reboot that btusb isn't loaded ```
lsmod | grep btusb
```has no results then ```
echo btusb | sudo tee -a /etc/modules
```

Edit: This should work as I was able to disable my built in Atheros bluetooth with a similar edit to the btusb code and my USB external bluetooth device works

I added this to btusb.c line 135 from the linux 3.13 source
[/FONT][/COLOR]```
/*Faulty Realtek Bluetooth ignore*/  
  { USB_DEVICE(0x0bda, 0xb728), .driver_info = BTUSB_IGNORE },
```

---

### Post by afriendcalledben on 2015-01-29
Hi Jeremy,

Sorry, I was away from my laptop yesterday but I was just able to try all your suggestions. The very last one solved it! I'm so incredible grateful all for your help and for taking time to craft a solution. Got all 7 of my controllers paired today for Johann Sebastian Joust, a game I've been trying to get working on my laptop for the best part of two years.

Again thank you so much. 

All the best, 

Ben

---

### Post by jeremy31 on 2015-01-29
I might have to write up a tutorial on what I did because it will have to redone everytime your kernel updates

---

### Post by r0bb3d on 2015-03-22
Hi Jeremy,

Read this thread with great interest today. Noticed you ended op solving the problem for OP by writing him a custom kernel module. I was wondering if you would describe the steps to do that so we can all learn from it. I'm assuming your fix is applicable to anybody with a similar problem. The first solutions you suggested in this thread didn't work for me by the way. I really appreciate any help with this problem, because I'm really screwed here!

I have the same problem as OP:

I have another bluetooth card and another laptop (Dell Inspiron 15R SE) as OP, but the exact same problem. Internal BT card can't be disabled in BIOS and it's actually a little WiFi and BT combo card by Intel. The internal BT is ****, it lags especially when playing stuff in Google Chrome like Youtube, weirdly enough not when playing movies in VLC. I don't know what the problem is with this card, but I wan't to troubleshoot by trying an external BT USB dongle, which seems impossible.

I can't get the external USB BT dongle to work because the primary card is always picked. No rfkill or other tricks seem to work as both BT adapters get disabled that way. At least the CLI "bluez-test-device" and Ubuntu applet won't work at all unless they can use hci0 (the built in BT adapter). So my only solution seems to be disabling this device from boot time somehow. At least that's what I'd like to try.

Relevant info:

# lsmod|grep blue
bluetooth             391136  26 bnep,btusb,rfcomm

# lsusb
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2015-03-22
> **r0bb3d said:**
> Hi Jeremy,

Read this thread with great interest today. Noticed you ended op solving the problem for OP by writing him a custom kernel module. I was wondering if you would describe the steps to do that so we can all learn from it. I'm assuming your fix is applicable to anybody with a similar problem. The first solutions you suggested in this thread didn't work for me by the way. I really appreciate any help with this problem, because I'm really screwed here!

I have the same problem as OP:

I have another bluetooth card and another laptop (Dell Inspiron 15R SE) as OP, but the exact same problem. Internal BT card can't be disabled in BIOS and it's actually a little WiFi and BT combo card by Intel. The internal BT is ****, it lags especially when playing stuff in Google Chrome like Youtube, weirdly enough not when playing movies in VLC. I don't know what the problem is with this card, but I wan't to troubleshoot by trying an external BT USB dongle, which seems impossible.

I can't get the external USB BT dongle to work because the primary card is always picked. No rfkill or other tricks seem to work as both BT adapters get disabled that way. At least the CLI "bluez-test-device" and Ubuntu applet won't work at all unless they can use hci0 (the built in BT adapter). So my only solution seems to be disabling this device from boot time somehow. At least that's what I'd like to try.

Relevant info:

# lsmod|grep blue
bluetooth             391136  26 bnep,btusb,rfcomm

# lsusb
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Is the Cambridge the bluetooth that is on the wifi card, or is there something else?

---

### Post by r0bb3d on 2015-03-24
Hi Jeremy,

Sorry didn't know you replied already, just enabled email notification for this thread.

My internal Wifi/BT card is the Intel Centrino N 2230 ([http://www.intel.com/content/www/us/en/wireless-products/centrino-wireless-n-2230.html](http://www.intel.com/content/www/us/en/wireless-products/centrino-wireless-n-2230.html)). I'm running Ubuntu 14.04 amd64.

Yes I'm pretty sure this is the driver "Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)". I think the Cambridge Silicon Radio is something like a generic driver for BT devices. It can't be any other bluetooth device as they are not connected.

Any help with this is much appreciated. The internal BT really is a mess, it's crapping out on everything including simple MP3 playback. I would remove the module (already had the laptop open on sunday) but that would remove my WiFI as well. FML :)

Just to be clear, looking mostly for a walkthrough on building this kernel module with the custom ID blacklist (have very little experience with building/compiling, I use apt for everything), so I can apply it in the future as well. And probably others reading this will benefit as well.

Thanks a lot man!
Robin

---

### Post by jeremy31 on 2015-03-24
> **r0bb3d said:**
> Hi Jeremy,

Sorry didn't know you replied already, just enabled email notification for this thread.

My internal Wifi/BT card is the Intel Centrino N 2230 ([http://www.intel.com/content/www/us/en/wireless-products/centrino-wireless-n-2230.html](http://www.intel.com/content/www/us/en/wireless-products/centrino-wireless-n-2230.html)). I'm running Ubuntu 14.04 amd64.

Yes I'm pretty sure this is the driver "Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)". I think the Cambridge Silicon Radio is something like a generic driver for BT devices. It can't be any other bluetooth device as they are not connected.

Any help with this is much appreciated. The internal BT really is a mess, it's crapping out on everything including simple MP3 playback. I would remove the module (already had the laptop open on sunday) but that would remove my WiFI as well. FML :)

Just to be clear, looking mostly for a walkthrough on building this kernel module with the custom ID blacklist (have very little experience with building/compiling, I use apt for everything), so I can apply it in the future as well. And probably others reading this will benefit as well.

Thanks a lot man!
Robin

Can you post ```
hciconfig -a
``` as the Cambridge Silicon Radio is a bluetooth device and you might want to look at ```
modinfo -p btusb
``` as some kernels had a parameter option to ignore that specific device as most of them are junk, it is option "ignore_sniffer"

So you could try ```
echo "options btusb ignore_sniffer=1" | sudo tee /etc/modprobe.d/btusb.conf
``````
sudo modprobe -r btusb
``````
sudo modprobe btusb
```and see if there are any bluetooth devices with ```
hcitool dev
```

---

### Post by r0bb3d on 2015-03-24
OK, first some requested output after I inserted the external USB dongle as well (00:02:5B:00:A5:A5 is internal):

```

# hciconfig -a
hci1:	Type: BR/EDR  Bus: USB
	BD Address: 00:02:5B:00:A5:A5  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:1198 acl:7 sco:0 events:62 errors:0
	TX bytes:1175 acl:10 sco:0 commands:41 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0xdb 0xff 0x5b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'my.hostname.com-1'
	Class: 0x6c0100
	Service Classes: Rendering, Capturing, Audio, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 4.0 (0x6)  Revision: 0x1ebd
	LMP Version: 4.0 (0x6)  Subversion: 0x1ebd
	Manufacturer: Cambridge Silicon Radio (10)

hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:15:83:0C:BF:EB  ACL MTU: 339:8  SCO MTU: 128:2
	UP RUNNING PSCAN 
	RX bytes:496 acl:0 sco:0 events:23 errors:0
	TX bytes:346 acl:0 sco:0 commands:23 errors:0
	Features: 0xff 0x3e 0x85 0x30 0x18 0x18 0x00 0x00
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'my.hostname.com-0'
	Class: 0x000104
	Service Classes: Unspecified
	Device Class: Computer, Desktop workstation
	HCI Version: 2.0 (0x3)  Revision: 0xc5c
	LMP Version: 2.0 (0x3)  Subversion: 0xc5c
	Manufacturer: Cambridge Silicon Radio (10)

```

Also

```

# modinfo -p btusb
ignore_dga:Ignore devices with id 08fd:0001 (bool)
ignore_csr:Ignore devices with id 0a12:0001 (bool)
ignore_sniffer:Ignore devices with id 0a12:0002 (bool)
disable_scofix:Disable fixup of wrong SCO buffer size (bool)
force_scofix:Force fixup of wrong SCO buffers size (bool)
reset:Send HCI reset command on initialization (bool)

```

And

```

# lsusb
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Notice the two bluetooth dongles with different bus address but same ID. This is interesting, as the external dongle is just a cheap nameless thing I got off Amazon but works great.

What seems to be happening when I add ignore_sniffer to the ignore list as you suggested is nothing, both bluetooth devices show up in hciconfig. That makes sense as it says "ignore_sniffer:Ignore devices with id 0a12:0002" which doesn't match the ID. However when I add "ignore_csr:Ignore devices with id 0a12:0001" to the ignore list, both devices disappear. Seems like they use the same driver, only on another internal bus?

```

# cat /etc/modprobe.d/btusb.conf 
options btusb ignore_csr=1
#options btusb ignore_sniffer=1

```

Seems like this problem just became more difficult to solve....

---

### Post by jeremy31 on 2015-03-25
You might have to use rfkill to workaround this issue ```
rfkill list
``` and look for the number next to hci0 then use ```
rfkill block X
``` and replace X with the number or ```
sudo hciconfig hci0 down
``` might work also

---

### Post by r0bb3d on 2015-03-25
I tried working with rfkill already, just tried hciconfig. The problem is that I can put hci0 (the internal adapter) offline, but then bluetooth will stop working altogether. The bluetooth indicator in Unity will go in offline mode (grayed out). If I enable it again there, hci0 comes back up. If I try working in the commandline with bluez-test-adapter etc it will start crashing as soon as hci0 goes down with messages like "can't connect to bus" or something.

By the way I also tried making the external bluetooth adapter hci0, which I succeeded in. I just boot up the laptop with the external USB dongle connected and it will become hci0. Still when trying to connect to any device the internal adapter is used. Also trying the above methods of disabling the internal adapter (now hci1) results in the same outcome. I think the real problem here is that the kernel pretty much sees these devices as the same and always chooses the route to the internal card.

I'm happy to try more solutions if you have any, but I also hedged my bet by ordering a Dell DW1703 Wireless/BT card from eBay. Googling the Intel Centrino N 2230 I read an 18 page long thread about how that card sucks and drops WiFi connections (not a problem I have), but people where having good results replacing it with DW1703 cards in their Dell laptops. Cost is about $10-$15 on eBay. Replacing it requires some nerve as you need to open up your laptop with about 24 screws and lift a lot of stuff out, but there are good youtube tutorials on it for a lot of laptops. Even if this card ends up sucking too, I think it might use a different chipset (Atheros) and maybe different drivers which might solve my problem as well, but what do I know?!

---

### Post by jeremy31 on 2015-03-25
> **r0bb3d said:**
> I tried working with rfkill already, just tried hciconfig. The problem is that I can put hci0 (the internal adapter) offline, but then bluetooth will stop working altogether. The bluetooth indicator in Unity will go in offline mode (grayed out). If I enable it again there, hci0 comes back up. If I try working in the commandline with bluez-test-adapter etc it will start crashing as soon as hci0 goes down with messages like "can't connect to bus" or something.

By the way I also tried making the external bluetooth adapter hci0, which I succeeded in. I just boot up the laptop with the external USB dongle connected and it will become hci0. Still when trying to connect to any device the internal adapter is used. Also trying the above methods of disabling the internal adapter (now hci1) results in the same outcome. I think the real problem here is that the kernel pretty much sees these devices as the same and always chooses the route to the internal card.

I'm happy to try more solutions if you have any, but I also hedged my bet by ordering a Dell DW1703 Wireless/BT card from eBay. Googling the Intel Centrino N 2230 I read an 18 page long thread about how that card sucks and drops WiFi connections (not a problem I have), but people where having good results replacing it with DW1703 cards in their Dell laptops. Cost is about $10-$15 on eBay. Replacing it requires some nerve as you need to open up your laptop with about 24 screws and lift a lot of stuff out, but there are good youtube tutorials on it for a lot of laptops. Even if this card ends up sucking too, I think it might use a different chipset (Atheros) and maybe different drivers which might solve my problem as well, but what do I know?!

I put an Intel 7260 in my Dell N411Z and it sounds like what you have to go through to replace a wifi card.  It looks like the DW1703 is an Atheros AR5B225 card, I have one in my Lenovo.   The wifi is about average for Linux, they don't like TKIP and it works better with ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

The bluetooth issues are fixed in 3.16.0-32 as it needed a delay so it didn't try to load firmware to soon and fail.  And if the bluetooth does give you issues, using your USB dongle by itself should be as easy as blacklisting ath3k

---

### Post by r0bb3d on 2015-03-26
Thanks for the help! I will update this thread in a few weeks as soon as I find time to place the new card and test it out.

---

### Post by r0bb3d on 2015-03-30
Just wanted to update this thread: problem seems to be solved, although in a very hacky way. Still waiting for the internal mPCI bluetooth card from eBay, but I bought another bluetooth USB dongle at the store as well.

What I did was put both USB bluetooth dongles in different USB ports (one via a HUB) in the laptop and booted it up. The drivers for all 3 adapters still seem to be the same and all of the above still holds true, but the problem was immediately solved. From my understanding because one of the dongles (not even the new one) became hci0 and therefore the default device. I linked a bluetooth speaker via the Unity bluetooth indicator and confirmed which adapter I was dealing with by checking /var/lib/bluetooth. The hardware address of the adapter that is active will list the newly paired bluetooth speaker. Playback problems solved.

It could be that I missed this solution before, but I'm not sure. When I remove one dongle this solution still works, but then it tends to default back to the internal adapter at random (decided at boot time) and old problems reoccur. Switching USB ports does make a difference I think as for deciding boot order, so playing around with that could help. But booting with 2 external dongles seems a safe bet and internal adapter seems to be skipped every time. To confirm which dongle is active check which one is hci0 and only pair devices with the external dongles so you can't make a mistake. I know it's kind of a crap solution, but I don't really care. It works.

By the way once the system is booted up and it works, you can remove the second bluetooth dongle that is not active. When you don't halt the system every night, but suspend, I think this will go a long way. 

What I also noticed by the way is that when playing youtube with the crappy bluetooth adapter, entire playback tends to get choppy because the sounds it choppy. So the internal adapter basically lags my entire system.

I might still place the new mPCI card, but that's low priority at the moment.

---

