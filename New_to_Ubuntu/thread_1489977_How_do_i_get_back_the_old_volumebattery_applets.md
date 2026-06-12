---
title: "How do i get back the old volume/battery applets"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by josephellengar on 2010-05-21
The way that these applets are all stored in the indicator applet in 10.04 is really annoying me.  This indicator applet has a bluetooth applet, even though I don't want it, and the broadcast session applet, even though I don't even have evolution installed, much less use it for any of those features.  Plus, there is a huge amount of space between them, taking up a ton of the horizontal space on my one-bar setup on my netbook.  Is there any way that I can get back the old volume applet and get rid of the bluetooth and evolution buttons?  I couldn't find anything in gconf-editor.  I have attached a picture to explain what I mean. (possibly incomprehensible, but you get the idea)

---

### Post by -humanaut- on 2010-05-21
I'd recommend searching around synaptic for dock applets I don't know if it would be reverted back to what you want but you can probably find something to suit your tastes better.

---

### Post by owenll on 2010-05-21
> **rossholley said:**
> Is there any way that I can... get rid of the evolution buttons? 
```
sudo apt-get remove evolution-indicator
```

---

### Post by josephellengar on 2010-05-21
> **owenll said:**
> ```
sudo apt-get remove evolution-indicator
```

Already did that as part of my bloatware removal when I first did the clean install.  The evolution bit in the indicator applet is still there.  Must say that I am very annoyed with this decision to integrate everything into one applet.

---

### Post by josephellengar on 2010-05-22
bump.  Any other ideas?  I tried installing packages from the packages.ubuntu website, but those didn't work.  I kept getting the "more recent version installed" error and I'm worried about breaking other things.

---

