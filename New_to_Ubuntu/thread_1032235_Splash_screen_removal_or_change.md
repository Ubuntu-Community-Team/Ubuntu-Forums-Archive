---
title: "Splash screen removal or change"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by User X on 2009-01-06
I just installed Myth Control Center and MythTV and I am not fond of the Mythbuntu loadup and shutdown splash screens.  Is there an easy way to change them back to the standard Ubuntu screens or even something custom?  I tried searching but I am not sure what to look for...?  Thanks.

---

### Post by thunk77 on 2009-01-06
```
sudo apt-get remove mythbuntu-artwork-usplash && sudo apt-get install usplash-theme-ubuntu
```

This will remove the usplash theme of Mythbuntu and install the default Ubuntu usplash.

You could also install the debian package or the ubuntu studio and others. Just search for them in the repositories.

---

### Post by User X on 2009-01-06
Hey thanks.  Just so I know, how does one "search for them in the repositories"?  Just use synaptic package manager's search function?

---

### Post by thunk77 on 2009-01-07
yep.:)

---

