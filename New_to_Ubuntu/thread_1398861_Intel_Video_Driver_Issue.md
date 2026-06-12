---
title: "Intel Video Driver Issue"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Blayze187 on 2010-02-05
Hey ppl. so im brand new to linux, i had played around with PHLAK a few years ago, but lost the live cd and jsut never went back to it, so now im using Ubuntu 9.10, and im running it on a Dell Inspiron 6000, when i boot with the live cd all the fancy desktop enhancements work fine, but then i installed it on my hdd and got rid of windows, now i cant activate the desktop enhancements so im thinking its cuz the intel video drivers arent properly working? please correct me if i am wrong. i want to learn this stuff lol. i had already had problems from the get go with Ubuntu not recognizing my wireless card, and my wired card. but i have a live cd of knoppix that i use in my hhd-less gateway laptop so i read some of forums to get those working. 

but id like to get this working now, someone help please?

---

### Post by Blayze187 on 2010-02-05
Hey ppl. so im brand new to linux, i had played around with PHLAK a few years ago, but lost the live cd and jsut never went back to it, so now im using Ubuntu 9.10, and im running it on a Dell Inspiron 6000, when i boot with the live cd all the fancy desktop enhancements work fine, but then i installed it on my hdd and got rid of windows, now i cant activate the desktop enhancements so im thinking its cuz the intel video drivers arent properly working? please correct me if i am wrong. i want to learn this stuff lol. i had already had problems from the get go with Ubuntu not recognizing my wireless card, and my wired card. but i have a live cd of knoppix that i use in my hhd-less gateway laptop so i read some of forums to get those working. 

but id like to get this working now, someone help please?

---

### Post by Psumi on 2010-02-05
Your Dell Inspirion 6000 has ATI Mobility Radeon X300 according to CNET and google.

[http://ubuntuforums.org/showthread.php?t=1394136](http://ubuntuforums.org/showthread.php?t=1394136)

The mobility radeon x300 had issues, and probably still has issues. The FPS may be very slow in newer versions of ubuntu (in 8.04 the FPS was clear up to 30, but in 9.04 or so, it shot down to 6 according to a Phoronix test.)

And it isn't Intel, as I said, it's ATI, and ATI is known to a.) stop support for older hardware, and B.) not work sometimes.

---

### Post by Blayze187 on 2010-02-05
> **Psumi said:**
> Your Dell Inspirion 6000 has ATI Mobility Radeon X300 according to CNET and google.

[http://ubuntuforums.org/showthread.php?t=1394136](http://ubuntuforums.org/showthread.php?t=1394136)

The mobility radeon x300 had issues, and probably still has issues. The FPS may be very slow in newer versions of ubuntu (in 8.04 the FPS was clear up to 30, but in 9.04 or so, it shot down to 6 according to a Phoronix test.)

And it isn't Intel, as I said, it's ATI, and ATI is known to a.) stop support for older hardware, and B.) not work sometimes.

 yea when i run the check in the terminal it says Intel, and when i was using windows i tried to install the ATI drivers, stup said i didnt have an ATI graphics card, so i went to dell support dl'd the drivers, and it installed as INTEL. oh and btw the laptop is like 4 or more years old. so it has the old chipsets in it, not any of the fancy new ones, so my question still applys, and now i updated the kernel through the update manager and now when i log in it doesnt diplay the desktop just the terminal appears. i really need some help here, these problems are making me just want to reinstall windows, but i dont want to give up on this yet.

---

### Post by Leppie on 2010-02-05
intel video cards now only use kernel drivers.
what is the output of the following command:
```
lsmod
```

---

### Post by Grenage on 2010-02-05
There's a chance that the install is using xorg.conf, and specifying the vesa driver.

Type this into a terminal:

```
gksu gedit /etc/X11/xorg.conf
```

Look for:

```
Driver         "vesa"
```

If it's there, change it to:

