---
title: "How to force reinstall of all packages regardless of versions?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by jerrry94087@yahoo.com on 2009-10-28
Something is broken on my newly installed KUbuntu machine. I see damaged fonts in different applications.

How can I force reinstall of all packages to make sure that nothing is damaged?

'apt-get upgrade --reinstall' doesn't do anything.

Jerry

---

### Post by yeats on 2009-10-28
> Something is broken on my newly installed KUbuntu machine. I see damaged fonts in different applications.

When you say "damaged" fonts, do you mean that the fonts are not displaying correctly?  Are fonts the only issue?


> How can I force reinstall of all packages to make sure that nothing is damaged?

The only way to reinstall all packages is to reinstall completely.

But if fonts are the only thing not working well, I would focus on display issues...

---

### Post by jerrry94087@yahoo.com on 2009-10-28
> **chrissharp123 said:**
> When you say "damaged" fonts, do you mean that the fonts are not displaying correctly?  Are fonts the only issue?

Some letters are damaged sporadically, mostly in Firefox, but in other apps too. Particular letters will get some trash over them. Same on all appearances of that letter. Also some random graphical garbage on screen.

> **chrissharp123 said:**
> The only way to reinstall all packages is to reinstall completely.

What does this mean: "reinstall completely"? I can't tell apt-get to just refresh all packages? I am looking for the equivalent of FreeBSD command 'portupgrade -af' (all,force).

> **chrissharp123 said:**
> But if fonts are the only thing not working well, I would focus on display issues...

Not only fonts. There are some other graphics artifacts. Seems like xserver itself is damaged. Also KDE4 sometimes crashes when I move some windows around. And on my FreeBSD machine KDE4 is rock-solid. I suspect it's the same reason.

---

