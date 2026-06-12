---
title: "transparency in nautilus"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by libihero on 2010-03-02
i didnt activate RGB or watever its called lol but for some reason some of my themes give a nautilus a transparency.  is there any way to turn that off??

---

### Post by Enigmapond on 2010-03-02
Are you using compiz? If so try going to the manager and in "effects" uncheck the "reflections" setting.

---

### Post by libihero on 2010-03-02
reflections is off :(

---

### Post by libihero on 2010-03-03
bump :(

---

### Post by skymera on 2010-03-03
Could we have a screenshot?

---

### Post by libihero on 2010-03-03
here ya go :)

---

### Post by galdren on 2010-03-03
if you have the compizconfig-manager you should check under accessibility->opacity/brightness and saturation.

maybe some setting in the opacity tab is causing it. turn off this plugin and see if there's still any unwanted transparency.

---

### Post by neybis on 2010-03-03
if compiz does not seem to be the culprit you can attempt to reinstall nautilus as well...that should always fix the problem if the issue is actually nautilus related ;)

---

### Post by ammonkey on 2010-03-05
U're using nautilus-elementary it has rgba activated by default. U can disable it with a gconf key.

open a terminal
gconf-editor

go to apps/nautilus/preferences disable the key rgba_colormap

---

### Post by libihero on 2010-03-05
it's not there :S

---

### Post by ammonkey on 2010-03-07
> **libihero said:**
> it's not there :S

oups my bad sorry long time the package didn't update. This option is available only in the bzr for the moment. Anyway the ppa is gonna be updated in the next few days.

---

### Post by libihero on 2010-03-07
alright thanks!

---