```
Driver         "intel"
```

---

### Post by Leppie on 2010-02-05
> **Grenage said:**
> There's a chance that the install is using xorg.conf, and specifying the vesa driver.

Type this into a terminal:

```
gksu gedit /etc/X11/korg.conf
```
that should be:
```
gksu gedit /etc/X11/[COLOR=Red]**x**[/COLOR]org.conf
```

---

### Post by Grenage on 2010-02-05
> **Leppie said:**
> that should be:
```
gksu gedit /etc/X11/[COLOR=Red]**x**[/COLOR]org.conf
```

Thank you, damn typo; I have corrected it.

---

### Post by Leppie on 2010-02-05
> **Grenage said:**
> Thank you, damn typo; I have corrected it.
you're welcome.
btw, was xorg.conf there after you installed karmic? i'm running my system without any xorg.conf (karmic doesn't have one by default).

---

### Post by Grenage on 2010-02-05
Mine only had one in Karmic after an upgrade from Jaunty, fresh installs didn't. nvidia-settings will create one if you use it to save settings.

---

### Post by Leppie on 2010-02-05
i've got an intel card, but never have had the need for a xorg.conf

---

### Post by Grenage on 2010-02-05
Neither have I on a fresh Karmic Intel install, not unless there were EDID problems.  Some people do seem to have them, and occasionally they reference the vesa driver, God knows why - probably the result of some playing around.

---

### Post by Leppie on 2010-02-05
well, it could also be a bug. like normally karmic should install grub2 and only use grub-legacy when a system upgrade is done. but i've seen several cases that a clean install results in a mixture of grub2 and grub legacy.

---

### Post by Leppie on 2010-02-05
cross posting doesn't really help you... i replied in your other thread...

btw, dell always has had the habit of producing a whole range of different machines under the same model number. this is also why you will always find several different drivers for like graphics, sound and networking.

---

### Post by overdrank on 2010-02-05
Threads merged. Please do not create multiple threads on the same issue.

---

### Post by Blayze187 on 2010-02-05
> **overdrank said:**
> Threads merged. Please do not create multiple threads on the same issue.

yea sorry about that, im new to forums and linux. ive had my fill of windows tho. i can do alot on it, and i want something new. k so after the issue i had with it not booting after i updated the kernel. i just wiped it and installed windows again, split the hdd into two partitions, and dual boot installed ubuntu 9.04 again. now i still have the video issue, but a new problem has occured, after i got my wireless working again, its got a low transfer rate, like wayyy lower then when i had just ubuntu installed on the hdd, i was gettin at least 150 kbps but now im maxin at around 60 kbps, but hovering around 30-40 kbps
strange? i think so. anyway along those same lines, the update manager cant retrieve the index thing for the upgrade to 9.10 and says to check my internet connection, but since im posting on this forum im pretty sure my internet works ok. the other updates are downloading fine too, just not the Karmic update.

any insights? much appreciated, and ill post another reply with the results of the tweaking you guys said for me to do.

---

### Post by Blayze187 on 2010-02-05
> **Leppie said:**
> intel video cards now only use kernel drivers.
what is the output of the following command:
```
lsmod
```

this is the result of that:

blayze@blayze-laptop:~$ lsmod
Module                  Size  Used by
rfkill_input           12800  0 
arc4                    9856  2 
ecb                    10752  2 
b43                   131484  0 
mac80211              217208  1 b43
cfg80211               38032  1 mac80211
led_class              12036  1 b43
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  1 b43
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
pcmcia                 44748  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 18368  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcspkr                 10496  0 
dcdbas                 15264  0 
soundcore              15200  1 snd
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
psmouse                61972  0 
serio_raw              13316  0 
video                  25360  0 
output                 11008  1 video
intel_agp              34108  1 
agpgart                42696  2 intel_agp
hid_bright              9984  0 
usbhid                 42336  1 hid_bright
b44                    35984  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
ssb                    41220  2 b43,b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by Blayze187 on 2010-02-05
> **Grenage said:**
> There's a chance that the install is using xorg.conf, and specifying the vesa driver.

