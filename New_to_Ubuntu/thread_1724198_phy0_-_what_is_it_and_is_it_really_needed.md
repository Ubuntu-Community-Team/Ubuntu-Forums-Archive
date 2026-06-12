---
title: "phy0 - what is it and is it really needed?"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2011-04-08
Curious as to why music when playing stutters, I ran 'top' from terminal and noticed 'phy0' hogging upto 60% CPU at the same time the music stutters. The phy0 only lasts a couple of seconds, and when it dissapears from top, the music plays smoothly again until phy0 pops up again.

I'm wondering what phy0 actually does; if it's checking for something on-line, can it be disabled and if it can, will it have an adverse effect on my PC in a disabled state?

I'm running Ubuntu 10.04.2, on a Sempron 3300+ desktop. It has 2g ram (max) installed.

It doesn't seem to matter which music app is playing at the time either.

I've included a screenshot of 'top' showing the dreaded phy0 issue in progress.

Any help would be very much appreciated.

Baldrick

---

### Post by kyle6513 on 2011-04-08
[http://www.linuxquestions.org/questions/linux-newbie-8/phy0-using-100-cpu-sluggish-ubuntu-9-10-a-819002/](http://www.linuxquestions.org/questions/linux-newbie-8/phy0-using-100-cpu-sluggish-ubuntu-9-10-a-819002/)

Seems that it is your NIC causing the problem. Is it an Atheros card? Does disabling/removing it cure the problem?

---

### Post by Baldrick_NZ on 2011-04-08
> **kyle6513 said:**
> [http://www.linuxquestions.org/questions/linux-newbie-8/phy0-using-100-cpu-sluggish-ubuntu-9-10-a-819002/](http://www.linuxquestions.org/questions/linux-newbie-8/phy0-using-100-cpu-sluggish-ubuntu-9-10-a-819002/)

Seems that it is your NIC causing the problem. Is it an Atheros card? Does disabling/removing it cure the problem?

After checking 'lspci' in terninal, it would appear that I have an Atheros wifi card installed. 

Since I'm using an ethernet connection I'll remove the offending card and see if that makes any difference. I'll report back my findings.

Thanks for your help thus far!

Is there an easier way of disabling the Atheros card without removing it? I'll try unticking 'enable wireless' in network manager first to see whther that fixes it.

---

### Post by Baldrick_NZ on 2011-04-08
Disabling it in network manager wasn't enough, I had to remove the card altogether.

Any suggestions as to what type of replacement wifi card I should get? I'm sure I'll want to go wireless someday again.

I also removed an old TV Card which doesn't get uesed any more, so two more free PCI slots..

So, yep, prob solved.

Thanks again!

---

### Post by kyle6513 on 2011-04-08
No problem mate, glad I could help. I do think, if we find out what this phy0 does, we should be able to figure out what the problem is and if we could disable phy0 altogether. I have an Atheros card aswell and don't have this process at all. Of course, I'm installing 11.04 at the moment and I'll run a few more tests. Ultimately I hear Atheros cards are quite uh, hated. I don't understand considering the sources for the drivers have been released. I'll get back to you, but I highly doubt you'll need to buy another card ;).

edit:
Just tested while running banshee with my card connected. Couldn't even find the process phy0. I'll have a google around for it.

Figured it out, it's evidently a bad driver for 5k cards. I'm not sure if there are any more suitable drivers, (meanwhile I use an 8k card). I'll have a look around for a fix.

[http://ubuntuforums.org/showthread.php?t=1191012](http://ubuntuforums.org/showthread.php?t=1191012)
turned up this, that's about it. Pretty hard to find this, good luck on your searching!

---

