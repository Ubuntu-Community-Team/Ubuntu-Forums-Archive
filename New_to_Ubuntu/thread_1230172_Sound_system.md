---
title: "Sound system"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by harfin on 2009-08-03
I have just posted another new message regarding my Trust Webcam WB-1400T and Skype. This is the second issue that I have so not managed to resolve.

I have only just started using Ubuntu, (just converted from Windows XP Pro) and I have to say apart from the two unresolved issues, Ubuntu is a fantastic operating system.

[LIST]
[*] I have a Dell Dimension E520 with 1.5G of RAM.
[*] It has an in-built sound card
[*]I have Dell speakers plugged into the speaker jack.
[*] I have a Soyntec VOIP handset which I've used and continue to use (successfully) with Skype.
[*] I play and hear audio CD's through the attached speakers.
[/LIST]
 
_Problem: _
Whenever I activate a media file off of a website, e.g. BBC i-Player or a movie file received from friends and family, the sound comes through my VOIP handset and not through the speakers.  Probably connected with this issue is that I have also noticed that when I switch the PC in the morning, I hear the first 'beep' through my speakers, and then when the successful sign-on to Ubuntu is aired the sound comes through the VOIP phone.

Any suggestions?

Alan

---

### Post by motrax on 2009-08-03
> **harfin said:**
> I have just posted another new message regarding my Trust Webcam WB-1400T and Skype. This is the second issue that I have so not managed to resolve.

I have only just started using Ubuntu, (just converted from Windows XP Pro) and I have to say apart from the two unresolved issues, Ubuntu is a fantastic operating system.

[LIST]
[*] I have a Dell Dimension E520 with 1.5G of RAM.
[*] It has an in-built sound card
[*]I have Dell speakers plugged into the speaker jack.
[*] I have a Soyntec VOIP handset which I've used and continue to use (successfully) with Skype.
[*] I play and hear audio CD's through the attached speakers.
[/LIST]
 
_Problem: _
Whenever I activate a media file off of a website, e.g. BBC i-Player or a movie file received from friends and family, the sound comes through my VOIP handset and not through the speakers.  Probably connected with this issue is that I have also noticed that when I switch the PC in the morning, I hear the first 'beep' through my speakers, and then when the successful sign-on to Ubuntu is aired the sound comes through the VOIP phone.

Any suggestions?

Alan

Have you checked that nothing is muted on the Volume Control? I had a similar problem when my headphone was not playing sound. Try selecting all options under Preferences, set all of them to max volume and see if you get sound.

---

### Post by harfin on 2009-08-03
> **motrax said:**
> Have you checked that nothing is muted on the Volume Control? I had a similar problem when my headphone was not playing sound. Try selecting all options under Preferences, set all of them to max volume and see if you get sound.

Yes none of the listed items are muted

Alan
:mad:

> **harfin said:**
> Yes none of the listed items are muted

Alan
:mad:

So anyone else have any ideas?

Alan

---

### Post by CatKiller on 2009-08-03
> **harfin said:**
>  Whenever I activate a media file off of a website, e.g. BBC i-Player or a movie file received from friends and family, the sound comes through my VOIP handset and not through the speakers.  Probably connected with this issue is that I have also noticed that when I switch the PC in the morning, I hear the first 'beep' through my speakers, and then when the successful sign-on to Ubuntu is aired the sound comes through the VOIP phone.

It sounds like you've got the default sound device for your user configured to your VoIP phone rather than your speakers. The configuration is different depending on whether you're using ALSA or PulseAudio for your sound.

---

### Post by harfin on 2009-08-03
> **CatKiller said:**
> It sounds like you've got the default sound device for your user configured to your VoIP phone rather than your speakers. The configuration is different depending on whether you're using ALSA or PulseAudio for your sound.

The sound preferences window shows the following:
**Sound Events **Sound Playback HDA Intel STAC92xx Analog (OSS)
**Music & Movies **Sound Playback HDA Intel STAC92xx Analog (OSS)
**Audio Conferencing **Sound Playback HDA Intel STAC92xx Analog (OSS);      Sound Capture OSS - Open Sound System
**Default Mixer Tracks **HDA Intel (Alsa Mixer)

What do I need to change please?
Alan

---

### Post by CatKiller on 2009-08-03
OSS has some limitations over the others (only one sound at a time, fixed sound device location, that kind of thing). Change them to the equivalent ALSA or PulseAudio devices. (I use PulseAudio without any problems, but others prefer the older ALSA method). There may be a couple listed for each, since you've got two sound devices. Or it may be that you've got a couple of outputs for one device, with the speakers plugged into one and the VoIP phone plugged into the other. In which case, it's a case of identifying which output is which.

Hopefully that will sort you out.

