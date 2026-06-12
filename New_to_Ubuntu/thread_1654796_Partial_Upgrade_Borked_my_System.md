---
title: "Partial Upgrade Borked my System"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-12-28
Ah if only I had clonezilla'd my system recently.

Here's the story. The only other time I've partially upgraded my system, it caused no problems, so I thought it was probably a safe operation (although I should have been tipped off by the word "upgrade" and known better). I added ppa:compiz to my software sources list, and the update manager asked if I wanted to do a partial upgrade. I figured, "Well, if I want the latest compiz files, I ought to do the upgrade." 

But it didn't work out as smoothly as I'd hoped. Now, Thunderbird has no window bar, and other applications have a malfunctioning window bar. What's worse is that I can no longer use synaptic or apt-get. There may be other problems, but those are the two that I've noticed.

I'd like to fix it if that's possible -- a complete reinstall would not be pleasant. Will someone help me restore my system?

Just for reference, here's a few commands I've tried:
  489  sudo dpkg --configure -a
  490  sudo apt-get install -f
  491  sudo dpkg-reconfigure -phigh -a

Any help would save me a lot of frustration and I'd get to keep the system the way I have it configured.

---

### Post by JC Cheloven on 2010-12-28
Hi,

What did you exactly "upgrade"? The distribution version (for example, lucid to maverick) or only some packages (accepting a system update notified by the update manager, upgrading compiz to the newer version using a ppa, etc) ?

I'd say that [COLOR="Blue"]**sudo dpkg-reconfigure -a**[/COLOR] should have put to work at least apt-get, but you already tried, so no cake here.

A bit as a shot in the dark: did you try disabling desktop visual effects? As you said you changed the source for compiz it could have something to do...

---

### Post by EnigmaticCoder on 2010-12-28
"What did you exactly "upgrade"?" I just glanced at it, but I think it was something for compiz. One of the packages that was installed was a new linux kernal.

"The distribution version (for example, lucid to maverick) or only some packages (accepting a system update notified by the update manager, upgrading compiz to the newer version using a ppa, etc) ?"

If anything it would be maverick to natty, but I think I just updateded compiz. At any rate, it was a partial upgrade.


"A bit as a shot in the dark: did you try disabling desktop visual effects? As you said you changed the source for compiz it could have something to do..."
I thought the same thing, but when I looked to see if desktop visual effects were on, the window said I was using "none."

---

### Post by EnigmaticCoder on 2010-12-29
I figured out why this command didn't fix apt-get

```

$ sudo dpkg-reconfigure -phigh -a 

```

It didn't finish. I get this error and dpkg-reconfigure fails

```

dpkg-maintscript-helper: error: couldn't identify the package

```

Perhaps if I can get dpkg-reconfigure to work, I could possibly fix broken packages in synaptic?

---

### Post by philinux on 2010-12-29
Are you running version 10.10?

---

### Post by EnigmaticCoder on 2010-12-29
Yes, unless the partial upgrade moved me to 11.04. Is it possible that a full upgrade (when 11.04 is released) will fix this problem? I have a laptop I could use until April.

---

### Post by arpanaut on 2010-12-29
Sounds like a good case for ppa-purge:

[http://www.webupd8.org/2010/04/ppa-purge-now-available-via-getdeb.html](http://www.webupd8.org/2010/04/ppa-purge-now-available-via-getdeb.html)

Not sure it will work because of the partial upgrade, but might be worth a shot.

Your call.

---

### Post by EnigmaticCoder on 2010-12-29
That seemed to fix most issues. A couple problems, however, still remain.

[IMG]http://i.imgur.com/ZKlgQ.png[/IMG]

The close, maximize, and minimize buttons are backward on the dust theme.

Also, when I opened an .odt file, it tried to open with gedit instead of open office writer. 

And alt-print screen did not take a screenshot of the currently opened window. I don't know if these are the only problem or not, but I'll keep trying to fix what I can.

---

### Post by EnigmaticCoder on 2010-12-29
Just found out that update manager won't download updates. Could this be related to the failed dpkg-reconfigure attempts?

---

### Post by arpanaut on 2010-12-29
Try:
```
sudo apt-get update && sudo apt-get upgrade
```

and see what the error messages have to say, usually they give suggestion on how to fix.

good luck!

---

### Post by EnigmaticCoder on 2010-12-30
Yep, that tipped me off. The GDebi repository that I had enabled was really slow, although I no longer have updates, so I haven't been able to check if that was the only problem.

---

