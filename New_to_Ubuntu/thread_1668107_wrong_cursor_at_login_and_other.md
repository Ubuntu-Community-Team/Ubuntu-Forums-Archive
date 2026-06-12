---
title: "wrong cursor at login and other"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by labatts on 2011-01-15
I have run into this problem before, and have never figured out the solution so I thought I would see if I could get some help. =)

After installing new cursor themes, the cursor will show the incorrect theme at certain times.  Right now, it is the wrong theme at login.  It is also wrong if I try to drag an item (file, icon, etc).  It appears to be the appropriate cursor animation, but for the wrong theme (hope that makes sense).

The first incorrect cursor that it showed was "comix", when I had reverted back to the standard "oxygen white" cursor.  I unistalled the comix theme and rebooted.  The incorrect theme has been replaced with another incorrect theme.  All the while, I have oxygen cursor theme selected.

Any help is appreciated.

---

### Post by labatts on 2011-01-16
Okay, I haved solved PART of the problem by issueing the following terminal command:  sudo update-alternatives --config x-cursor-theme .  Pick the correct one, and then presto.

Unfortunately, the rest of the problem remains.  See the attached screenshot for a better description.  I have checked the actual cursor files, and everything is correct.  The system is not recognizing it correctly.

---

### Post by pSYcl0Ne on 2011-02-11
Old post, I know - but I just solved this after having this exact problem.

I think it has something to do with having compiz enabled.



Edit as root the index.theme file located in usr/share/icons/default and remove the spaces where it says Inherits = blah

eg.

Inherits = oxy-black

to

Inherits=oxy-black

this worked for me anyway.

---

### Post by labatts on 2011-02-11
Well, I was certainly excited to see a possible solution, but it unfortunately does not seem to have any effect.  I am still getting a mix of the cursors.

I also tried suspending desktop effects, but that did not do anything either.  Thanks for the suggestion! =/

---

### Post by Old *ix Geek on 2011-02-11
I have the same problem--and didn't have a clue how to word it so it would sound even remotely coherent! :) That's why I didn't bother posting. You've put it very well--at least *I* certainly get it.

---

### Post by labatts on 2011-02-12
Okay, after playing around with cursor themes some more, I have found a pattern. I was inspired by a post by pSYcl0Ne. The theme.index files (for the individual cursors) that have a line saying "Inherits=Core" display properly.  The themes that don't work do not have a "inherits" line at all.

I tried adding the line "Inherits=Core" to these index.theme files, but it does nothing.  I then tried "Inherits=(name of cursor theme)".  THAT makes the system settings crash when you try to select the cursor.

Obviously, I have no idea what I am doing, but whatever "inherits" is seems to be the culprit.

---

