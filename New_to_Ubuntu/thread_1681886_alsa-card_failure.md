---
title: "alsa-card failure"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by liatodua on 2011-02-04
Hi,

I have ubuntu on IBM T30 laptop.

Just discovered that user log reports full with lines like this:

Jan 25 08:54:55 LT pulseaudio[1290]: module-alsa-card.c: Failed to find a working profile.
Jan 25 08:54:55 LT pulseaudio[1290]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jan 25 08:54:56 LT pulseaudio[1364]: pid.c: Daemon already running.
Jan 25 08:55:01 LT pulseaudio[1290]: ratelimit.c: 2 events suppressed
Jan 25 19:18:44 LT pulseaudio[1290]: ratelimit.c: 1 events suppressed
Jan 25 20:08:10 LT pulseaudio[1290]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 336016 bytes (1904 ms).
Jan 25 20:08:11 LT pulseaudio[1290]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.

What should I do?

---

