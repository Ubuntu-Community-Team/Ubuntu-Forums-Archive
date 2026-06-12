---
title: "Need help with Edimax EW7811UN driver installation"
date: 2015-05-17
forum: Networking &amp; Wireless
---

### Post by godzillathecing92 on 2015-05-17
Hi.

I installed this Ubuntu(14.04)-based distro a couple of days ago, and after failing at getting my wifi to work I bought this adapter, Edimax EW7811UN.

I can connect now, but it's very slow (around 150kb/s on average). I'm assuming this is because I haven't installed the drivers, but seeing as I'm new to this whole terminal thing, I have no idea how I'm supposed to do that, so I was wondering if one of you guys could walk me through this.

I got the driver from here: [http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_n150/ew-7811un](http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_n150/ew-7811un)

Thanks in advance.

---

### Post by chili555 on 2015-05-17
Is your driver rtl8192cu?```
lsmod
```It is very doubtful that the antique you downloaded, circa 2013, will help. Remarkably, it almost never helps to install an older driver than you already have.

Let's also see:```
lsusb
```> after failing at getting my wifi to workDid you ask for help here or elsewhere?

---

### Post by godzillathecing92 on 2015-05-17
Thank you for the reply Chili.

Got this from ```
lsmod
```:
```

 Module                  Size  Used byctr                    13049  2 
ccm                    17773  2 
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
dm_crypt               23216  0 
wl                   6367833  0 
arc4                   12608  4 
rt2800pci              13630  0 
rtl8192cu              67741  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
intel_rapl             18783  0 
gpio_ich               13586  0 
rtl_usb                18448  1 rtl8192cu
uvcvideo               81073  0 
rt2x00pci              13287  1 rt2800pci
joydev                 17393  0 
rtlwifi                64255  2 rtl_usb,rtl8192cu
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
x86_pkg_temp_thermal    14205  0 
rtl8192c_common        53172  1 rtl8192cu
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
intel_powerclamp       18823  0 
mac80211              652718  6 rtl_usb,rtlwifi,rt2x00lib,rt2x00pci,rt2800lib,rtl8192cu
snd_hda_codec_hdmi     47548  1 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
coretemp               13441  0 
videobuf2_core         59104  1 uvcvideo
snd_hda_codec_realtek    77467  1 
v4l2_common            15681  1 videobuf2_core
kvm_intel             143590  0 
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
kvm                   452043  1 kvm_intel
snd_hda_intel          30469  10 
cfg80211              494362  4 wl,mac80211,rtlwifi,rt2x00lib
media                  21903  2 uvcvideo,videodev
snd_usb_audio         161729  0 
xpad                   22327  0 
snd_hda_controller     31056  1 snd_hda_intel
snd_usbmidi_lib        29828  1 snd_usb_audio
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
ff_memless             13573  1 xpad
snd_hwdep              17698  2 snd_usb_audio,snd_hda_codec
crct10dif_pclmul       14307  0 
snd_pcm               104112  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
eeprom_93cx6           13344  1 rt2800pci
crc32_pclmul           13133  0 
snd_seq_midi           13564  0 
crc_ccitt              12707  1 rt2800lib
ghash_clmulni_intel    13230  0 
snd_seq_midi_event     14899  1 snd_seq_midi
aesni_intel           152552  601 
snd_rawmidi            30876  2 snd_usbmidi_lib,snd_seq_midi
aes_x86_64             17131  1 aesni_intel
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
lrw                    13286  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd                    79468  33 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
ablk_helper            13597  1 aesni_intel
soundcore              15047  2 snd,snd_hda_codec
serio_raw              13483  0 
cryptd                 20359  301 ghash_clmulni_intel,aesni_intel,ablk_helper
mei_me                 19696  0 
shpchp                 37047  0 
mei                    87875  1 mei_me
lpc_ich                21093  0 
mac_hid                13227  0 
tpm_infineon           17131  0 
parport_pc             32741  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
nouveau              1206535  0 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  1 nouveau
i2c_algo_bit           13413  1 nouveau
r8169                  71694  0 
pata_acpi              13053  0 
ttm                    93588  1 nouveau
mii                    13934  1 r8169
drm_kms_helper         61574  1 nouveau
drm                   311018  3 ttm,drm_kms_helper,nouveau

```

I should probably mention I think it may be showing results both for my built-in adapter (Ralink RT 3060) and new Edimax EW7811UN.

And ```
lsusb
``` gave this:
```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 003 Device 002: ID 9886:0002  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 005: ID 0c45:6310 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 007: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

> **chili555 said:**
> Did you ask for help here or elsewhere?
I made a thread here yesterday, but the adapter's pretty old and was starting to give me trouble on my Windows as well so I figured I'd spare those few pounds and get a new one while I'm at it.

Thanks again, hope you can make sense out of this..

---