---

### Post by harfin on 2009-08-03
> **CatKiller said:**
> OSS has some limitations over the others (only one sound at a time, fixed sound device location, that kind of thing). Change them to the equivalent ALSA or PulseAudio devices. (I use PulseAudio without any problems, but others prefer the older ALSA method). There may be a couple listed for each, since you've got two sound devices. Or it may be that you've got a couple of outputs for one device, with the speakers plugged into one and the VoIP phone plugged into the other. In which case, it's a case of identifying which output is which.
Hopefully that will sort you out.

I am even more confused !
I have as options (the text in blue is the result of using the Test button with that option selected) [INDENT]**Sound Events** & **Music & Movies**

[LIST=1]
[*]Auto Detect [COLOR=Blue]test button causes sound through VoIP phone[/COLOR]
[*]Generic USB Audio Device USB Audio (ALSA) Error - [COLOR=Blue]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.[/COLOR]
[*] HDA Intel STAC92xx Analog (ALSA) [COLOR=Blue][COLOR=Black]Error[/COLOR] audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.[/COLOR]
[*]Generic USB Audio Device USB Audio (OSS) Error [COLOR=Blue]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.[/COLOR]
[*]Generic USB Audio Device USB Audio (OSS) Error [COLOR=Blue]as for 4[/COLOR]
[*]HDA Intel STAC92xx Analog (OSS) [COLOR=Blue]test button [/COLOR][COLOR=Blue]causes[/COLOR][COLOR=Blue] sound through speakers[/COLOR]
[*]HDA Intel STAC92xx Analog (OSS) [COLOR=Blue]test button [/COLOR][COLOR=Blue]causes[/COLOR][COLOR=Blue] sound through speakers[/COLOR]
[*][COLOR=Blue][COLOR=Black]ALSA - Advanced Linux Sound Architecture  [/COLOR][/COLOR][COLOR=Blue]test button [/COLOR][COLOR=Blue]causes[/COLOR][COLOR=Blue] sound through VoIP phone[/COLOR]
[*][COLOR=Blue][COLOR=Black]OSS - Open Sound System [/COLOR][/COLOR] [COLOR=Blue]test button makes sound through speakers[/COLOR]
[*][COLOR=Blue][COLOR=Black]Pulse Audio Sound Server [/COLOR][/COLOR][COLOR=Blue]test button [/COLOR][COLOR=Blue]causes[/COLOR][COLOR=Blue] sound through VoIP phone[/COLOR][COLOR=Blue]
[/COLOR]
[/LIST]
[/INDENT] Alan

:confused:

---

### Post by CatKiller on 2009-08-03
> **harfin said:**
> 
 HDA Intel STAC92xx Analog (ALSA) [COLOR=Blue][COLOR=Black]Error[/COLOR] audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.[/COLOR]

I think this is probably because OSS has claimed the sound device.

> 
[COLOR=Blue][COLOR=Black]ALSA - Advanced Linux Sound Architecture  [/COLOR][/COLOR][COLOR=Blue]test button [/COLOR][COLOR=Blue]causes[/COLOR][COLOR=Blue] sound through VoIP phone[/COLOR]

[COLOR=Blue][COLOR=Black]Pulse Audio Sound Server [/COLOR][/COLOR][COLOR=Blue]test button [/COLOR][COLOR=Blue]causes[/COLOR][COLOR=Blue] sound through VoIP phone[/COLOR]

I don't know much about configuring ALSA, but with PulseAudio you can use either **pavucontrol** or **padevchooser** to pick which is the default device (called a "sink" in general in PulseAudio parlance). Otherwise, you should post some details on how you've got everything wired up to help someone that knows more about it than me to show you how to configure the devices how you want. For example, you've got a "Generic USB Audio Device." What is that?

---

### Post by harfin on 2009-08-03
> **CatKiller said:**
> I think this is probably because OSS has claimed the sound device. 
I don't know much about configuring ALSA, but with PulseAudio you can use either **pavucontrol** or **padevchooser** to pick which is the default device (called a "sink" in general in PulseAudio parlance). Otherwise, you should post some details on how you've got everything wired up to help someone that knows more about it than me to show you how to configure the devices how you want. For example, you've got a "Generic USB Audio Device." What is that?

There are only three sound devices on my system.

