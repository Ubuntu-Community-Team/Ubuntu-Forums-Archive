---
title: "Help!!!!no sound in my ubuntu 9.10!"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by stormsurge on 2009-12-05
Hey guys! I am a newbie in this site and with Ubuntu. I started to play with it and I really enjoy the benefits of being an Ubuntu (9.10) user. I only have one problem.... My Ubuntu does not play any audio, music, sound, alerts etc. My audio used to work perfectly not until I installed all the updates for Ubuntu. Can anyone help me?

---

### Post by Sir Jasper on 2009-12-05
Hi,

Have you checked your Volume Control to see if your sound is now muted?

My regards

---

### Post by stormsurge on 2009-12-05
Sir Jasper,

My sound is not muted in my Volume Control. Thanks!

---

### Post by LuisGMarine on 2009-12-05
Before I can help you I'm going to need some more information about your current hardware.

Open up a Terminal window by going to **Applications > Accessories > Terminal**

once the terminal window is up, type this command into the prompt and hit <enter> aftwerwards:

```
sudo lshw -C multimedia
```

paste the output of it.  Sorry that you are currently experiencing problems, hopefully we can go about fixing this =)

-xkill

---

### Post by stormsurge on 2009-12-05
Hi Luis!

Here is the output from my Terminal:

*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:d4340000-d4343fff

Thanks!

---

### Post by LuisGMarine on 2009-12-05
what is the output when you type this into a command prompt?

```
lsmod
```

Also run this command: restart your computer and let me know if you are still having the same issues.

```
sudo adduser $USER audio
```

---

### Post by stormsurge on 2009-12-05
Hi! After running lsmod, I got this from the terminal:

Module                  Size  Used by
usbhid                 38208  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
snd_hda_codec_si3054     4636  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  3 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
lib80211_crypt_tkip     8636  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
psmouse                56500  0 
serio_raw               5280  0 
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
usb_storage            52576  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
tg3                   109600  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

After this I will re-post what will happen after I run the next command you gave me. Thanks!

---

### Post by The_Pirate_King on 2009-12-05
I had a similar problem with Ubuntu Hardy.  It was fixed when I switched  to Karmic.  You could try installing an older version of Ubuntu, might clear things up...

---

### Post by Roger Allott on 2009-12-05
The complete loss os sound seems to be a common problem with karmic.

I had a nice stable jaunty until about a week or so ago. No sound issues at all.

Then I upgraded to karmic, and I lost my sound.

So I ran karmic from LiveUSB, and sound was there. So I decided to do a fresh install.

At first, I had sound, but then I ran Update Manager and ever since I've had no sound.

I've posted a plea for help on these forums, but thus far no assistance has been offered.

If anyone fancies heklping, here's my output of sudo lshw -C multimedia
```
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fc400000-fc403fff
```

---

