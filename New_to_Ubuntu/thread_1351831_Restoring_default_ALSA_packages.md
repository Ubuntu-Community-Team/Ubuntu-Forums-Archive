---
title: "Restoring default ALSA packages"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by sleepee on 2009-12-10
First of all, i'd like to say, Woohoo!! my very first post! jaja..  anyway, thanks beforehand to everybody that provides assistance in this forum.   it's been a great help..

ok..  now down to my problem..   this might be a little long, but please bear with me.
i guess i'll start first with a little history..
ok, so i just got this new hp dv7 laptop the other day and the first thing i did was install ubuntu 9.10.   after a while i noticed that the sound was pretty bad, which was due to the speakers not working..  only the subwoofer worked.. but at least the sub worked well.
after doing some digging around these forums and some tinkering..  i managed to make it worse.  i followed some advice that apparently wasn't exactly made for my situation and i took out the sound for everything, even the subwoofer.. and also replaced the output in the sound preferences for a "dummy output."

so at this point, i'm desperate, and since i didn't know how to undo what i did, i just searched for "alsa" in the synaptic package manager and i just randomly added packages i thought i might need.

the good thing is that now i have sound for youtube videos, and mp3 files (but only when i play them in the alsaplayer, nothing else).
the bad thing is that i can't control the volume from my laptop controls or anywhere except the vol. control in youtube's player and the vol. control in the alsa app.
the ugly thing is that now i also have added a whole bunch of kernel versions in my boot menu (including server versions !?!?!?) that i want to somehow get rid of.

so, after all that, i guess what i'm asking for is just a little help on at least restoring the alsa defaults, so even if i don't have sound from the speakers, i'll at least be able to start from scratch and undo the mess i made..  jaja

thanks.. any kind of help is appreciated.

---

### Post by Geoff918 on 2009-12-11
Oh my...

Okay, well in Synaptic you can do a lot of what you need to do.

There are right-click options for "mark for complete removal" and "mark for reinstallation"

from CLI you could try

aptitude search alsa

and see what comes up (anything marked with an "i" is already installed).

In order to get rid of your settings you'd need to do the following:

*** CAUTION *** this could make things worse! Keep this in mind, but maybe wait for some more experienced help, too.

You can remove custom settings by doing an

sudo aptitude remove (whatever package)

and then you can do a 

sudo aptitude purge (whatever package)

That will clear all the settings from the system and any configuration you've done to it.

You can then install the packages again...

sudo aptitude install (whatever package)

Again, I'd wait for someone to point you in the best direction. This would be a failsafe option barring any other solution.

---

### Post by sleepee on 2009-12-11
hmmm.. thanks for that new command i just learned..  looks handy.
but yea, i think i will wait for somebody to tell me something more specific, because i haven't been doing too well just installing/removing packages on my own.. lol!

but hey, i did find out a way to take out old kernel versions from the boot menu!!  one less thing to fix..

---

### Post by sleepee on 2009-12-11
btw, now that i think about it, i'm not sure if i should have posted this in the "multimedia" section or not..
i mean, i'm a noob, so i posted here, but it is a multimedia issue isn't it??
if i need to redirect this question to another section, hopefully someone will let me know..

---

### Post by sleepee on 2009-12-15
hmmm...  nothing??
i know this can't be an uncommon question.  i mean, there has to be a way at least...
(without reinstalling the OS, i mean)

---

### Post by Hampster on 2009-12-16
Hi Sleepee,

Sorry I can't help.  I too along with so many others are in the same great big boat.  I think it's called "Kalamity Koala"  Perhaps we just have to go back to Interesting Ibis and wait for Laughing Lizard and then hopefully all things will be Micky Mouse.  Meanwhile we await the keepers. Beware of the white coats.

---

### Post by sleepee on 2009-12-16
lol!!  as long as i don't have to wait for zombied zebra..
but yea, i actually booted from the 9.04 cd and i didn't have any sound there either..
so idk.. maybe there's just no proper support for my sound card yet or something..  i'll just keep looking

---

### Post by Chesamo on 2009-12-16
What *is* your sound card?

