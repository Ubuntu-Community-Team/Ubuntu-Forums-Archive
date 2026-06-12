---
title: "Change  google Earth font size"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by nnjond on 2009-05-18
Hi, can anyone tell me the way to  specifically enlarge G Earth font size?

Thanks

---

### Post by mprince on 2009-05-18
See if you have the file:

home/**user**/.config/Google/GoogleEartPlus.conf

In the [Render] section try changing the font size to something larger:

GuiFontFamily=Arial
GuiFontSize=9
GuiFontStyle=0
GuiFontWeight=50

...

PrimaryFontVersion2Family=Arial
PrimaryFontVersion2Size=12
PrimaryFontVersion2Style=0
PrimaryFontVersion2Weight=75

...

SecondaryFontVersion2Family=Bitstream Vera Sans
SecondaryFontVersion2Size=12
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75

---

### Post by nnjond on 2009-05-18
Thanks for your interest. My  home/.config/Google/GoogleEartPlus.conf

In the [Render] section  only consists of:


[Render]
CompassVisible=true
FeetMiles=false

[Search]
input0-4_3=exeter, kent, l

---

### Post by unutbu on 2009-05-18
Edit or create:

~/.googleearth/Registry/google/googleearthplus/User/render/guifontfamily

You can put the name of a ttf font here. For example:
```

Arial
```

You can set the font size by editing or creating:

~/.googleearth/Registry/google/googleearthplus/User/render/guifontsize

For example, mine contains just this:
```

10
```

---

### Post by nnjond on 2009-05-18
Solved. Thanks

---

