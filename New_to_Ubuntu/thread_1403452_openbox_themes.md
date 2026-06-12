---
title: "openbox themes"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by dzon65 on 2010-02-10
Hi.I'm using openbox as windowmanager.Does anyone know where the openbox-themes are stored on the pc?

---

### Post by mwcrowley on 2010-02-10
[https://help.ubuntu.com/community/Openbox#Configuration](https://help.ubuntu.com/community/Openbox#Configuration)

cheers

---

### Post by dzon65 on 2010-02-10
What I ment was where the themes (the ones  in openbox configurator ) are stored,the default ones so to speak.

---

### Post by Jefferythewind on 2010-02-10
Try Emerald, it is really nice and easy to use.  Get themes here:

[http://compiz-themes.org/]("http://compiz-themes.org/")

---

### Post by mcduck on 2010-02-10
*/usr/share/themes*  for system-wide installed themes, and *~/.themes* for themes installed for one user only.

---

### Post by m_duck on 2010-02-10
On my box (which is Arch at present so may not be the same for you), the default openbox themes are stored in:
```
/usr/share/themes/*theme_name*/openbox-3/
```

---

### Post by dzon65 on 2010-02-10
> **Jefferythewind said:**
> Try Emerald, it is really nice and easy to use.  Get themes here:

[http://compiz-themes.org/](http://compiz-themes.org/)

Next to openbox I got emerald.It's nice but twice as slow as openbox.

[http://dzon65.deviantart.com/art/someone-144029882](http://dzon65.deviantart.com/art/someone-144029882)

---

### Post by dzon65 on 2010-02-10
aha,found them.So at first glance there doesn't seem to be a png for the theme.If I'd like to remove the bottom-border of that theme I'll have to edit it in the script I guess?

---

### Post by mcduck on 2010-02-10
> **dzon65 said:**
> aha,found them.So at first glance there doesn't seem to be a png for the theme.If I'd like to remove the bottom-border of that theme I'll have to edit it in the script I guess?

correct, Openbox only uses pixmaps for button images, everything else is just defined in the theme file.

---

### Post by dzon65 on 2010-02-10
I see.Okay,will give it a go.Thanks for the info.
Kind regards,J.

---

### Post by mcduck on 2010-02-10
So, you want to remove the line from under of the titlebar?

I have good news, and then some bad ones... That line doesn't actually come from any border, but the titlebar that has been set to "raised", which creates a bit of a 3D look.

You can get rid of the line by changing these two lines:

```
window.active.title.bg: raised bevel1 gradient vertical
window.inactive.title.bg: raised gradient vertical
```

to these:
```
window.active.title.bg: flat bevel1 gradient vertical
window.inactive.title.bg: flat gradient vertical
```

..the downside is that you'll also loose the light borders from top and sides of the titlebar. As far as I know Openbox has no way to define borders with different colors for left, right and top so there's no way to get those borders back without also getting a border under the titlebar. (well, perhaps creating a light 1-pixel border around the whole window would look OK and be close enough.. That's the color you have set in your second screenshot, just make sure also to change the border width (couple of lines downwards) to something else than 0..)

---

### Post by dzon65 on 2010-02-10
Yeah!Thanks a lot.In fact,running a minimal ubuntu right now so tried some in an openbox session.To me,used to tweaking gtk's and so,openbox seemed "hard to configure" but I guess I'll spend some more time in the openbox sessions.
Hey,thaanks for those scripts.
Kind regards,J.

---

### Post by dzon65 on 2010-02-11
Hey McDuck.Worked like a charm.Exactly the smoothness I was looking for.

---

