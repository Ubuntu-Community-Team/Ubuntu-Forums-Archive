---
title: "No sound on my Dell Vostro 1500"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by Edward in CT on 2010-08-13
I love Ubuntu, but I can't get sound on my Dell Vostro 1500.  I am a new Ubuntu user and not very technical.  I have little experience doing any programming, but I can usually follow instructions.   I can't imagine I'm the only guy who has experienced this problem and would really appreciate any help.  Thanks in advance.

---

### Post by jtarin on 2010-08-13
Time for some terminal work.....```
lspci
```This should give you your sound card/chip type. List here.
```
lsmod | grep snd 
```this is too determine what modules are loaded for sound.

---

### Post by Edward in CT on 2010-08-13
Thanks.

After typing  lspci, I got a list of devices.  The audio one was: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

After the second command I got this:
orestes@orestes-laptop:~$ lsmod | grep snd
snd_hda_codec_idt      51978  1 
snd_hda_intel          21941  1 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm

I'm sorry but I haven't a clue what any of this means.

---

### Post by jtarin on 2010-08-13
Some [documentation here]("https://help.ubuntu.com/community/SoundTroubleshooting") to try first.

In case it did not help you may wanna try the following steps :

    * sudo apt-get install module-assistant
    * sudo m-a update
    * sudo m-a prepare
    * sudo m-a a-i alsa


That's it, reboot the system and I hope it's fixed so you can play music or use your skype and things like that.

---

### Post by Edward in CT on 2010-08-13
tried that, but no luck.  I looked through the documentation and I think my card is being recognized, but I still can't get it to work.  Thanks for your help anyway.

---

### Post by jtarin on 2010-08-13
> **Edward in CT said:**
> tried that, but no luck.  I looked through the documentation and I think my card is being recognized, but I still can't get it to work.  Thanks for your help anyway.
The best way is still the terminal-based alsamixer.```
sudo alsamixer
```Check that all settings are on.

[Extra documentation help.]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by lidex on 2010-08-13
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Edward in CT on 2010-08-14
OK  here it is....


orestes@orestes-laptop:~$ uname -a
Linux orestes-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
orestes@orestes-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
orestes@orestes-laptop:~$ dpkg -l grep "alsa"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  alsa           <none>         (no description available)
ii  grep           2.5.4-4build1  GNU grep, egrep and fgrep
orestes@orestes-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9205

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06
orestes@orestes-laptop:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'[   22.548935] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   23.271703] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   23.271807]   alloc irq_desc for 29 on node -1
[   23.271811]   alloc kstat_irqs on node -1
[   23.271826] HDA Intel 0000:00:1b.0: irq 29 for MSI/MSI-X
[   23.271866] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.368593] ppdev: user-space parallel port driver
[   23.547941] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   23.568438] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   23.568533] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   25.837375] b44: eth0: Link is up at 100 Mbps, full duplex.
orestes@orestes-laptop:~$ 


Thanks.

Ed

---

### Post by Edward in CT on 2010-08-14
PC Laptop make is Dell, Model is Vostro 1500

---

### Post by lidex on 2010-08-14
Please copy & paste this command into terminal and post results:
```
dpkg -l | grep "alsa"

```

Now try this: Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel enable_msi=0 model=eapd 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by Edward in CT on 2010-08-14
Here is the results of the first command:


orestes@orestes-laptop:~$ dpkg -l |grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-modules-2.6.32-24-generic        1.0.22.1+dfsg-0ubuntu3+2.6.32-24.39             ALSA modules for kernel 2.6.32-24-generic
ii  alsa-source                           1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library

I opened the file and inserted the line of code at the bottom.  I'll reboot now and let you know if it works.  Thanks again for all your help.

---

### Post by Edward in CT on 2010-08-14
It worked perfectly!!!!!!
Speakers and headphones are perfect!!!
Thanks so much.  You are awesome!!!!
Gosh, I wish I was able to program like you guys can!!!  But having this forum is a reasonable substitute!!!

Thanks to all for the help.

---

### Post by lidex on 2010-08-14
Not a problem. Enjoy. 
Please mark the thread solved using 'Thread Tools' up top.

---

