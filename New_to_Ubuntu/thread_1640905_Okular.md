---
title: "Okular"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by beew on 2010-12-08
I mainly use Evince to view pdfs, but I have Okular as well because it has more functions that may come in handy.

Okular always takes a long time to start, I always thought that this is just the nature of the program. But today I was trying out Fedora' KDE edition and Okular appears to be ligntning fast, almost as fast as Evince in Ubuntu. I am wondering if this is because of KDE or Fedora, but in any case it is not because of the program itself that it is slow in starting up. I would like to know if there is a way to speed up its load time in Gnome (I have already set memory usage to "agressive" but it still takes a long time to start in Ubuntu)
Thanks.

---

### Post by Simian Man on 2010-12-08
It's because, if you are using KDE, then the KDE shared libraries will already be loaded and running.  When using Gnome, the KDE libraries must be loaded, *then* Okular starts up.  If you used Kubuntu, Okular will likely start quickly as well.

I do find Fedora a little snappier than Ubuntu, but not by as much as you describe.

---

### Post by mikechant on 2010-12-08
I suppose Okular would take longer to load as it is KDE based and will need to load the relevant KDE libraries when running under Gnome in Ubuntu, whereas Evince is Gnome based so its libraries would probably already be loaded. Obviously when running Okular under Fedora KDE, the KDE libs would already be loaded so it would be faster.

You could install the 'preload' package from the repositories and see if that helps - it preloads programs into RAM before they are needed, based on previous use.

Edit: Partly duplicated previous post as I started writing this before I saw it.

---

### Post by beew on 2010-12-08
What you say makes sense. No, I am not saying Fedora is in general much faster, I am only talking about Okular. Based on what you said I think it would probably be just as slow in Fedora's gnome edition and other KDE apps I have in Ubuntu would load faster in other KDE distros as well.

---

