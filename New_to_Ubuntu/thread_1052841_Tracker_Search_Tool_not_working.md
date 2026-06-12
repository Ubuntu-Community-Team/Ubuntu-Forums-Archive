---
title: "Tracker Search Tool not working"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by futuroimperfetto on 2009-01-28
Hey,

 last week I start poking around installing and unistalling things with the Add/Remove frontend on my Ubuntu 8.04.

I happened to install Beagle to see if it were a better search tool than Tracker. Then I uninstalled it.

I don't know what happened, but now Tracker can't index anything. If I search for anything on my computer I get no results (instead, before it used to work perfectly and scan my whole hard drive).

Is there any way I can kickstart it again? I tried to brutally unistall it and install it again, but I had no luck.

Thanks

---

### Post by Rohag on 2009-02-27
I haven't tried Beagle, but Tracker Search Tool has also stopped working on my Ubuntu 8.10 system. Tried the uninstall/reinstall but still no function.

---

### Post by llamabr on 2009-02-27
I just right clicked, and told mine to re-index.  Have you tried that?

It looks like it just runs trackerd in the background.  Make sure that's running.

Also, check your config file at:

       $HOME/.config/tracker/tracker.cfg

---

