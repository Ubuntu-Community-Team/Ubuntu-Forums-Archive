---
title: "No sound with 910 - any ideas what next?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-03
Hi I just installed 910 on a new out of the box laptop. No sound. By the sounds of it I am not the only person with this issue. Can anyone suggest what I ought to do next? Or at least a good tutorial.

Thanks in advance

---

### Post by sad_iq on 2010-01-03
Start by posting the laptop model, if you made sure the volume is turned up, and paste from the terminal the output of:
 ```
lspci | grep Audio
```
```
lsmod | grep snd*
```
```
aplay -l
```

---

### Post by listerdl on 2010-01-03
> **sad_iq said:**
> Start by posting the laptop model, if you made sure the volume is turned up, and paste from the terminal the output of:
 ```
lspci | grep Audio
```

This was: 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```
lsmod | grep snd*
```

This was: snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_analog    59292  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```
aplay -l

This was: **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So I guess that there is good news in that ubuntu recongises the drivers but why no sound? I have checked for mute, (via preference and cant seem to find anything to indciate mute..)

Any help is GREATLY appreciated!

Thanks

---

### Post by robertcoulson on 2010-01-03
Hi....I installed 9.10 also (I am not a computer genius) but I noticed my speaker icon on the top right hand part of my top bar was set to MUTE...Maybe, just maybe.
Bob

---

### Post by listerdl on 2010-01-03
> **robertcoulson said:**
> Hi....I installed 9.10 also (I am not a computer genius) but I noticed my speaker icon on the top right hand part of my top bar was set to MUTE...Maybe, just maybe.
Bob

Hey Bob

Yeah, I know what your saying....no joy....

To be honest the only problem I have with ubuntu is the sound issue....there often is a sound problem but thats ok!

Wish i could fix it though!

---

### Post by robertcoulson on 2010-01-03
Ya...Hope some one smarter than me out there can jump in and help you...That is very annoying...
Bob

---

### Post by k64 on 2010-01-03
Interestingly enough, my Realtek HD Audio Device was recognized - and also used PERFECTLY by Ubuntu 9.10 - right out of the box.

---

### Post by listerdl on 2010-01-03
Its not that I am not checking the mute functions somewhere else? I checked the preferences > sounds > and there seems no muted action.

can you think of somewhere else that it might be muted?

THANKS!

---

### Post by Marrkk on 2010-01-03
this is probably a known bug in pulseaudio .. 
thats one of the reasons i use KDE..
Linux audio is going through a weird phase  at the moment IMO.
Pulseaudio is, for many people, broken in Ubuntu .. even the pulseaudio developer said he doesnt like the way Ubuntu shipped with pulseaudio broken.
 - and of course, some people have no probs, 

Some, like me, hate pulseaudio.
Kubuntu 9.10 is much prettier and has no pulseaudio really. but some folks have a similar prob. but not as bad. Xubuntu has no trace of pulseaudio at all, and is sweet.. if you like XFCE.

---

### Post by listerdl on 2010-01-03
> **Marrkk said:**
> this is probably a known bug in pulseaudio .. 
thats one of the reasons i use KDE..
Linux audio is going through a weird phase  at the moment IMO.
Pulseaudio is, for many people, broken in Ubuntu .. even the pulseaudio developer said he doesnt like the way Ubuntu shipped with pulseaudio broken.
 - and of course, some people have no probs, 

Some, like me, hate pulseaudio.
Kubuntu 9.10 is much prettier and has no pulseaudio really. but some folks have a similar prob. but not as bad. Xubuntu has no trace of pulseaudio at all, and is sweet.. if you like XFCE.

So basically I cant have sound :( that is a bummer.

Is there any way around this?

Should I even consider re-installing an earlier version say 8.04 or 8.10?

Thanks.....

---

### Post by sad_iq on 2010-01-05
> **listerdl said:**
> Its not that I am not checking the mute functions somewhere else? I checked the preferences > sounds > and there seems no muted action.

can you think of somewhere else that it might be muted?



Try **alsamixer**  in a terminal and see if there's anything muted.maybe PCM controls the sound level..also..what laptop model do you have?
 Any messages about sound in **/var/log/messages**. try to run rhythmbox from the terminal and see if it prints some error messages.
Also could you paste the output of ```
cat /proc/asound/card0/codec#* | grep Codec
```
 You could even install **paman** and check some info about your hardware.
 If I remember correctly there are(were) some bugs with your card's driver, so switching from Gnome to KDE/Xfce didn't always solve the problem.
 Some ppl reported that adding the folowing 3 lines at the end of **/etc/modprobe.d/alsa-base.conf**(gksu gedit /etc/modprobe.d/alsa-base.conf) work (after a reboot!): ```
