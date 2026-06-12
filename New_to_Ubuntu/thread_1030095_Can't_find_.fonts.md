---
title: "Can't find .fonts"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Jaz969 on 2009-01-04
I'm looking to install some more microsoft fonts (I installed msttcorefonts, but it didnt have tahoma?), so my friend told me that its ~/.fonts/ but I only have .fontconfig which is full of cache.

---

### Post by MenZa on 2009-01-04
Simple solution: create it. (**mkdir ~/.fonts**). Alternatively, if you want all users on the system to have access to the fonts, put them in /usr/share/fonts.

After installing the fonts, run **sudo fc-cache -r** to refresh your font cache.

---

### Post by Jaz969 on 2009-01-04
Thanks that's what I thought I should do.

---

### Post by adobrakic on 2009-01-04
When i do

```

whereis fonts

```

I come up with:

```

ado@ado-desktop:~$ whereis fonts
fonts: /etc/fonts /usr/share/fonts
ado@ado-desktop:~$ 

```

And that's where I put all of the microsoft fonts. Specifically, I think it was in the /usr/share/fonts one under mtscorefonts.

---

