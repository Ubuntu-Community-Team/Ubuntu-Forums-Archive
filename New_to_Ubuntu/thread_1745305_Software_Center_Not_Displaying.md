---
title: "Software Center Not Displaying"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Shie6meepo on 2011-04-30
I was in Ubuntu Software center (running 11.04, in case it matters), and as it was doing some Firefox updates I tried to uninstall Epiphany Web Browser, which I tried for a dew days and found not to my liking. When it started slowing down, I went into the in progress page and cancelled the Epiphany thing, thinking I would do it after I was done installing the Firefox updates. When I went back to Software Center after the updates, it just gave me a blank window and has been doing so for half an hour. I've tried opening a program link in Software Center, and it didn't work either. any ideas?


[IMG]http://i56.tinypic.com/11w593m.png[/IMG]

---

### Post by RJ12 on 2011-04-30
I may not be able to help as much as others, but I'm sure someone is going to ask you to open up the terminal and type in
```
software-center
```

and post the output, at least now someone can skip this step of asking you and get directly to fixing it :)

---

### Post by gtaskeraus on 2011-05-08
I got this problem after I opened, or tried to open, a Debian package with the software centre.

I cleared out the config files but still no luck.  Running it from the terminal produced no messages at all to speak of.

I completely removed the package and re-installed it. Still no luck.  I'm not sure where else to go to get it back to "normal".  I guess I'm stuck with synaptic for now.

---

### Post by nonabhai on 2011-05-21
Same problem with me! :-(

---

### Post by wildmanne39 on 2011-05-21
> **nonabhai said:**
> Same problem with me! :-(

Hi, try these commands one at a time, one right after the other.```

sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Big Lizard on 2011-05-22
[obviously a dead thread]

---

