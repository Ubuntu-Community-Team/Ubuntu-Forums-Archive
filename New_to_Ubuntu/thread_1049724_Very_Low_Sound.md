---
title: "Very Low Sound"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by rob_gf on 2009-01-24
I have just installed Ubuntu 8.04 on an Everex Stepnote 1502.  I have never used linux before, but I like what I see so far except I cannot hear any sounds.  I have put the volume on the taskbar to max, the volume on the notebook to max, and neither works.  I can hear a little sound when on Youtube, with the youtube volume at max.  The audio worked fine while using vista yesterday.  

Any ideas or suggestions?

Thanks

---

### Post by Michael.Godawski on 2009-01-25
hi,

have a look at this general guide first:


[LIST]
[*][https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[/LIST]

then please post the result of this Terminal command:
```

sudo lshw -C multimedia
```

---

### Post by rob_gf on 2009-01-25
*-multimedia            
       description: Audio device
       product: VIA High Definition Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by diablo75 on 2009-01-25
Double-click on that little speaker icon in your upper panel.  Click on the Preferences button.

Check off all sound sources (e.g., "Front PCM", "Front", "Surround PCM", "Surround", "Center PCM" etc.).  Basically anything that looks like it could produce sound.

Click OK.

After the sound levels have been added to your mixer, play with the new levels that have been added while playing some music in the background.

---

### Post by habtool on 2009-01-25
alsamixer -Dhw

---

### Post by rob_gf on 2009-01-25
> **diablo75 said:**
> Double-click on that little speaker icon in your upper panel.  Click on the Preferences button.

Check off all sound sources (e.g., "Front PCM", "Front", "Surround PCM", "Surround", "Center PCM" etc.).  Basically anything that looks like it could produce sound.

Click OK.

After the sound levels have been added to your mixer, play with the new levels that have been added while playing some music in the background.

I did that and it worked fine.....Thanks all for your help

---

### Post by diablo75 on 2009-01-25
:)  Slam dunk!

---

### Post by deeflex on 2009-06-16
> **habtool said:**
> alsamixer -Dhw

Thanks this helped me by raising the "Side" channel to max!

---

