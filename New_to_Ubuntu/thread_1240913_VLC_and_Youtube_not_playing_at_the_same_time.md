---
title: "VLC and Youtube not playing at the same time"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-08-15
Hi,

I am using ubuntu hardy heron. I don hear any audio from VLC player when a youtube video is open in browser. It happens vice versa also. 
I cant use both simultaneously. Its totally annoying,

Is there any solution for this :)

---

### Post by Liolikas on 2009-08-15
Sounds like you use ancient sound system without mixer?
You really have pulse audio in this century produced sound card etc?

---

### Post by stoogiebuncho on 2009-08-15
Sound in Hardy is, unfortunately, not that great.  As I understand it, hardy uses a mixture of PulseAudio and ALSA, and sometimes they don't want to share your sound card and that's why you will only be able to hear the output from one program.

I had the same issue in Hardy - I agree it is quite annoying.  After updating to Jaunty, everything worked great.

If you don't want to upgrade to Jaunty, there is another trick I used that solved *some* of the conflicts, but not all of them.

1) Install these packages:
alsa-firmware
alsa-firmware-loaders
alsa-mixer-gui

2) Go to Preferences > Sound and set everything to ALSA

I can't remember if you have to restart or not.  I don't think so.

As I said, this didn't solve everything for me, but it solved more than half of the problems I was having.  However, if it's really bothering you, I'd recommend upgrading to Jaunty.

---

