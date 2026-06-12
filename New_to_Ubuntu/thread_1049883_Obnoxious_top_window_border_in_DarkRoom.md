---
title: "Obnoxious top window border in DarkRoom"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-01-25
I just upgraded to Intrepid. I love the new Gnome and was excited that a decent dark theme was actually included but what the hell is up with that orange gradient along the top border of the active window? It's just aweful...

So I played with some of the other borders in the theme customisation and none of them look decent. Is there an easy way to just make that top border look like the other sides of the windows without the orange patch? Or maybe a way to just pick a different color to replace the orange parts of the theme with?

---

### Post by kavon89 on 2009-01-25
> **HittingSmoke said:**
> what the hell is up with that orange gradient along the top border of the active window?

I think that is one of those design thingies.

[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by Alterax on 2009-01-25
Not to the best of my knowledge; at least not without actually editing the theme itself (which I'm not scheduled to learn until late spring).  However, there are other themes you might consider, even if they're not part of the standard install.  Try installing the **art manager** application from add/remove programs.  You can search for new window borders from there and install them, then go into appearances.  Click on customize and try on the ones you picked for installation.

---

### Post by Alterax on 2009-01-25
Looking at the theme's XML files, it appears that the orange bits (including the top part of the active window title bar aren't part of a static image, but instead reference the Selected Items background color that's set in the Customize/Colors properties of the DarkRoom theme.

I'm about to remote in to the server that has that theme loaded (I'm on a laptop that lacks that theme at the moment) and see if this color is set statically and if so how we can work around it.  I'll post my findings when I'm done.

---

### Post by Alterax on 2009-01-25
Yeah, it was that simple.  Select DarkRoom, click Customize, then the colors tab.  The orange is about as stealthy as a herd of stampeding neon elephants, so pick it and change it to one you'd like.  

And that's it....

---

### Post by HittingSmoke on 2009-01-26
> **Alterax said:**
> Yeah, it was that simple.  Select DarkRoom, click Customize, then the colors tab.  The orange is about as stealthy as a herd of stampeding neon elephants, so pick it and change it to one you'd like.  

And that's it....

Thats perfect! Thanks! It's not that i dont like orange, that's just very bad design imo.

---

