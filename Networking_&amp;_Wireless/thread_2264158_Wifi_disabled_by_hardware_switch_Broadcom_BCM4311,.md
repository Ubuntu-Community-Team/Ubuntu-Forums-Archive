---
title: "Wifi disabled by hardware switch Broadcom BCM4311, hard blocked = yes, using b43"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by fraz3 on 2015-02-05
Hi Chili555,

apologies. Here's a thread

I've been reading quite a few thready this evening and I strongly believe you might be able to assist me - I'd be incredibly grateful if you could.
This evening I ridded of my realtek wifi unit as it kept dropping out. I had Broadcom Corporation BCM4311 [14e4:4311] (rev 01) kicking about spare. Naturally I gave it a shot.

I've removed obsolete drivers from kernel etc.. and I've had better results using the b43 package.. the computer has finally recognised the hardware. However, as you've come across in the past with many of your threads, the device is disabled by hardware switch, or better known as 'rfkill'.

I've attempted to "sudo rfkill unblock all", furthermore "sudo ifconfig wlan1 up" - no luck :(

I've reset my bios. I've even tried more of your harder commands "sudo modprobe -rfv b43" and "dmesg | grep -e rt2 -e 0000:14:00.0"

fraser@Ubuntu-Satellite-L500:~$ sudo rfkill list all[sudo] password for fraser: 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes



I wondered if you would be so kind as to help me.

regards

fraser

