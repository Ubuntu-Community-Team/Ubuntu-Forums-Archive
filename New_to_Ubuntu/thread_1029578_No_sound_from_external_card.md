---
title: "No sound from external card"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by CinemaScope on 2009-01-03
Can someone shed some light on this for me? I have a Sound Blaster SB Live USB external sound card. In System/Sound devices, "Creative Technology SB Live! 24-bit external USB Audio (OSS)" works when I test it (I hear the series of test beeps). But when I actually play a music CD or a video DVD (in say Kaffeine or VLC), there is no sound output. :(
Thanks.

---

### Post by CinemaScope on 2009-01-04
Just bumping this: I do not have an internal sound card, only the USB external card, so until I get this solved I don't have sound on my Ubuntu machine. Why is it the sound check works, but Kaffeine or VLC does not give off sound?

---

### Post by tomtom1982 on 2009-01-04
Please open a terminal, type in

```
cat /proc/asound/cards 
```

and post the output.

Please also post the output of

```
lsusb
```

---

### Post by CinemaScope on 2009-01-05
TomTom -- here's the terminal results (I don't of course know what it all means!). Does this shed some light on my problem?
Thanks.  


john@Complete7:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC658D at irq 17
 1 [External       ]: USB-Audio - SB Live! 24-bit External
                      Creative Technology SB Live! 24-bit External at usb-0000:00:1d.2-2, full speed



john@Complete7:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 041e:3040 Creative Technology, Ltd SoundBlaster Live! 24-bit External SB0490
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by CinemaScope on 2009-01-12
Sorry, just bumping this back up. Any ideas why I can't hear sound with this card? Thanks.

---

