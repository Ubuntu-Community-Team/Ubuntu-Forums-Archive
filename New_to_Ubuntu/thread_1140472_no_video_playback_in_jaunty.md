---
title: "no video playback in jaunty"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by alphasurfari on 2009-04-27
I recently upgraded from a fresh install of ibex (8.10) to Jaunty (9.04). I installed the restricted extras package after upgrading.

Neither VLC nor the built in video player will play .avi files, or any video files I have. These videos played fine in Ibex. VLC and the movie player crash immediately when trying to open any video file.

I have seen a few threads about video driver issues but I am new at this and they don't seem to describe this specific problem. I do not have jerky or slow playback. Just none.

My computer is a dell optiplex 170L. Here are the specs if that is helpful: [http://support.dell.com/support/edocs/systems/op170l/en/UG/specs.htm](http://support.dell.com/support/edocs/systems/op170l/en/UG/specs.htm)

Thanks.

---

### Post by alphasurfari on 2009-04-28
No ideas?

---

### Post by Praxicoide on 2009-04-28
Intel video drivers have been blacklisted in Jaunty. There are several people with video issues right now. Do a search for "Intel Jaunty" in the boards and you will find some workarounds.

---

### Post by alphasurfari on 2009-04-28
indeed i have, but none seem to be clear enough for me to get through. i am hoping for a 'step by step' solution, or an update that will fix it for me.

---

### Post by MockY on 2009-04-28
I simply didn't upgrade my laptops at all due to the Intel issue. I won't do such until there is an official fix for this, and not just some workaround that might break down the line.

---

### Post by cariboo on 2009-04-28
I was having a bit of a tearing problem when playing back videos, I installed the drivers from [here]("http://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/"), video quality seems better and my tearing problem went away.

---

### Post by Praxicoide on 2009-04-29
If it is an intel issue, this guide seems very thorough.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Mocky is correct, though, in saying that this is a workaround, one that involves installing a kernel still under testing.

---

### Post by Marat Galiev on 2009-04-29
You have compiz enabled?

---

