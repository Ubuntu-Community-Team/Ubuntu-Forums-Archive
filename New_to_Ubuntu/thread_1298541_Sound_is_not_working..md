---
title: "Sound is not working."
date: 2009-10-22
forum: New to Ubuntu
---

### Post by cumanzor on 2009-10-22
Hello everyone. I'm using 9.10 beta. Been having a few issues, but this is one is actually pissing me off :p.

I have no sound output. MPD crashes if I try to play something, any other program is simply not playing any type of files.

Attached is the user.log entries of today. I set my computer to turn on at 5am (so it wakes me up), that's why there is a time difference of 15h, work + school.

```
Oct 22 05:01:01 desktop pulseaudio[2228]: module-alsa-card.c: Failed to find a working profile.
Oct 22 05:01:01 desktop pulseaudio[2228]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Oct 22 05:01:07 desktop pulseaudio[2228]: ratelimit.c: 2 events suppressed
Oct 22 20:06:47 desktop pulseaudio[10397]: module-alsa-card.c: Failed to find a working profile.
Oct 22 20:06:47 desktop pulseaudio[10397]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Oct 22 20:06:48 desktop pulseaudio[10397]: socket-server.c: bind(): Address already in use
Oct 22 20:06:48 desktop pulseaudio[10397]: socket-server.c: bind(): Address already in use
Oct 22 20:06:48 desktop pulseaudio[10397]: module.c: Failed to load  module "module-native-protocol-tcp" (argument: "auth-anonymous=1"): initialization failed.
Oct 22 20:06:48 desktop pulseaudio[10397]: main.c: Module load failed.
Oct 22 20:06:48 desktop pulseaudio[10397]: main.c: Failed to initialize daemon.
Oct 22 20:06:52 desktop pulseaudio[2228]: sink-input.c: Failed to create sink input: sink is suspended.
Oct 22 20:16:31 desktop pulseaudio[2228]: sink-input.c: Failed to create sink input: sink is suspended.
Oct 22 20:16:31 desktop pulseaudio[2228]: sink-input.c: Failed to create sink input: sink is suspended.
Oct 22 20:16:31 desktop pulseaudio[2228]: sink-input.c: Failed to create sink input: sink is suspended.

```

I have no idea at all what's going on :(. Any ideas?

---

### Post by OrangeVixen on 2009-10-22
Are audio files not being played or you hear nothing?

---

### Post by cumanzor on 2009-10-23
> **OrangeVixen said:**
> Are audio files not being played or you hear nothing?

I hear nothing.:(

---

### Post by OrangeVixen on 2009-10-23
Use synaptic and try reinstalling some of the audio drivers, and also try System -> Preferences -> Sound.

---

### Post by cumanzor on 2009-10-23
Ok, got it. It all happened because I was trying to configure mpd to work while other apps where playing audio. (edited)

So I pretty much followed the advice from [https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735](https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735).

1. Add the following code to mpdconf
```
audio_output {
 # use the pulse output
    type "pulse"
 # name
    name "My Pulse Device"
 }
```

2. add the following line to /etc/pulse/default.pa
```
"load-module module-native-protocol-tcp auth-anonymous=1" 
```

Apparently it was step 2 that screwed things up. Instead of removing the line (and leaving me with a half functional MPD) I just did a 
```
apt-get remove pulseaudio pulseaudio-esound-compat
```

and then reinstalled the packages again (advised followed from the same link).

Thanks!!!

---

### Post by taavi on 2009-10-23
I installed 9.10 RC today and trying to get mpd working here, but no luck.

My mpd.conf has:

```
audio_output {
    type "pulse"
    name "My Pulse Device"
 }
```

and I added to  /etc/pulse/default.pa: ```
load-module module-native-protocol-tcp auth-anonymous=1
```

I didn't uninstall-remove any packages tho, what effect do they give?

this pulseaudio-esound-compat gets pulled in with pulseaudio reinstall anyway:s

Any better advices what to do next?

In 9.04 i just didn't use pulseaudio so everything worked(tm) : P

EDIT: After I restarted I saw mpd in Sound Preferences -> Applications (Could change volume etc), but the system was mute. I uninstalled mpd overall -- I still want to work this out :'(

---

### Post by cumanzor on 2009-10-23
> **taavi said:**
> I installed 9.10 RC today and trying to get mpd working here, but no luck.

My mpd.conf has:

```
audio_output {
    type "pulse"
    name "My Pulse Device"
 }
```

and I added to  /etc/pulse/default.pa: ```
load-module module-native-protocol-tcp auth-anonymous=1
```

I didn't uninstall-remove any packages tho, what effect do they give?

this pulseaudio-esound-compat gets pulled in with pulseaudio reinstall anyway:s

Any better advices what to do next?

In 9.04 i just didn't use pulseaudio so everything worked(tm) : P

EDIT: After I restarted I saw mpd in Sound Preferences -> Applications (Could change volume etc), but the system was mute. I uninstalled mpd overall -- I still want to work this out :'(

Hmmm I did a few thing more actually. First my .mpdconf file is in my home directory. I applied those two changes I mentioned but I also make MPD run as me (my user name) otherwise it won't have access to my exteral disk (where my music is stored).

---

### Post by WA4MOE on 2009-10-28
Sound not working but also crashes with Firefox, usually directly after loading. The sound stopped working sevarl days before the crashes stated, so have been using Ephiphany- it seems to run ok.

system messages are repeated: 

Oct 28 06:28:20 moses-desktop pulseaudio[3180]: sink-input.c: Failed to create sink input: too many inputs per sink.
Oct 28 06:28:21 moses-desktop last message repeated 5 times
Oct 28 06:29:00 moses-desktop kernel: [226312.710473] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:29:01 moses-desktop kernel: [226313.711826] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:29:03 moses-desktop kernel: [226315.714030] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:29:07 moses-desktop kernel: [226319.718209] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:29:15 moses-desktop kernel: [226327.719048] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:29:31 moses-desktop kernel: [226343.735251] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:30:03 moses-desktop kernel: [226375.737957] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:31:07 moses-desktop kernel: [226439.802171] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:33:16 moses-desktop kernel: [226567.902569] KMF: IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=86 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=66 
Oct 28 06:57:27 moses-desktop -- MARK --

++++++++++++++=

Any suggestions?

---

