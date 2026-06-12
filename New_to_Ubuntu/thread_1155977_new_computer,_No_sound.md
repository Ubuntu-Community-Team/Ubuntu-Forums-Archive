---
title: "new computer, No sound"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by hellomoto on 2009-05-11
Hi guys,

Got a new laptop today, loaded on 9.04 everything seams to be running well apart from a lack of sound. 

Can anyone please advise as possible solutions to this?

lspci:

```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

lspci -n:
```

00:00.0 0600: 8086:2a40 (rev 07)
00:02.0 0300: 8086:2a42 (rev 07)
00:02.1 0380: 8086:2a43 (rev 07)
00:03.0 0780: 8086:2a44 (rev 07)
00:19.0 0200: 8086:10f5 (rev 03)
00:1a.0 0c03: 8086:2937 (rev 03)
00:1a.1 0c03: 8086:2938 (rev 03)
00:1a.2 0c03: 8086:2939 (rev 03)
00:1a.7 0c03: 8086:293c (rev 03)
00:1b.0 0403: 8086:293e (rev 03)
00:1c.0 0604: 8086:2940 (rev 03)
00:1c.1 0604: 8086:2942 (rev 03)
00:1c.2 0604: 8086:2944 (rev 03)
00:1d.0 0c03: 8086:2934 (rev 03)
00:1d.1 0c03: 8086:2935 (rev 03)
00:1d.2 0c03: 8086:2936 (rev 03)
00:1d.7 0c03: 8086:293a (rev 03)
00:1e.0 0604: 8086:2448 (rev 93)
00:1f.0 0601: 8086:2917 (rev 03)
00:1f.2 0106: 8086:2929 (rev 03)
01:00.0 0280: 8086:4232
05:0b.0 0607: 1180:0476 (rev ba)
05:0b.1 0c00: 1180:0832 (rev 04)
05:0b.2 0805: 1180:0822 (rev 21)
05:0b.3 0880: 1180:0843 (rev ff)
05:0b.4 0880: 1180:0592 (rev 11)
05:0b.5 0880: 1180:0852 (rev 11)

```

aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

thanks

---

### Post by Triptol on 2009-05-11
I guess you did check alsamixer to see that your channels are actually unmuted?

---

### Post by hellomoto on 2009-05-11
yeh, they are all unmuted

---

### Post by hellomoto on 2009-05-11
anyone  else able to offer any solutions? Thank you.

---

### Post by hellomoto on 2009-05-11
i have just compiled the latest version of alsa mixer (1.0.20) from source and that didn't help the problem. 
~

coould really use some help guys

---

### Post by hellomoto on 2009-05-11
I have solved this problem myself by following the instructions on this link:

[http://ubuntuforums.org/showthread.php?t=1117238]("http://ubuntuforums.org/showthread.php?t=1117238")

---

