---
title: "Problems with Amarok (mplayer, vlc, totem etc) + Youtube and alike."
date: 2009-02-04
forum: New to Ubuntu
---

### Post by kajman on 2009-02-04
It is impossible to listen to music using Amarok (or to watch any movie using mplayer, vlc or totem) when I have an open tab in firefox with youtube movie in it. I doesn't have to be playing at all, being there is enough to cause problems.
It's REALLY annoying. I have to restart Amarok if I try to play something having any youtube movie open in firefox, because it freezes.
An the other way: If I listen to music using Amarok, or watch a movie using one of the players, I can watch a movie in youtube but without any sound.

So maybe something with sound drivers? Or something similar.

Any solutions?

---

### Post by klytu on 2009-02-04
> **kajman said:**
> It is impossible to listen to music using Amarok (or to watch any movie using mplayer, vlc or totem) when I have an open tab in firefox with youtube movie in it. I doesn't have to be playing at all, being there is enough to cause problems.
It's REALLY annoying. I have to restart Amarok if I try to play something having any youtube movie open in firefox, because it freezes.
An the other way: If I listen to music using Amarok, or watch a movie using one of the players, I can watch a movie in youtube but without any sound.

So maybe something with sound drivers? Or something similar.

Any solutions?

Might be that your soundcard is not configured to handle multiple apps at the same time. Try searching the forums for that issue and you may find a solution. I remember having a similar issue with an older version of Ubuntu, but I was using different hardware. I found a solution at the time by doing a similar search.

Here are the results of a sample search to get you started:

[http://ubuntuforums.org/search.php?searchid=55289363](http://ubuntuforums.org/search.php?searchid=55289363)

---

### Post by kajman on 2009-02-04
Hmmm... when I click on the link you've provided i get the following message: 
vBulletin Message
Sorry - no matches. Please try some different terms.

---

### Post by klytu on 2009-02-05
> **kajman said:**
> Hmmm... when I click on the link you've provided i get the following message: 
vBulletin Message
Sorry - no matches. Please try some different terms.

Sorry about that. Try typing the words "sound", "multiple", and "apps" in the search area. You'll get the results I was trying to direct you to. If you read through some of the shorter ones, you may find some quick things to try (like setting your sound server to ALSA, for example) One of the best threads for more detailed sound troubleshooting is the [[COLOR="Blue"]_Comprehensive Sound Problem Solutions Guide_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by kajman on 2009-02-05
Ok, I've solved it.

The solution was to change every option in system->preferences->sound to ALSA, and then same thing in Amarok, mplayer and every other app that expirienced this problem.

Thanks for your help.

---

