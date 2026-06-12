---
title: "No Sound At All"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by lanetherif on 2010-03-31
While I was dealing with Alsa and Pulseaudio, I messed up things so much  that there is no sound now and I have not a clue of steps I have taken  (I am sort of a toddler playing with a gun -as if existence of my whole  data on PC is not dependent to what I am doing :P ).

Is there a way to remove all sound related packages -or a list to guide  me in doing this and a way to re-install all anew?

Thanks. :)

---

### Post by lanetherif on 2010-03-31
Nevermind... I've fixed it.

---

### Post by edanto on 2010-03-31
pssst I've done the same thing!  

I started out with working sound, and was trying to get my mic working.  Then did an uninstall and reinstall of a sound package (but I'm rather clueless)... and now I got nuttin'!

Any idea how I can troubleshoot and fix, please? What did you do?

---

### Post by Chris Edgell on 2010-03-31
Hi, edanto,

I have just spent quite a bit of time talking to Sentoguy about sound...don't make me type that all again to you.

Please go and read that thread then after you have gone through my posts, get back to me here and tell me how it went, and where you're at, okay?

Till then

Good luck
Chris

GO to:  [http://ubuntuforums.org/showthread.php?t=1440711](http://ubuntuforums.org/showthread.php?t=1440711)

---

### Post by edanto on 2010-04-02
Hi Chris,

Thanks for the link.  I have gone through the steps, but I'm afraid I'm not sure of what I'm doing at all!

Symptoms - when I go to System/Preferences/Sound , nothing happens and then I get a 'Waiting for sound system to respond' error message which I eventually 'Cancel' to get it off the screen.

But the speakers are working, when Ubuntu is opening after being restarted, I get those drum beats fine.

So, I'm pretty sure it's something that I've done to the system in my blind tinkering!

I tried to get Synaptic working, but when it starts up it says that it's running without administrator privileges... not entirely sure how to start it in the right way.

I'm that much of a novice!

---

### Post by ibuclaw on 2010-04-02
If you switch to guest account, does everything work fine?

---

### Post by edanto on 2010-04-02
Nope, in Guest account I also got the drums as the account opened, but when I started to play an mp3 there was no sound.  

The volume buttons on my computer don't have any effect at all (previously a window popped up on screen to show the volume adjusting), so I reckon I've gone and killed that important bit somehow.

Thanks for the quick response. I'm afraid I have to leave home now, but I'll return to this tomorrow.

---

### Post by lidex on 2010-04-02
Can you provide some info to help in diagnosis?
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by edanto on 2010-04-03
I've downloaded that file, and saved it in the folder which has my name.  The same folder also contains Documents, Downloads etc.

But when I run that command in a terminal it says 

bash: utils_alsa-info.sh: No such file or directory

.. even though in the directory where alsa-info.download is saved I can see a file called alsa-info.sh

Have I saved the file in the right directory?

---

### Post by ibuclaw on 2010-04-03
1) ensure it is there:
```
ls ~/utils_alsa-info.sh
```
2) mark it executable
```
chmod +x ~/utils_alsa-info.sh
```
3) run it
```
sudo ~/utils_alsa-info.sh
```

Regards
Iain

---

### Post by edanto on 2010-04-11
It's a bit embarassing, but I can't get past step 1! It says the file isn't there.

I'm a complete beginner in Ubuntu and I think I don't understand what's meant by "*"save as" to your user folder*"

Do you mean to save it in "/home/edanto"

Or somewhere in /usr ?

(apologies for the basic, basic questions!)

---

### Post by lidex on 2010-04-11
> **edanto said:**
> It's a bit embarassing, but I can't get past step 1! It says the file isn't there.

I'm a complete beginner in Ubuntu and I think I don't understand what's meant by "*"save as" to your user folder*"

Do you mean to save it in "/home/edanto"


(apologies for the basic, basic questions!)


Yes.

---

### Post by edanto on 2010-05-07
> **lidex said:**
> Can you provide some info to help in diagnosis?
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

Dammit I just can't get this basic thing right!

```
eoin@eoin-laptop:~$ ls
alsa-info.download  Documents  examples.desktop  Pictures   Videos
alsa-info.sh        Downloads  from old laptop   Public
Desktop             Dropbox    Music             Templates
eoin@eoin-laptop:~$ chmod +x alsa-info.sh
eoin@eoin-laptop:~$ sudo bash utils_alsa-info.sh
bash: utils_alsa-info.sh: No such file or directory
eoin@eoin-laptop:~$ ls
alsa-info.download  Documents  examples.desktop  Pictures   Videos
alsa-info.sh        Downloads  from old laptop   Public
Desktop             Dropbox    Music             Templates
eoin@eoin-laptop:~$ sudo bash utils_alsa-info.sh
bash: utils_alsa-info.sh: No such file or directory
eoin@eoin-laptop:~$ 

```

