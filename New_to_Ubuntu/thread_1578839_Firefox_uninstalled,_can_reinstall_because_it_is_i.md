---
title: "Firefox uninstalled, can reinstall because it is installed."
date: 2010-09-21
forum: New to Ubuntu
---

### Post by gamadaya on 2010-09-21
I'm running 8.0.4 as a vm in vmware, and I was informed that firefox was not installed. I have no idea what happened to it though. When I tried running it in the terminal, it told me to install it by typing sudo apt-get install firefox-3.0. When I did this, it told me 3.0 was the newest version, nothing was installed, and nothing was upgraded. I checked add and remove programs, and firefox was listed as installed. Synaptic also lists it as installed, so I just don't know what's going on.

---

### Post by dirghrabadia on 2010-09-21
In the terminal:
> firefox -versionIf it does show a version, then you have indeed have FF installed :)

---

### Post by gamadaya on 2010-09-21
No, same message as just trying to run it. So then it isn't installed. Why does everything say it is, and how do I go about actually installing it?

---

### Post by 3rdalbum on 2010-09-21
Isn't FireFox 3 known in Hardy as its codename? (shiroko or something like that, check your Applications menu)

---

### Post by gamadaya on 2010-09-21
Yeah, sorry, I should have said I checked there first. Nothing in there looks anything like firefox. The quicklaunch icon looks like it was replaced by a spring with some flat object on top. It can't be launched though. No command (Exec) to launch.

[B]Edit:
[/B]It's apparently back. Something was installed in an update which caused it to work again.

---

### Post by lovinglinux on 2010-09-21
Try this:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo apt-get install firefox
```

---