Also, try this:
```
sudo apt-get purge pulseaudio*
sudo apt-get install pulseaudio*
```
What this will do, is essentially clean out and reinstall Pulse Audio (Ubuntu's primary sound control framework). If you are still having problems, [FONT="Courier New"]sudo apt-get install alsa-base[/FONT] should do the trick.

---

### Post by sleepee on 2009-12-17
lol!  i totally forgot to give all the sound info..
ok, so if i'm not mistaken the command "aplay -l" should give out the sound card info right??
so here it is:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

btw, i also tried the command "speaker-test -c2 -l5 -twav" to perform a speaker test, and i heard the lady's voice perfectly..
i just thought that might be important.

oh yea, and i tried purging and reinstalling pulseaudio* and alsa-base, but nothing seems to change..

EDIT:  actually, something did change. now i have system sounds..  like bootup sounds, clicking sounds, error sounds, etc..  i just didn't notice it until i rebooted.  but everything else stayed the same.
still no sound using any app. besides alsaplayer and flash videos in Firefox.  and still no volume control either...

---

### Post by Chesamo on 2009-12-17
On one of my older laptops, I ended up removing pulse (sudo apt-get purge pulseaudio*) and using gnome-alsamixer (sudo apt-get install gnome-alsamixer) for volume control.

---

### Post by sleepee on 2009-12-17
ok, so i did the purge pulseaudio (w/out reinstalling it) and installed gnome-alsamixer..
even though it removed some programs that i wanted (like avidemux, ffmpeg, vlc, etc.), it did let me hear audio through banshee and movie player.
also apparently, the microphone doesn't work either, of course.. (i tried on skype and sound recorder)
but the volume control still doesn't work...

and i want those programs too though, so.. i don't know if i want to remove pulseaudio if i have to sacrifice those progs..
but this is actually a newer laptop, so maybe that's why it's not working on mine..

---

### Post by Chesamo on 2009-12-17
The volume control applet won't work without pulseaudio installed (use gnome-alsamixer in its place), but all of the oher apps you mentioned (VLC, for example) will. I've used them with no problem.

Check the recording properties in gnome-alsamixer and make sure your audio in is enabled.

---

### Post by sleepee on 2009-12-17
> **Chesamo said:**
> The volume control applet won't work without pulseaudio installed (use gnome-alsamixer in its place), but all of the oher apps you mentioned (VLC, for example) will. I've used them with no problem.

Check the recording properties in gnome-alsamixer and make sure your audio in is enabled.


well, i tried it again like you said.. and like before, it works for banshee and movie player, but i realized that the sound preferences were wrong in vlc.  i had to change it to use alsa (after i reinstalled it, because it got purged along with pulseaudio), and then it worked.  :cool:  
but the volume control still doesn't work.

also, for some reason there's some other programs that don't have audio playback, either.  like skype and avidemux.  there's no sound there..  idk if it's the sound preferences or what..

and for some weird reason, i tried recording myself on cheese and i was able to hear something, but it was distorted really bad.. but then the second time i tried it, no luck.  but no other program that requires audio input works either..  not skype, not RecordMyDesktop, not even Sound Recorder.

and i'm sorry if i didn't express myself right.. the alsa mixer's volume control works fine...and i can also control volume from within the applications' controls..
but what i meant was that the volume control from the actual laptop controls, and also from the volume control button from the panel on the upper right, have no effect on the volume (even though i can see the slider going up and down)

---

### Post by sleepee on 2009-12-17
btw, another thing i'm worried about is that, even though i do hear some sound, it seems like my sound card isn't recognized because i still get no sound card appearing under my sound preferences..
apparently, my sound works even though the sound card isn't recognized, but it still would be kinda nice to see something there..  but i guess that's minor as long as i have sound..  i mean, at least we're making some success right?  i do have more sound than before..  lol!

here's some pics to show you what i mean..

---

### Post by sleepee on 2009-12-17
alright, so i was messing around with the alsa mixer and the sound preferences in some apps, and i managed to get cheese and sound recorder working right.  (i just had to put the levels right in the alsamixer so the mic volume was just right)
and i got avidemux working too..  i had to use the "Sdl" audio device instead of alsa, for some reason...

so i'm guessing the problems i'm having with skype and RecordMyDesktop have to do with the apps themselves and not the sound drivers..

anyway, i don't know what purging pulseaudio did, but it seems to have fixed some of my problems.. thanks Chesamo!

---

### Post by lidex on 2009-12-18
I recently purchased a dv7t and installed Jaunty. Had no sound at all. After much searching fixed it with an alsa update via this process:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

Didn't have to remove pulseaudio; volume controls all work fine.

---

### Post by sleepee on 2009-12-18
> **lidex said:**
> I recently purchased a dv7t and installed Jaunty. Had no sound at all. After much searching fixed it with an alsa update via this process:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Didn't have to remove pulseaudio; volume controls all work fine.


hmm.. i just tried this and on first instance, i have sound only on alsaplayer and vlc media player (i have it configured for alsa audio output), and system sounds.
but there's no sound on other programs, microphone doesn't work, and no volume control..
but i'll keep tinkering around a little bit, messing with the sound configurations, and i'll get back to you..

---

### Post by lidex on 2009-12-18
Also follow this guide:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by sleepee on 2009-12-19
> **lidex said:**
> Also follow this guide:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

thanks for pointing me to that thread.  it seems to be pretty helpful and there's a lot of info there that i learned.
but i seem to be stuck on #5 of part A.  there's nothing in my input or output devices..  in fact, there's nothing shows up in any tab..  as if it didn't pick up a sound card or anything...
for some reason, i keep asking myself if this has to do with the script i ran a while ago that replaced my sound output with a "dummy output."  i'm not sure, but i know that script didn't help out at all.

but basically, i'm getting problems B (some apps play sound, but nothing shows up in playback tab) and E (Connection failed error when opening PA vol. control) from appendix A.

but so far, vlc is working with PA and so is banshee.  for some reason the audio doesn't work for any other app.  and it appears i cant use the mic either..

i'll keep reading and looking for answers though, and i'll let you know what happens..
if it comes to it, i might just reinstall KK and then try to follow this guide for configuring Pulse Audio..  i'll let you know either way..

---

### Post by lidex on 2009-12-19
Error E means pulseaudio daemon is not running. Try rebooting and if still no go run the commands they recommend:
```
pulseaudio & pavucontrol
```


I'm thinking the other error (A) could be the result of that.
Just for kicks, before you reboot run these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

---

### Post by sleepee on 2009-12-19
> **lidex said:**
> Error E means pulseaudio daemon is not running. Try rebooting and if still no go run the commands they recommend:
```
pulseaudio & pavucontrol
```
I'm thinking the other error (A) could be the result of that.
Just for kicks, before you reboot run these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

well, i had rebooted, and i didn't mention that it pavucontrol command did work the first time, but then i re-did the first few steps just to make sure i did it right, and then i went re-entered pavucontrol command, but i got that connection failure error...

but anyway, i rebooted another time, and this time it works no problem, so i guess the daemon is working fine.. kinda weird, but i'm not complaining.  lol!
so anyway, i'm still not getting anything for input devices... and for the output, i just get that "dummy output"

here's some pics..

---

### Post by Perturbed Penguin on 2009-12-19
Yeah sound can be an issue in Linux sometimes but it is getting better, truly. In my opinion Karmic has been a miracle in various aspects, Karmic was the first Ubuntu distro to support even my X-fi out of the box which is WAY sick! But I'll bet you are having some kind of pulse-audio issue as others have suggested, unfortunately I don't know much about maintaining audio stuff on Linux. 

... You mentioned you found a way to remove the old kernel entries from the boot menu - this may or may not be easier for you but Ubuntu Tweak is a wonderful program that can help you in this regard. To remove the old kernel entries just go to the applications/'package cleaner' tab, here you can clean up old kernel entries, old and unnecessary packages that are used for updating software and that sort of stuff - it is very much like Ccleaner if you have ever used that program on Windows. I think you will have to search for the .deb file on the web if you want to use it, I don't think it is in the repos. If you prefer the other way of cleaning kernel entries then more power to ya', I'm just giving you options.

Good luck with your audio, I'll be sure to post anything I come across that seems useful! ;)

---

### Post by sleepee on 2009-12-19
> **Perturbed Penguin said:**
> Yeah sound can be an issue in Linux sometimes but it is getting better, truly. In my opinion Karmic has been a miracle in various aspects, Karmic was the first Ubuntu distro to support even my X-fi out of the box which is WAY sick! But I'll bet you are having some kind of pulse-audio issue as others have suggested, unfortunately I don't know much about maintaining audio stuff on Linux. 

... You mentioned you found a way to remove the old kernel entries from the boot menu - this may or may not be easier for you but Ubuntu Tweak is a wonderful program that can help you in this regard. To remove the old kernel entries just go to the applications/'package cleaner' tab, here you can clean up old kernel entries, old and unnecessary packages that are used for updating software and that sort of stuff - it is very much like Ccleaner if you have ever used that program on Windows. I think you will have to search for the .deb file on the web if you want to use it, I don't think it is in the repos. If you prefer the other way of cleaning kernel entries then more power to ya', I'm just giving you options.

Good luck with your audio, I'll be sure to post anything I come across that seems useful! ;)

thanks for the recommendation... i just installed it, but hopefully i won't get sidetracked too much from fixing this sound problem like i usually do because i keep finding other little problems to fix all the time lol!
but i'm definitely going to try it out..  thanx

---

### Post by Perturbed Penguin on 2009-12-19
Hehe, yeah it happens - I do the same all the time... but I think my system is just about to the point now where I have everything setup to work and to look and feel just the way I like it. ;) ... now what were we talking about, oh yeah, **AUDIO**. lol

