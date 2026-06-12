---
title: "No WLAN on Lenovo Yoga 2 Pro (Would love some looks on this)"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by Henrik_Edholm on 2014-09-09
Hello good folks!

So I reformated my Ubuntu partition today after a major ongoing issue I've had for a couple of weeks.
Anyhow, the issue I'm having is that I cant get my Wireless to work.

I know it's a common issue, and I've fixed it before. Just cant recall exactly how I did.

The first thing that struck me was that I couldn't enable Wi-Fi while installing, and that issue stil remains.
The second thing was that when I ran "rfkill list all" I got:
```

0: ideapad_wlan: Wireless LAN
   Soft Blocked: no
   Hard Blocked: yes
1: ideapad_bluetooth: Bluetooth
   Soft Blocked: no
   Hard blocked: yes
2: phy0: Wireless LAN
   Soft Blocked: no
   Hard blocked: no
3: hci0: Bluetooth
   Soft Blocked: no
   Hard blocked: no
```

When I run "iwconfig" the return is:
```

lo              no wireless extensions.

wlan0         IEEE 802.11abgn    ESSID:off/any
                 Mode:Managed Acces Point: Not-Associated      Tx-Power=0 dBm
                 Retry long limit:7     RTS thr:off      Fragment  thr:off
                 Power Management:off
```

When I run "lshw" I get the following:
```

*-network DISABLED
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes drive=iwlwifi driverversion=3.11.0-12-generic firmware=22.0.7.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:60 memory:b0400000-b0401fff
```

Upon running "lspci" I can only find one row about networks, which is the following:
Network controller: Intel Corporation Wireless 7260 (I expected that I would get two rows about it)
The other rows is info about: Audio device, 2x USB, Host bridge, 2x Signal processing controller, PCI bridge, ISA bridge, SATA controllers, SMBus
Unsure if this info is of any use.

When running "lspci -nnk | grep -iA2 net" I get:
```
Network controller [0280]: Intel Corporation Wirelss 7260 [8086:08b2] (rev 6b)
Subsystem: Intel Corporation Wireless-N 7260 [8086:c262]
Kernel driver in use: iwlwifi
```

Running "lsmod" gives me:
```

iwlmvm      161349 0
iwlwifi        165398 1 iwlmvm
```

"ifconfig" gives me the following:
```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr:  : :1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:65536 Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets: 128 errors:0 dropped:0 overruns: 0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10112 (10.1 KB) TX bytes:10112 (10.1 KB)
```

I don't have any ethernet converter for my laptop, so I havn't tried anything of that.
However! What I can recall is that I'm pretty sure I had to blacklist one item last time I ran Ubuntu on this machine.

Is there any other information you want or more code snippets just say so.
All help is welcome!

---

### Post by chili555 on 2014-09-09
Please try:```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```Any improvement? If so, we'll blacklist it!

---

### Post by Henrik_Edholm on 2014-09-09
That did the trick!

Thanks so much :)

---

### Post by chili555 on 2014-09-09
> **Henrik_Edholm said:**
> That did the trick!

