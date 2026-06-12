---
title: "Restore Panels In Ubuntu Back To Their Default Settings"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-02-18
HI everyone..
I found this while i was browsing... This may help many of you.
In case you accidently delete something from your panels, restore your panel back to default with this commands!!

1.first type:

*gconftool – -recursive-unset /apps/panel*

2. then type:

*rm -rf ~/.gconf/apps/panel*

3.Finally type:

*pkill gnome-panel*

TThen you are done!!!

---

### Post by Bucic on 2011-02-18
Thanks a lot!

P.S. Where is that "thank" forum feature?

---

### Post by de_island on 2011-04-12
That was of absolutely no help to me...

It deleted everything from my panel except for two buttons that I'd recently added and then added in a quarter sized panel below my main one. Also, there's a typo in your first line of code. It should be --recursive.

Can you review this method before more people try this?

---

### Post by seawolf167 on 2011-04-12
> **amitpokhrel said:**
> HI everyone..
I found this while i was browsing... This may help many of you.
In case you accidently delete something from your panels, restore your panel back to default with this commands!!

1.first type:

*gconftool **– -**recursive-unset /apps/panel*

2. then type:

*rm -rf ~/.gconf/apps/panel*

3.Finally type:

*pkill gnome-panel*

TThen you are done!!!

There shouldn't be a space at --recursive. This will restore the panels to their defaults, if you accidentally delete something, I suggest right-clicking the panels and selecting "Add to Panel" before you restore everything (only need to restore if you accidentally delete all the panels & their contents or something)

---

