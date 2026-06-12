---
title: "Shiretoko shortcut not loading"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Flynsarmy on 2009-07-10
I installed firefox-3.5 from the repository but found that if i type 'firefox' into the 'run applications' menu (alt+f2) it loads the version of FF ubuntu came with instead of 3.5. So i did a sudo rm /usr/bin/firefox;sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox. Now when i type 'firefox' into any terminal window it loads 3.5 (shiretoko) successfully. However if I type it into the run applications menu nothing happens. How do I fix this?

---

### Post by FoxFireX on 2009-07-10
type in firefox-3.5 instead or whatever its named.

---

### Post by Flynsarmy on 2009-07-11
I'd prefer a proper solution. It's annoying not being able to type fire then hit tab and enter.

---

### Post by lovinglinux on 2009-07-11
> **Flynsarmy said:**
> I installed firefox-3.5 from the repository but found that if i type 'firefox' into the 'run applications' menu (alt+f2) it loads the version of FF ubuntu came with instead of 3.5. So i did a sudo rm /usr/bin/firefox;sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox. Now when i type 'firefox' into any terminal window it loads 3.5 (shiretoko) successfully. However if I type it into the run applications menu nothing happens. How do I fix this?

First, revert what you have done with this command:

```
sudo rm /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.0 /usr/bin/firefox
```

Then run this:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox
```

This should fix your problem.

More inf about Firefox 3.5 installation methods at [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Flynsarmy on 2009-07-11
That got it, thanks :)

---

