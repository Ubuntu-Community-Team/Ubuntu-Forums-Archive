---
title: "still no sound"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by papahonk on 2010-02-14
ok  im going to try here as well, this is the 2nd time i installed 9.10 on this box. neither time have i been able to here a thing. i know the speakers work i but them on the laptop. I had sound  with windows xp.  i did alot of reading  on the forums most of it was above my head  here is what i tried so far

System > admin>user and groups> made both root and user able to use pulse and pulse-access. it worked on the netbook with UNR so i thought  id give it a try

found link  searching forums to 

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

followed this to 

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

followed these intructions nothing changed

 followed steps on trouble shooting and  i posted this like it instructed 

                                                                       **no sound ubuntu 9.10**

               
[LIST=1]
[*]     [       Ubuntu            ]("https://launchpad.net/ubuntu")
[*]     [       Questions            ]("https://answers.launchpad.net/ubuntu")
[*]     [              Question #101113     ]("https://answers.launchpad.net/ubuntu/+question/101113")
[/LIST]
              
                            tried to follow instructions  on [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) says to  post output here.
 naker@honaker-desktop:~$ bash alsa-info.sh --pastebin
ALSA Information Script v 0.4.58
--------------------------------
 This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.
   dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)
 See 'alsa-info.sh --help' for command line options.
 Automatically upload ALSA information to pastebin? [y/N] : y
