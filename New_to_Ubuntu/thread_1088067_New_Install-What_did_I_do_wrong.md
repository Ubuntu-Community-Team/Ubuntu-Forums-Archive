---
title: "New Install-What did I do wrong"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Gerg7836 on 2009-03-05
This is my first time working with Linux, and I'm a bit stumped. I did a fresh install of Ubuntu 64-bit Server 8.10 on a new 6-bit HP PC. The install seemed to go OK until it ejected the CD and restarted. Then it took it what seemed to be forever to scroll through a huge list of something, but then it seemed to finally finish and restart. I next saw what looked like a bunch of start-up variables, then I got to a user name and password prompt, which I entered. Now, I'm at the equivalent of a Command Prompt, looking for an entry (*user@host*:~$).

What am I supposed to do now? Shouldn't it instead be booting to a desktop of some sort?

Sorry if this is covered somewhere, I couldn't seem to find the right answer.

---

### Post by UbuntuNerd on 2009-03-05
the server version doesn't have a GUI or desktop you can install the desktop onto it by typing this command at the prompt:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Gerg7836 on 2009-03-05
Huh, I didn't see that little caveat anywhere!

Installing the desktop now, thank you!

---

### Post by Rocket2DMn on 2009-03-05
It's been awhile since I've done a server install, but I think it does give you the option at one of the menus, it's just not selected by default.  You would select a desktop environment and it would install what you need.  
Installing ubuntu-desktop (which is a metapackage) installs everything needed for X and gnome.  If you wanted KDE, or Xfce, you would install kubuntu-desktop or xubuntu-desktop, respectively.

---

