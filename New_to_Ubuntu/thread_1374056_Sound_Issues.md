---
title: "Sound Issues"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by neurostu on 2010-01-06
I've had ubuntu installed on my computer since 7.10. I'm currently running 9.10. 

I did a clean install of 8.10 or 8.04 and have been doing the dist-upgrades since then.

I have never had working sound on my computer and I am finally fed up with it. 

When I run lspci I get the following output:
```

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE6145 SATA II PCI-E controller (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:02.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```
It appears that my audio device is getting detected:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

When I run lsmod it appears that the kernel module is installed as well:
```

odule                  Size  Used by
binfmt_misc            16776  1 
openafs               571292  1 
vboxnetflt             92296  0 
vboxnetadp             85736  0 
vboxdrv               128552  1 vboxnetflt
snd_hda_intel         435636  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
hid_logitech           16256  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ff_memless             13320  1 hid_logitech
nvidia               9594120  26 
snd                    62628  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
psmouse                61972  0 
iptable_filter         10752  0 
ip_tables              19472  1 iptable_filter
i82975x_edac           12292  0 
ppdev                  15620  0 
sbp2                   30476  0 
joydev                 18368  0 
raw1394                32732  0 
x_tables               23044  1 ip_tables
usbhid                 42336  1 hid_logitech
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
serio_raw              13316  0 
parport_pc             40100  1 
edac_core              47404  1 i82975x_edac
agpgart                42696  1 nvidia
lp                     17156  0 
video1394              23740  0 
parport                42220  3 ppdev,parport_pc,lp
usb_storage            82880  0 
ohci1394               38576  1 video1394
ieee1394               94660  4 sbp2,raw1394,video1394,ohci1394
3c59x                  49192  0 
mii                    13312  1 3c59x
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
here is the line:
```

snd_hda_intel         435636  0 

```
But when I try to configure the sound under System-->Prefs-->Sound, do devices show up under the Hardware tab, and the only device that shows up under the Output tab is: DUmmy Output.

I would really like to get sound working on my machine.... please help!

---

### Post by neurostu on 2010-01-07
bump...

---

### Post by candtalan on 2010-01-07
It seems like you are using onboard sound, on the mainboard (?) I wonder if there are any audio related entries in the bios settings?

It would be useful to verify that you can get sound by at least some means, for example, that you do not have an actual hardware disconnection or other fault. Does a Live CD allow any sound to be played, for example, from the Examples folder in Live CD?

---

### Post by proxess on 2010-01-07
First add this to alsaconfig (sudo gedit /etc/modprobe.d/alsa-base.conf):
```
options snd-hda-intel power_save=10 power_save_controller=N **[COLOR="Red"]model=auto[/COLOR]**
```
Find the corresponding line and add the model text.

Create a script like this:
```
#!/bin/bash
killall pulseaudio
alsa force-reload
sleep 2
killall pulseaudio
```

Make it executable, and add something like this to visudo (sudo visudo):
```
%<USERNAME> ALL=NOPASSWD: /FULL/PATH/TO/SCRIPT
```

and then add the script as this to startup:
```
gksu /FULL/PATH/TO/SCRIPT
```

Your sound will be muted when you start up.

---

### Post by neurostu on 2010-01-13
I tried that and it still doesn't work...

---

### Post by spartan777 on 2010-01-13
I have the exact same sound (82801G ICH7 Intel Audio on my Toshiba NB 205 netbook), and I have the same issue. I got the netbook this week, made a fresh install of Ubuntu 9.10, and cannot get sound. Odd thing is that my mic works. I can tell because when I go into the "Sound Preferences" and in the tab "Input" the "Input Level meter" corresponds with sounds I make.

And even with that, I still have no sound output.

---

### Post by neurostu on 2010-01-14
So nobody here has the time, desire, or know how to help me trouble shoot this bug, which is totally fine. 

Does anybody else know a place where I can go to get support for this issue?

---

### Post by halitech on 2010-01-14
what is the result of
```
aplay -l
```

---

### Post by neurostu on 2010-01-15
```
 
$aplay -l
aplay: device_list:223: no soundcards found...

```

---

### Post by halitech on 2010-01-15
so it sees the hardware but its not loading the proper module for it. Never did like trying to figure out what modules were actually needed for sound, seems like the most pain in the butt feature to get working when it doesn't work after an install

---

### Post by neurostu on 2010-01-18
*bump

anybody?

---

### Post by maheanuu on 2010-02-02
I am working on exactly the same problem, and I believe that it has to do with 9.10 not playing with the AMD ATI Drivers, at least on my notebook.  I am running a Toshiba Satellite A355D  That worked perfectly under Windoze Vista, but upon installing Karmic, I have not found any sound at all.  My Mic is working or at least modulating the output meter.  I have tried to run a DVD and it isn't working either.  

My major prob. is that I need to learn more about the operational aspects of Ubuntu, how to install drivers, use the terminal better and the language to do these things.  I am still looking for books, and being that I live in French Polynesia, sorta complicates things...

I am very used to not getting things done quickly as down here, knowledge is power, and if you have it you do not want to give it up.  

I very much want to learn this system and to teach it to others here, the endless repair of "Windoze" based equipment is a never ending battle.  Too many virii, being spawned too quickly and I think by too many people who want to make a living repairing the damages they wrought.  I could be wrong, but having lived here for over 30 years, I have seen the scams come and go, and with computers being the newest thing and those who make a living doing repairs running a land office business, I don't think that I am wrong.  I do repairs on the family's machines, I work in english only as the french tech terms for computers are in a language new to me. 

I will subscribe to your thread, and if I come up with anything I will let you know.

Ken Jackson 
CPO USN Ret.

---

### Post by listerdl on 2010-02-02
> **maheanuu said:**
> I am working on exactly the same problem, and I believe that it has to do with 9.10 not playing with the AMD ATI Drivers, 

Exactly the same for me but I have a slighly different Sound Driver. I am trying so many different things it really is problematic.....

---

### Post by listerdl on 2010-02-02
> **listerdl said:**
> Exactly the same for me but I have a slighly different Sound Driver. I am trying so many different things it really is problematic.....

To be honest this is a nightmare. There seems to be a million people with sound issues....why is this so difficult to fix?

---

### Post by maheanuu on 2010-02-02
listerdl, I am looking here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
because I have an ATI based motherboard in this Toshiba Notebook that I am trying very hard to get running....  

I have been googling and reading and from what I am seeing it is a problem between the Karmic and the hardware, from what I understand that ubuntu 9.6 ran fine on this same notebook....    Like I said, I am not at the end of the world I am over it.  We have DSL but it is really throttled down and the company is making a killing while we all suffer...   I knew that this particular thing was not going to be easy, but again that old Navy addage "No Pain, No Gain".

Here's another one that might come in handy... [http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)   Please let me know if you find anything that looks interesting also...  I have been reading so long that my eyes are 2 lava pools...

Thanks for the quik comeback, and even if I find a solution I am not sure how to do everything in Linux to be able to repair it...   Damn, I sure could use a manual, but here at the end of the world it takes forever to get anything and then it costs you your firstborn for the shipping

Ken

---