Uploading information to [www.pastebin.ca]("http://www.pastebin.ca") ...  Done!
 Your ALSA information is located at [http://pastebin.ca/1796776](http://pastebin.ca/1796776)
 Please inform the person helping you.
 honaker@honaker-desktop:~$
 any help is greatly appreciated, still very new to linux and slowly trying to learn how to use the terminal.


had one post said ot  make sure sound card was able to use Alsa  and it was listed

honaker@honaker-desktop:~$ sudo lshw -C multimedia
[sudo] password for honaker: 
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
       resources: irq:22 ioport:f000(size=256) ioport:ec00(size=256) memory:febfd000-febfdfff
honaker@honaker-desktop:~$ 

 looked up  nvidia ck804 compatibility with alsa and i found many links with running with the right kernal cant remember command to get kernal but they posted it and i had right one

somewhere some one asked for this 

honaker@honaker-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30104  4 
snd_ac97_codec        101536  1 snd_intel8x0
ac97_bus                1596  1 snd_ac97_codec
snd_pcm_oss            37472  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_pcm                76480  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29216  0 
snd_seq_midi            6656  0 
snd_rawmidi            22336  1 snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  3 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    61188  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
psmouse                56500  0 
serio_raw               5280  0 
k8temp                  4188  0 
soundcore               7264  1 snd
snd_page_alloc          9124  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               7089800  34 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
e1000                 119264  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
floppy                 54916  0 
forcedeth              54152  0 
honaker@honaker-desktop:~$ 


right now im just listting every thing i can think of that i seen others  ask for  in hopes that all these jumbled numbers  make since to someone. ill check tomorrow evening as my eyes hurt from all the reading 
Thanks for any help 

Mike

---

### Post by Eredeath on 2010-02-14
have you tried going into the terminal and typing
```
alsamixer -V all
```
and making sure that your speakers are enabled and not muted?

---

### Post by lidex on 2010-02-14
> **Eredeath said:**
> have you tried going into the terminal and typing
```
alsamixer -V all
```
and making sure that your speakers are enabled and not muted?

Yes, do that.
If it doesn't help post the output of this command in a terminal:
```
head -n 1 /proc/asound/card0/codec*
```

---

### Post by papahonk on 2010-02-15
ok i used  alsa mixer control in terminal only one im worried about it says Master mono i turned it up but the numbers at the bottom still say MM isnt that muted how do i unmute  and is it the problem?

---

### Post by papahonk on 2010-02-15
honaker@honaker-desktop:~$ head -n 1 /proc/asound/card0/codec*
head: error reading `/proc/asound/card0/codec97#0': Is a directory
honaker@honaker-desktop:~$

---

### Post by mhgsys on 2010-02-15
Kindly try this;


open a terminal; typ

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

change the line

```
options snd-hda-intel power_save=10 power_save_controller=N
```

into

```
options snd-hda-intel power_save=0 power_save_controller=N
```




[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/442463](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/442463)

---

### Post by lidex on 2010-02-15
> **papahonk said:**
> ok i used  alsa mixer control in terminal only one im worried about it says Master mono i turned it up but the numbers at the bottom still say MM isnt that muted how do i unmute  and is it the problem?

Not sure what that indicates - mine doesn't have it, just 0 at the bottom and 100 at the top. Try the gnome version. In an Alt+F2 run dialog enter:
```
gnome-alsamixer
```
click run.

Go to the "Edit" menu to configure listed elements.

---

### Post by lidex on 2010-02-15
Can you post the output of these commands please:
```
cat /proc/asound/card*/codec* | grep Codec
```
```
sudo which alsactl
```

---

### Post by papahonk on 2010-02-15
Mhgsys  did it and restarted  didnt do anything went back  into terminal to make sure i did get it saved and it was still set at 0

lidex    posted yours  mixer came up  lists master then master M.... Master M is always checked. i have unchecked it many times now is that the same as the master mono in the terminal control that i had listed as MM ? 

 went into  Edit> sound card properties... every thing is checked

 then  Edit > program preferences... sound card Realtek ALC850 rev 0 is checked... i doubt the slider preference matter much

---

### Post by papahonk on 2010-02-15
Lidex  here is the out put  from both. i cut and pasted  them  what did i do wrong?


honaker@honaker-desktop:~$ cat /proc/asound/card*/codec* | grep Codec
cat: /proc/asound/card0/codec97#0: Is a directory
honaker@honaker-desktop:~$ sudo which alsactl
/usr/sbin/alsactl
honaker@honaker-desktop:~$

---

### Post by papahonk on 2010-02-15
every time i restart computer and use  nome-alsamixer
 the Master Mono is checked  mute how do i get it to stay unchecked

---

### Post by etherealknight on 2010-02-15
I also do not have sound on my HP Pavillion dv6119us laptop.. can anyone help me out?

---

### Post by papahonk on 2010-02-16
bump... please dont forget me... lol  still no sound

---

### Post by lidex on 2010-02-16
Try this:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line to the bottom of the file:
```
options snd-intel8x0 ac97_quirk=3
```

Oh yeah, while you're in there comment out this line (put a # in front of it):
```
snd-hda-intel: power_save=10 power_save_controller=N
```

Save file, close, **[SIZE="4"]reboot[/SIZE]**

---

### Post by papahonk on 2010-02-16
no luck so i thought id reopen  and post it here.. maybe i did something wrong


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=0 power_save_controller=N
options snd-intel8x0 ac97_quirk=3

---

### Post by papahonk on 2010-02-16
just noticed that you had

#options snd-hda-intel power_save=10 power_save_controller=N 

with a 10  on the power save some one earlier  had me change it to 0  so i just went back in and changed it back to 10  and rebooted.. still no sound just so you know why its at  0 in the above post

---

### Post by papahonk on 2010-02-16
how are you guys getting the code in the boxes?

---

### Post by lidex on 2010-02-17
You got it right. Try adding this line as well to alsa-base.conf:
```
alias snd-card-0 snd-intel8x0

``` make sure you reboot.

> how are you guys getting the code in the boxes? 

Code tags. The # in the toolbar. Either click it and paste text - the cursor will be between tags already - or highlight text, then click on #

---

### Post by lidex on 2010-02-17
What is the make and model of your laptop?
Run these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Reboot. Go into bios and make sure onboard audio is enabled (it happens). Click on the pulseaudio link in my sig. Follow that howto.
Make sure your hardware volume is up/not muted - no orange lights.
Do you have nvidia graphics and if so, what driver version are you using?

---

### Post by onmyown on 2010-02-17
I installed 9.10 and had no sound. Sound Blaster Audigy 2 card. None of the Pulse Audio software helped restore sound but the Pulse Audio Volume Control indicated there was output which led me to believe the card was functioning but the audio just wasn't geting to the speakers. Google led me to [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and the first option was Alt+F2 and type gnome-volume-control in the run app window. This installed the GNOME ALSA Mixer. I cranked up all of the faders and  checked the box for audigy analog/digital output jack and there was SOUND!!! I  had to adjust some settings but it worked. It took about 8 hours to get to this point. I did try some trouble shooting suggestions with the terminal but only succeeded in breaking Rhythmbox and had to reinstall it. This of course also gave me audio in Firefox flash videos which was another story. Don't download flash and try to install. Go to a web page and install when prompted. Ease of use is not a problem in Ubuntu ease of set up is.

---

### Post by papahonk on 2010-02-17
added the code like you asked. in Bios  intergrated peripherals  the AC97 audio is on auto. it only gave me auto or disable. that was the only referance to sound i could find.  

 this is the desktop im working on  its a older amd  and i would have to open the box to get you the MoBo numbers  i cant remember off hand. ill have to do it after class today  running short on time this morning.


Thanks

---