### Post by chili555 on 2015-05-17
> wl                   6367833  0 Interesting. Please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
```> the adapter's pretty old and was starting to give me trouble on my Windows as well
......
I think it may be showing results both for my built-in adapter (Ralink RT 3060)Let's just blacklist it:```
sudo -i
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if connectivity is improved.

If not, this is probably the next step: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

---

### Post by godzillathecing92 on 2015-05-17
> **chili555 said:**
> 
If not, this is probably the next step: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

I tried doing that, but running ```
 sudo dkms install 8192cu/1.9 
``` gives me this: ```
Error! Could not find module source directory.
Directory: /usr/src/8192cu-1.9 does not exist.
```

I think this might have to do with my distro being Elementary OS 0.3 Freya, and not Ubuntu. It's an Ubuntu derivative based on Ubuntu 14.04 though, so I don't know.. Please help :(

---

### Post by chili555 on 2015-05-17
I just built it myself and at this step:```
sudo dkms add ./rtl8192cu-fixes
```...I notice that the terminal returns:```
Creating symlink /var/lib/dkms/8192cu/1.10/source ->
                 /usr/src/8192cu-1.10

DKMS: add completed.
```Therefore, I updated the next command to:```
sudo dkms install 8192cu/[COLOR="#FF0000"]1.10[/COLOR]
```And then:```
sudo depmod -a
```It builds without complaint. Please try and then report.

---

### Post by godzillathecing92 on 2015-05-18
> **chili555 said:**
> I just built it myself and at this step:```
sudo dkms add ./rtl8192cu-fixes
```...I notice that the terminal returns:```
Creating symlink /var/lib/dkms/8192cu/1.10/source ->
                 /usr/src/8192cu-1.10

DKMS: add completed.
```Therefore, I updated the next command to:```
sudo dkms install 8192cu/[COLOR=#FF0000]1.10[/COLOR]
```And then:```
sudo depmod -a
```It builds without complaint. Please try and then report.

Alright.. I tried that. The sudo dkms install part went without errors, so I moved on to sudo depmod -a, which didn't return anything. No errors, no lines, nothing. I assumed that's a good thing and restarted my computer, and right before the login screen I got something along the lines of "rtl8192cu already exists". I ignored that and tested my internet again, and it's still as slow. 

In the original AskUbuntu reply you sent here ([http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)), after: ```
 sudo depmod -a 
``` came:
```

sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit

```

Should I do that? Just in case something goes wrong, what's the command to un-blacklist the driver? Thanks.

---

### Post by chili555 on 2015-05-18
> ```
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```
Should I do thatAbsolutely. It does no good to follow some but not all of the essential instructions.> Just in case something goes wrong, what's the command to un-blacklist the driver? Think positive! Let's cross that bridge when we get to it; which we won't!

---

### Post by godzillathecing92 on 2015-05-18
> **chili555 said:**
> Absolutely. It does no good to follow some but not all of the essential instructions.Think positive! Let's cross that bridge when we get to it; which we won't!

Okay, I blacklisted the driver and rebooted. It feels more stable (although that just might be a placebo effect in action), but speedtest.net still reports very slow speed.. :(

---

### Post by godzillathecing92 on 2015-05-18
Actually, update:

I removed the new driver and tried remaking it using the instructions here: [https://github.com/vincent-t/rt8192cu_dkms](https://github.com/vincent-t/rt8192cu_dkms)

At the third stage of the installation (sudo make install_dkms 8192cu)
I'm getting this:
```

make: *** No rule to make target `8192cu'.  Stop.

```

I may have missed it when I was installing it the way you suggested.

[EDIT] Another update: nevermind, I just misspelled it or something.. I am getting this when I'm trying to reinstall the driver the way you suggested though:

```

Good news! Module version v4.0.2_9000.20130911 for 8192cu.ko
exactly matches what is already found in kernel 3.16.0-38-generic.
DKMS will not replace this module.
You may override by specifying --force.


```

Probably because it's detecting the one I installed the first time but I don't know..

---

### Post by chili555 on 2015-05-18
Have you evidence that the files at *vincent-t* are in any way superior to what you installed and removed? I don't.  Moreover, I find his build instructions suspect. As an example, although his files include a Makefile, he doesn't follow the usual make, sudo make install, sudo depmod -a recipe. As I'd therefore expect, the build fails.

I would rather you start with the 'known' rather than the 'unknown' and then let's troubleshoot.

It is seldom a viable strategy to always look for a different, maybe older, maybe newer driver for every problem.

---

### Post by godzillathecing92 on 2015-05-18
> **chili555 said:**
> Have you evidence that the files at *vincent-t* are in any way superior to what you installed and removed? I don't.  Moreover, I find his build instructions suspect. As an example, although his files include a Makefile, he doesn't follow the usual make, sudo make install, sudo depmod -a recipe. As I'd therefore expect, the build fails.

I would rather you start with the 'known' rather than the 'unknown' and then let's troubleshoot.

It is seldom a viable strategy to always look for a different, maybe older, maybe newer driver for every problem.

Yeah, you're right. I reverted back to the driver you sent me ([http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)). Speed is still slow though.. didn't give any installation error so I'm assuming it installed correctly but just isn't working? It did show this however:


[COLOR=#000000]```

Good news! Module version v4.0.2_9000.20130911 for 8192cu.ko
exactly matches what is already found in kernel 3.16.0-38-generic.
DKMS will not replace this module.
You may override by specifying --force.

```
[/COLOR]

---

### Post by chili555 on 2015-05-18
To get the fixes version to take over for the slow and unstable in-kernel version, it will need to be forced. Please proceed and then reboot.

---

### Post by godzillathecing92 on 2015-05-19
> **chili555 said:**
> To get the fixes version to take over for the slow and unstable in-kernel version, it will need to be forced. Please proceed and then reboot.

How do I do that?

---

### Post by chili555 on 2015-05-19
I would try substituting in the linked sequence:```
sudo dkms install --force 8192cu/1.10

```As always, post back any warnings, errors, etc.

---

### Post by godzillathecing92 on 2015-05-19
> **chili555 said:**
> I would try substituting in the linked sequence:```
sudo dkms install --force 8192cu/1.10

```As always, post back any warnings, errors, etc.

Got this:

```

Module 8192cu/1.10 already installed on kernel 3.16.0-38-generic/x86_64

```

---

### Post by chili555 on 2015-05-19
Let's next address the instability. Are there any clues in the logs as to its cause?```
cat /var/log/syslog | grep -e rtl -e wlan | tail -n20
```Have you checked the usual suspects?

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by godzillathecing92 on 2015-05-19
> **chili555 said:**
> Let's next address the instability. Are there any clues in the logs as to its cause?```
cat /var/log/syslog | grep -e rtl -e wlan | tail -n20
```Have you checked the usual suspects?

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Alright, ```
cat /var/log/syslog | grep -e rtl -e wlan | tail -n20
``` returned:
```

May 19 19:07:13 Shepard-P67A-D3-B3 avahi-daemon[827]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::76da:38ff:fe26:abf2.
May 19 19:07:13 Shepard-P67A-D3-B3 avahi-daemon[827]: Registering new address record for fe80::76da:38ff:fe26:abf2 on wlan1.*.
May 19 19:07:13 Shepard-P67A-D3-B3 avahi-daemon[827]: Withdrawing address record for fe80::76da:38ff:fe26:abf2 on wlan1.
May 19 19:07:13 Shepard-P67A-D3-B3 avahi-daemon[827]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::76da:38ff:fe26:abf2.
May 19 19:07:13 Shepard-P67A-D3-B3 avahi-daemon[827]: Interface wlan1.IPv6 no longer relevant for mDNS.
May 19 19:07:13 Shepard-P67A-D3-B3 NetworkManager[949]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 19 19:07:13 Shepard-P67A-D3-B3 dhclient: Listening on LPF/wlan1/74:da:38:26:ab:f2
May 19 19:07:13 Shepard-P67A-D3-B3 dhclient: Sending on   LPF/wlan1/74:da:38:26:ab:f2
May 19 19:07:13 Shepard-P67A-D3-B3 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3 (xid=0x40f4fa06)
May 19 19:07:14 Shepard-P67A-D3-B3 avahi-daemon[827]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::76da:38ff:fe26:abf2.
May 19 19:07:14 Shepard-P67A-D3-B3 avahi-daemon[827]: New relevant interface wlan1.IPv6 for mDNS.
May 19 19:07:14 Shepard-P67A-D3-B3 avahi-daemon[827]: Registering new address record for fe80::76da:38ff:fe26:abf2 on wlan1.*.
May 19 19:07:16 Shepard-P67A-D3-B3 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7 (xid=0x40f4fa06)
May 19 19:07:23 Shepard-P67A-D3-B3 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9 (xid=0x40f4fa06)
May 19 19:07:32 Shepard-P67A-D3-B3 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10 (xid=0x40f4fa06)
May 19 19:07:33 Shepard-P67A-D3-B3 NetworkManager[949]: <info> (wlan1): IP6 addrconf timed out or failed.
May 19 19:07:33 Shepard-P67A-D3-B3 NetworkManager[949]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 19 19:07:33 Shepard-P67A-D3-B3 NetworkManager[949]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 19 19:07:33 Shepard-P67A-D3-B3 NetworkManager[949]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 19 19:07:42 Shepard-P67A-D3-B3 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12 (xid=0x40f4fa06)
shepard@Shepard-P67A-D3-B3:~$ 

```

I did all things with the router settings and stability seems to be fine now, thanks! Speed, however, remains sluggish..

---

### Post by godzillathecing92 on 2015-05-21
Nevermind, changing the adapter's location seemed to do the trick (along with the drivers and the rest of the fixes, of course)! Thanks a ton for the help Chili!! :)

---