Thanks so much :)Before you go away and nominate me for mayor, let's blacklist the module:```
sudo -i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```Then use thread tools at the top to mark Solved. The searchers with a similar problem will appreciate it.

---

### Post by Henrik_Edholm on 2014-09-10
Rebooted the system after various updates and the issue is somewhat back on.
When I open /etc/modprobe.d/blacklist.conf with gedit I can see that ideapad-laptop is blacklisted, however it doesn't seem to do anything for me.
I have re-written the line 3 times in hope that I've just misspelled, however it doesn't seem to be that easy.

Any ideas what it can be?

---

### Post by chili555 on 2014-09-10
> **Henrik_Edholm said:**
> Rebooted the system after various updates and the issue is somewhat back on.
When I open /etc/modprobe.d/blacklist.conf with gedit I can see that ideapad-laptop is blacklisted, however it doesn't seem to do anything for me.
I have re-written the line 3 times in hope that I've just misspelled, however it doesn't seem to be that easy.

Any ideas what it can be?When you reboot with the module blacklisted 3 times (!!), is it nevertheless loaded?```
lsmod
```Does this fix it?```
sudo rfkill unblock all
```If it does, we'll get that to run on boot. If not, we'll dig a bit deeper.

---

### Post by Henrik_Edholm on 2014-09-10
"sudo rfkill unblock all" does nothing on it's own. Need to do it in combo with "sudo modprobe -r ideapad-laptop"

From lsmod:
```
Module                                         Size  Used by
hid_sensor_hub                      19096  0 
hid_multitouch                         17407  0 
uvcvideo                                   80885  0 
videobuf2_vmalloc                  13216  1 uvcvideo
videobuf2_memops                13362  1 videobuf2_vmalloc
videobuf2_core                        40499  1 uvcvideo
videodev                                 133509  2 uvcvideo,videobuf2_core
hid_logitech_dj                         18581  0 
usbhid                                        53014  0 
hid                                            101762  5 hid_multitouch,hid_sensor_hub,usbhid,hid_logitech_dj
btusb                                          28267  0 
parport_pc                                 32701  0 
ppdev                                         17671  0 
bnep                                           19704  2 
rfcomm                                       69130  12 
x86_pkg_temp_thermal           14162  0 
bluetooth                                  372330  22 bnep,btusb,rfcomm
coretemp                                    13435  0 
kvm                                           431746  0 
crct10dif_pclmul                        14289  0 
crc32_pclmul                             13113  0 
ghash_clmulni_intel                  13216  0 
aesni_intel                                  55624  2 
aes_x86_64                               17131  1 aesni_intel
lrw                                                13286  1 aesni_intel
gf128mul                                     14951  1 lrw
glue_helper                                13990  1 aesni_intel
ablk_helper                                13597  1 aesni_intel
cryptd                                          20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                                         17377  0 
snd_hda_codec_hdmi             41154  1 
snd_hda_codec_realtek          56475  1 
arc4                                             12608  2 
snd_hda_intel                            52267  5 
snd_hda_codec                       188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep                                13602  1 snd_hda_codec
nls_iso8859_1                           12713  1 
snd_pcm                                  102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc                         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi                             13324  0 
snd_seq_midi_event                 14899  1 snd_seq_midi
iwlmvm                                      161300  0 
microcode                                   23656  0 
mac80211                                601410  1 iwlmvm
snd_rawmidi                               30095  1 snd_seq_midi
psmouse                                  102329  0 
snd_seq                                     61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw                                   13413  0 
iwlwifi                                        165636  1 iwlmvm
snd_seq_device                       14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer                                   29433  2 snd_pcm,snd_seq
lpc_ich                                        21080  0 
cfg80211                                 480503  3 iwlwifi,mac80211,iwlmvm
snd                                             69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                                      18421  0 
mei                                              77784  1 mei_me
soundcore                                  12680  1 snd
i915                                            661468  5 
mac_hid                                      13205  0 
video                                            19318  1 i915
drm_kms_helper                        52710  1 i915
drm                                             297056  4 i915,drm_kms_helper
intel_smartconnect                     12690  0 
i2c_algo_bit                                 13413  1 i915
lp                                                   17759  0 
parport                                          42299  3 lp,ppdev,parport_pc
ahci                                               25819  3 
libahci                                            32009  1 ahci

```
Sorry about the crappy formating, not sure how to do it here on the forums.

---

### Post by slickymaster on 2014-09-10
Hi Henrik_Edholm, I've edit your last post, adding code tags to it. take a look at [this post]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") on how you do it.

I'll leave you then in the hands of chili555, one of our most powerful sorcerers.

---

### Post by Henrik_Edholm on 2014-09-10
Thanks for that slickymaster!

---

### Post by chili555 on 2014-09-10
I wonder if the module needs to be loaded at boot and then removed; sounds crazy, I know. Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove all three or four lines that blacklist ideapad-laptop. Proofread carefully, save and close the text editor. Now do:> gksudo gedit /etc/rc.localRight above exit 0 add:```
modprobe -r ideapad-laptop
sleep 2s
rfkill unblock all
```Proofread carefully, save and close the text editor. Reboot and run and post:```
rfkill list all
lsmod | grep idea
```Thanks.

---

### Post by Henrik_Edholm on 2014-09-10
Works like a charm 3 reboots in a row!
Upon running "rfkill list all" i only get:
```
2: phy0: Wireless LAN
   Soft Blocked: no
   Hard blocked: no
3: hci0: Bluetooth
   Soft Blocked: no
   Hard blocked: no
```

Not sure what lsmod | grep idea are supposed to do, not getting any printouts in the terminal though.

Thanks for all the support chili555, I really appreciate it.

---

### Post by slickymaster on 2014-09-10
@Henrik_Edholm:
Told you that chili555 is one of the forum most powerful sorcerers.

Now please mark the thread as SOLVED, so other people searching the forums know that it provides a working solution for this problem. Just follow the link in my signature if you don't know how to do it.

---

### Post by chili555 on 2014-09-10
Glad it's working! You will have helped many searchers, I'm sure.

---