---

### Post by lidex on 2009-12-19
Let me see the output of these commands:

```
sudo lshw -C sound
```

```
find /lib/modules/`uname -r` | grep snd
```

---

### Post by sleepee on 2009-12-19
> **lidex said:**
> Let me see the output of these commands:

```
sudo lshw -C sound
``````
find /lib/modules/`uname -r` | grep snd
```

ok, so for the first command, i get this:

> *-multimedia UNCLAIMED  
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d3000000-d3003fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:38 memory:dd100000-dd103fff


and here's the second one:

> /lib/modules/2.6.31-16-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.31-16-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.31-16-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.31-16-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.31-16-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.31-16-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.31-16-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.31-16-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/2.6.31-16-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.31-16-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.31-16-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.31-16-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.31-16-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/snd-hrtimer.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/snd-seq-midi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/snd-seq-dummy.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/snd-seq-virmidi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/snd-rawmidi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.31-16-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.31-16-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.31-16-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.31-16-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ca0106.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-oxygen-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-intel.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mona.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-opl3-synth.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-au8820.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-als300.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-indigo.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-indigodjx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hrtimer.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-rme9652.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-indigoio.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mixart.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-pcm.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-maestro3.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mts64.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-page-alloc.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-au8810.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-usb-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mpu401.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-cs8427.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-echo3g.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-intel8x0m.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-atiixp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-emux-synth.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-oxygen.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-usb-audio.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-i2c.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-asihpi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-es1938.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-sonicvibes.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq-device.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-emu10k1x.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-bt87x.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-au8830.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-via82xx-modem.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-usb-us122l.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-analog.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-nm256.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq-midi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ens1370.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ens1371.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-pdaudiocf.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-cs5530.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-es1968.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-via.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ak4114.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-intel8x0.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq-oss.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-indigoiox.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-pcm-oss.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-usb-caiaq.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq-dummy.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-soc-core.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-gina20.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-vx222.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-riptide.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-rme32.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-rawmidi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-timer.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-als4000.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-virmidi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-atiixp-modem.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-vxpocket.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-trident.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-aloop.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-cs46xx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-pt2258.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq-virmidi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-virtuoso.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-darla20.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-darla24.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ice1724.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-emu10k1.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-indigodj.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-cs4281.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-tea575x-tuner.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-sb16-dsp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ali5451.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-pcsp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-aw2.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-dummy.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-via82xx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-cmipci.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-opl3-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-fm801.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hdspm.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ctxfi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hifier.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-util-mem.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mia.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mtpav.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-layla20.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-usb-usx2y.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ak4117.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ak4xxx-adda.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-serial-u16550.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq-midi-event.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ac97-codec.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-lx6464es.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-portman2x4.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-sb-common.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-rme96.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-cirrus.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-layla24.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-azt3328.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-gina24.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-korg1212.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mixer-oss.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-mpu401-uart.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-emu10k1-synth.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-seq-midi-emul.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ad1889.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-pcxhr.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hdsp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-idt.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ice1712.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-soc-wm-hubs.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-vx-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-pdplus.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-hwdep.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ymfpci.ko
/lib/modules/2.6.31-16-generic/kernel/sound/modules/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/pdplus/snd-pdplus.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ca0106.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-oxygen-lib.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-intel.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mona.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-opl3-synth.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-au8820.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-als300.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-indigo.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-indigodjx.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hrtimer.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-rme9652.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-indigoio.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mixart.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-pcm.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-maestro3.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mts64.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-page-alloc.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-au8810.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-usb-lib.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mpu401.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-cs8427.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-echo3g.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-intel8x0m.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-atiixp.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-emux-synth.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-oxygen.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-usb-audio.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-i2c.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-asihpi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-es1938.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-sonicvibes.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq-device.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-emu10k1x.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-bt87x.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-au8830.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-via82xx-modem.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-usb-us122l.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-analog.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-nm256.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq-midi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ens1370.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ens1371.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-pdaudiocf.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-cs5530.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-es1968.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-via.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ak4114.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-intel8x0.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq-oss.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-indigoiox.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-pcm-oss.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-usb-caiaq.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq-dummy.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-soc-core.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-gina20.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-vx222.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-riptide.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-rme32.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-rawmidi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-timer.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-als4000.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-virmidi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-atiixp-modem.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-vxpocket.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-trident.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-aloop.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-cs46xx.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-pt2258.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq-virmidi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-virtuoso.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-darla20.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-darla24.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ice1724.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-emu10k1.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-indigodj.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-cs4281.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-tea575x-tuner.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-sb16-dsp.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ali5451.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-pcsp.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-aw2.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-dummy.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-via82xx.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-cmipci.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-opl3-lib.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-fm801.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hdspm.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ctxfi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hifier.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-util-mem.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mia.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mtpav.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-layla20.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-usb-usx2y.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ak4117.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ak4xxx-adda.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-serial-u16550.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq-midi-event.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ac97-codec.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-lx6464es.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-portman2x4.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-sb-common.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-rme96.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-cirrus.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-layla24.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-azt3328.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-gina24.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-korg1212.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mixer-oss.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-mpu401-uart.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-emu10k1-synth.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-seq-midi-emul.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ad1889.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-pcxhr.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hdsp.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-idt.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ice1712.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-cs5535audio.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-soc-wm-hubs.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-vx-lib.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-pdplus.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-hwdep.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ymfpci.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ak4113.ko
/lib/modules/2.6.31-16-generic/updates/alsa/snd-ice17xx-ak4xxx.ko

