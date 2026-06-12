---
title: "Easier way to switch between Ubuntu/Windows XP"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by sashag on 2011-03-07
Hi!

I am having a problem with switching between Windows XP and Ubuntu.
The reason is that I set the 'boot up time' to only one second, so now, whenever the computer boots up, it doesn't give me enough time to put it to Ubuntu since Windows XP is the 'default' OS. Is there a way to get into Ubuntu at startup to change the boot up time? Since I didn't download Ubuntu to run 'inside' Windows, I can't even select the OS that I want to start at boot up in Windows. Anyway, I wanted the OS's to boot faster, but NOT that fast:D Thanks!

---

### Post by oldfred on 2011-03-07
Start hitting down arrow as soon as BIOS is part way thru. At some point it remembers key strokes.

Then reset startup time.

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Or you can change the grub file from a liveCD.

---

### Post by sashag on 2011-03-08
Hi!

Thanks for the suggestion. It seemed to have helped the problem. I already had the Startup Manager downloaded, so I went back in and
then I 'reset' the timeout to 5 seconds. However, when I tried out the new 'timeout' and the timeout reached 'zero', nothing happened!
I still saw the boot screen. Anyway, thanks for the help, I will keep it in mind the next time I fool around with the OS!

---

### Post by oldfred on 2011-03-08
I primarily boot Ubuntu and very occassionly now XP. Standard settings have worked for me, so I have not changed. drs305 has several threads discussing the issues on various timeout settings.

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

---

