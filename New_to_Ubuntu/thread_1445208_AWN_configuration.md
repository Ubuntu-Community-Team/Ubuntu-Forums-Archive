---
title: "AWN configuration"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-02
Hii , 
First of all I thank you all for all the wonderful support that I have got from this forum . 
Now I need a little help with this. 
Installed AWN on Karmic with the info on the below link :-
[http://wiki.awn-project.org/Installation:Ubuntu](http://wiki.awn-project.org/Installation:Ubuntu)

It says that I need the AWN Manager to configure it properly, but whenever I try to install AWN manager it says that AWN settings trunk will have to be removed. So should I go ahead with it or do we have some alternate way.
Thanks 
Vivek!

---

### Post by qyot27 on 2010-04-02
AWN Manager **is** awn-settings-trunk.  It's an alias (just like the Configuration Editor is really gconf-editor, Shisen-Sho is kshisen, or so on).  On the dock, it's usually the farthest-left icon.  You can also find the configuration in System->Preferences.

The problem you're running into is that you're trying to have both the repository and PPA versions installed at the same time, or the the repo one is trying to overtake the PPA.

---

### Post by vivek40 on 2010-04-02
Thanks a lot qyot!
No I was not having PPA versions and repository at the same time.
I guess the confusion lay in I not knowing that awn settings trunk and awn manager were the same.. However thanks for the clarification..
Regards
Vivek

---

### Post by praveenthivari on 2010-04-02
You can allow tht to remove , it will install it's own trunk.

---

