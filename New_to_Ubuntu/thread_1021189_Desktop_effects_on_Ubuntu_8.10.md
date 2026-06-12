---
title: "Desktop effects on Ubuntu 8.10"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Steve05TSX on 2008-12-25
last question, I swear! 

Back on Ubuntu 7.10 there was a desktop effect where I would minimize the window and fire would eat the window + a bunch of other cool effects that I can't find in compiz.  Anyone have any idea what I'm talking about?

I love the wavy windows that compiz offers, but that's about it

---

### Post by igknighted on 2008-12-25
Install compizconfig-settings-manager and click on animations (in the effects section).  I didn't see anything that looked like fire in my quick search of the various transition effects you can choose from, but take a look and see if there is something similar that you like.

---

### Post by balaknair on 2008-12-25
You may need to install the package "compiz-fusion-plugins-extra" and "compiz-fusion-plugins-unsupported".
Then in Compiz Config Settings Manager, select 'Animations add-on'> Burn

---

### Post by nhasian on 2008-12-25
Its under Effects -> Paint Fire on the Screen.

---

### Post by Steve05TSX on 2008-12-25
> **balaknair said:**
> You may need to install the package "compiz-fusion-plugins-extra" and "compiz-fusion-plugins-unsupported".
Then in Compiz Config Settings Manager, select 'Animations add-on'> Burn

sounds like what I'm looking for, can't find it anywhere though (I went to applications/add/remove programs)

I think the thing I was using in the past is Beryl

---

### Post by Steve05TSX on 2008-12-25
> **nhasian said:**
> Its under Effects -> Paint Fire on the Screen.

not the same thing, this was a minimize, maxmize, close type of effect

---

### Post by igknighted on 2008-12-25
> **Steve05TSX said:**
> sounds like what I'm looking for, can't find it anywhere though (I went to applications/add/remove programs)

I think the thing I was using in the past is Beryl

Compiz-fusion (what ubuntu currently uses) is beryl + compiz, so essentially you are still using the same thing, just renamed.  Most of the really out-there stuff like fire is in the extras package.

> fitzgid@lappy:~$ apt-cache search compiz-fusion
compiz-fusion-bcop - Compiz Fusion option code generator[B]
compiz-fusion-plugins-extra - Collection of extra plugins from OpenCompositing for Compiz[/B]
emerald - Decorator for compiz-fusion
libemeraldengine0 - Decoration engines for compiz-fusion
compiz-fusion-plugins-main - Collection of plugins from OpenCompositing for Compiz[B]
compiz-fusion-plugins-unsupported - Compiz Fusion plugins - "unsupported" collection[/B]


---

### Post by Steve05TSX on 2008-12-25
> **igknighted said:**
> Compiz-fusion (what ubuntu currently uses) is beryl + compiz, so essentially you are still using the same thing, just renamed.  Most of the really out-there stuff like fire is in the extras package.


found it, a little hidden in there, gotta click on Animation-Add On and then it pops up under the animation window

now a new problem has arised, the effects don't even change when I change it in Compiz.  I haven't noticed any effects even work

---

### Post by nhasian on 2008-12-25
oh yeah now i know what your talking about.  open up the compizconfig settings, then go to effects then animations.  change the close animation to burn.  then you'll get it to close like this:

[http://www.youtube.com/watch?v=9o17CU50ihA](http://www.youtube.com/watch?v=9o17CU50ihA)

> **Steve05TSX said:**
> not the same thing, this was a minimize, maxmize, close type of effect

---

