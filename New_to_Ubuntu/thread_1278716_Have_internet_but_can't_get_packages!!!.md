---
title: "Have internet but can't get packages!!!"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by VikingMetalGod on 2009-09-29
Hi, big time noob here so bear with me. I have installed Jaunty on my Dell Latitude D800. I can't get the wireless card to work. I did my research in the Ubuntu forums and found that my Broadcom wireless card needs some fiddling to get working. That's only the issue that led to my current problem. I can't get packages after putting the proper command into terminal. (I would post that command for reference sake but I don't actually have my Ubuntu machine with me at the moment. It was a sudo command.) I tried to see if my internet was working at all (connected to ethernet) and I can get websites through firefox but absolutely nothing through terminal, synaptec, or update manager. When I go to a site that has flash content and try to install the plugins through the browser, it still says it can't find anything. I'm confused and frustrated. Sorry for the long winded message. Anyone have a clue? :confused:

---

### Post by fiddler616 on 2009-09-29
Get back on the internet with your Cat5 port (ethernet), and then go to System>Administration>Hardware Drivers. There should be an option to check for drivers--use it. My memory is getting flaky, but I believe it'll give you the option to install the Broadcom wireless driver (do it--accepting the warning about not using free software). Then see if you can use the wireless card (use the network applet in the panel).

If that doesn't work...wait for someone more knowledgeable than I to come along. For your not-being-able-to-install packages problem, it may be that you typed something in wrong (it'd be really fantastic if you could give us the gist of the error you get), or there may be a problem with the package providers...

---

### Post by VikingMetalGod on 2009-09-29
As far as typing the commands wrong, it was copy and paste from a number of sources (how to's and such). Terminal would tell me "E: could not find package" or along those lines. Or if i went to myspace.com a bar would pop up in firefox saying that I need plugins to view all the material on the site. (myspace is riddled with stupid flash stuff). When I would try to install any of the three availible plugins it showed me, it would also say "could not find xxxxx" to whatever plugin i choose. Very strange.

Also when I go to hardware drivers, nothing shows at all. Why would nothing show up there or in automatic updates if i'm indeed getting internet? I would assume there would be a long list of updates after a fresh install...

Thanks for your quick response! And killer avatar BTW :)

---

### Post by Miljet on 2009-09-29
Try going to System -> Administration -> Software sources. You will have to enter your password. Then check to make sure that all four repositories are checked. Also make sure that an appropriate download source is selected. If the CD ROM selection is checked, remove the check beside that. Then close and try again to install some package.

---

