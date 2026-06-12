---
title: "Revert or installs by date?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Gotaro on 2009-01-27
Is there any way for me to list the packages installed by date? Or is there a way to revert installs back to a certain date? Sure, Linux is better than Windows in that when you uninstall, it actually removes everything. But how am I supposed to remember everything I installed and every package that came with it? :P I tried sorting by the Ubuntu symbol in Synaptic, but that was only moderately effective, and I KNOW I left some extra packages hidden in the deceptive Ubuntu symbols -.O; I went through everything, but I really just have no way of knowing what needs to stay or can go.

I found Add/Remove Applications, and that is the equivalent IMO to Windows' Add/Remove Programs. However, there are still plenty of other packages I installed, or I should say came bundled in packages I installed, but won't rebundle for the uninstall :???:, that aren't listed as apps. Also, can't sort by date.
Synaptic can't sort by date.
Adept can't sort by date.

Any help is appreciated!

---

### Post by emarkd on 2009-01-27
This isn't exactly what you're looking for, but if you've uninstalled some apps and want to clean up unneeded dependencies that were installed with that app, open your terminal and run:

```

sudo apt-get autoremove

```

It'll remove every supporting package on your computer that isn't needed by one of the installed apps.

---

### Post by Gotaro on 2009-01-27
> **emarkd said:**
> This isn't exactly what you're looking for, but if you've uninstalled some apps and want to clean up unneeded dependencies that were installed with that app, open your terminal and run:

```

sudo apt-get autoremove

```

It'll remove every supporting package on your computer that isn't needed by one of the installed apps.
I love you.  Thank you!  It didn't answer my question, but it sure solved my problem!  :)

---

### Post by emarkd on 2009-01-27
Glad I could help.  Love you too and welcome to the community. :)

---

