---
title: "New Convert to Ubuntu, but..."
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Zenmij on 2009-03-31
I recently switched my entire OS to Ubuntu from Windows and am very happy except for two recurring issues which I haven't been able to solve.

1, Sometimes when using the version of Firefox from the repos it will crash when viewing youtube. This usually happens as soon as I click to view a new video.

2, There is something up with the sound - If I have been watching some videos (on youtube for example) and want to play a game, I usually have to re-boot as I get no sound and vice-versa. 

I can't really hazard a guess at why this is happening and hoped someone else might have stumbled upon these issues already.

Thanks.

---

### Post by mike555 on 2009-03-31
I also had trouble with crashing , till I installed the latest Flash from their site ....
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by ibuclaw on 2009-03-31
What you are describing sounds like a Pulse/ALSA configuration issue.

How many soundcards do you have present on your Desktop? And what type of arch did you install (32bit, 64bit)?

If you installed the 64bit version, I found that uninstalling the adobe-flashplayer and getting the 64bit beta version from the Adobe Labs helped me substantially with any issues.

With soundcard configuration. Looking up and installing **asoundconf-gtk** from the **Synaptic Package Manager** may help if you have more than one soundcard and would like to allow easy switching.

Also, for know-how on installing some really nice non-free features that may help your overall experience:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

