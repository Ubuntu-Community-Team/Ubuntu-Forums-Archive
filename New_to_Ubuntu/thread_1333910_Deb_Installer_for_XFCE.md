---
title: "Deb Installer for XFCE?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Psumi on 2009-11-21
Does anyone know of a GUI for installing DEB Packages locally? Or do I have to install gdebi?

---

### Post by wilee-nilee on 2009-11-21
> **Psumi said:**
> Does anyone know of a GUI for installing DEB Packages locally? Or do I have to install gdebi?

Are you using xubuntu or pure xfce?

---

### Post by Psumi on 2009-11-21
> **wilee-nilee said:**
> Are you using xubuntu or pure xfce?

pure xfce (ubuntu mini.iso)

I even replaced notification daemon with the xfce version.

And I use parole instead of totem.

---

### Post by wilee-nilee on 2009-11-21
> **Psumi said:**
> pure xfce (ubuntu mini.iso)

I even replaced notification daemon with the xfce version.

And I use parole instead of totem.

It has been a while since I used xubuntu or additional xfce on a minimal install. I mainly asked the question for others to have more information. I like gdebi so if it was me I would see if that is a easy solution, I like to keep things simple. Hopefully others will chime in.

---

### Post by kerry_s on 2009-11-21
gdebi is the only installer. if you don't want it you can just do a script & use the thunar action.

example:

```

#!/bin/sh
xfce4-terminal -x sudo dpkg -i "$@"

```

i think that will work. not sure about the execute switch for xfce4-terminal, you might want to check the man page.

---

### Post by Psumi on 2009-11-21
> **kerry_s said:**
> gdebi is the only installer. if you don't want it you can just do a script & use the thunar action.

example:

```

#!/bin/sh
xfce4-terminal -x sudo dpkg -i "$@"

```

i think that will work. not sure about the execute switch for xfce4-terminal, you might want to check the man page.

xfce4-terminal is not installed in xfce by default, just so you know. I obviously installed it of course. But, where do I put this script?

---

### Post by Psumi on 2009-11-21
Also, does anyone know if the xfce team is making a multiprotocol messaging client like pidgin? Or their own port of gksu?

Because pidgin and gksu rely on gconf.

And will there ever be a gui configuration for xbanner or xdm?

---

### Post by kerry_s on 2009-11-22
> **Psumi said:**
> xfce4-terminal is not installed in xfce by default, just so you know. I obviously installed it of course. But, where do I put this script?

you can use xterm if you want. **xterm -e sudo dpkg -i "$@"**

create a folder in your home folder called "bin" log out & back in, put your scripts in there & then you can just use the name to launch it. don't forget to set your scripts executable.

> Also, does anyone know if the xfce team is making a multiprotocol messaging client like pidgin? Or their own port of gksu?

Because pidgin and gksu rely on gconf.

And will there ever be a gui configuration for xbanner or xdm? 

nope

xdm is ancient, hasn't been updated in years. you should try slim instead.

---

### Post by Psumi on 2009-11-22
> **kerry_s said:**
> xdm is ancient, hasn't been updated in years. you should try slim instead.

slim isn't in karmic on packages.ubuntu.com

---

### Post by kerry_s on 2009-11-22
> **Psumi said:**
> slim isn't in karmic on packages.ubuntu.com

i see, guess i should have checked first. i wonder why it was dropped?

---

### Post by Psumi on 2009-11-22
> **kerry_s said:**
> i see, guess i should have checked first. i wonder why it was dropped?

There still is wdm however, which will suffice for now.

---

