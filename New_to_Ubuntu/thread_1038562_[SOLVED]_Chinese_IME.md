---
title: "[SOLVED] Chinese IME"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-01-12
Hi! 
Problem: I'm trying to get the chinese input method editor to work...

So far I did:
```

apt-get install scim scim-chinese scim-config-socket scim-frontend-socket scim-gtk2-immodule scim-server-socket scim-tables-zh xfonts-intl-chinese xfonts-intl-chinese-big ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp ttf-arphic-bsmi00lp

```

I have all locales generated
started the scim daemon with:
scim -d


It displays the scim icon on the top right pane, but I cannot switch it on...

If I press ctrl + space, it doesn't switch to chinese...

What am I doing wrong?

---

### Post by WitchCraft on 2009-01-12
Oh I got it!!!

gedit ~/.xsession

and paste that content:
```

scim -d
export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session

```

&#26089;&#19978;&#22909;&#12290;
Debian &#30340;&#30707;&#38957;&#65281;

---