Above is what I get when I try to use the command - it says the file isn't there.  It took me a few weeks to figure out the whole 'making a file executable' thing - I don't even deserve the name newb.

In the meantime, a friend has had a look at the computer and did, briefly, get the sound back running.  

Unfortunately now there is a persistent whining sound (sounds like low level feedback), so I have to have it muted!

I thought running the script would help me diagnose this new problem, but as you can see from the extract above, I can't even do that!

I doubt there is a typo in what you've written, but I can't for the life of me figure out what I should be doing differently to follow your instructions. Thanks for your patience!

ps upgraded to 10.04, still have buzzing sound

---

### Post by lidex on 2010-05-08
You somehow edited the filename. Try this:
```
sudo bash alsa-info.sh 
```

---

### Post by edanto on 2010-05-08
[IMG]http://www.cksinfo.com/clipart/signssymbols/smileys/set1/smiley-embarrassed.png[/IMG]

[http://www.alsa-project.org/db/?f=b1ea30a388eec03d22a7cfdb85dd22fcc8731614](http://www.alsa-project.org/db/?f=b1ea30a388eec03d22a7cfdb85dd22fcc8731614)


```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat May  8 08:29:32 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Compaq nc6120 (PY505ET#ABU)


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 103c:099c


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x103c
PCI Subsys Device: 0x099c

Flags: 10
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 0e0e
0:04 = 0e0e
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 0008
0:0e = 000b
0:10 = 0202
0:12 = 0606
0:14 = 0000
0:16 = 0808
0:18 = 0808
0:1a = 0000
0:1c = 0303
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0031
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 180c
0:74 = 1001
0:76 = 2050
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 May  7 22:24 /dev/snd/controlC0
crw-rw----  1 root audio 116,  9 May  7 22:38 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  8 May  8 09:28 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  7 May  7 22:24 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  6 May  7 22:24 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  5 May  7 22:24 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116,  4 May  7 22:24 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116,  3 May  7 22:24 /dev/snd/seq
crw-rw----  1 root audio 116,  2 May  7 22:24 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  7 22:24 .
drwxr-xr-x 3 root root 240 May  7 22:24 ..
lrwxrwxrwx 1 root root  12 May  7 22:24 pci-0000:00:1e.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1981B at irq 21'
  Mixer name	: 'Analog Devices AD1981B'
  Components	: 'AC97a:41445374'
  Controls      : 25
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 29 [94%] [9.00dB] [on] Capture [off]
  Front Right: Playback 29 [94%] [9.00dB] [on] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-4.50dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 3 [20%] [4.50dB] [on]
  Front Right: Capture 3 [20%] [4.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 17
		value.1 17
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 23
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 20
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 29
		value.1 29
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 true
		value.1 true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 23
		value.1 23
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 23
		value.1 23
	}
	control.20 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 3
		value.1 3
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Stereo Mic'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value true
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
binfmt_misc
michael_mic
arc4
lib80211_crypt_tkip
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
ipt_addrtype
xt_state
rfcomm
sco
ip6table_filter
fbcon
tileblit
font
bitblit
softcursor
ip6_tables
vga16fb
bridge
stp
snd_intel8x0
vgastate
bnep
snd_ac97_codec
nf_nat_irc
nf_conntrack_irc
l2cap
ac97_bus
nf_nat_ftp
snd_pcm_oss
snd_mixer_oss
nf_nat
nf_conntrack_ipv4
snd_pcm
joydev
i915
snd_seq_dummy
nf_defrag_ipv4
snd_seq_oss
nf_conntrack_ftp
drm_kms_helper
nf_conntrack
snd_seq_midi
drm
snd_rawmidi
snd_seq_midi_event
snd_seq
intel_agp
iptable_filter
i2c_algo_bit
psmouse
snd_timer
tifm_7xx1
pcmcia
serio_raw
video
agpgart
ipw2200
snd_seq_device
irda
sdhci_pci
libipw
yenta_socket
rsrc_nonstatic
tifm_core
sdhci
ppdev
led_class
ip_tables
lp
snd
output
pcmcia_core
parport_pc
soundcore
x_tables
parport
crc_ccitt
btusb
snd_page_alloc
lib80211
bluetooth
ohci1394
tg3
ieee1394


!!ALSA/HDA dmesg
!!------------------



```

Thanks lidex.

Since my problem is now related to a 'humming' sound, the discussion can move to that thread. [http://ubuntuforums.org/showthread.php?t=1396390](http://ubuntuforums.org/showthread.php?t=1396390)  thx

---

### Post by lidex on 2010-05-08
You have mismatched driver versions. I would suggest using the alsa-upgrade-script link in my sig to fix that.

---

### Post by edanto on 2010-05-08
Thanks, I'm reading through that thread now. The instructions are clear in it, I think I'll be able to do it (once I figure out how to backup whatever I should).

Many thanks for the advice.

---

