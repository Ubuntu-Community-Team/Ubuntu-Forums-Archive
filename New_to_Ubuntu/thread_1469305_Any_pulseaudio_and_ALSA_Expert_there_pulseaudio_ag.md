---
title: "Any pulseaudio and ALSA Expert there?? pulseaudio again crash in ubuntu 10.04 LTS."
date: 2010-05-02
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2010-05-02
Hi All

 I'm using Ubuntu 10.04 LTS and kernal 2.6.32-21-generic. whenever I play sound in my system. I get a message below in  syslog . Sometime pulseaudio demeon whill not be running itself.  I noticed the same issue in Ubuntu 10.04 Beta2 also. 

Any pulseaudio or ALSA expert can fix this issue.

```

 pulseaudio[5111]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
pulseaudio[5111]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ca0106'. Please report this issue to the ALSA developers.
 pulseaudio[5111]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

```

---

### Post by vipin.balakrishnan on 2010-05-21
Hi 

Can anyone help me to solve this issue.

---

### Post by 3111994 on 2010-05-30
I have had this problem and i have found a solutionwhen this happen use to have to log out and log back in, but i had a light bulb go off in my head and i said w8 all sound comes from alsa so what i did is

          sudo alsa force-reload

and this fixed the problem temp. until Ubuntu comes out with a patch

---

