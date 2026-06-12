---
title: "how to get COMPLETE themes"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by thomz92 on 2009-10-07
hi all

i recently downloaded a few themes from gnomelook, and i thought i found one that i liked (moomex), but later on i opened synaptic, and its theme looked like old windows 95. only synaptic has that problem, all my other programs look great. im guessing that this is because moomex isn't a complete theme. anyway, what i want to know is, how do i get completely complete themes like those that come with ubuntu? (except cooler :)) also, whats the difference between GTK 1.x, GTK 2.x, and metacity themes in gnomelook?

---

### Post by tom66 on 2009-10-07
What looks like Windows 95? Are the icons incorrect? You might need to restart an application to get the new theme to apply.

---

### Post by Viva on 2009-10-07
Synaptic runs as root, so uses the default theme. Try [this]("http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/") to theme applications run as root

P.S That article looks quite old, so I'm not sure if it works anymore.

---

### Post by thomz92 on 2009-10-07
> **Viva said:**
> Synaptic runs as root, so uses the default theme. Try [this]("http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/") to theme applications run as root

P.S That article looks quite old, so I'm not sure if it works anymore.

yeah thats exactly whats happening to mine. why do the themes that come with ubuntu work with synaptic though?

---

### Post by Viva on 2009-10-07
Probably because they are not installed in your home directory unlike the themes you install using appearance settings.

---

### Post by CatKiller on 2009-10-07
> **thomz92 said:**
> why do the themes that come with ubuntu work with synaptic though?

Because they come with Ubuntu. In particular, because they are installed system-wide and are so available to all users, including *root*. Themes that you install through the Appearance tool are only installed for your user and won't affect other users, including *root*. Although I don't know why the theme for applications run as root is changed at all. The behaviour I've seen has been that applications run as root are themed with whatever the default is for new users, which means that they don't look out of place on a default install since the normal user is using the same (default) theme.

FWIW, you can change the theme for applications run as root in exactly the same way that you would for a normal user; it's just that you need to run the Appearance tool as root for it to affect root's settings, by running ```
gksudo gnome-appearance-properties
```

---

### Post by ankspo71 on 2009-10-07
> 
 Re: how to get COMPLETE themes
Synaptic runs as root, so uses the default theme. Try this to theme applications run as root

P.S That article looks quite old, so I'm not sure if it works anymore.

Thanks, that link worked for me. (karmic-beta)
James

---