alias snd-card-0 snd-hda-intel
options snd slots=snd-hda-intel
options snd-hda-intel model=auto

```

---

### Post by listerdl on 2010-01-08
> **sad_iq said:**
> Try **alsamixer**  in a terminal and see if there's anything muted.maybe PCM controls the sound level..also..what laptop model do you have? [COLOR="Red"]* It is a Panasonic CF F8, also known as a Toughbook...[/COLOR]
 Any messages about sound in **/var/log/messages**. try to run rhythmbox from the terminal and see if it prints some error messages. [COLOR="Red"]* Rhythmbox seems to be working fine, no error reports[/COLOR]
Also could you paste the output of ```
cat /proc/asound/card0/codec#* | grep Codec [COLOR="Red"]* This is Codec: Analog Devices AD1883
Codec: Intel G45 DEVCTG[/COLOR]

```
 You could even install **paman** and check some info about your hardware. [COLOR="Red"]* Havent done that, will it still help?[/COLOR]
 If I remember correctly there are(were) some bugs with your card's driver, so switching from Gnome to KDE/Xfce didn't always solve the problem.
 Some ppl reported that adding the folowing 3 lines at the end of **/etc/modprobe.d/alsa-base.conf [COLOR="Red"]* hhhmm I tried that code in terminal and permission denied, even when I tried the sudo command. Should I be accessing this via terminal? [/COLOR]**(gksu gedit /etc/modprobe.d/alsa-base.conf) work (after a reboot!): ```
alias snd-card-0 snd-hda-intel
options snd slots=snd-hda-intel
options snd-hda-intel model=auto

```

[COLOR="Red"]Thanks guys - all help very much appreciated. I have a dual boot going but I find myself in windows for a lot of the time, not out of choice just b/c it works with sound!!

Thanks![/COLOR]

--------- UPDATE

having googled my soundcard and hardware I discovered that someone made this fix....

"I have a [sound] problem with openSUSE 11.1 installation on HP 2230s laptop - 

My laptop soundcard is Intel 82801I (ICH9 Family), this is the "lspci | grep Audio" result

    slowhand:/home/medwinz # lspci | grep Audio
    00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)  

This is the workaround and the steps I took:

    cat /proc/asound/card0/codec#* | grep Codec
    the result of mine
       Codec: Analog Devices AD1984A
       Codec: LSI ID 1040
       Codec: Intel G45 DEVCTG

checking through less /usr/src/linux-2.6.27.7-9/Documentation/sound/alsa/ALSA-Configuration.txt, I found out some entries for AD1984A

    AD1884A / AD1883 / AD1984A / AD1984B
             desktop       3-stack desktop (default)
             laptop          laptop with HP jack sensing
             mobile         mobile devices with HP jack sensing
             thinkpad      Lenovo Thinkpad X300
    AD1984
             basic          default configuration
             thinkpad      Lenovo Thinkpad T61/X61
             dell             Dell T3400

Then I modified /etc/modprobe.d/sound become:

    options snd slots=snd-hda-intel
    options snd-hda-intel model=laptop  &#8212;> this is I added, coz alsa seems confused
    # u1Nb.s7WKievqWt5:82801I (ICH9 Family) HD Audio Controller
    alias snd-card-0 snd-hda-intel
    alias sound-slot-0 snd-hda-intel

--------------- 

So, my question is, how do I edit and find the /usr/src/linux-2.6.27.7-9/Documentation/sound/alsa/ALSA-Configuration.txt, AND the /etc/modprobe.d/sound - ?

I guess that my folders are different...

Basically the long and short of it is that my soundcard seems to be the unlucky buggy one with sound and 910 ubuntu...

Any ideas gratefully received!!!!!!!!

---

### Post by sad_iq on 2010-01-08
In Ubuntu there is no /etc/modprobe.d/sound , you have to edit /etc/modprobe.d/alsa-base.conf:
Type this in a terminal: ```
gksu gedit /etc/modprobe.d/alsa-base.conf
``` You will be asked for your password, and you can add the lines at the end of the file that opens.

---

### Post by listerdl on 2010-01-09
Alas that didnt work which is a shame...

Have I run out of options?

I guess I have to install an earlier less buddy version of ubuntu - thats a real shame though, it would have been better to have the latest version...

Thanks

---

### Post by sad_iq on 2010-01-09
> **listerdl said:**
> 
Have I run out of options?


Not yet...let's try some more things :)
 Open a terminal, type in it ```
