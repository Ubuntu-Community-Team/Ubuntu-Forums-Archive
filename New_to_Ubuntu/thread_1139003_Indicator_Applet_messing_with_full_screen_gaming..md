---
title: "Indicator Applet messing with full screen gaming."
date: 2009-04-26
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-04-26
Ok is there anyway to remove this thing but still keep pidgin there? I remember in the older ones i could set it to be there but not notify. Yes the notifications are very nice. But ingame they go over everything else. I can't no matter what i do disable the "someone signed on" message. That's very annoying as it messes up the ingame display. I attempted to remove the events in pidgin and that doesn't seem to do it. So is there anyway to fix this?

---

### Post by Didius Falco on 2009-04-26
In the Pidgin menu go to Tools/Plugins and uncheck the "libnotify" plugin.

---

### Post by 133794m3r on 2009-04-28
ok thanks :D it helped me.

---

### Post by Didius Falco on 2009-04-28
You are welcome!!

---

### Post by mfearby on 2009-05-04
> **Didius Falco said:**
> In the Pidgin menu go to Tools/Plugins and uncheck the "libnotify" plugin.

Thanks, helped me, too. I thought I would solve this by getting rid of the Indicator applet from my startup applications, but I still kept getting these Pidgin popups.

---

### Post by Didius Falco on 2009-05-04
Gotta love a twofer.  :guitar:

---

### Post by akoskm on 2009-05-04
Hmm... that was a solution. :)
Can I disable the popup message on full screen gaming (video, etc) - I don't want to disable completely, just to prevent it from popping up when something is running on fullscreen.
Thank you!

---

### Post by kpkeerthi on 2009-05-04
Yes. I find this annoying too. I filed a bug report for this very issue.
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/371529]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/371529")

---

### Post by Didius Falco on 2009-05-04
[COLOR=Red]NOTE:[/COLOR] I found this via Google. I haven't used it and won't be and take no responsibility for any ill effects from using it:

[http://www.zybez.net/community/index.php?showtopic=1229881&st=0&p=11271973&#entry11271973](http://www.zybez.net/community/index.php?showtopic=1229881&st=0&p=11271973&#entry11271973)

Note that you'll have to disable them and reboot (Maybe logging out and back in would do it...not sure)

Same thing to re-enable them.

---

### Post by prvteprts on 2009-06-01
I have had a similar experience.

When I play a video in fullscreen, then someone messages me, the message notification does not popup, but somehow causes the playback controls to popup. And then when the video window closes, the popup notifications do not work anymore, and sometimes after that, the indicator applet crashes. (I understand the indicator applet and the notify-osd are different)

I need the notifications but, maybe they could get fixed so they don't affect or get affected by fullscreen mode either in gaming or video.

(Perhaps these details could be added to the already filed bug report?)

---

### Post by bj0 on 2009-06-08
A really nice feature would be to add a 'toggle' feature on the right-click menu that would turn off pop-ups until you re-enable it.

Compiz + Full screen OpenGL games + notification pop-ups are really annoying.

---

### Post by prvteprts on 2009-06-17
> **bj0 said:**
> A really nice feature would be to add a 'toggle' feature on the right-click menu that would turn off pop-ups until you re-enable it.

Compiz + Full screen OpenGL games + notification pop-ups are really annoying.

+1

A good suggestion.

---