tag: [COLOR=#000000]*lsmod*[/COLOR]

---

### Post by jeremy31 on 2015-02-05
You could give Chili more info by following the instructions for running the script and posting the results, info- [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by westie457 on 2015-02-05
Hello fraz3,
The usual routine for the BCM4311 driver goes something like this. 
With a temporary wired connection run the following.```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install --reinstall firmware-b43-installer b43-fwcutter
sudo modprobe -rfv b43
sudo modprobe b43
```
You can safely ignore all errors and warnings. The last command should return to a blank line with no output.
Unplug the cable and check for wireless networks.

Let us know what happens.

---

### Post by fraz3 on 2015-02-05
Hey Westie457,

Thank you for helping. I had zero errors on the latter command. Unplugged the ethernet, but still "disabled by hardware switch".

I quickly checked the terminal:
fraser@Ubuntu-Satellite-L500:~$ sudo rfkill list all
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
fraser@Ubuntu-Satellite-L500:~$ sudo ifconfig wlan1 upSIOCSIFFLAGS: Operation not possible due to RF-kill
fraser@Ubuntu-Satellite-L500:~$ 

any ideas?

I noticed on Chili555's "how to,install,, broadcom" list, that there isn't a model number for [COLOR=#000000][FONT=Ubuntu Mono]14e4:4311 (rev 1)  would this make a difference to the driver package? or should it still be b43-fwcutter?

Kindest Regards[/FONT][/COLOR]

---

### Post by chili555 on 2015-02-05
> **westie457 said:**
> Hello fraz3,
The usual routine for the BCM4311 driver goes something like this. 
With a temporary wired connection run the following.```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install --reinstall firmware-b43-installer b43-fwcutter
sudo modprobe -rfv b43
sudo modprobe b43
```
You can safely ignore all errors and warnings. The last command should return to a blank line with no output.
Unplug the cable and check for wireless networks.

Let us know what happens.From his PM, I believe he has done all that but thanks.> I noticed on Chili555's "how to,install,, broadcom" list, that there isn't a model number for 14e4:4311 (rev 1) would this make a difference to the driver package? or should it still be b43-fwcutter?I think firmware-b43-installer will do it. Didn't you do so already?

Is there no effect from pressing the wireless key combination? [http://www.microcentertech.com/tech_center/DB/HowTos/images5/HOW5002071B-001.gif](http://www.microcentertech.com/tech_center/DB/HowTos/images5/HOW5002071B-001.gif)

---

### Post by fraz3 on 2015-02-05
It'll bump the 'rfkill list' to soft blocked = yes, and viceversa.

Sadly it won't do anything to the 'hard' line item.

---

### Post by chili555 on 2015-02-05
May we also see:```
lsmod
```

---

### Post by fraz3 on 2015-02-05
Sure:

```
fraser@Ubuntu-Satellite-L500:~$ lsmod
Module                  Size  Used by
b43                   387371  0 
bcma                   52096  1 b43
mac80211              630669  1 b43
cfg80211              484040  2 b43,mac80211
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
arc4                   12608  2 
binfmt_misc            17468  1 
ip6t_REJECT            12939  1 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18894  8 
nf_defrag_ipv6         34768  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17717  10 
xt_limit               12711  13 
xt_tcpudp              12884  18 
xt_addrtype            12635  4 
nf_conntrack_ipv4      15012  8 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  16 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 21841  1 nf_nat_ftp
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack           96976  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_intel          56531  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ssb_hcd                12869  0 
coretemp               13435  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
i915                  784111  4 
joydev                 17381  0 
serio_raw              13462  0 
snd                    69322  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
drm_kms_helper         55071  1 i915
drm                   303102  5 i915,drm_kms_helper
soundcore              12680  1 snd
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi
wmi                    19177  1 toshiba_acpi
i2c_algo_bit           13413  1 i915
video                  19476  1 i915
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106714  0 
ahci                   29915  2 
libahci                32716  1 ahci
ssb                    62379  2 b43,ssb_hcd
r8169                  67581  0 
mii                    13934  1 r8169
fraser@Ubuntu-Satellite-L500:~$
```

Thanks for helping me out Chili555

---

### Post by chili555 on 2015-02-05
Is this a dual-boot system? Please check: [http://ubuntuforums.org/showthread.php?t=2245267](http://ubuntuforums.org/showthread.php?t=2245267)  Post #12.

---

### Post by fraz3 on 2015-02-05
Negative, Sir - It isn't.

Went through all of the threads. No luck.

Btw, I don't mind buying a completely different WLAN card..? Just a thought. If an alternative'll do the job, it might be simpler maybe?

Just gonna take dog for a WLK, back in a bit.

Thanks again.

---

### Post by chili555 on 2015-02-06
>  I don't mind buying a completely different WLAN cardThat's the thing; almost every case I've worked on, if the internal card is hard-blocked, the USB will be as well. If you wanted to do anything, I might look into a wireless ethernet bridge.

We are mighty low on possibilities. Please try:```
sudo modprobe -r toshiba_acpi
sudo rfkill unblock all
rfkill list all
```Thanks.

---

### Post by fraz3 on 2015-02-06
> **chili555 said:**
> That's the thing; almost every case I've worked on, if the internal card is hard-blocked, the USB will be as well. If you wanted to do anything, I might look into a wireless ethernet bridge.

We are mighty low on possibilities. Please try:```
sudo modprobe -r toshiba_acpi
sudo rfkill unblock all
rfkill list all
```Thanks.

Think there might be a tad confusion here. It's the PCI-wifi unit we're playing with here. Are you saying there's a confliction with the USB ports and PCI's?

I installed the broadcom under the keyboard of the laptop. Anyway, this morning when I booted up, there were way more problems.. command "lspci" couldn't even detect the wifi pci-board. Nothing could. Very strange. It was almost like it disappeared. So.. I installed the realtek again: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10).

The reason I pulled this wifi unit out is because it periodically drops off the wifi network, and prompts me to re-connect to the network (if it can see it again). It tends to happen after the computer has had lengthy up-time / or / woken-up from standby.

Incase you weren't talking about PCI-style units. I was thinking about buying a whole new one. Any recommendations on an appropriate one to buy that has decent support?
[ATTACH=CONFIG]259756[/ATTACH]

Sorry to give up on the broadcom unit, it's just when it lost vision of the hardware I thought, nah..

Any ideas regarding the RTL8191SEvB Wireless LAN Controller (rev 10)?

Kindest Regards,

Newbie fraz

---

### Post by chili555 on 2015-02-06
Yes, exactly. I have worked on several cases where the hard block couldn't be fixed by any of the several tricks we use and the OP buys a USB wireless device and it is hard blocked, too. Moreover, it, like its PCI brother, can't be tricked to work.> Incase you weren't talking about PCI-style units. I was thinking about buying a whole new one. When you install the Realtek, does it also show as hard-blocked?```
rfkill list all
```

Perhaps what we have been dealing with all along is an electrical defect in the Broadcom.

---

### Post by fraz3 on 2015-02-06
Haha, yup - true that. Can't bulsht a bulsht'r.

No blocks at all. All clear on soft and hard:

```
fraser@Ubuntu-Satellite-L500:~$ sudo rfkill list all
[sudo] password for fraser: 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
Now that's a good point - Maybe it is a defect..

---

### Post by chili555 on 2015-02-06
If you are having trouble connecting, I suggest you start a new thread as this is no longer a Broadcom b43 issue.

---