sudo apt-get install gnome-alsamixer
``` and when it finishes installing go to Applications -> Sound & Video -> Gnome Alsa Mixer. **make sure there is nothing muted or on low volume** and try to play some music.
 If that still doesn't work you can still try to edit (if you didn't do it already) /etc/modprobe.d/alsa-base.conf : ```
gksu gedit /etc/modprobe.d/alsa-base.conf
``` and add at the end of it : ```
alias snd-card-0 snd-hda-intel
options snd slots=snd-hda-intel
options snd-hda-intel model=[COLOR="Red"]auto[/COLOR]
``` 
Save the file, REBOOT, and see it works. If not re-edit that file and replace [COLOR="Red"]auto[/COLOR] with one of the folowing : [COLOR="Red"]desktop[/COLOR] or [COLOR="Red"]laptop[/COLOR] or [COLOR="Red"]mobile[/COLOR]  or [COLOR="Red"]thinkpad[/COLOR] (taken from [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=blob_plain;f=Documentation/sound/alsa/ALSA-Configuration.txt](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=blob_plain;f=Documentation/sound/alsa/ALSA-Configuration.txt)). Remember to reboot each time you edit that file (many ppl complained that only a reboot works so it's best to play it safe).

 If all that doesn't work read this howto: [http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137") and if that doesn't work...I'm clueless for now. :(

---

### Post by listerdl on 2010-01-10
I tried everything - and no joy....

The last option was sort of interesting though...

I edited ```
gksu gedit /etc/modprobe.d/alsa-base.conf
``` and added at the end of it : ```
alias snd-card-0 snd-hda-intel
options snd slots=snd-hda-intel
options snd-hda-intel model=[COLOR="Red"]auto[/COLOR]
``` 

and replaced with the [COLOR="Red"]auto[/COLOR] with either : [COLOR="Red"]desktop[/COLOR] or [COLOR="Red"]laptop[/COLOR] or [COLOR="Red"]mobile[/COLOR]  or [COLOR="Red"]thinkpad[/COLOR] (taken from [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=blob_plain;f=Documentation/sound/alsa/ALSA-Configuration.txt](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=blob_plain;f=Documentation/sound/alsa/ALSA-Configuration.txt)).  

And nothing happened - BUT - if I look the above link I note that my laptop is almost exactly mentioned....

[COLOR="Red"]STAC9200[/COLOR]
	  ref		Reference board
	  dell-d21	Dell (unknown)
	  dell-d22	Dell (unknown)
	  dell-d23	Dell (unknown)
	  dell-m21	Dell Inspiron 630m, Dell Inspiron 640m
	  dell-m22	Dell Latitude D620, Dell Latitude D820
	  dell-m23	Dell XPS M1710, Dell Precision M90
	  dell-m24	Dell Latitude 120L
	  dell-m25	Dell Inspiron E1505n
	  dell-m26	Dell Inspiron 1501
	  dell-m27	Dell Inspiron E1705/9400
	  gateway	Gateway laptops with EAPD control
	  [COLOR="Red"]panasonic	Panasonic CF-74[/COLOR]

My laptop, the last one, is a Panasonic CF - F8 so it is I guess in the same laptop family...I edited the code with the STAC9200, as mentioned at the top of this list, so

alias snd-card-0 snd-hda-intel
options snd slots=snd-hda-intel
options snd-hda-intel model=[COLOR="Red"]STAC9200[/COLOR]

Was that correct? It didnt work unfortunately......

Of interest, that information page also mentions " 

```