### Post by muse3332 on 2009-12-05
hey, i have the same problem =[ im not a wiz

---

### Post by LuisGMarine on 2009-12-05
Who manufactures your guys computers?  If it's toshiba and dell try reading this thread and let me know if it helps you guys out.  

[http://ubuntuforums.org/showthread.php?t=845331]("http://ubuntuforums.org/showthread.php?t=845331")

Good Luck :popcorn:

---

### Post by Sir Jasper on 2009-12-05
Hi,

I am almost certain someone posted a common reason and a solution (though it may not apply in every 9.10 situation) within the last 24 hours or so.

Try the Search box at the top of this page using:

sound update

My regards

If no joy try some alternative keywords.

Added:

If the post immediately above this one does not help, then
try my suggestion.

---

### Post by alexfish on 2009-12-05
> **Roger Allott said:**
> The complete loss os sound seems to be a common problem with karmic.

I had a nice stable jaunty until about a week or so ago. No sound issues at all.

Then I upgraded to karmic, and I lost my sound.

So I ran karmic from LiveUSB, and sound was there. So I decided to do a fresh install.

At first, I had sound, but then I ran Update Manager and ever since I've had no sound.

I've posted a plea for help on these forums, but thus far no assistance has been offered.

If anyone fancies heklping, here's my output of sudo lshw -C multimedia
```
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fc400000-fc403fff
```
Hi 
try checking the kernels

  and post results here
try this 

[I]for sound output list for your card 
from the terminal

 aplay -l

[/I][I]maybe / check web to see if its " alsa compliant "
[/I]
[I] 
to check sound kernel

[/I][I]

modinfo soundcore[/I]

then 

uname -vr


  
check your system kernel /  menu     system /admin / system monitor
   click on the tab  system  /  check that they both match 

also look here
[https://help.ubuntu.com/community/So...otingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")



 sometimes pulse audio needs to be set up / and the speaker channels

    in the etc files  

pulseaudio device chooser helps with most of this  RE:
pavucontrol

---

### Post by Sir Jasper on 2009-12-05
Another good keyword may be kernel.

---

### Post by Taeyeon on 2009-12-05
Yeah, I have the same problem sometimes...
It will do that with most multimedia I find.
But after restarting it usually works fine?
I'd advise re-installing to be honest.

---

### Post by Roger Allott on 2009-12-05
> **alexfish said:**
> Hi 
try checking the kernels

  and post results here
try this 

[I]for sound output list for your card 
from the terminal

 aplay -l

[/I][I]maybe / check web to see if its " alsa compliant "
[/I]
[I] 
to check sound kernel

[/I][I]

modinfo soundcore[/I]

then 

uname -vr


  
check your system kernel /  menu     system /admin / system monitor
   click on the tab  system  /  check that they both match 

also look here
[https://help.ubuntu.com/community/So...otingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")



 sometimes pulse audio needs to be set up / and the speaker channels

    in the etc files  

pulseaudio device chooser helps with most of this  RE:
pavucontrol

The output from those commands:
```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
:~$ modinfo soundcore
filename:       /lib/modules/2.6.31-16-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 
```

```
:~$ uname -vr
2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009
```

---

### Post by l-x-l on 2009-12-05
I had the same prob after upgrading to the latest kernel. This fixed my problem. It may help you.

[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

Good luck.

---

### Post by Roger Allott on 2009-12-05
> **l-x-l said:**
> I had the same prob after upgrading to the latest kernel. This fixed my problem. It may help you.

[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

Good luck.

I've done all of that, but still no sound.

---

### Post by stormsurge on 2009-12-06
Still, I can't hear anything after running:

CODE
sudo adduser $USER audio

---

### Post by alexfish on 2009-12-06
> **Roger Allott said:**
> I've done all of that, but still no sound.

Hi there is a software modem

  there is a solve for this/ possible look here follow[  Bunnybugs]("http://ubuntuforums.org/member.php?u=945183")  I think,  but click on this link below

[http://ubuntuforums.org/showthread.php?t=1327449](http://ubuntuforums.org/showthread.php?t=1327449)

       
           then need to check permissions RE: pulseaudio

card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

also check this / it may help / don't know if it will work on your system

If you are using a dual boot system (even with Windows and Ubuntu installed on separate partitions), then make sure to set the sound volume in Windows to a high level before booting into Ubuntu. Also make sure to use the special function keys in Windows to make sure the loudspeakers are physically switched ON and working properly in Windows before installing and testing Ubuntu. This step is necessary with certain Toshiba Tecra laptops.  

also need to check these and post the results please

   from the terminal

cat /proc/asound/card*/codec* | grep Codec

then


sudo which alsactl

regards alex fish

---

### Post by iamgeniusrnti on 2009-12-06
> **The_Pirate_King said:**
> I had a similar problem with Ubuntu Hardy.  It was fixed when I switched  to Karmic.  You could try installing an older version of Ubuntu, might clear things up...

HAHAHA!  My sound used to work perfectly, then I upgraded to Karmic, received an update and lost my sound.

---

### Post by stormsurge on 2009-12-06
> **LuisGMarine said:**
> Who manufactures your guys computers?  If it's toshiba and dell try reading this thread and let me know if it helps you guys out.  

[http://ubuntuforums.org/showthread.php?t=845331](http://ubuntuforums.org/showthread.php?t=845331)

Good Luck :popcorn:
Luis,

Mine is Lenovo.

---

### Post by iamgeniusrnti on 2009-12-06
> **stormsurge said:**
> Still, I can't hear anything after running:

CODE
sudo adduser $USER audio

I just ran a search and discovered that never works HAHA for OUR particular problem.

---

### Post by iamgeniusrnti on 2009-12-06
> **l-x-l said:**
> I had the same prob after upgrading to the latest kernel. This fixed my problem. It may help you.

[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

Good luck.

Trying this now...

---

### Post by TimW2 on 2009-12-06
I have a similar story.

Finally junked by Pentium III Dell running Redhat and installed Ubuntu 9.10 64 bit on an Asus machine with an P5KPL-VM motherboard. The installation went well. Some recommended upgrades were installed. Everything works so far except for sound:

[LIST]
[*]System/Preferences/Sound just reports "Waiting for sound system to respond"
[/LIST]

[LIST]
[*]I check alsamixer and that appears to be ok.
[*]lshw -C multimedia reports:
[/LIST]
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:fea78000-fea7bfff

Any thoughts and help will be greatly appreciated.

TimW2

---

### Post by iamgeniusrnti on 2009-12-06
> **iamgeniusrnti said:**
> Trying this now...

OK, it worked!!! I clicked on the link and then clicked on the first link provded (or just click [here]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/") and it worked like a charm!!!  I have sound on alsa again!

BUT.. I am typing this on my Windows machine because my ath5k wireless driver took a crap... I have no wireless internet!!!!!!!!!!!!

WHY?!?!?!?!?!  What does the damn sound card have to do with the price of tea in China?!?!?!

I will start a new thread....

---

### Post by LuisGMarine on 2009-12-06
> **stormsurge said:**
> Hi Luis!

Here is the output from my Terminal:

*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:d4340000-d4343fff

Thanks!

Try this and see if it works:

Open up terminal and type this in:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

Add this line to the end of the file:
```
options snd-hda-intel model=6stack-dig
```

Save & Reboot.  Once the computer is back up right-click on the sound icon on your top panel, select "Sound Preferences."  In the hardware tab, select a profile with "surround" in it, or try all of the other ones to see which one gives you sound.

let me know if it works. :p

---

### Post by TimW2 on 2009-12-06
Before posting I should have read the basics. So it seems that the problem, very embarrassingly, was just that one or more of the inputs visible in AlsaMixer were muted i.e. the box under the slider was showing "MM".

So now the speakers are working despite not getting anything sensible from **System/Preferences/Sound**. I now need to get the microphone working. I have tried **Applications/Sound & Video/Sound Recorder** but that just tells me:

[COLOR=Red]Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu.[/COLOR]

Which would be fine if I could access the sound preferences.

TimW2

---

### Post by alexfish on 2009-12-06
> **TimW2 said:**
> Before posting I should have read the basics. So it seems that the problem, very embarrassingly, was just that one or more of the inputs visible in AlsaMixer were muted i.e. the box under the slider was showing "MM".

So now the speakers are working despite not getting anything sensible from **System/Preferences/Sound**. I now need to get the microphone working. I have tried **Applications/Sound & Video/Sound Recorder** but that just tells me:

[COLOR=Red]Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu.[/COLOR]

Which would be fine if I could access the sound preferences.

TimW2

Hi
if you are using pulseaudio as the server
have got 
pulseaudio device chooser installed / helps with most of this  RE:
pavucontrol 		                   		  		  		  		  		 		/ 			 				from synaptic

---

### Post by LuisGMarine on 2009-12-06
> **stormsurge said:**
> Luis,

Mine is Lenovo.

If that is the case try reading the guide, but when I say to change the thing to dell, just put lenovo and give it a try.  I think it comes out to snd_hda_intel=lenovo, or what ever the module name is just make sure you try it with lenovo.  Make sure you make a copy of your original files thought.

---

### Post by CylnZ on 2009-12-06
> **Roger Allott said:**
> The complete loss os sound seems to be a common problem with karmic.

I had a nice stable jaunty until about a week or so ago. No sound issues at all.

Then I upgraded to karmic, and I lost my sound.

So I ran karmic from LiveUSB, and sound was there. So I decided to do a fresh install.

At first, I had sound, but then I ran Update Manager and ever since I've had no sound.

I've posted a plea for help on these forums, but thus far no assistance has been offered.

If anyone fancies heklping, here's my output of sudo lshw -C multimedia
```
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fc400000-fc403fff
```

I had pretty much the same problems and have seen and posted in the same threads you did. I have the "(ICH8 Family) HD Audio Controller" in a gateway 6860fx. Even when I could get sound to work, in a couple days or hours or minutes POOF! itd be dead again. I found this thread earlier [http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse](http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse) followed the coded section (post #4) and I have system sound, good running video for the first time, and wine audio, and after choosing "alsa HDA 0.0" in mplayer I have sound everywhere with no stuttering or crackling.

It did cost me my hardware audio controls and panel mixer, but I replaced that with a link to gnomealsamixer on the panel, and I can live without buttons alot more than without audio and crap video as a trade. Hope this finally helps. If you read the whole thread I just pointed to I probably asked the same question you have been :)

good luck!

---

### Post by Roger Allott on 2009-12-06
> **CylnZ said:**
> I had pretty much the same problems and have seen and posted in the same threads you did. I have the "(ICH8 Family) HD Audio Controller" in a gateway 6860fx. Even when I could get sound to work, in a couple days or hours or minutes POOF! itd be dead again. I found this thread earlier [http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse](http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse) followed the coded section (post #4) and I have system sound, good running video for the first time, and wine audio, and after choosing "alsa HDA 0.0" in mplayer I have sound everywhere with no stuttering or crackling.

It did cost me my hardware audio controls and panel mixer, but I replaced that with a link to gnomealsamixer on the panel, and I can live without buttons alot more than without audio and crap video as a trade. Hope this finally helps. If you read the whole thread I just pointed to I probably asked the same question you have been :)

good luck!

Thanks for the link. I tried doing the command list in post #4 but got scared with step 1 when terminal told me that it was about to remove ubuntu-desktop, which I'd guess is quite an important package.

---

### Post by dr_gonzos on 2009-12-06
Hey I had the same problem in LinuxMint and Jaunty. What worked for me was heading into terminal and tying
 
sudo apt-get install gnome-alsamixer 
 
type in your password and wait for it to install. Once thats done go to Applications --> Sound&Video and find the Gnome Alsamixer. Mess with the setting in there. For me I had to unmute Center and that solved my issues. Best of luck! Also are you running an acer? I had a compatibility issue with the Intel soundcard. Fixable but not the first thing I would do.

---

### Post by alexfish on 2009-12-06
Hi

  tip

 I have posted some screen shots of the "pulse audio manager"

   most of what you can do from the terminal is available from the "pulse audio manager"

   This is available from the pulse audio device chooser

it is worth just browsing around it to see how good it is

also a good Desktop Tool for seeing your system
 and generating a report is the

System Profiler and BenchMark

 This can be installed from the Panel Menu / Applications  / Ubuntu Software Center / System Profiler and BenchMark

---

### Post by LuisGMarine on 2009-12-06
Follow this guide, I hope this can help you out.  I totally missed this guide, but it has somewhat the same steps I was trying to have you go through. 

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Best of luck

---

### Post by stormsurge on 2009-12-07
Guys,
 
Due to a very hectic schedule, I decided to re-install my Ubuntu 9.10. But I still hope that we could resolve this problem for the benefit of other users who may encounter this. Just for the record, I started to have my audio problem when I updated my Ubuntu. Thank you very much!

---

### Post by Roger Allott on 2009-12-07
> **LuisGMarine said:**
> Follow this guide, I hope this can help you out.  I totally missed this guide, but it has somewhat the same steps I was trying to have you go through. 

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Best of luck

Been through that, but I've still got no sound.

Because sound works fine (for most) on a fresh install, but then doesn't (for many) upon first update, it seems obvious that there is a problem with one (or more) of the packages that have been 'updated' since 28 October.

Is there any way of ascertaining what, if anything, Canonical is doing to identify and resolve the problem?

---

### Post by alexfish on 2009-12-07
> **Roger Allott said:**
> Been through that, but I've still got no sound.

Because sound works fine (for most) on a fresh install, but then doesn't (for many) upon first update, it seems obvious that there is a problem with one (or more) of the packages that have been 'updated' since 28 October.

Is there any way of ascertaining what, if anything, Canonical is doing to identify and resolve the problem?
                                  Hi  
 

  did you try the link from bunnybugs ,in previous post  
 [http://ubuntuforums.org/showthread.php?t=1346644&page=2](http://ubuntuforums.org/showthread.php?t=1346644&page=2)

  if your really stuck then vlc may throw some light
 

   on the situation  
 

    it has a message box in the tools
 

   when using increase the verbosity level  until you get the  messages
 

    then play the dvd
 

   the output can be saved in a file  
 

  don't always work  but worth a shot

---

### Post by Roger Allott on 2009-12-07
> **alexfish said:**
> Hi  
 

  did you try the link from bunnybugs ,in previous post  
 [http://ubuntuforums.org/showthread.php?t=1346644&page=2](http://ubuntuforums.org/showthread.php?t=1346644&page=2)

  if your really stuck then vlc may throw some light
 

   on the situation  
 

    it has a message box in the tools
 

   when using increase the verbosity level  until you get the  messages
 

    then play the dvd
 

   the output can be saved in a file  
 

  don't always work  but worth a shot

There wasn't a post from someone called 'bunnybugs' in the linked page that you provided.

And who is Vic????

---

### Post by Saprissa on 2009-12-07
> **LuisGMarine said:**
> Before I can help you I'm going to need some more information about your current hardware.

Open up a Terminal window by going to **Applications > Accessories > Terminal**

once the terminal window is up, type this command into the prompt and hit <enter> aftwerwards:

```
sudo lshw -C multimedia
```paste the output of it.  Sorry that you are currently experiencing problems, hopefully we can go about fixing this =)

-xkill

Having the same problem.  I get something strange.
> 
*-multimedia **UNCLAIMED**  
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 3
       bus info: pci@0000:04:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=4
       resources: ioport:9080(size=32) ioport:9000(size=128)

Any thoughts?

---

### Post by alexfish on 2009-12-07
> **Roger Allott said:**
> There wasn't a post from someone called 'bunnybugs' in the linked page that you provided.

And who is Vic????

here 

[http://ubuntuforums.org/showthread.php?t=1327449](http://ubuntuforums.org/showthread.php?t=1327449)


VLC

[http://www.videolan.org/](http://www.videolan.org/)

---

### Post by Saprissa on 2009-12-07
> **Saprissa said:**
> Having the same problem.  I get something strange.


Any thoughts?


My problem was a physical (or perhaps configuration) solved by removing the sound card, rebooting without it, shutting down and replacing the sound card and rebooting.

Thanks all.

---

### Post by Roger Allott on 2009-12-07
> **alexfish said:**
> here 

[http://ubuntuforums.org/showthread.php?t=1327449](http://ubuntuforums.org/showthread.php?t=1327449)
Ah, that's better!

So, the idea is that one should remove the software modem from Hardware Drivers. It's not that there's something wrong with the software modem, but apparently it's triggering a bug in pulseaudio.

Well, before I remove my software modem to give this solution a try, what is meant to be the purpose of the software modem? What (if anything) will I be losing in order to gain sound?



> **alexfish said:**
> VLC

[http://www.videolan.org/](http://www.videolan.org/)

Ah, VLC! Sorry, the L looked like an i in lower case.

---

### Post by alexfish on 2009-12-07
Hi Can't say but if you catch up on BunnyBugs ,He May have the Answers

to your problem on this one

---

### Post by Roger Allott on 2009-12-07
> **Roger Allott said:**
> Ah, that's better!

So, the idea is that one should remove the software modem from Hardware Drivers. It's not that there's something wrong with the software modem, but apparently it's triggering a bug in pulseaudio.

Well, before I remove my software modem to give this solution a try, what is meant to be the purpose of the software modem? What (if anything) will I be losing in order to gain sound?

It would appear that I lied, as I didn't wait for a response to my question but removed software modem from Hardware Drivers and rebooted.

And upon a reboot, ............

.......... I HAVE SOUND!!!!!!

---

### Post by alexfish on 2009-12-07
> **Roger Allott said:**
> It would appear that I lied, as I didn't wait for a response to my question but removed software modem from Hardware Drivers and rebooted.

And upon a reboot, ............

.......... I HAVE SOUND!!!!!!

Good luck

---

### Post by stormsurge on 2009-12-08
> **Roger Allott said:**
> It would appear that I lied, as I didn't wait for a response to my question but removed software modem from Hardware Drivers and rebooted.
 
And upon a reboot, ............
 
.......... I HAVE SOUND!!!!!!
 Hahahahaha! I tried this one also!!! It worked!!!!

---

### Post by xxclsxx on 2009-12-19
> **LuisGMarine said:**
> what is the output when you type this into a command prompt?

```
lsmod
```

Also run this command: restart your computer and let me know if you are still having the same issues.

```
sudo adduser $USER audio
```


Hi guys, I'm really new to ubuntu, got the same problem and have the same ICH7 audio device as the original post-er. Tried the above command (the sudo adduser $USER audio) as was suggested earlier and now my linux won't boot, it says something about a kernel panic. I have both windows vista and ubuntu on my computer, so am having to use windows for the moment. What can i do to undo what i did?

---

### Post by racer13fly on 2009-12-19
Yes, I have this same problem, too, in 9.10. Has this been reported yet?

---

### Post by airmertana on 2009-12-20
I'm having the same problems with the intel chipset and to get sound working I open a terminal and type sudo alsa force-reload

---

### Post by racer13fly on 2009-12-20
I'll try what you guys did up there.

---

### Post by jsland on 2009-12-20
Fresh install of 9.10 over Hardy had sound working right out of the box on a Soundblaster Audigy.

There are 3 potential sound sources on this machine. Motherboard, Soundblaster Audigy and HDMI output from the graphics card.

Motherboard is ASUS M2N-SLI Deluxe with AMD X2 64.

I started mucking with the machine to get digital sound output from the motherboard and lost all sound.

The following was first seen entering terminal

 $ aplay -l 

card 0 HDMI
card 1 CA0106

So the sound sources were recognized.

Sound was restored merely accessing from terminal

 $ alsamixer

The mixer showed the CA0106 (Audigy Source).  Toggling the settings for stereo and exiting was enough to restore sound.  The settings toggled seemed to make no difference, sound still worked.  After exiting alsamixer from terminal again

 $ aplay -l

now shows the Audigy is card 0 and HDMI source is card 1.  This is inverted from the original sequence and sound now works.  That simple.

Many thanks to the poster of this thread for helping me solve the problem here.

[http://www.shareconnector.com/no-sound-issue-sb-audigy-in-ubuntu-904](http://www.shareconnector.com/no-sound-issue-sb-audigy-in-ubuntu-904)

Before entering alsamixer in terminal I went through the following;

$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
$ sudo apt-get install linux-sound-base alsa-base alsa-utils

and because I run Gnome to restore all that was removed

$ sudo apt-get install gdm ubuntu-desktop

This erased whatever messy history may have been left behind due to earlier efforts and was intended to get the machine back to the clean install state without a brute force install of the entire OS.

Many posts about removing pulse audio and my first suspicion when seeing the output of $ aplay -l have me still thinking the key may not be so much getting rid of pulse audio but merely getting the source you want into the card 0 position at the top of the list.  (after making sure your machine has found or sees the sound sources and you have verified the mute on is not checked in alsamixer).

Maybe someone with a good deal more experience than I can elaborate and explain how to manipulate and reorder the card sequence numbers.

---

### Post by CylnZ on 2009-12-24
Well, after a month of no pulse, my system is running better than ever. I have sound everywhere, it's crisp and clean, i put the gnomealsamixer on my toolbar, and video plays 1080p perfectly. Sound never goes away and the system as a whole just works a lot smoother.

I did lose the ability to use simultaneous audio hardware. (I can live  with this sacrifice easily given the rewards of a working , useable system)

Alsa 1021 with as many alsa goodies as I could find in synaptic and Pulse totally locked out/killed/removed/kicked to the curb, is a happy thing :)

Merry Christmas !

---

### Post by eeeandrew on 2009-12-27
Hi guys! I come with a fix thats worked for me since ubuntu 7.04 for this particular card. Its simply adding a line to the alsa base configuration file.

Start off by opening terminal and typing:
> gksudo nautilus
to give you a browser with root privelages. The usual warning applies. You are working as root and can do severe damage to your system if you do something daft. You should NOT ordinarily work as root.

Next, use this browser, select the filesystem and navigate to etc/modprobe.d and open file alsa-base config. Scroll to the bottom of this file and add this line:
> options snd-hda-intel position_fix=1 model=3stack

This has worked for me to fix all sound problems to date without changing any other settings from default. 

Hope this helps!

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

