---
title: "random cut off characters"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by chris doe on 2011-04-22
Hi.

Very new newbie here.

I've installed Ubuntu 10.10 recently, after experimenting with Ubuntu since HH. This is the first time this has happened: beginning a couple of days, characters on the screen are simply cut off. It happens, afaik, with most characters, random, but let me show you right now:
a b c d e f g h j k l m n o p q r s t u v w x y z

(screenshot attached of above paragraph)

There's a second attchmnt with another instance, where r isn't showing...

This mostly happens with Firefox (4) (can't say right now that it happens only in FF...)

I honeslt don't recall recent installs/ uppgrades of drives / software that interferes with visuals.

I have a HP Pavillion Entertainment Notebook 5 years old, and am at a loss right now as how to find other information you may need to help me solve this...

Thank you!

---

### Post by sanguinoso on 2011-04-22
Try running this command: ```
sudo apt-get install msttcorefonts
```

All it does is install some extra fonts. Which may be why they aren't displaying.

---

### Post by chris doe on 2011-04-22
Thank you for your quick reply.

Tried, got this message:
> Note, selecting 'ttf-mscorefonts-installer' instead of 'msttcorefonts'
ttf-mscorefonts-installer is already the newest version.
ttf-mscorefonts-installer set to manually installed.


---

### Post by sanguinoso on 2011-04-22
Hmm so its already installed... Does this only happen in firefox or does it occur elsewhere in ubuntu?

---

### Post by chris doe on 2011-04-22
Haven't seen it happen elsewhere (yet?).

You gave me an idea, and I changed fonts in FF preferences, but it's still happening with several fonts, serif or sans,using the site's font or defining it myself.

I'll try reinstalling FF 3.something, see if that works :)

ETA: hmm, sorry, seems to be solved by reverting to a previous version of FF... thank you for the help!

---

### Post by sanguinoso on 2011-04-22
Not at all! You figured it out! Which version of firefox is it? Consider posting a bug on launchpad?

For the version type this command 
```

firefox --version

```

---

### Post by chris doe on 2011-04-22
Thank you :) It's version 4. I tried 3.6, and it looked good.

I wouldn't even know how to begin to post a bug report, I had problems trying to articulate it without a screenshot, so I'd better not :)

---

