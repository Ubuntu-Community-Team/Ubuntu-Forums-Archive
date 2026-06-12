---
title: "Ho to install urw chancery l"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Buce on 2009-07-13
I need the "urw chancery l" font. I tried installing t1-cyrillic with apt-get, since the repos say the Chancery font family is included in this package, but the font isn't showing up.

---

### Post by Buce on 2009-07-15
Looks like URW Chancery L isn't in the repositories, but Free Chancery is a suitable replacement. I had a webpage that I created with the style:

```
.script {
font-family: "monotype corsiva", "lucida handwriting", "zapf chancery", "urw chancery l", cursive;
font-size: 30px;
}
```

It wasn't displaying correctly, so what I really needed was one of the first four fonts listed, or another suitable font to be aliased to the 'cursive' font family. The fix was to do the latter by creating ~/.fonts.conf and pasting this in the file:

[HTML]<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
  <alias>
    <family>cursive</family>
    <prefer>
      <family>Free Chancery</family>
    </prefer>
  </alias>
</fontconfig>[/HTML]

YMMV, but I think you should be able to do this for any font/family combo -- especially useful for the "cursive" or "fantasy" font families, since firefox doesn't have a setting to set either of those under Edit -> Preferences -> Content -> Fonts & Colors -> Advanced

---

### Post by autonomy on 2009-11-15
Where is Free Chancery?

---

### Post by Buce on 2010-01-10
In the t1-cyrillic package.

```

sudo apt-get install t1-cyrillic
```

---

