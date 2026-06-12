---
title: "Wireless internet dies after suspens"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by Niemil on 2013-11-18
When I flipping down my screen on my laptop, I have chosen to make it go suspend/hibernate.
But, when opening from that state, and getting back on. The internet is gone. It says my wireless network aren't in reach. And my wireless network is the only one I can see also (even though there are many others here around), it just completely stops working. So fixing that I always have to restart my computer. So suspend option for me seems to be useless so far.

I wonder how i can fix this problem?

I have a dual boot on the computer, using windows 7 and ubuntu 13.10. And it's on ubuntu 13.10 this problem is on.

---

### Post by chili555 on 2013-11-18
Please see here: [http://ubuntuforums.org/showthread.php?t=2004690&highlight=suspend](http://ubuntuforums.org/showthread.php?t=2004690&highlight=suspend)  As I said in the thread, be sure to substitute your driver if it isn't iwlwifi. If in doubt, post back with the result of:```
sudo lshw -C network
```

---

### Post by kurt18947 on 2013-11-18
To add to Chili555's post, some RealTek adapters require the "SUSPEND_MODULES" trick as well.  Here is a test I've used.  Determine the wifi module in use with "lsmod" in a terminal.  In my case:
```

$ lsmod
Module                  Size  Used by
cfg80211              479757  0 
hid_generic            12548  0 
parport_pc             32701  0 
ppdev                  17671  0 
joydev                 17377  0 
hid_logitech_dj        18581  0 
usbhid                 53014  0 
**8192cu                542183  0 **

```

Then from an account with sudo privileges
```

sudo modprobe -r <wifi module> without the <> e.g. sudo modprobe -r 8192cu
sudo modprobe 8192cu

```

If the wifi wakes up, the "SUSPEND_MODULES" trick should work in my experience.  As I understand it, the problem is that the wifi module should unload prior to suspending, then reload when resuming.  Sometimes modules don't unload cleanly prior to suspending so can't be reloaded upon resuming because they're still loaded, or partially so.  I've never used hibernate, haven't seen an advantage over a full reboot.  YMMV on that, I guess.

---

### Post by Niemil on 2013-11-18
Well, I don't understand a single thing.
But I wrote[COLOR=#000000][FONT=Ubuntu Mono]**sudo lshw -C network **first and then I wrote [/FONT][/COLOR]**[COLOR=#000000]lsmod[/COLOR]**

```
[B]user@UB:~$ sudo lshw -C network
[/B][sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 64:31:50:84:04:74
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d003ffff
  *-network
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d2100000-d2103fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: cc:52:af:0e:13:be
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.11.0-12-generic firmware=610.812 ip=192.168.0.102 link=yes multicast=yes wireless=IEEE 802.11bgn



**user@UB:~$ lsmod**
Module                  Size  Used by
btrfs                 815968  0 
raid6_pq               97812  1 btrfs
zlib_deflate           26885  1 btrfs
xor                    21411  1 btrfs
ufs                    74590  0 
qnx4                   13317  0 
hfsplus               102646  0 
hfs                    54590  0 
minix                  36111  0 
ntfs                   96882  0 
msdos                  17332  0 
jfs                   180909  0 
xfs                   884143  0 
libcrc32c              12615  2 xfs,btrfs
reiserfs              245794  0 
ext2                   72832  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  12 
bnep                   19564  2 
snd_hda_codec_hdmi     41276  1 
joydev                 17377  0 
btusb                  28267  0 
hid_logitech_dj        18581  0 
arc4                   12608  2 
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387185  0 
mac80211              596969  2 b43,brcmsmac
bluetooth             371874  22 bnep,btusb,rfcomm
hid_generic            12548  0 
cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
usbhid                 53014  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
hid                   101512  4 hid_generic,usbhid,hid_logitech_dj
videodev              133390  2 uvcvideo,videobuf2_core
kvm                   431315  0 
microcode              23518  0 
snd_hda_codec_idt      50341  1 
psmouse                97626  0 
serio_raw              13413  0 
k10temp                13126  0 
sp5100_tco             13979  0 
edac_core              62312  0 
edac_mce_amd           22617  0 
snd_hda_intel          48171  7 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  24 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
radeon               1402449  4 
bcma                   46670  3 b43,brcmsmac
ttm                    83995  1 radeon
lp                     17759  0 
drm_kms_helper         52651  1 radeon
parport                42299  3 lp,ppdev,parport_pc
drm                   296739  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
soundcore              12680  1 snd
i2c_piix4              22106  0 
ohci_pci               13561  0 
shpchp                 37032  0 
wmi                    19070  1 hp_wmi
video                  19318  0 
mac_hid                13205  0 
ahci                   25819  2 
libahci                31898  1 ahci
r8169                  67341  0 
mii                    13934  1 r8169
user@UB:~$ 



```

---

### Post by chili555 on 2013-11-18
This technique sometimes, but not always works. We are going to add a file that tells the system that we have a module (a.k.a. driver) that we want to explicitly unload on suspend and reload on resume. The driver we'll unload and reload is your wireless driver brcmsmac. Let's use the text editor gedit to write a file.```
sudo gedit /etc/pm/config.d/config
```

Add one line:```
SUSPEND_MODULES="brcmsmac"
```

Proofread carefully, save and close gedit. Reboot.

How does it work now? 

By the way, there is some controversy about the best driver for your device in Ubuntu 13.10. How does it work for you?

---

### Post by Niemil on 2013-11-18
> **chili555 said:**
> This technique sometimes, but not always works. We are going to add a file that tells the system that we have a module (a.k.a. driver) that we want to explicitly unload on suspend and reload on resume. The driver we'll unload and reload is your wireless driver brcmsmac. Let's use the text editor gedit to write a file.```
sudo gedit /etc/pm/config.d/config
```

Add one line:```
SUSPEND_MODULES="brcmsmac"
```

Proofread carefully, save and close gedit. Reboot.

How does it work now? 

By the way, there is some controversy about the best driver for your device in Ubuntu 13.10. How does it work for you?

Alright, I just tried this, I made that command in Terminal and a gedit window popped up and I copied+pasted that code and saved the file.
Then I tried put down the laptops screen again so it goes to the suspend mode, then opened it up again and pressed the power button so it starts up from the suspend mode. But still, it goes to disconnect and force me to restart computer in order to get network to work again.

Also your last question I don't understand. I had Ubuntu 12.04.3 LTS on this computer for some days ago and it worked fine what I remember.
But since I made dual boot with ubuntu 13.10 and windows 7 it doesn't work.

On Windows 7 I installed some drivers I found on internet, wasn't sure if it's correct but it made the wireless work on Windows 7 anyway.

For Ubuntu I haven't downloaded anything because I got no idea what I even need. I just had it plugged in with wire as it first had problem with wireless network, but when I then made update the wireless network worked.
And well, now it sure works but not when after suspend.

[edit]
This is how it looks when it's disconnected after suspent
[http://oi41.tinypic.com/315cp3s.jpg](http://oi41.tinypic.com/315cp3s.jpg)

---

### Post by chili555 on 2013-11-18
I apologize if my question was unclear. There are two possible drivers for your wireless device. You are using one of them, brcmsmac. Does your wireless connectivity work well? That's really all I am asking.

What it did under previous Ubuntu versions or under Windows is not what I'm asking. Does it work well now?

One other note; I asked that you reboot after you wrote the file, not simply suspend. Would you please?

---

### Post by Niemil on 2013-11-18
Yeah I also did the suspend after reboot.
Now I found some update stuffs though. On "Additional drivers", there is one that I cannot select, that says it doesn't work, I think it's the one I have on Windows 7.
Then there is one driver named "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (propiertary)".
I will try apply that one.

I also tried apply that one earlier just for some minutes ago, but my internet went crazy and I think DNS died or something because Facebook were the only site I could connect, I could chat with my friend but couldn't access youtube or ubuntuforums at all.
I unplugged the wifi sender/router or whatever it is and plugged it back, which usually fixing that.

Otherwise, yes, my internet/wifi working good, always been doing that except sometimes problems with DNS or something.
Now I will apply this driver and hope it will be applied correctly now and then I will restart computer again and try suspend.

---

### Post by Niemil on 2013-11-18
Now I have tried apply that wireless driver that ubuntu found, but it still doesn't work.
As I said, the wireless network works fine when I start the computer. But after suspend it just doesn't work.

The only noticable change I have found during this change of driver, is the wireless button I have on my laptop. I remember when I started from suspend before (atleast very early today morning, when I made this thread), then the button were making orange color when I started from suspend.
Now when I start from suspend, it's orange for just a second, and it goes fast back to blue, which is the color at the button now when internet is on and working.

However, it still just are disconnected and all after suspend.

---

### Post by chili555 on 2013-11-18
So your internet was working well except for suspend and now, because I simply asked a question, you decided to try a different driver and now, as you say:> I also tried apply that one earlier just for some minutes ago, but my internet went crazy and I think DNS died or something because Facebook were the only site I could connect, I could chat with my friend but couldn't access youtube or ubuntuforums at all.I'm sorry I even said a word. I just want to know if it was working as expected. I didn't intend to see if we could wreck your system!

Did you repair it? Do we have some work to do?

---

### Post by Niemil on 2013-11-18
> **chili555 said:**
> So your internet was working well except for suspend and now, because I simply asked a question, you decided to try a different driver and now, as you say:I'm sorry I even said a word. I just want to know if it was working as expected. I didn't intend to see if we could wreck your system!

Did you repair it? Do we have some work to do?

My internet has always been working great. Except after suspend.
You asked me simple questions, I did them, answered you on them.

I searched some more,  I found some driver that ubuntu said I am available to apply, I wanted try it out in case that would work, during the time I wait for more solving ideas.
Because, why not try things out? what if it had helped.

However, this apply driver did nothing really what I can see, other than showing that light color on my computer.

What sorry to even said a word?
This apply thing didn't repair it at all.

---

### Post by chili555 on 2013-11-18
Please, after suspend, run and post:```
lsmod
```Try to get the wireless to start with:```
sudo modprobe brcmsmac
sudo modprobe bcma
```Does that start it?> What sorry to even said a word?Yes, I am sorry because it evidently raised a doubt in your mind and then you decided to try another driver which, as you say:> I also tried apply that one earlier just for some minutes ago, but my internet went crazyI didn't mean to try another driver and see if we can wreck your system, so I am sorry.

---

### Post by Niemil on 2013-11-18
Okey, I tried the command and here it is

```
user@UB:~$ lsmod

Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  12 
bnep                   19564  2 
lib80211_crypt_tkip    17619  0 
hid_generic            12548  0 
hid_logitech_dj        18581  0 
wl                   4207474  0 
snd_hda_codec_hdmi     41117  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
usbhid                 53014  0 
hid                   105818  4 hid_generic,usbhid,hid_logitech_dj
joydev                 17377  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
kvm                   431315  0 
microcode              23518  0 
psmouse                97626  0 
snd_hda_codec_idt      50341  1 
lib80211               14352  2 wl,lib80211_crypt_tkip
serio_raw              13413  0 
snd_hda_intel          48171  10 
k10temp                13126  0 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
edac_core              62312  0 
snd_hwdep              13602  1 snd_hda_codec
edac_mce_amd           22617  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
btusb                  28267  0 
bluetooth             371880  22 bnep,btusb,rfcomm
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  31 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
sp5100_tco             13979  0 
i2c_piix4              22106  0 
cfg80211              479757  1 wl
radeon               1402449  4 
ttm                    83995  1 radeon
drm_kms_helper         52651  1 radeon
drm                   296739  6 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
shpchp                 37032  0 
wmi                    19070  1 hp_wmi
video                  19318  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
r8169                  67341  0 
mii                    13934  1 r8169
ohci_pci               13561  0 
ahci                   25819  2 
libahci                31898  1 ahci



```
That's when I done the suspend and when wireless not working for me.


And I also made those commands you told me to do, but internet didn't fix itself.
I tried log out and in, but still internet did not work.
So now I restarted computer again.

[I]I will very soon go to sleep, so may continue try fix this tomorrow morning, I will try and do stuffs on morning if there is anything else you think I can try.
But after tomorrow morning in about 7 hours from now, I wont really be able to fix this as I will go away for a few days and leave laptop at home, but will be back on this computer then at Thursday.[/I]

---

### Post by chili555 on 2013-11-18
> cfg80211              479757  1 [COLOR="#FF0000"]wl[/COLOR]So wl, the driver you mistakenly installed, is now loaded is here instead of brcmsmac. And your wireless doesn't work. Great. 

Please open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and tell me if your wireless is working. If so, then we will return to the suspend issue following this detour.

---

### Post by Niemil on 2013-11-19
I just tried this:
1. Made the command you told me, and it was installing/removing stuffs or something, as supposed to do.
2.  Restarted computer
3.  Wifi internet worked when it was restarted (so far so good)
4.  Flipped down the screen so it went on suspend
5   Opened the screen and clicked powerbutton so it starts from suspend

And internet does not work afterwards, like before.

Now I also did that command I done multiple times.

```

user@UB:~$ lsmodModule                  Size  Used by
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
rfcomm                 69070  12 
bnep                   19564  2 
parport_pc             32701  0 
ppdev                  17671  0 
snd_hda_codec_hdmi     41117  1 
arc4                   12608  2 
b43                   387185  0 
joydev                 17377  0 
mac80211              596969  2 b43,brcmsmac
hid_generic            12548  0 
hid_logitech_dj        18581  0 
cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
usbhid                 53014  0 
hid                   105818  4 hid_generic,usbhid,hid_logitech_dj
kvm                   431315  0 
microcode              23518  0 
psmouse                97626  0 
serio_raw              13413  0 
edac_core              62312  0 
k10temp                13126  0 
snd_hda_codec_idt      50341  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
edac_mce_amd           22617  0 
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
btusb                  28267  0 
bluetooth             371880  22 bnep,btusb,rfcomm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
radeon               1402449  4 
sp5100_tco             13979  0 
i2c_piix4              22106  0 
snd                    69141  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    83995  1 radeon
bcma                   46670  3 b43,brcmsmac
drm_kms_helper         52651  1 radeon
soundcore              12680  1 snd
drm                   296739  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
shpchp                 37032  0 
wmi                    19070  1 hp_wmi
video                  19318  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
r8169                  67341  0 
mii                    13934  1 r8169
ohci_pci               13561  0 
ahci                   25819  2 
libahci                31898  1 ahci



```

I also tried doing the commands
sudo modprobe brcmsmac
sudo modprobe bcma

but those didn't help

---

### Post by chili555 on 2013-11-19
> cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43I don't believe b43 is correct for your device; I think brcmsmac is and I suspect there is a conflict. May I see:```
cat /etc/modules
lspci -nn -d 14e4:
```Thanks.

---

### Post by Niemil on 2013-11-20
> **chili555 said:**
> I don't believe b43 is correct for your device; I think brcmsmac is and I suspect there is a conflict. May I see:```
cat /etc/modules
lspci -nn -d 14e4:
```Thanks.

```
user@UB:~$ cat /etc/modules# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc
user@UB:~$ lspci -nn -d 14e4:
06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
user@UB:~$ 



```
This when I were connected to internet (wifi). If I shall be connected? I can also try when disconnected and see if it make difference in output.
[edit] it was same output when I were going on suspend and back up when internet not working

---

### Post by chili555 on 2013-11-20
You don't need b43 for that device. We wonder how it gets loaded. Let's see:```
cat /etc/modules
```

---

### Post by Niemil on 2013-11-20
> **chili555 said:**
> You don't need b43 for that device. We wonder how it gets loaded. Let's see:```
cat /etc/modules
```

b43?

Well, I just runned that code, here is output:

```
user@UB:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc
user@UB:~$ 



```

*I'll very soon head to bed and wakeup in about 6 hours from now and may be able run some more codes.*

---

### Post by chili555 on 2013-11-21
I am still wondering how b43 and ssb get loaded. They are not required for your 14e4:4727 device. I suggest we try, at least temporarily, blacklisting them.```
sudo -i
echo  "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo  "blacklist ssb" >> /etc/modprobe.d/blacklist.conf 
modprobe -r b43
modprobe -r ssb
exit
```Any improvement?

---

### Post by Niemil on 2013-11-21
> **chili555 said:**
> I am still wondering how b43 and ssb get loaded. They are not required for your 14e4:4727 device. I suggest we try, at least temporarily, blacklisting them.```
sudo -i
echo  "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo  "blacklist ssb" >> /etc/modprobe.d/blacklist.conf 
modprobe -r b43
modprobe -r ssb
exit
```Any improvement?

I just tried that out. Tried after restart too, but still not working.

---

### Post by Niemil on 2013-11-21
Well.

I noticed that an option "hibernate" exist (didn't see it earlier, maybe it didn't exist for ubuntu 12.04.3 LTS that I had earlier? if it did though I may just didn't notice).
Anyway, now when i went into Tweak Tool I checked those settings and now I tried this hibernate.
I have no idea what the different is on hibernate and suspend?!? Only different I finding is on hibernate I have to write password.

But guess what. On Hibernate the internet seems to continue work in. So, if there is no big deal and differents, and if this suspend doesn't work to fix (well I am sure willing to continue try fix if you've ideas, but I can instead use the hibernate if so).

---

### Post by kurt18947 on 2013-11-22
As I understand it (and I'm no expert)  suspend keeps contents in RAM alive while the machine is inactive so requires some small amount of power.  Hibernate writes the contents of RAM to the swap partition on the hard drive then shuts down so requires no power to maintain its contents.  Why that difference would make a difference on whether a device functions correctly after resuming I have no idea.  As I related earlier, some Realtek based wifi adapters do no suspend correctly so do not resume correctly.  I don't normally have swap partitions do can't try hibernate vs. suspend and have no Broadcom based adapters.

---

### Post by chili555 on 2013-11-22
> **Niemil said:**
> Well.

I noticed that an option "hibernate" exist (didn't see it earlier, maybe it didn't exist for ubuntu 12.04.3 LTS that I had earlier? if it did though I may just didn't notice).
Anyway, now when i went into Tweak Tool I checked those settings and now I tried this hibernate.
I have no idea what the different is on hibernate and suspend?!? Only different I finding is on hibernate I have to write password.

But guess what. On Hibernate the internet seems to continue work in. So, if there is no big deal and differents, and if this suspend doesn't work to fix (well I am sure willing to continue try fix if you've ideas, but I can instead use the hibernate if so).I have tried every trick I know to try. If hibernate does what you need and resumes correctly, I think I'd just stick with it. I'm sorry I have no further suggestions.

---

