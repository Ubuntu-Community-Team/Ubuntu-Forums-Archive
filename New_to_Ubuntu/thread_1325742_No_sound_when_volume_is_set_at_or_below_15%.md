---
title: "No sound when volume is set at or below 15%"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by zorblek on 2009-11-13
Ever since I installed Karmic, I've been having a problem with sound volume. When the volume slider is set at or below 15%, I get no sound. It doesn't fade out, it just goes from 15% straight to mute (although the icon doesn't say it's muted until the slider is at 0%). This is system-wide, regardless of what program the sound is coming from.

Does anybody know what might be causing this?

---

### Post by brandonsh on 2009-11-13
Maybe bad sound drivers or low volume on the speakers themselves?

---

### Post by kansasnoob on 2009-11-13
> **zorblek said:**
> Ever since I installed Karmic, I've been having a problem with sound volume. When the volume slider is set at or below 15%, I get no sound. It doesn't fade out, it just goes from 15% straight to mute (although the icon doesn't say it's muted until the slider is at 0%). This is system-wide, regardless of what program the sound is coming from.

Does anybody know what might be causing this?

What version of Ubuntu?

Post the output from Terminal of:

```
cat /etc/issue
```

---

### Post by zorblek on 2009-11-13
> **brandonsh said:**
> Maybe bad sound drivers or low volume on the speakers themselves?

I don't know about the drivers, but it's definitely not just low speaker volume. It jumps from a moderate volume to complete silence.

Here's the output of cat /etc/issue:

> Ubuntu 9.10 \n \l

Before I installed Karmic, I used several previous versions of Ubuntu on this same computer with no volume problems. I did a clean install of Karmic rather than an upgrade, if that matters.

---

### Post by zorblek on 2009-11-13
I filed a bug report, and someone there pointed me to [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies"). The first fix listed there dealt with the problem.

Thanks for your suggestions!

---

### Post by kansasnoob on 2009-11-13
> **zorblek said:**
> I don't know about the drivers, but it's definitely not just low speaker volume. It jumps from a moderate volume to complete silence.

Here's the output of cat /etc/issue:



Before I installed Karmic, I used several previous versions of Ubuntu on this same computer with no volume problems. I did a clean install of Karmic rather than an upgrade, if that matters.

OK if you have a VIA VT82xx sound card the problem is largely solved with proposed linux-image-2.6.31-15-generic.

You can check your audio card version by running:

```
lspci | grep Audio
```

What they did was move the VIA-DXS toggles to PCM in the alsa-mixer.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451813)

---

### Post by zorblek on 2009-11-14
I have onboard Intel audio. The output is of "lspci | grep Audio" is:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

