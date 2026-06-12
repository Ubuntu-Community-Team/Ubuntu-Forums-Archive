---
title: "sound card not recognized"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by seraphim23 on 2009-06-16
hey folks, thought I should put up a new thread, with the specific issue at hand

so I have an Hp Dv3 1075 us

My sound has not been working with 9.04.  Ive been trying to figure out whats wrong and so far this is what ive done.

ok, so ive been trying to mess around, i tried something that is supposed to be for kubuntu, didnt work :razz: and now now sound through the headphones.

Ok so by myself ive gotten to the sound troubleshooting page, i know, im stupid. should have gone there first thing, but w/e. So I got there and I was going through the lists and then I saw the "is your soundcard recognized by alsa" so I went trhough the whole alsa diagonstic, and came up with a web page

[http://www.alsa-project.org/db/?f=9f...2d54466ed35570]("http://www.alsa-project.org/db/?f=9f88a7d6cd8eaf2fcb080e152f2d54466ed35570")

Now as you can see, this diagnostic recognized no soundcard on my system and no modules loaded for it.

I checked the 

aplay -l

in the terminal, and I got the "no soundcard" as well

I also ran this command

"lspci -v | less"

and got the list of everything, and I did however find my audio device there


I got this output

"00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Hewlett-Packard Company Device 1506
        Flags: bus master, slow devsel, latency 0, IRQ 5
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

so as you can see, im at a loss. In the troubleshooting maual it says that I might have to go through the BIOS and enable my sound card, well I did go into the BIOS, but I saw no soundcard option.....idk someone have some insight on this?



so the sound card is not recgonized and I have no idea how to fix it, help?

---

### Post by shifty_powers on 2009-06-16
it might sound daft but have you tried

```
alsamixer
```

in a terminal and checked all of the levels?

---

### Post by seraphim23 on 2009-06-16
[FONT=monospace]alsamixer: function snd_ctl_open failed for default: No such file or directory


thats what i get :/
[/FONT]

---

