---
title: "evolution/envelope deleted from clock panel after install"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by brookie on 2009-11-02
Hi all,
I just installed Karmic and removed an envelope looking thingy in the right side of the panel where the clock/date/time is. I don't know what it was for but would like to put it back if it is an evolution mail notifier. 
Where oh where did it go? Anybody know?

---

### Post by Excedio on 2009-11-02
Try this:
 
System > Administration > Synaptic Package Manager
 
 
Then search for:
 
evolution
 
List off what is there that begins with evolution-
 
 
I am not at my computer right now so cannot check for the exact name of the file at the moment.

---

### Post by stinger30au on 2009-11-02
i just did a right click properties on the envelope you talk about

its called

indicator applet

hope that helps

---

### Post by stinger30au on 2009-11-02
if oyu right click the top panel and click on

add to panel

you will see

indicator applet

this might help too

---

### Post by Excedio on 2009-11-02
THAT'S IT!
 
look for evolution-indicator

---

### Post by brookie on 2009-11-02
Thanks guys. You rock! I right clicked and added indicator applet, but in Synaptic, the evolution-indicator is not installed. I just thought it would be an mail notifier like in Thunderbird when you get a new mail. So it's like a quick switch button to go between Evolution and Empathy software. I'll give it a try. Cheers. :)

---

### Post by Excedio on 2009-11-02
> **brookie said:**
> Thanks guys. You rock! I right clicked and added indicator applet, but in Synaptic, the evolution-indicator is not installed. I just thought it would be an mail notifier like in Thunderbird when you get a new mail. So it's like a quick switch button to go between Evolution and Empathy software. I'll give it a try. Cheers. :)
 
evolution-indicator will add Evolution to that little envelope when the program is running. It will also provide you with a small notification whne you have an email waiting for you and you were not around to see it popup with libnotify. :-)

---

### Post by stinger30au on 2009-11-04
how did ya go??

all sorted?

---

### Post by brookie on 2009-11-05
thanks stinger, got it all sorted. these forums are awesome for figuring things out. cheers.

---

