---
title: "Broadcom BCM4322: Wifi not working, 14.10"
date: 2014-12-17
forum: Networking &amp; Wireless
---

### Post by wyrm2 on 2014-12-17
Hello Community,

I'm basically a vanilla Windows user with only minor exposure to Unix/Linux/Mac.  

Last week I decided to try Lubuntu on my HP Mini 2140 to see "what it's like" and also (mainly) whether I could get better performance on the netbook with a "lite"r OS.

I downloaded the "LinuxLive USB Creator" tool and, using it, created a bootable Lubuntu 14.10 installer on an 8GB USB memory stick.
I installed the OS on the netbook without out a hitch (quick, smooth, and encouraging).

However, after the OS starts up there is no wifi connection, or any way to find or connect to a wifi network.

I have read a few posts on this issue that instruct me to go to Preferences > Default applications for LXSession > Autostart, add "nm-applet", and then restart the OS.

I have also read other posts that instruct me to execute nm-applet manually.

While these approaches appear to have worked for others, neither approach fixes the problem in my install.


Executing "nm-applet" manually on the command line produces the following output:

```
[FONT=arial]** (nm-applet:2221): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.[/FONT][FONT=arial]ServiceUnknown: The name org.a11y.Bus was not provided by any .service files[/FONT]
[FONT=arial]nm-applet-Message: using fallback from indicator to GtkStatusIcon
[/FONT]
```

Has anyone else had a similar problem?  Is there a known solution?


Thanks...

---

### Post by carl4926 on 2014-12-18
Did the wifi work from the Live session before install?

Post the output of

```
lspci -nnk | grep -iA2 net
```

---

### Post by wyrm2 on 2014-12-18
Thanks for your reply Carl4926.

Regrettably, I believe I skipped the "Live session" and (not knowing what it was) went straight to the install.

I know the local wifi network is ok, as I'm able to access it from other devices.

The output of the command line you requested is:
```

[FONT=arial]08:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)[/FONT]
[FONT=arial]    Subsystem: Hewlett-Packard Company Device [103c:1380][/FONT]
[FONT=arial]    Kernel driver in use: b43-pci-bridge[/FONT]
[FONT=arial]20:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8072 PCI-E Gigabit Ethernet Controller [11ab:436c] (rev 10)[/FONT]
[FONT=arial]    Subsystem: Hewlett-Packard Company Device [103c:3056][/FONT]
[FONT=arial]    Kernel driver in use: sky2

```

[/FONT]

---

### Post by carl4926 on 2014-12-18
With a wired connect
Do

```
sudo apt-get install bcmwl-kernel-source
```

Once it's done, just reboot

---

### Post by wyrm2 on 2014-12-18
It says:

```

[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]E: Unable to locate package bcmwl-kernel-source
```

[/FONT]

---

### Post by carl4926 on 2014-12-18
You have a network connection ?

```
sudo apt-get update
```

And try again

---

### Post by wyrm2 on 2014-12-18
Yes, I have a wired internet connection. I am able to browse the web and send/receive emails.

[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR] produced a flood of output and seemed to complete happily.

