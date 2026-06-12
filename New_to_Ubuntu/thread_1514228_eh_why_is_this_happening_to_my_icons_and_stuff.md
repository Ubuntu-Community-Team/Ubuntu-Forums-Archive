---
title: "eh? why is this happening to my icons and stuff?"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-20
Out of the blue, my icons on firefox changed along with everything else, some reverted back, some didn't. This is how my files look like now (the grey one) and what they should look like.

---

### Post by J V on 2010-06-20
Did you recently install something? It looks like ubuntu lost the theme you are on, rightclick the desktop and choose the "light"/"dark" or "human" themes depending on your OS...

---

### Post by arrange on 2010-06-20
Look at */var/log/apt/term.log* and check what you have (un)installed recently. (Alt+F2 &#8594; *gksudo gedit /var/log/apt/term.log)*

---

### Post by Legendary_Bibo on 2010-06-20
I haven't installed anything before that, it just happened. Oh well I just logged out then logged back in and now everything is back to normal. What's cool is that from this little issue I found out I can change the background of the file browser. :D
Thanks for you help anyways!

---