i hope you can make some sense of all that, because i sure can't  lol!
all i know is that dummy output's gotta go.  so i'm guessing that snd-dummy.ko and snd-seq-dummy.ko are getting deleted somehow right??

---

### Post by lidex on 2009-12-19
sleepee:
When you post text output use the code tags rather than quote. I think that dummy output needs to go but may not be the main issue. Do you know what kernel you're booting with?

More troubleshooting:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

---

### Post by sleepee on 2009-12-19
well, i've been working with the kernel 2.6.31-16...

btw, i tried this out, but it didn't work..

[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

actually, besides system sounds, and alsa player, i only get sound on vlc player when i tell it to use alsa.

but i think i'm going to just stick with what you tell me, because i'm not doing so well trying out random fixes.. lol!
so i'm just going to try out that troubleshoot in the meantime..

---

### Post by sleepee on 2009-12-19
btw, step 3 in the troubleshooting process gave me this:

[http://pastebin.ca/1720786](http://pastebin.ca/1720786)

there seems to be a lot of useful info there about my setup in case you needed it..

oh, and sorry about the quote tags..
i'm guessing i have to use code tags for everything terminal related right?  i'll try to remember that...

---

### Post by lidex on 2009-12-19
I may have something here. Post the contents of /etc/modprobe.d/alsa-base.conf.

---

### Post by sleepee on 2009-12-19
i'm not sure if i've modified this or not, but here you go..

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
options snd-hda-intel power_save=10 power_save_controller=N

---

### Post by lidex on 2009-12-19
OK. In a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Scroll to the bottom and insert these lines just below 
"options snd-pcsp index=-2":
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
```

Save, then close.

Now open synaptic. Search "modem". If you see "sl-modem-daemon" is installed, mark it for complete removal. Apply. Still in synaptic, go to "Repositories" in "Settings" menu. On the "Ubuntu Software" tab make sure the restricted repository is checked. On the "Updates" tab, make sure backports are enabled.

Now close "Software Sources" and allow to update. Close synaptic.
Open a terminal and enter these commands, one line at a time please and apply any updates:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Now reboot.

---

### Post by sleepee on 2009-12-19
alright.. well, i did everything just like you told me.. except the updating grub didn't work for some reason..  for some reason it said command not found..
but i rebooted, and tried out some progs to see if the audio worked..

so apparently, i still have youtube vids working, still have system sounds, and vlc still works when i tell it to use alsa output..
but nothing else works.. when i put vlc to use pulseaudio, i hear nothing..
and banshee, skype, movie player, avidemux, etc.. still none of it plays audio..

could it really be the updating grub part that went wrong???

---

### Post by sleepee on 2009-12-19
btw, i don't know if i should have mentioned this earlier, but i have an intel core i7 processor..  i'm not sure if that has to do with anything..  but i thought i'd put that out there just in case..
hopefully, that wasn't terribly necessary info..

---

### Post by lidex on 2009-12-19
I screwed up. The command is:
```
sudo update-grub
```

But before that do this:
```
sudo apt-get install linux-backports-modules-generic
``` 

and in your alsa-base.conf comment out that last line so that:

```
options snd-hda-intel power_save=10 power_save_controller=N 
```

looks like this:
```
#options snd-hda-intel power_save=10 power_save_controller=N 
```

Reboot

---

### Post by sleepee on 2009-12-19
ok  so it couldn't find "linux-backports-modules-generic" so i went to synaptic and installed "linux-backports-modules-2.6.31-16-generic"
i thought that might be the one for me..

but anyway, i rebooted and everything, but apparently, nothing's changed..
still no sound, no volume control, and nothing shows up in sound preferences for input or output devices..  except the dummy one..

---

### Post by lidex on 2009-12-19
Whatever you did to get that dummy output, can you undo it? And try rebooting - this time hold down the shift key after bios screen until you get a grub screen. Make sure you're booting with correct kernel.


> ok so it couldn't find "linux-backports-modules-generic" so i went to synaptic and installed "linux-backports-modules-2.6.31-16-generic" i thought that might be the one for me..

Did that also install:
linux-backports-modules-karmic
linux-backports-modules-karmic-generic

---

### Post by lidex on 2009-12-19
Now let's see this output again:
```
sudo lshw -C sound
```

---

### Post by sleepee on 2009-12-19
```
*-multimedia UNCLAIMED  
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d3000000-d3003fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:37 memory:dd100000-dd103fff
```

well, i have to leave right now, but i'll leave you with that for now..  hopefully i'll be back in a little while..  thanks..

---

### Post by lidex on 2009-12-19
OK. Here's what mine looks like:
```
*-multimedia            
       description: Audio device
       product: R700 Audio Device [Radeon HD 4000 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

Let's see this output also:
```
lspci
```
and this
```
cat /proc/asound/version
```
and one more time:
```
gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by sleepee on 2009-12-20
> **lidex said:**
> Whatever you did to get that dummy output, can you undo it? And try rebooting - this time hold down the shift key after bios screen until you get a grub screen. Make sure you're booting with correct kernel.

Did that also install:
linux-backports-modules-karmic
linux-backports-modules-karmic-generic

actually, it didn't install those... but i just went back into synaptic and installed them and rebooted, but i got the same results.
and i'm booting into 2.6.31-16.  i think that's the kernel i should be in right??
as far as that script i ran that got me the dummy output.. i've been looking for it forever..  it was really a bad idea to run it..  i think i found in some blog somebody had recommended, but i don't remember how to get there..  most likely, it did more than just give me a dummy output...
i don't know if i'll ever find it though..  i'm thinking about just doing a fresh reinstall of KK and then start over from there..

> **lidex said:**
> OK. Here's what mine looks like:
```
*-multimedia            
       description: Audio device
       product: R700 Audio Device [Radeon HD 4000 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```Let's see this output also:
```
lspci
```and this
```
cat /proc/asound/version
```and one more time:
```
gedit /etc/modprobe.d/alsa-base.conf
```


hmmm.. ours don't look all that different except the configuration part (which i thought i had changed already)... and the UNCLAIMED part too.. idk what that's about..

anyway, here's lspci

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a28 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
05:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

and here's cat /proc/asound/version: 

```
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec  2 2009 for kernel 2.6.31-16-generic (SMP).
```

and the alsa-base.conf file:

```
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
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

anyway...  i'm seriously thinking about reinstalling.  i'm starting to think there's no way of fixing this unless i knew what that script did..
:sad:
it might not give me my sound back, but at least i'll get predictable results when i troubleshoot..

---

### Post by lidex on 2009-12-20
I feel your pain. Funny thing - I dragged my laptop out to see config and ended up installing updates. Guess what? No sound after that. I ran the alsa upgrade script again and it came right back. It would probably be worth your while to redo that also as some updates tend to overwrite the alsa changes.

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

Do you have 2 soundcards?
> 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

---

### Post by lidex on 2009-12-20
As I delve into your situation, I realize your chipset probably requires different options in alsa-base.conf.

Can you post the output of this command:
```
head -n 1 /proc/asound/card0/codec*
```

Remove these lines from alsa-base.conf:
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
```

and add these:
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

```
Reboot

---

### Post by sleepee on 2009-12-21
> **lidex said:**
> I feel your pain. Funny thing - I dragged my laptop out to see config and ended up installing updates. Guess what? No sound after that. I ran the alsa upgrade script again and it came right back. It would probably be worth your while to redo that also as some updates tend to overwrite the alsa changes.

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Do you have 2 soundcards?

wait a minute...  so you installed an update, and it ended up taking your sound out???
hmmm.. that doesn't sound like a very well thought out update.. 
anyway, i already upgraded alsa, even though i had the latest version, but i guess i could try it one more time, just in case.

oh, and from what i know, i'm pretty sure i only paid for only one sound card when i bought this comp..even though apparently my comp. tells me different.
i do have regular speakers and a separate subwoofer, but i thought they were controlled by only one sound card...

> **lidex said:**
> As I delve into your situation, I realize your chipset probably requires different options in alsa-base.conf.

Can you post the output of this command:
```
head -n 1 /proc/asound/card0/codec*
```Remove these lines from alsa-base.conf:
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
```and add these:
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

```Reboot

```
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

```

btw, i deleted those lines, and then added the others in the same exact place.
i'll reboot after i upgrade alsa and then see what happens

---

### Post by sleepee on 2009-12-21
btw lidex, i reallly got to thank you for helping and sticking around for so long...
you've got to really have a lot of patience to deal with a problem like this  lol!!
i mean, i've been ready to reinstall karmic for a while now.. i would've done it already if you hadn't stuck around...  so thanx again

---

### Post by lidex on 2009-12-21
This line in alsa-base.conf worked for some others with same codec.
(Codec: IDT 92HD75B3X5).

```
options snd-hda-intel model=hp-m4 enable_msi=1
```

So try adding it.

---

### Post by sleepee on 2009-12-21
> **lidex said:**
> This line in alsa-base.conf worked for some others with same codec.
(Codec: IDT 92HD75B3X5).

```
options snd-hda-intel model=hp-m4 enable_msi=1
```So try adding it.

well, that is my codec, but i added that line to alsa-base and rebooted, but still no sound, except when i use alsa.. not when i use pulseaudio..

anyway, here's what my alsa-base.conf looks like currently..

```
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
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
options snd-hda-intel model=hp-m4 enable_msi=1
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

---

### Post by lidex on 2009-12-21
OK. The sucky thing about making these changes is you have to reboot to see if they worked. But we also have to make sure pulseaudio is set up correctly. Press the Alt+F2 key combo and enter: ```
gnome-alsamixer
``` In the mixer go to "Edit>Sound Card Properties" and make sure any relevant channels are enabled. Do you see an entry for "Speakers"?. In mixer make sure channels are unmuted and turned up. Anything? Go here and follow procedure to setup PA on Karmic:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
 If nothing still go back to alsa-base.conf and comment out (#) these two lines:
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
``` and reboot.

---

### Post by sleepee on 2009-12-22
so everything's enabled and turned up in alsamixer...
i tried that PulseAudio fix again, and well... it sorta works, but mostly not.
when i installed the PA libraries, banshee started playing immediately.  and vlc played also..  but that's it.
other than that, nothing changed.  still no volume control, and the sound capture device doesn't work either..
and for some reason, i still get no input or output devices when i get into pavucontrol.

anyway, i'm going to change that alsa-base.conf, reboot and see what happens..

---

### Post by sleepee on 2009-12-22
you know what? i'm reinstalling.
i mean, i rebooted, and then no sound with vlc or banshee or anything..
then i put back those lines in alsa-base.conf, rebooted again, and still no sound..
this is retarded...
whatever that script was that i ran, it totally screwed up my system..  i have some time today, so im just going to reinstall everything and just start from scratch...
i'll let you know what happens..

---

### Post by lidex on 2009-12-22
Yeah, retarded is a good word. Something should have worked by now.

---

### Post by sleepee on 2009-12-23
wooohoooo!!!!!!!!!!!!!  FINALLY!!!!!  it's workingggggg!!!!!!
jajajaja...
i had to reinstall ubuntu, upgrade alsa, i tried the pulse audio fix (even though it didn't work), and then i did what you had told me to try a while ago...

> **lidex said:**
> OK. In a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Scroll to the bottom and insert these lines just below 
"options snd-pcsp index=-2":
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
```Save, then close.

Now open synaptic. Search "modem". If you see "sl-modem-daemon" is installed, mark it for complete removal. Apply. Still in synaptic, go to "Repositories" in "Settings" menu. On the "Ubuntu Software" tab make sure the restricted repository is checked. On the "Updates" tab, make sure backports are enabled.

Now close "Software Sources" and allow to update. Close synaptic.
Open a terminal and enter these commands, one line at a time please and apply any updates:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```Now reboot.

and then after that, reboot, and i got SOUND!!!!! and VOLUME CONTROLL!!!! on ALL my apps!!!

:guitar:

jajajaja..  now i don't know if my microphone is working, but i'll check that tomorrow because it's late now..
but as soon as i check that i'm marking this as solved, thanks to lidex  lol!!!!

EDIT:  mic works too!!!  tried it on Cheese, RecordMyDestkop, SoundRecorder... everything works!!!!!!!!

---

### Post by sleepee on 2009-12-23
btw, where exactly do i go to mark this thread as solved???  lol!!

---

### Post by lidex on 2009-12-23
> **sleepee said:**
> btw, where exactly do i go to mark this thread as solved???  lol!!

First post. Top-right. Click on "thread tools" in red.

I might be happier than you. :lolflag:

---

### Post by ijenk86 on 2013-01-31
Thanks, halped me too... :D

> **sleepee said:**
> wooohoooo!!!!!!!!!!!!!  FINALLY!!!!!  it's workingggggg!!!!!!
jajajaja...
i had to reinstall ubuntu, upgrade alsa, i tried the pulse audio fix (even though it didn't work), and then i did what you had told me to try a while ago...



and then after that, reboot, and i got SOUND!!!!! and VOLUME CONTROLL!!!! on ALL my apps!!!

:guitar:

jajajaja..  now i don't know if my microphone is working, but i'll check that tomorrow because it's late now..
but as soon as i check that i'm marking this as solved, thanks to lidex  lol!!!!

EDIT:  mic works too!!!  tried it on Cheese, RecordMyDestkop, SoundRecorder... everything works!!!!!!!!

---

### Post by oldos2er on 2013-02-01
Old thread closed, please don't bump old threads.

---