Following that, [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install bcmwl-kernel-source[/FONT][/COLOR] also produced a flood of output and also seemed to complete happily.

After that I rebooted, and... still no wifi.

Wired network still works okay.

Manually executing nm-applet still fails, now although with a different error message.

I notice that after failing, nm-applet opens a dialog (which can hardly be read due to the stripped background) and another instance of the "wired network icon" appears in the bottom right of screen (two small squares connected by a backward-L shape).

If I click the network icon it opens a context menu with two grayed-out entries (I'm pretty sure I didn't see these before, but maybe I just didn't look):

Wi-Fi Networks
Wi-Fi is disabled by hardware switch


This seems important, but it's unexpected because wifi was working fine with Windows prior to installing Lubuntu. 
Unfortunately it's non-trivial to test wifi via Windows again; I'd have to physically switch the HDD out which is a bit painful.

Having seen this clue in the context menu I now notice that the wifi LED on the front of the netbook is lit orange (indicating off), and I can't switch it to blue (indicating on). Flicking the switch does nothing.

---

### Post by wyrm2 on 2014-12-18
I notice that during the cold reboot process the wifi indicator is initially unlit, then goes orange (off), then goes blue (on), but then changes to orange (off) again just before Lubuntu presents the log in dialog.  From there on it is permanently orange (off).

---

### Post by monkeybrain20122 on 2014-12-18
You said you are running from a live usb so none of the above suggestions would work because no settings are saved on reboot. You need to create the live usb with persistence to use those suggestions. Also I am not sure if you can install broadcom driver in a live session.

---

### Post by wyrm2 on 2014-12-18
I installed Lubuntu from a bootable USB.

Thereafter I have been running it from the HDD.

---

### Post by carl4926 on 2014-12-18
Install rfkill and get the output of

```
rfkill list
```

---

### Post by wyrm2 on 2014-12-19
> **carl4926 said:**
> Install rfkill and get the output of

```
rfkill list
```

Sorry Carl4926, I am a total noob.  How do I install rfkill?

---

### Post by carl4926 on 2014-12-19
```
sudo apt-get install rfkill
```

---

### Post by wyrm2 on 2014-12-19
Okay thanks.

Turns out that rfkill was already installed.

The output is as follows:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by carl4926 on 2014-12-19
Try

```
sudo rfkill unblock all
```

Also worth trying, as strange as it seems: Power OFF. Remove the power supply to the machine. Pull the battery and wait a min. Reassemble and try Ubuntu.
Can we assume Windows is also present?
Is the wireless switch a Fn combo or key rather than a physical switch on the side of the machine?

---

### Post by wyrm2 on 2014-12-19
I physically removed the HDD with Windows isntalled on it.  Then I put in a brand new unformatted HDD and installed Lubuntu.  So Windows is not present in any capacity.

The wireless switch on the HP Mini 2140 is a physical LED switch on the front of the case; there is no funtion key to control the wireless as far as I know (looking at the icons on the fucntion keys it doesn't look like any one them will affect wifi).

sudo rfkill unblock all completed without producing any output, so I assume that is success?

Re-executing sudo rfkill list thereafter produces exactly the same output as before. So it appears that unblock all had no discernable affect.

I will try the powerdown cycle shortly...

---

### Post by jeremy31 on 2014-12-19
Any wmi modules loaded ```
lsmod
```

---

### Post by wyrm2 on 2014-12-19
lsmod produces the following output:

```
Module                  Size  Used by
snd_hda_codec_analog    14537  1 
snd_hda_codec_generic    62849  1 snd_hda_codec_analog
hp_wmi                 13741  0 
sparse_keymap          13708  1 hp_wmi
snd_hda_intel          29211  1 
snd_hda_controller     29944  1 snd_hda_intel
snd_hda_codec         120356  4 snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
coretemp               13201  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                91280  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13324  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25722  1 snd_seq_midi
uvcvideo               71457  0 
joydev                 17072  0 
wl                   6148792  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
serio_raw              13210  0 
videobuf2_core         48344  1 uvcvideo
v4l2_common            15132  1 videobuf2_core
snd_seq                56638  2 snd_seq_midi_event,snd_seq_midi
videodev              131257  3 uvcvideo,v4l2_common,videobuf2_core
i915                  824137  2 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
media                  20951  2 uvcvideo,videodev
snd_timer              28579  2 snd_pcm,snd_seq
cfg80211              430618  1 wl
lpc_ich                16877  0 
drm_kms_helper         55051  1 i915
snd                    66629  12 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
drm                   255383  4 i915,drm_kms_helper
rfcomm                 58045  0 
shpchp                 32136  0 
soundcore              14604  2 snd,snd_hda_codec
i2c_algo_bit           13190  1 i915
bnep                   18829  2 
bluetooth             390981  10 bnep,rfcomm
6lowpan_iphc           18262  1 bluetooth
hp_accel               25778  0 
lis3lv02d              19500  1 hp_accel
wmi                    18689  1 hp_wmi
video                  19528  1 i915
parport_pc             32021  0 
input_polldev          14247  1 lis3lv02d
ppdev                  17391  0 
lp                     17395  0 
parport                40795  3 lp,ppdev,parport_pc
mac_hid                13059  0 
uas                    22720  0 
usb_storage            52598  1 uas
psmouse                95318  0 
ahci                   25622  2 
pata_acpi              12901  0 
libahci                31066  1 ahci
sky2                   52917  0 

```

---

### Post by jeremy31 on 2014-12-19
Does changing the position of the wireless switch result in any change in ```
rfkill list
```

If it doesn't try ```
sudo modprobe -r hp_wmi
``````
sudo rfkill unblock all
``` and see if rfkill list info changes

---

### Post by wyrm2 on 2014-12-19
I tried the complete powerdown/unplug/remove battery/wait/power up cycle.  No change to the output of rfkill list.

I tried modprobe -r hp_wmi. No change to the output of rfkill list.

So... does anyone have a Mini 2140 with wireless working?

---

### Post by carl4926 on 2014-12-19
I'm not sure, but should it be

```
sudo modprobe -rv hp_wmi
``` to remove that mod

---

### Post by wyrm2 on 2014-12-20
I tried sudo modprobe -rv hp_wmi too.  It had no impact on the output of rf kill list.

Is there any reason to think a Ubuntu install might include working wireless for my hardware?  Or is it the same software as Lubuntu underneath?

---

### Post by carl4926 on 2014-12-20
Should be the same

Your hardware is supported, after a fashion.

To explain. The drivers/firmware you have options for are twofold. 
1. b43 lists your device partially supported : [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
2. wl is the other option, which I used for you. But it's proprietary so is not included in Ubuntu directly.

I had a google on your device and didn't really turn up much.

I guess we could try this:

```
[COLOR=#000000][FONT=SmartGothic]sudo apt-get remove bcmwl-kernel-source[/FONT][/COLOR]
```this will remove 'wl'

then do
```
[COLOR=#000000][FONT=courier]sudo apt-get install firmware-b43-installer[/FONT][/COLOR]
```
then when it's done, reboot

---

### Post by wyrm2 on 2014-12-20
OKay, I did that. 

install firmware-b43-installer failed the first time, apparently it was unable to download a necessary file.  I added --fix-missing to the command line and it worked.

Then I rebooted. 

Then I executed rfkill list again, and it now says this:

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

Which is less output than before, but I still can't turn the wifi on at the physical switch :(

---

### Post by carl4926 on 2014-12-20
OK
So try the unblock all with rfkill option again

Do you have a wireless light, (sometimes they are blue colour) is it indicating that you have active wireless. Can you see your wireless access point?

---

### Post by wyrm2 on 2014-12-22
Thanks Carl,

Okay, yes. Now after I rebooted the rfkill list says this:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Moreover, the wifi LED switch on the front of the case is lit blue (on), and there is a wireless network menu in the bottom right of screen.

From there I was able to connect to my local wifi without a hitch, and I am posting this message via wifi.

Thanks Carl, you've been a fantastic help.  No way would I have figured all that out for myself.

No I can continue my Lubunu experiment :)

---

### Post by carl4926 on 2014-12-23
> **wyrm2 said:**
> Thanks Carl,

Okay, yes. Now after I rebooted the rfkill list says this:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Moreover, the wifi LED switch on the front of the case is lit blue (on), and there is a wireless network menu in the bottom right of screen.

From there I was able to connect to my local wifi without a hitch, and I am posting this message via wifi.

Thanks Carl, you've been a fantastic help.  No way would I have figured all that out for myself.

No I can continue my Lubunu experiment :)

Wow. I'm pleased about that

---

