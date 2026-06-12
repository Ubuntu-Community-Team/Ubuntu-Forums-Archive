---
title: "Intel ALC883 + ubuntu blues!"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by shreeyashattal on 2010-09-06
I have been tryin over a month to sort and get my 5.1 surround sound working on my Intel ALC883 card, however it somehow just does not work.. Here is my edited /etc/pulse/daemon.conf file...
```

; default-sample-format = s16le
; default-sample-rate = 44100
 default-sample-channels = 6
; default-channel-map = front-left,front-right


```Somehow my sound card shows multiple input options but only one output option! I get various types of line in and mic inputs, but only one output.. Is there a hack to get system to treat other ports as output rather than multiple output? Maybe the pulse/alsa is treating the ports wrong

My aplay -l results are ```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Is there anything wrong i'm doing? Perhaps a .asoundrc file? or a complete switch of sound drivers??

---

### Post by mastablasta on 2010-09-06
Surrond or digital sound coupled with Intel has poor linux support it would seem. i got some issues resolved by upgrading alsa. i could turn on the digital sound on, however it didnt' work in duplex mode (i.e. mic wasn't working in that option), so i now use analog instead.

---

### Post by shreeyashattal on 2010-09-06
> **mastablasta said:**
> Surrond or digital sound coupled with Intel has poor linux support it would seem. i got some issues resolved by upgrading alsa. i could turn on the digital sound on, however it didnt' work in duplex mode (i.e. mic wasn't working in that option), so i now use analog instead.

i got no issues with no working mic.. can u please guide me to switch to alsa?

i'm tired of this screen in alsamixer(chk attachment)
:(

---

### Post by mastablasta on 2010-09-07
these are my support threads:
[http://ubuntuforums.org/showthread.php?p=9644308#post9644308](http://ubuntuforums.org/showthread.php?p=9644308#post9644308)
 
[http://ubuntuforums.org/showthread.php?p=9705500#post9705500](http://ubuntuforums.org/showthread.php?p=9705500#post9705500)
 
maybe one of these can help you clear out what is happening.
 
i upgraded alsa following these instructions:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
note that the tools needed for upgrade are quite big and they might take time to download (depending on your internet connection)

---

