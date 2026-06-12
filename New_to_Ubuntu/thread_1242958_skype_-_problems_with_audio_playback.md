---
title: "skype - problems with audio playback"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by al.adab on 2009-08-17
Skype on Ubuntu 9.04...on a Dell Vostro 1310. If I click on "Open Volume Control", I find it set on HDA Intel (Also mixer). On Skype, the only way not to get the message "problems with audio playback" is to set the sound at "Pulse". I can hear the ringing and the voice of the test phone call clearly. When it comes to record my voice, though, it doesn't work, I can't hear myself back.

I've had a look at a number of threads on the subject, but I still can't understand the "pulse" concept (is it automatically installed?). What's more, I'm even more confused as I tested Skype on this very machine (same OS, Ubuntu 9.04, I'm now on a fresh installation), and it worked perfectly...

I tried to move around "Front Mic Boost" and "PCM" on "Open Volume Contol", but nothing changes...I also tried the "Sound Recorder" (from the only option listed, "Capture"), and in fact I can't record...

Can you please help? Thanks!

---

### Post by expatCM on 2009-08-17
Skype can be a bit annoying to set up ...........   

I think you need to have a separate sound device for Sound In and Sound Out.  In my set up I have Ringing the same as Sound Out and use Pulse for these.

Before doing anything with Skype I tend to first check that I can hear a CD play and also make a recording from the Mic to Sound Recorder.

---

### Post by al.adab on 2009-08-18
Here's how it eventually worked (through the usual trial & error process and with no evidence any of the following is entirely relevant to the process): 

a) *sudo apt-get install pulseaudio pavucontrol padevchooser* (although "pulse" appeared under sound settings, some stuff did get installed;

b) System>Preferences>Sound>Devices: all on "Autodetect" except for Sound Capture (on "Pulse Audio Sound Server") and Device under Default Mixer Tracks (on HDA Intel - Alsa mixer); 

c) Volume Control: 
- Device = HDA Intel (Alsa mixer). 
- Playback= disable Front Mic Boost.
- Recording= Capture enabled (Capture 1 disabled).

d) Skype: 
- Sound IN: HDA Intel (hw: intel,0).
- Sound OUT: pulse.
- Ringing: HDA Intel (hw: intel,0). 

If anyone thinks this could be improved - for instance, when I record my voice on Capture full blast and playback on maximum volume, I can't exactly hear myself loud and clear. Clear, yes, but loud, well, no...but this is also the case when I listen to a CD: I'm not able to pump up the volume, it remains quite low altogether. But maybe this has to do with this laptop sound system?

---

### Post by Hilko on 2009-12-19
I had the same problem.
For some mysterious reason the sound in and output in the skype preferences was set to Bluetooth.

I set the sound input to 'pulse'
and sound out and ringing to 'HDA Intel (hw:intel,0)'
and then it worked again. I hope it helps

---

### Post by Zzl1xndd on 2009-12-19
I had a similar issue, although mine was because Skype was set to adjust my mixer settings and was turning down the amplification on my Mic. Disabling this option in Skype and turning up the Amplification on my mic settings fixed it right up.

---

### Post by hobo14 on 2009-12-20
I had a similar problem (although it's fixed since I installed 9.10), I fixed it by:

Of the three device choices: Sound In, Sound Out, and Ringing, I set 2 of them to pulse, and the other to  "HDA Intel 0" (or similar, whatever it is).

But I can't remember which two were pulse, sorry.  A little bit of trial and error will soon tell you whether this will work for you.

---

### Post by KayakJim on 2009-12-21
sudo killall pulseaudio before starting Skype gets my audio working for me.

---