Type this into a terminal:

```
gksu gedit /etc/X11/xorg.conf
```Look for:

```
Driver         "vesa"
```If it's there, change it to:

```
Driver         "intel"
```

and uh when i put that in this is what comes up in the editor:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2304 800
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

---

### Post by Leppie on 2010-02-05
did you set the virtual desktop to 2304x800?
if not, try renaming the file:
```
sudo mv /etcX11/xorg.conf /etcX11/xorg.conf.old
```
then reboot

---

### Post by Blayze187 on 2010-02-05
> **Leppie said:**
> did you set the virtual desktop to 2304x800?
if not, try renaming the file:
```
sudo mv /etcX11/xorg.conf /etcX11/xorg.conf.old
```then reboot

 
lawl not that high, i set it to 1280x800 so it displayed in 16:9, other wise there are ugly black borders on the left and right side of my screen.

should i try reloading the old file anyway? at least then my desktop effects would work again lol

---

### Post by Leppie on 2010-02-05
> **Blayze187 said:**
> lawl not that high, i set it to 1280x800 so it displayed in 16:9, other wise there are ugly black borders on the left and right side of my screen.

should i try reloading the old file anyway? at least then my desktop effects would work again lol
as i said, i use my intel card without any issues running x without a xorg.conf present.
just rename the file and see the result, if it's worse you can always put it back.

---

### Post by Blayze187 on 2010-02-05
> **Leppie said:**
> as i said, i use my intel card without any issues running x without a xorg.conf present.
just rename the file and see the result, if it's worse you can always put it back.

k i will once my slow updater finishes. then ill reply to this. thanks for the help so far.

---

### Post by Blayze187 on 2010-02-05
k so after security updates i tryed that command code, and this is what shows up:
blayze@blayze-laptop:~$ sudo mv /etcX11/xorg.conf /etcX11/xorg.conf.old
mv: cannot stat `/etcX11/xorg.conf': No such file or directory

so what now...?

---

### Post by Leppie on 2010-02-05
> **Blayze187 said:**
> k so after security updates i tryed that command code, and this is what shows up:
blayze@blayze-laptop:~$ sudo mv /etcX11/xorg.conf /etcX11/xorg.conf.old
mv: cannot stat `/etcX11/xorg.conf': No such file or directory

so what now...?
sorry about that...
forgot a slash...
here's the command again, but the correct version:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

---

### Post by Blayze187 on 2010-02-05
> **Leppie said:**
> sorry about that...
forgot a slash...
here's the command again, but the correct version:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

ahh ok that makes sense, wow i shoulda caught that it was missing.
anyway so i got the updates installed, and then got the update mnanager to retrieve the release notes, and got Karmic installed(thank fully), and now mny resolution says taht its in 4:3 but there are no borders, so its displaying in 16:10. i guess the system is confused.
and now my desktop effects can be activated. so the update, and upgrade did something good. but im still kinda wary, cuz id like to play games and whatnot, but i dont want to launch one with out the proper driver support, last time i did when i installed ubuntu the first time the screen tried to resize when the game launched but then got stuck between resolutions but the sound still played.

so yeaaa, sorry about all my long winded responses.

---

### Post by Leppie on 2010-02-05
i have an intel i915 card and am using the kernel modules without any problems. also, as stated before my system doesn't have a xorg.conf

---

### Post by Blayze187 on 2010-02-05
> **Leppie said:**
> i have an intel i915 card and am using the kernel modules without any problems. also, as stated before my system doesn't have a xorg.conf

yea i guess with 9.10 its fixed. thanks for the help man.

---

### Post by Leppie on 2010-02-06
you're welcome.

if you consider this issue to be solved, use the thread tools to set it to solved.

---

