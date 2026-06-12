---
title: "Need help with ALSA"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by 4chan on 2010-08-30
hello. i'm using Kubuntu Lucid

i have problem with audio & video playback, i have 5.1 speakers but amarok, vlc, dragon can only give me sound output from rear speakers.

i try anything from [http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound) and [http://www.halfgaar.net/surround-sound-in-linux](http://www.halfgaar.net/surround-sound-in-linux) but none of it fix my problem.

this is my current /etc/asound.conf

pcm.upmix_20to51 {
    type plug
    slave.pcm lowpass_21to21
    slave.channels 3
    ttable {
        0.0     1       # left channel
        1.1     1       # right channel
        0.2     0.5     # mix left and right ...
        1.2     0.5     # ... channel for subwoofer
    }
}

pcm.lowpass_21to21 {
    type ladspa
    slave.pcm upmix_21to51
    path "/usr/lib/ladspa"
    channels 3
    plugins {
        0 {
            id 1098 # Identity (Audio) (1098/identity_audio)
            policy duplicate
            input.bindings.0 "Input";
            output.bindings.0 "Output";
        }
        1 {
            id 1672 # 4 Pole Low-Pass Filter with Resonance (FCRCIA) (1672/lp4pole_fcrcia_oa)
            policy none
            input.bindings.2 "Input";
            output.bindings.2 "Output";
            input {
                controls [ 300 2 ]
            }
        }
    }
}

pcm.upmix_21to51 {
    type plug
    slave.pcm surround51
    slave.channels 6
    ttable {
        0.0     1       # front left
        1.1     1       # front right
        0.2     1       # rear left
        1.3     1       # rear right
        0.4     0.5     # center
        1.4     0.5     # center
        2.5     1       # subwoofer
    }
}

---

### Post by Windows Nerd on 2010-08-30
Check that your front speakers are not muted:

```
alsamixer
```

Try unmuting certain channels that are muted and see if that changes it.

Have the speakers in 5.1 worked before?

Is it only those certain apps that you mentioned that play sound only from the rear speakers?


Scott

---

### Post by 4chan on 2010-08-31
hello thank you for your reply :D

nothing is muted in alsamixer and it is fine with Ubuntu (pulseaudio), all applications related to audio & video playback.

i can has all sounds coming from my 5.1 speakers if in Kmix i unmuted 'duplicate front' but that's not good because when i play dvd i cannot has Dolby 5.1 or DTS but only normal stereo :(

---

### Post by Windows Nerd on 2010-08-31
> **4chan said:**
> hello thank you for your reply :D

nothing is muted in alsamixer and it is fine with Ubuntu (pulseaudio), all applications related to audio & video playback.

i can has all sounds coming from my 5.1 speakers if in Kmix i unmuted 'duplicate front' but that's not good because when i play dvd i cannot has Dolby 5.1 or DTS but only normal stereo :(

So this is an Alsa issue...are you still Using Ubuntu then or a different distro?

This is the only way I think your speakers are muted, as I am no Alsa expert. See the highlighted line below? I might be forcing 3.1 audio. Try changing it to "channels 5". Make a backup if you want before making any changes to the file (cp /etc/asound.conf /etc/asound.conf.bak).

```
pcm.upmix_20to51 {
type plug
slave.pcm lowpass_21to21
slave.channels 3
ttable {
0.0 1 # left channel
1.1 1 # right channel
0.2 0.5 # mix left and right ...
1.2 0.5 # ... channel for subwoofer
}
}

pcm.lowpass_21to21 {
type ladspa
slave.pcm upmix_21to51
path "/usr/lib/ladspa"
[COLOR="Red"]channels 3[/COLOR]
plugins {
0 {
id 1098 # Identity (Audio) (1098/identity_audio)
policy duplicate
input.bindings.0 "Input";
output.bindings.0 "Output";
}
1 {
id 1672 # 4 Pole Low-Pass Filter with Resonance (FCRCIA) (1672/lp4pole_fcrcia_oa)
policy none
input.bindings.2 "Input";
output.bindings.2 "Output";
input {
controls [ 300 2 ]
}
}
}
}

pcm.upmix_21to51 {
type plug
slave.pcm surround51
slave.channels 6
ttable {
0.0 1 # front left
1.1 1 # front right
0.2 1 # rear left
1.3 1 # rear right
0.4 0.5 # center
1.4 0.5 # center
2.5 1 # subwoofer
}
}
```

---

