---
title: "Configuring Movie Player to Use OSS Insteada ALSA"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by fleamour on 2010-11-09
Pidgin alerts used to cause the buzzing of a hundred angry bees till I recompiled my ALSA kernel via this guide:

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

This solved one problem but previously OK Exaile & Movie Player output would now distort/buzz.

Exaile can be set to use OSS in it's menu but Movie Player has no such configuration.

Anyone think of a work around?  

PS. On the rare occasion of using Windows Media Player plugin in Chromium/Firefox it also distorts.

---

### Post by Mike3 on 2010-11-21
I think you can get it in the terminal by typing in:
```
mplayer -ao oss
```
Not so sure yet how you'll get it to work in a menu entry in Xubuntu, however. I'll have to get to my Xubuntu machine & see if I can edit it in there, though.

---

### Post by gradinaruvasile on 2010-11-21
Movie Player = totem, right? It uses Gstreamer, so you have to set Gstreamer to OSS output.
Launch

gstreamer-properties

either in a terminal or via alt+f2 and set what you want.

But bear in mind that OSS does not permit multiple sound sources at one given time, so if you listen to music you wont be able to hear anything else (in Firefox etc). Any other sound (like Pidgin sounds) will be blocked if a program plays any kind of sound.
Flash player in Firefox uses ALSA anyway - i dont know if there is any possibility to set it to OSS.

---

### Post by fleamour on 2010-11-22
Thanks for the replies.

Will check out your suggestions later on today.

---

### Post by fleamour on 2010-11-22
I get terminal output:

"The program 'gstreamer-properties' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-media"

I am running the LXDE GUI on-top of Xubuntu if that makes a difference?

EDIT:  First suggestion "mplayer -ao oss" returns:

"The program 'mplayer' is currently not installed.  You can install it by typing:
sudo apt-get install mplayer"

Once again not sure if running LXDE makes a difference?

---