[LIST=1]
[*]A VoIP handset which is plugged into a USB socket on the PC
[*]A microphone which is plugged into the Microphone jack on the front of my Dell Dimension E520 (I haven't ried using that yet)
[*]A pair of Dell speakers that are plugged into the Sound Card jack on the rear of the PC.
[/LIST]
I can only assume that the Generic USB Audio Device is the VoIP phone.

Following your suggestion I have installed **padevchooser **and I have selected the Pulse Audio Sound Server on the drop down list for Sound Events and Music and Movies

When I click the test button on each item the sound plays through the VoIP phone handset.

I am afraid I am now getting horribly lost!

Alan

---

### Post by CatKiller on 2009-08-03
Now that you aren't using OSS for anything, do the tests that use the HDA Intel STAC92xx Analog device produce sound?

PulseAudio ultimately uses the ALSA device to output sound. It seems like the default ALSA device is set for the USB device still. I believe that per-user ALSA configuration is done through the ~/.asoundrc file, although I don't know that much about it. There's a utility called asoundconf that does things with the ALSA configuration, but I don't know too much about that either. It does have the options to list the ALSA devices with ```
**asoundconf list**
``` and to set the default device with ```
**asoundconf set-default-card** _PARAMETER_
``` where _PARAMETER_ is the name of the card displayed by the **list** option. Perhaps those will get you started.

---

### Post by harfin on 2009-08-03
> **CatKiller said:**
> ]**asoundconf list** 
This produces the result[INDENT][COLOR=Blue]Names of available sound cards:
Intel
Device[/COLOR]

[/INDENT]I then entered **asoundconf ****[B] set-default-card Intel, **[/B]and got the following error message (in blue) as a result of using the Test button with HDA Intel STAC92xx Analog (ALSA)  - [COLOR=Blue]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.[/COLOR][COLOR=Black]

The same error resulted for Sound Events and Music and Movies

As before [/COLOR]as a result of using the Test button with the drop down list item of [COLOR=Blue][COLOR=Black]ALSA - Advanced Linux Sound Architecture the [/COLOR][/COLOR][COLOR=Black]test button [/COLOR][COLOR=Black]causes[/COLOR][COLOR=Black] sound through VoIP phone[/COLOR][COLOR=Black]

The only item from the drop down list when I use the test button that produces sound through the speakers is [/COLOR]HDA Intel STAC92xx Analog (OSS)

If I run **asoundconf ****[B] set-default-card Device**[/B] and repeat in Sound Preferences -> Sound with the use of the Test button with HDA Intel STAC92xx Analog (ALSA) the results are exactly the same as above[U].

I'm confused and lost!

[/U]Alan

> **harfin said:**
> This produces the result[INDENT][COLOR=Blue]Names of available sound cards:
Intel
Device[/COLOR]
[/INDENT]I then entered **asoundconf ****[B] set-default-card Intel, **[/B]and got the following error message (in blue) as a result of using the Test button with HDA Intel STAC92xx Analog (ALSA)  - [COLOR=Blue]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.[/COLOR][COLOR=Black]
The same error resulted for Sound Events and Music and Movies
As before [/COLOR]as a result of using the Test button with the drop down list item of [COLOR=Blue][COLOR=Black]ALSA - Advanced Linux Sound Architecture the [/COLOR][/COLOR][COLOR=Black]test button [/COLOR][COLOR=Black]causes[/COLOR][COLOR=Black] sound through VoIP phone[/COLOR][COLOR=Black]
The only item from the drop down list when I use the test button that produces sound through the speakers is [/COLOR]HDA Intel STAC92xx Analog (OSS)
If I run **asoundconf ****[B] set-default-card Device**[/B] and repeat in Sound Preferences -> Sound with the use of the Test button with HDA Intel STAC92xx Analog (ALSA) the results are exactly the same as above[U].
I'm confused and lost! [/U]Alan


[COLOR=Red]Is there anyone who can offer any suggestions at to what I should do now?[/COLOR]

[COLOR=Red]The Linux terminology is so different from XP, and I am really floundering around in the dark here - and I don't have a torch!!

Alan[/COLOR]

---

### Post by Fancycakes on 2009-08-04
I have the same error: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. But for HDA ATI SB Analog (ALSA).

Only instead of going through an imaginary voip, there just isn't any sound. Period.

---

### Post by harfin on 2009-08-04
> **Fancycakes said:**
> I have the same error: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. But for HDA ATI SB Analog (ALSA).
Only instead of going through an imaginary voip, there just isn't any sound. Period.

Puzzling isn't it?

The only way I can get audio cd's to play through my speakers is to use one of the drop down list options I get for Preferences -> Sound is to select Open Sound System.

At the risk of repeating myself I'm in the dark and no-one has a torch!

Alan

---

### Post by braete on 2009-08-04
do you have in mixerdevice dropdovn list an item "Playback: Intel xxxx Analog(PulseAudio Mixer)" or something similar?

if you do install asoundconf-gtk (sudo apt-get install asoundconf-gtk)
it's a neat gui for asoundconf (probably all it does can be done trough the console, but a gui is always good ;) )
start it and in the dropdown list chose pulse
then in sound set all to pulse, and mixer to Playback: Intel xxxx Analoag(PulseAudio Mixer).
reboot and you hopefully you should have your sound ok

---

### Post by harfin on 2009-08-04
> **braete said:**
> do you have in mixerdevice dropdovn list an item "Playback: Intel xxxx Analoag(PulseAudio Mixer)" or something similar? if you do install asoundconf-gtk (sudo apt-get install asoundconf-gtk) it's a neat gui for asoundconf (probably all it does can be done trough the console, but a gui is always good ;) ) start it and in the dropdown list chose pulse then in sound set all to pulse, and mixer to Playback: Intel xxxx Analoag(PulseAudio Mixer). reboot and you hopefully you should have your sound ok

For sound events, music and movies & audio conferencing the only item that actually mentions 'Pulse' is "PulseAudio Sound Server". Under 'Default Mixer Tracks' though I do have "Capture: HDA Intel - STAC92xx Analog (Pulse Audio Mixer).

I did as you suggested and installed the asoundconf-gtk and selected Pulse. I then reset the drop downs to PulseAudio Sound Server and I then re-booted.

Using the 'Test' button on Preferences -> sound, the test sound came through on my VOIP phone; and an audio CD plays through the phone handset too.

Any other ideas?

Alan

---

### Post by braete on 2009-08-04
please run in terminal: 
aplay -l
and paste output

and

paste .asoundrc and .asoundrc.asoundconf (both in ur home folder, hidden)
also please check if you have an asoundrc file in /etc and paste it(if any)

---

### Post by harfin on 2009-08-04
aplay -l  produced[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/INDENT] .asoundrc produced[INDENT]bash: .asoundrc: command not found
alanhart@ubuntu:~$ 
[/INDENT].asoundrc.asoundconf[INDENT]bash: .asoundrc.asoundconf: command not found
[/INDENT]asoundrc file in /etc[INDENT]No file found

[/INDENT]Alan

---

### Post by braete on 2009-08-04
.asoundrc and asoundrc.asoundconf are 2 files located in ur home folder (they are hidden, so you need to press ctrl+h to see them , unless you edited nautilus preferences to show hidden files by default))
paste the contents of those 2 files

---

### Post by harfin on 2009-08-04
> **braete said:**
> .asoundrc and asoundrc.asoundconf are 2 files located in ur home folder (they are hidden, so you need to press ctrl+h to see them , unless you edited nautilus preferences to show hidden files by default))
paste the contents of those 2 files

asoundrc
[INDENT]# ALSA library configuration file
# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/alanhart/.asoundrc.asoundconf>
[/INDENT]asoundrc.asoundconf
[INDENT]# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Device
defaults.ctl.card Device
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
pcm.!default { type pulse }
ctl.!default { type pulse }

[/INDENT]Does that help?

Alan

---

### Post by braete on 2009-08-04
in asoundrc add:
```
pcm.!default { 
type hw 
card 0 
device 0 
}

```
save, reboot
if sound is ok, enjoy
if still goes trough voip device
also add (although i dont think it should make much of a difference)
```
ctl.!default { 
type hw 
card 0 
device 0 
}
```

edit: after this in sound at mixer it should also become available Playback: Intel STAC92xx Analog(Pulse audio)
so you should select it.

---

### Post by harfin on 2009-08-04
Bloomin' marvelous!
All working properly now!
Thankyou so much!
As the saying goes 
[COLOR=Blue]"**[FONT=Verdana][FONT=Verdana][FONT=Comic Sans MS]*In a world without walls and fences, who needs Windows and Gates?*[/FONT][/FONT][/FONT]**"
[/COLOR] 
Thanks again
Alan

---

### Post by braete on 2009-08-04
no problem
hope you never need help again!

but, did you test the voip? does it work as it should now that it isnt the default output device ?

---

### Post by harfin on 2009-08-04
> **braete said:**
> no problem. hope you never need help again! but, did you test the voip? does it work as it should now that it isnt the default output device ? 

Yep. Only did a test call, but that should be sufficient proof.  I tried on-line movies (BBC i-Player) - worked great through the speakers.  I played an audio CD and that worked great through the speakers also.

I'll get used to the Linux terminology and the layout in the fullness of time, but even with the glitches changing to Ubuntu is one of the best moves I've ever made..

Thanks once again
Alan

---

### Post by harfin on 2009-08-05
> **braete said:**
> no problem hope you never need help again! but, did you test the voip? does it work as it should now that it isnt the default output device ?

One small point though, that came to light this morning, is that when I ran a slide show of a Presentation File I received via email (including a soundtrack), it played via the VoIP handset?  Strange or what? Every other aspect regarding sound works like a charm

Alan

---

