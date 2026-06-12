---
title: "Two Questions"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-02-05
Can I install compiz fustion and how do I install all of the fonts available in microsoft to xubuntu?

---

### Post by diwas on 2009-02-05
Compiz is automatically installed but you can install the compiz settings manager by running this command:
```

sudo apt-get install compiz-settings-manager

```

And regarding the windows font:
```

sudo apt-get install msttcorefonts

```

---

### Post by diwas on 2009-02-05
Oh! I am sorry, I didn't see the xubuntu.
I am not sure if compiz works there, sorry again.

---

### Post by Sup3r3g0 on 2009-02-05
That's okay. I've been thinking it over and think that I'll go for a minimalist approach for xubuntu. I'm running it inside of a virtualbox, so I can only allocate 300MB of ram. 

Thanks for the speedy reply.

---

### Post by diwas on 2009-02-06
Anytime.
:)

---

### Post by Paqman on 2009-02-06
Xubuntu actually includes a compositing window manager by default. It'll give you some basic effects like transparency and dropshadows, as well as allow you to run apps that need a compositor (like AWN). So no need for Compiz at all unless you want some of it's flashier effects.

---

### Post by yellowaeroplane on 2009-02-06
Do you also have Windows installed on the machine?

If so, it's really simple to copy fonts (other than the msttcorefonts package) over to your Xubuntu install.

The Windows fonts should be located in Windows -> Fonts

Copy anything from there you'd like into the folder called ".fonts" in your Xubuntu home directory. If the .fonts folder doesn't already exist, just create it!

Hope that helps a bit.

---

### Post by Bölvaður on 2009-02-06
if you are on a virtual machine you are not able to get compiz to do anything without the graphic accelaration which isnt a default thing yet... so I would be supriced if you'd get it working

---