Module snd-maestro3
  -------------------

    Module for Allegro/Maestro3 chips

    external_amp     - enable external amp (enabled by default)
    amp_gpio         - GPIO pin number for external amp (0-15) or
                       -1 for default pin (8 for allegro, 1 for
                       others) 

    This module supports autoprobe and multiple chips.

    Note: the binding of amplifier is dependent on hardware.
    If there is no sound even though all channels are unmuted, try to
    specify other gpio connection via amp_gpio option. 
    [COLOR="Red"]For example, a Panasonic notebook might need "amp_gpio=0x0d"
    option.[/COLOR]" 
```

Again, keyword being Panasonic, my laptop - does that help at all in my eternal quest to get sound working!!

THANKS ! ALL HELP APPRECIATED!

---

### Post by Secrest on 2010-01-10
Try this. I'm not in front of my computer so hope this is right.  Double click the speaker icon.   Click On devices tab and uncheck the box in there and see if that might work

---

### Post by garvinrick4 on 2010-01-10
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4]**Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)**[/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR][/SIZE][/FONT][/COLOR]


REBOOT

---

### Post by listerdl on 2010-01-10
Hey thanks for the advice...

With point 1: 

"1. Backup (and then delete) your previous configuration files:
Code:
$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/ $ rm -r ~/.pulse ~/.asound* $ sudo rm /etc/asound.conf Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system."

Does that mean in terminal I ought to place this code: [COLOR="Red"]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/ $ rm -r ~/.pulse ~/.asound* $ sudo rm /etc/asound.conf[/COLOR] - i.e. the entire string?

---

### Post by lidex on 2010-01-11
I'm a little confused as to the pertinent codec. Could you please post the output of this command:
```
head -n 1 /proc/asound/card0/codec*
```

This would help also:
```
cat /proc/asound/version
```

And:
```
uname -a
```

---

### Post by lidex on 2010-01-11
3 typical problems with new Karmic install and audio are:
1) Muted mixer elements
2) Booting into wrong kernel (grub not updated)
3) Modem driver stealing output

That's why I always suggest looking to that first. You've already checked alsamixer.
```
sudo apt-get remove sl-modem-daemon
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
 Then reboot.
Next is an alsa update. (Linked to above:[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810"))

---

### Post by listerdl on 2010-01-11
> **lidex said:**
> 3 typical problems with new Karmic install and audio are:
1) Muted mixer elements
2) Booting into wrong kernel (grub not updated)
3) Modem driver stealing output