### Post by Mike3 on 2010-11-23
Duh. My bad. I should have realized that you aren't running GNOME! The way I know that would run OSS for all applications would be the following, at least on my Xubuntu box:
```
xfce4-mixer
```
& to select anything that resembles OSS. As [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640") pointed out, only one application can utilize OSS at a time. In plain English, that means that you won't be able to hear your music player while listening to a video in Firefox. I still have to dig up some more info on this. I'm trying to see if there's a way to set an option in the config file of totem to use OSS. I'll let you know what it is as soon as I can find it. Later.

---

### Post by fleamour on 2010-11-23
OK, tried each setting in turn, restarting M-Player each time.  None work.  The movie will play with no sound unless clicking on time line to reset vid, whereupon you get glitchy crackling.

If mixer makes system wide changes then maybe OSS is not the answer?

---

### Post by Mike3 on 2010-11-24
I'm not 100% sure what direction to go to fix this problem. Try & use this tool, I had no clue it existed, but just found it on another thread that was solved relating to audio problems. Try the following link:
<**[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)**>
& make sure you run the debugging tool using:

```
ubuntu-bug audio
```If you find specific issues with your sound card, you could post them here. Maybe we can catch some sort of problem in it. This should at least point you in the direction to report the bug.

Type in "alsamixer" (w/o quotes) in the terminal, & see if the PCM is turned all of the way up. Try turning it down a little. Could also be power saving enabled for your sound card. I've had snap crackle pop noises coming out before. May be problems with power saving. Try to disable power saving, on certain cards (esp. older Intel ones) it causes audio to go haywire. Go to the terminal & enter in:

```
gksu mousepad /etc/modprobe.d/alsa-base.conf
```Make sure the last lines look like this, to disable power saving:

options snd-hda-intel power_save=0 power_save_controller=N

That could be a potential fix.


 Another way to disable power saving could be to enter in:

```
gksu thunar /etc/pulse
```And comment out (place a number sign before each line) **every** file that you find with the line:

load-module module-suspend-on-idle

In that entire folder. It should then look like this:

#load-module module-suspend-on-idle

Otherwise, if you just do it for *one*, power saving will kick back in during times like at logon & attempt to distort the sounds again. 

Otherwise, try to upgrade your kernel. I have also found that to be a success before. This, I hope, is enough to fix the sound problems.

---

### Post by fleamour on 2010-11-24
> **Mike3 said:**
> Try the following link:
<**[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)**>
I have yet to assimilate/digest this resource.  I am to try your three suggestions first.

> & make sure you run the debugging tool using:
```
[FONT=monospace][/FONT]ubuntu-bug audio
```
Using the sound debugging tool, Apport'll hang trying to collect info indefinitely.  Another option is to maybe file bug against Movie Player?  Is the correct package Totem?

> ...see if the PCM is turned all of the way up.  
It is not.

> Go to the terminal & enter in:
```
gksu mousepad /etc/modprobe.d
```
I get this error:
"Error reading file '/etc/modprobe.d': Is a directory"

> ```
gksu thunar /etc/pulse
```
And comment out (place a number sign before each line) **every** file that you find with the line:

load-module module-suspend-on-idle

In that entire folder. It should then look like this:

#load-module module-suspend-on-idle
Done!  Will reboot & try again..Will let you know what transpires...

---

### Post by Mike3 on 2010-11-25
The reason why you couldn't edit the file in /etc/modprobe.d? Because I forgot to finish the command!  ](*,) Should have mentioned the correct command is:
[FONT=monospace]
[/FONT]```
gksu mousepad /etc/modprobe.d/alsa-base.conf
```Sorry about that!

---

### Post by fleamour on 2010-11-25
Ahhh, Cheerz!

---

### Post by fleamour on 2010-11-25
Things are complicated by sound not working after sleep/hibernate.  This is a regression with latest kernel. 

When running:
```
ubuntu-bug audio
```
I get:

"The problem cannot be reported:

This is not a genuine Ubuntu package"

I'm guessing by recompiling ALSA from source, I've chosen to go it alone in the big wild world.  Is it possible to restore ALSA to stock version? I can try recompiling but will I need to do so with every new kernel release?

EDIT: It would appear ALSA needs recompiling for every kernel, if you go that route.  A strange side effect is that the function F12 hotkey does not hibernate after compiling ALSA, a small price to pay for working sound I guess.

---

### Post by fleamour on 2010-11-26
VLC displays same crackly sound.

EDIT:  Here is "lsmod | grep snd" output

```
snd_cs46xx             77978  6 
gameport                9089  2 snd_cs46xx
snd_ac97_codec        100600  1 snd_cs46xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            34539  0 
snd_mixer_oss          13897  2 snd_pcm_oss
snd_pcm                71550  5 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1434  0 
snd_seq_oss            27242  0 
snd_seq_midi            4557  0 
snd_rawmidi            19077  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47530  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18646  2 snd_pcm,snd_seq
snd_seq_device          5988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56303  20 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  2 snd
snd_page_alloc          7076  2 snd_cs46xx,snd_pcm
```

Anything amiss?

---

### Post by Mike3 on 2010-11-26
Is Totem still crackly? If it's just VLC, try going to Tools>Preferences in VLC & under "Show Settings", selecting "All".  Since it appears that tou're using OSS, go under the left context pane & selecting Audio>Output Modules. Then make sure the appropriate output module is selected. From there, go to "OSS" under "Output Modules" & try selecting "work around buggy OSS drivers." That may be a potential fix. Also try changing around the settings under "File" & potentially "ALSA." Make sure you press the "Save" button afterwords.

---

### Post by fleamour on 2010-11-26
Totem is still crackly.  Did as you suggested & selected ALSA under VLC's Audio>Output Modules menu.  Problem solved!  Movie Player could do with similar configuration options.

---

### Post by fleamour on 2010-11-26
As an aside, I only have an 8MB graphics accelerator.  But holiday vid appears poorer quality, blockier & more pixelated, full screen, than I remember it playing via WMP under Win2k.  

Is there a setting to increase quality?  Or is this the Linux driver?

(Maybe I should start a whole 'nother thread.)

EDIT:  I am prone to looking for problems where there is none, my memory is also shockingly bad.

---

### Post by Mike3 on 2010-11-26
Looking at what VLC says on mouse-over, it appears that somehow you need to increase your total internal buffer size, or increase it's free time. There must be some way I can find how to change this... I personally use ALSA, but maybe a LiveCD with an OSS install & some config file hunting may help with this. If this is part of the work-around, possibly finding VLC's settings & changing this system-wide would eliminate the hashing completely. If only I knew where to start... Going to start looking.

---

### Post by Mike3 on 2010-11-27
I have found the config files for OSS. I'm guessing you're using OSS version 4. They're located in "/etc/oss4/conf". If you want to fix the movie player issues, this may do it. Enter in the following into the terminal:

```
gksu thunar /etc/oss4/conf
```

Now you'll have to make back-ups. To make this easier, just copy & paste the following files right into the same folder you're in now. To make them backup files, in case something goes wrong, give all the backup files the file extension .bak after the already in use .conf extension. For example, "sample(copy).txt" would become "sample.txt.bak" Do this with the three files that we're going to edit: "oss_imux.conf", "oss_cs461x.conf" & "oss_sbpci.conf". Editing the first file (listed above, not that you see in Thunar) should give less total audio to buffer, stopping distortion, the second one should give an IBM Thinkpad-specific fix, & the final one raise latency & perhaps also stop choppiness. Don't forget to remove the first "#" sign in each line of the respective config file being edited. First, open up "oss_imux.conf" & change the value from 48000 to 24000 or 32000. After uncommenting the line, save & exit that file. Now open up "oss_cs461x.conf" & change the value "cs461x_clkrun_fix" from 0 to 1. Uncomment, save & exit. Go to "oss_sbpci.conf" & raise acpi_latency to 96 or 128. If any of the above methods cause the situation to get worse, delete the offending modified file(s) & remove the ".bak" file extension to the backups you need to restore. Hope this is the fix!

---

### Post by I'mGeorge on 2010-11-27
another way to do it would had been installing alsa-oss. If the application was written to support OSS executing it with the following command

```

aoss /the_path_to_program_executable

``` 

should also do the trick

---

### Post by fleamour on 2010-12-01
@Mike3

Thanks very much for your hard work.  I installed VLC, & that will play video without crackling through ALSA.

---

