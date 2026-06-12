---
title: "Playing music file simultinously"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-10-13
Hi,

    I'm using Ubuntu 8.04LTS and kernel version 2.6.24.24 Generic. How can I play two music file simultinously in Ubuntu 8.04 LTS. Now when I try to play two file other one Will not play. Can anyone tell me what is the reason behind it and how to solve this issue.

Regards,
Vipin Balakrishnan.

---

### Post by freak42 on 2009-10-13
I'm not an expert with the linux audio architecture, but I think some sound servers/daemons/whatever only support one audio stream (namely OSS?), see what sound 'device' you have chosen in system->sound preferences for sound playback and try switching to ALSA or Pulse Audio if you can?

hth

---

### Post by anaconda on 2009-10-13
hmm..

I can play two files simultineously! And I have not changed any audio settings after installation.

However It seems that I need to use 2 different programs. eg. totem and VLC (of kaffeine).

---

### Post by vipin.balakrishnan on 2009-10-13
Hi,

    That is fine. But my problem is I can open two file But the sound come only from the first file opened. Can anyone tell me a solutions for this problem. For Video files also the same problem I'm getting..

---

### Post by vipin.balakrishnan on 2009-10-13
Hi,

   Atlast I found a solution for my problem after a long search in internet. Here I'm giving for people those who have the same problem....

 [https://help.ubuntu.com/community/EnableSoftwareMixin]("https://help.ubuntu.com/community/EnableSoftwareMixing")g

 After doing the above url steps sometime If you play youtube and local mp3 file simultinously sound wont come. This due to bug in pulse audio that can  be fix by below URL.
[http://warrence.com/tech/?p=12](http://warrence.com/tech/?p=12)

---

### Post by sandyd on 2009-10-13
```

sudo apt-get remove pulseaudio*

```
try that.

---

