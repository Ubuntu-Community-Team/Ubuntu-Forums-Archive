---
title: "Varoius issues (sound in notebook hp6730s) &amp; upgrading convenience"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by webwiller on 2009-05-06
Hi all!
I upgraded my notebook hp6730s from Hardy to Jaunty. As it happened with Hardy I had no sound at all. The fixes that worked for Hardy did NOT work for Jaunty and I went through all solution pages but I was not able to work it out and meanwhile I messed-up something and went for a fresh install of Hardy again. I fixed sound issue fast&easy ('cause I knew how to from hours of research..). Now I was wondering about re-trying an upgrade but while I had Jaunty I did NOT notice any real improvement. Nothing surprised me and I hardly noticed there was any difference (a part from my mute pc!).

My questions are...

With Hardy all I had to do to fix sound was adding a line to the file /etc/modprobe.d/alsa-base, but this wont work with Jaunty which does not find my sound card at all ( doing aplay -l in terminal it says: No soundcard found) and I know it's just a driver issue cause doing lspci -v I can see my soundcard there. Does anybody know what the difference might be? How do I fix this?

My second question is...What is there better, or nicer in Jaunty than Hardy? Do I have a reason to squeeze my head to make it all work?

Ty all guys!!!

---

### Post by webwiller on 2009-05-06
Hey hey hey! One at the time, please! Not alltoghether!!!!! lol ;)

Anyway...I still dont understand what the really improvs are with Jaunty... but this is my ignorance fault probably... also if it would have been nice to be suprised by some nice brand new feature.

But I am here to state that sound issue was a problem caused by the upgrade. I went for a clean install and the workaround adding a line to /etc/modprobe.d/alsa-base.conf worked fine with Jaunty too.

---

