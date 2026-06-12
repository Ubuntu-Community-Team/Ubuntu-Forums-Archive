---
title: "font icon has x on it"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by ave2 on 2009-03-18
iv been installing a few fonts, and copied arial narrow from windows, but when i place it in the fonts directory in ubuntu it displays the icon with x in the upper right corner- the font is a .TTF font, so im assuming it should work

---

### Post by kaixi on 2009-03-18
Just note that by simply copying the ttf file to the fonts folder won't add it to Openoffice unless you later import the fonts from the program itself.

And if what you want is to install the most common Microsoft fonts, open your terminal and type:
```

sudo aptitude install msttcorefonts
```

---

### Post by ave2 on 2009-03-18
hi kaixi, I did install the core fonts, but it seems like arial narrow is not included with those- so I copied it to user/share/fonts
 then sudo fc-cache -f -v
but like I said the icon displays a x on the top right corner as though its not valid

---

### Post by rendon on 2009-03-18
you can make a hidden directory in your home folder called .fonts

```

mkdir .fonts

```

then put windows fonts into that folder.  that's what I've done, and my fonts all show up in every software.

I'll leave it up to you to find the fonts.  maybe google True Type Fonts download...

of course you might need to restart x <ctrl>+<alt>+<backspace> or reboot for it to take effect...

---

### Post by ave2 on 2009-03-18
I didnt try rebooting- that may have worked

I found a program under add/remove called fontmatrix that allows you to easily manage your fonts- that seems to have sorted it out

---

### Post by kaixi on 2009-03-18
I think you shouldn't worry about it as long as you can use the font.

---