That's why I always suggest looking to that first. You've already checked alsamixer.
```
sudo apt-get remove sl-modem-daemon
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
 Then reboot.
Next is an alsa update. (Linked to above:[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810"))

Sorry I am getting a little bit confused - do you think I ought to do the above rather than the last advice?

Thanks for the help.

I am really after some confirmation b/c I am a little worried that I might end up twinkering too much with the kernel and audio that it goes beyond repair.

Please confirm if it is safe for me to do the above rather than garvinrick4 very useful post.

Rgds, Lister

---

### Post by hobo on 2010-01-11
FYI ......... [http://www.alsa-project.org/main/index.php/SoundcardTesting]("http://www.alsa-project.org/main/index.php/SoundcardTesting")

---

### Post by lidex on 2010-01-11
> **listerdl said:**
> 
Please confirm if it is safe for me to do the above rather than garvinrick4 very useful post.
Rgds, Lister

It's always a good idea to set up pulseaudio correctly. Pulseaudio sits on top of alsa however and if you read the documentation on the alsa site or the update thread you will understand a lot of soundcard issues are fixed in the newer versions.

I would suggest following my advice, then PA setup.

---

### Post by lkraemer on 2010-01-11
listerdl,
You might try the fix for PulseAudio at:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
and then this, if it applies:
[http://ubuntuforums.org/showthread.php?t=1179999](http://ubuntuforums.org/showthread.php?t=1179999)

lk

---

### Post by themightyrumpus on 2010-01-17
I am using UbuntuStudio, just upgraded to 9.10 and same thing.

The only thing I have figured out so far is GNOME has sound. I have tried Enlightnment on its own, and Gnome E-16, tried KDE and KDE E-16 and I am on Xfce right now.

NO SOUND, but it acts like it should be working unless I use GNOME.


DOH!

---

### Post by garvinrick4 on 2010-01-17
[SIZE=4][B]Just in case make sure alsa backports are installed in Synaptics kernal version.

HOWTO: PulseAudio Fixes & System-Wide Equalizer Support[/B][/SIZE]
*Overview:*
 
[COLOR=BLUE]**Note 1. Karmic & Jaunty users:** If you have dist-upgraded from a previous release, I recommend that you follow the guide to remove obsolete configuration. If you have performed a clean installation, follow the guide only if you are experiencing issues.
**Note 2. Jaunty & Intrepid users:** due to a bug in the ALSA libraries, your PCM mixer may occasionally become muted or reset to 0% volume. If you cannot hear sound - or hear a faint crackling - refer to Part A, Step 6.
**Note 3: OSSv4 users:** PulseAudio does not support OSSv4, so this guide will serve no purpose to you. If you have chosen to install OSSv4 and experience issues, you should seek guidance within the threads dedicated to OSSv4. I do not recommend users to install OSSv4 due to compatibility and support issues.
**Note 4: Kubuntu users:** Don't follow this guide - PulseAudio isn't used in your distribution.
[/COLOR]
PulseAudio is an advanced sound server which has been included in **U**buntu (i.e. the standard GNOME version) since the release of Hardy Heron (8.04). Unfortunately, Hardy shipped with a suboptimal configuration of PulseAudio which has resulted in users experiencing various problems, ranging from sporadic crashes in Firefox to sound mixing being completely broken. PulseAudio in Intrepid should work by default, but it is quite possible that your configuration is suboptimal. For more information, refer to the **FAQ** below.

For best results, I recommend all users who are interested in PulseAudio to install the latest release - Karmic Koala (9.10). The developers have done an excellent job with PulseAudio integration and configuration in this release - enough to make this guide virtually obsolete.

When you are ready to follow this guide, this is all you need to know:

Hardy users: Follow **Part A** & **B**.
Intrepid users: Follow **Part A** & **C**.
Jaunty users: Follow **Part A**.
Karmic users: Follow **Part A**.

Additionally: 
[LIST]
[*]**Appendix A** gives general troubleshooting tips - if you have problems, start here.
[*]**Appendix B** gives useful information on the more advanced/technical features of PulseAudio.
[*]**Appendix C** gives information on how to properly configure specific applications that may not work with PulseAudio by default, including (but not limited to): WINE, Skype, and all OSS applications.
[*]**Appendix D** (only for Intrepid and lower) will show you how to enable equalized audio for **all** applications on your system - this is especially useful for laptop users who experience poor audio quality with their internal speakers.
[/LIST]
[SIZE=4]**Frequently Asked Questions**[/SIZE]
*The most common queries are answered here.*

**Q. What exactly is PulseAudio?**
A. From the [homepage]("http://www.pulseaudio.org/"):
 	Quote:
 	 	 		 PulseAudio is a sound server for POSIX and Win32 systems. A sound server is basically a proxy for your sound applications. It allows you to do advanced operations on your sound data as it passes between your application and your hardware. Things like transferring the audio to a different machine, changing the sample format or channel count and mixing several sounds into one are easily achieved using a sound server.  	 	 
Simplified: PulseAudio is responsible for playback and mixing of audio on your system. It is not a sound driver - in fact, it runs on top of the [Advanced Linux Sound Architecture]("http://www.alsa-project.org/") (ALSA). Aside from all the cool effects PulseAudio provides, it serves as a replacement for ALSA's virtual sound mixing device ([DmixPlugin]("http://alsa.opensrc.org/DmixPlugin"), or "dmix") - thus allowing multiple applications to share access to your sound card.

**Q. PulseAudio? Bleh! I don't want it on my system.**
A. Well... tough! PulseAudio is *already* installed and active on Hardy and Intrepid by default; it replaces ESD (ESound Daemon) for system sounds, and most of Ubuntu's default applications already use it (Totem, Rhythmbox, and any other applications using the GStreamer framework). Although some high-profile applications support PulseAudio natively (such as VLC and mplayer), most applications use plain ALSA or OSS output, and thus don't have native PulseAudio support.

**Q. If PulseAudio is already installed, why do I need this guide?**
A. While PulseAudio has been installed by default since Hardy Heron (8.04), we dropped the ball when it came to the configuration part. A quote from the main PulseAudio developer, [Lennart Pöttering]("http://0pointer.de/blog/projects/jeffrey-stedfast.html"): 	Quote:
 	 	 		 Some distributions did a better job adopting PulseAudio than others. On the good side I certainly have to list Mandriva, Debian, and Fedora. OTOH Ubuntu didn't exactly do a stellar job. They didn't do their homework. Adopting PA in a distribution is a fair amount of work, given that it interfaces with so many different things at so many different places. The integration with other systems is crucial. The information was all out there, communicated on the wiki, the mailing lists and on the PA IRC channel. But if you join and hang around on neither, then you won't get the memo. To my surprise when Ubuntu adopted PulseAudio they moved into one of their 'LTS' releases rightaway. Which I guess can be called gutsy -- on the background that I work for Red Hat and PulseAudio is not part of RHEL at this time. I get a lot of flak from Ubuntu users, and I am pretty sure the vast amount of it is undeserving and not my fault.  	 	 
When PulseAudio is running, it requires exclusive access to your sound card in order to work correctly as it assumes responsibility for mixing application's sounds instead of ALSA's "dmix" device. If you launch a "regular" application that does not have explicit PulseAudio support, it will most likely try to open the "Dmix" device - and this will deprive PulseAudio of control over the sound card. From the user's perspective, they will observe that audio mixing between applications is broken. 

PulseAudio includes ALSA plugins (within the package "libasound2-plugins") which are designed make regular ALSA applications remap audio to the PulseAudio server (and thus avoid mixing problems as described above). Unfortunately, Hardy Heron shipped without these plugins enabled (or even installed) by default, which is causing many, many audio mixing issues for users. To compound the problem, the version of these PulseAudio ALSA plugins in the Hardy repositories do not function correctly, so updated versions are required for ALSA applications to work correctly with PulseAudio.

By following this guide, your system will be configured to use these PulseAudio ALSA plugins for Hardy users (and updated versions of necessary packages will get installed from my [PPA]("https://launchpad.net/%7Epsyke83/+archive")). Although Intrepid has these plugins installed and configured by default, following this guide is still worthwhile because a) it will ensure you have a clean PulseAudio configuration, and b) you will hopefully gain a better understanding of how PulseAudio works.

**Q. I'm glad to hear these issue are fixed in Intrepid, but why the hell aren't they fixed in Hardy already?**
A. The simplest answer to this question is: complexity. Hardy is a LTS (Long Term Support) release, and there is a very strict policy towards updates (SRU; even the most trivial of bugfixes are entered into a code review). In order to fix Hardy, many components will require updates and changes, including but not limited to: libflashsupport, ia32-libs, pulseaudio, libasound2, libasound2-plugins, flashplugin-nonfree, nspluginwrapper...

Up until the last moment of Hardy's development cycle, the PulseAudio ALSA plugins weren't functioning correctly, and Flash 9 absolutely would not work without the "evil" libflashsupport library (I say evil, because it caused frequent random crashes in Firefox) - and so it wasn't possible to enact the required changes before the final release. It's possible now, but there would require a huge amount of effort to review and apply these changes.

**Q. I followed your guide and PulseAudio still doesn't work!**
A. Refer to Appendix A and provide the requested information in your post.

**Q. I can't get Skype/WINE/an OSS application/XYZ working correctly with PulseAudio, what can I do?**
A. Some applications require some extra configuration, and some applications don't work with PulseAudio - please refer to Appendix C for information on specific applications.

**Q. Where can I find the appropriate bug reports related to these issues?**
A. If you click on a step number it will link to the appropriate bug report, if one exists.

**[SIZE=4]Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)[/SIZE]**
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files:  	Code:
 	$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf 
[COLOR=Red]**Warning:** As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=Blue]**Note:** Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
 	Code:
 	 $ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio 
[3]("https://bugs.launchpad.net/bugs/192888"). Ensure the evil "libflashsupport" library is **not** installed: 	Code:
 	$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound 
[COLOR=Blue]**Note:** the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=Blue]**Note:** Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=Blue]**Note:** If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
 	Code:
 	$ pulseaudio & pavucontrol 
[/COLOR]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):

 	Code:
 	$ alsamixer [COLOR=Blue]-Dhw[/COLOR] 
[COLOR=Blue]**Note:** When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect!

NOW REBOOT

---

