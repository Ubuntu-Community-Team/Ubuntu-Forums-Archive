---
title: "High CPU usage since uprgade"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by lsaplai on 2009-04-26
Hello everyone

I upgraded to Ubuntu 9.04 on Friday. Since then my CPU is running at 50% or more (it was at about 75% with System Monitor running) even with no app opened.
Running Top, I noticed Xorg is always toward the top of the list.

Consequently, the computer fan is also running at high (noisy) speed.

My system is a 3GHz Intel with 1GB of memory.

Any help in getting this CPU down would be greatly appreciated.

---

### Post by Sidewinder1 on 2009-04-26
Perhaps the problem is in the bug listed in this thread:
[http://ubuntuforums.org/showthread.php?t=1114261](http://ubuntuforums.org/showthread.php?t=1114261)
Hope I'm wrong...
Side

---

### Post by 4Orbs on 2009-04-26
If you have the little system monitor applet on your panel, try removing it then put it back after a reboot.

---

### Post by lsaplai on 2009-04-29
Hi Guys,

Thanks for the suggestions. I had already removed the tracker (which was having problems indexing my disk anyway) and removed the System Monitor.

Unfortunately, CPU usage is still pretty high: at least 30% when starting a work session then stabilising at about 40% when at rest.

An my system fan is on high gear and making almost as much noise as it possibly can.

Once again, on the top of the "TOP" list and besides my currently running apps, I find Xorg, if that's any indication.

Thanks in advance for any additonal help.

---

### Post by lsaplai on 2009-04-30
bump

Anyone has any suggestion as what could be the problem?

---

### Post by sandyd on 2009-04-30
sudo apt-get remove vino-server

does that help?

---

### Post by DavidTangye on 2009-05-01
There are many posts here all repeating your issue. For a solution see the launchpad bug reports, in this case [this one is good]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912") and there are many duplicate reports there too.
I can recommend you search before posting issues, especially [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), as your answers are often already there, and it saves these forums being filled with 10,000 'me too' issues.

---

### Post by lsaplai on 2009-05-01
@DavidTangye: thanks for the pointer, I am not familiar with launchpad. I did search the forum before posting and had already removed Tracker from my system, so it is not the one causing the issue any longer.

Problem is that despite tracker being disabled, my CPU usage is still hovering at around 50% and my system fan runs quite high (it's normally very silent when running the same apps but since I upgraded it works a lot more).

I'm only running Opera (which my use up memory resources but is not that CPU  intensive - I actually just closed a few tabs but it doesn't seem to nake any difference) and Evolution + Nautilus and a console.

I have just removed Vino from my start up apps. I'll report later if it makes any difference.

Thanks again for your help and any new suggestion is greatly appreciated.

Cheers!

---

### Post by lsaplai on 2009-05-01
OK, low and quiet...

After disabling Vino and restarting the computer (for good measure) It seems my CPU is under control again.

In all honesty, I might have to blame a bit also on the Flash plugin in Opera: I had a few pages opened previously with intense flash appelts (such as videos) and it seems just having them was sucking up quite a bit of resources. Interesting part is that they were not causing problems in Ubuntu 8.10.

Anyway, everything "sounds" good now.

Thanks a lot for your help and insight!

Cheers!

---

### Post by fjpos on 2009-05-04
> **carlee said:**
> sudo apt-get remove vino-server

does that help?

Hi 
It worked for me

---

### Post by Mattman624 on 2009-05-10
Does vino-server come with the normal install/upgrade of 9.04?

---

