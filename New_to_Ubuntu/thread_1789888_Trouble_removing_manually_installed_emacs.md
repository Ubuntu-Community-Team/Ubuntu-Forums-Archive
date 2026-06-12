---
title: "Trouble removing manually installed emacs"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by therog726 on 2011-06-24
Hi,

I'm pretty new to some aspects of Ubuntu such as package management. (Running 11.04 Natty)

The other day I installed emacs manually as I was trying to upgrade to the latest version without uninstalling the version I already had.

The install screwed up though and it looks really different so I want to uninstall and go back to what I had originally.

So I tried removing in synaptic, terminal and software centre but if I type emacs in terminal it (the new version) still comes up.

How do get rid of it? :confused:

Thanks

---

### Post by kimda on 2011-06-24
Did you install from source or from a package?

---

### Post by yeats on 2011-06-24
Ah... you're learning the value of sticking to the repositories while you're learning! ;-)

I'm assuming by "manually" you mean installed this from source?  You should be able to cd into the source directory and do:

```
sudo make uninstall
```

Which *should* just take care of the uninstallation of the source version.  For good measure it would probably be a good idea to:

```
sudo apt-get purge emacs # may have to tweak the package name if "emacs" is not the right one
sudo apt-get install emacs
```

That should clean things up for you.

If you still want a newer version of emacs, this might be helpful:

[https://launchpad.net/~ubuntu-elisp/+archive/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ppa)

This would add a custom repository on your system that would allow you to add/remove via Synaptic/Ubuntu Software Center/apt-get rather than fussing with source installations.

Hope that helps!

---

### Post by therog726 on 2011-06-25
> **yeats said:**
> Ah... you're learning the value of sticking to the repositories while you're learning! ;-)

I'm assuming by "manually" you mean installed this from source?  You should be able to cd into the source directory and do:

```
sudo make uninstall
```

Which *should* just take care of the uninstallation of the source version.  For good measure it would probably be a good idea to:

```
sudo apt-get purge emacs # may have to tweak the package name if "emacs" is not the right one
sudo apt-get install emacs
```

That should clean things up for you.

If you still want a newer version of emacs, this might be helpful:

[https://launchpad.net/~ubuntu-elisp/+archive/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ppa)

This would add a custom repository on your system that would allow you to add/remove via Synaptic/Ubuntu Software Center/apt-get rather than fussing with source installations.

Hope that helps!



Haha yeah i'll stick to the repository for now... :p

That sorted the problem out quick smart! Thanks heaps for your help :D

---

