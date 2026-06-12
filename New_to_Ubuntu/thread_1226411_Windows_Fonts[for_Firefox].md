---
title: "Windows Fonts[for Firefox]"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-07-29
Hello,
I think all web-pages are different from windows! (especially non-English ones) After a closer look, I found that reason is different fonts. I can't wait for websites to use HTML5 and see them with their online fonts! How can I solve this problem and see web-pages as they are in Windows? (should I install some fonts? or?)
Thanks.

---

### Post by gn2 on 2009-07-29
Have you installed the msttcorefonts package yet?

If not, open a terminal, Applications > Accessories > Terminal  and run:

```
sudo apt-get install msttcorefonts
```

---

### Post by Hoom@n on 2009-07-29
> **gn2 said:**
> Have you installed the msttcorefonts package yet?

If not, open a terminal, Applications > Accessories > Terminal  and run:

```
sudo apt-get install msttcorefonts
```
Thanks a lot! Web-pages are now look like what they really are!
But,
1-What was that package? [any useful info, please]
2-I'm not sure, but I think fonts are not clear and they don't have a sharp edge. Can I solve that?(it's not a new problem and I had it even before installing this package with old fonts-I'm using Ubuntu on my laptop)

---

### Post by ssdt on 2009-07-29
You can check out this link to see what it is: [http://ubuntuforums.org/showthread.php?t=585292]("http://ubuntuforums.org/showthread.php?t=585292")

---

### Post by Hoom@n on 2009-07-29
> **ssdt said:**
> You can check out this link to see what it is: [http://ubuntuforums.org/showthread.php?t=585292]("http://ubuntuforums.org/showthread.php?t=585292")
Thanks. But what to do to have fonts with sharp edges?

---

### Post by CatKiller on 2009-07-29
> **Hoom@n said:**
> I'm using Ubuntu on my laptop

System &#8594; Preferences &#8594; Appearance &#8594; Fonts &#8594; Details.

Set the subpixel order to match the alignment of the cells on your screen and set hinting and smoothing to what looks best to you on that screen.

---

### Post by Hoom@n on 2009-07-30
> **CatKiller said:**
> System &#8594; Preferences &#8594; Appearance &#8594; Fonts &#8594; Details.

Set the subpixel order to match the alignment of the cells on your screen and set hinting and smoothing to what looks best to you on that screen.
Thanks. I'll try it soon.

---

### Post by Hoom@n on 2009-07-30
> **Hoom@n said:**
> Thanks a lot! Web-pages are now look like what they really are!
**Oops! I was wrong! Just some of web-pages are like their real look. A lot of others are not.[even some of web-pages which was OK before installing that are now changed into a bad look]**

---

### Post by emeraldgirl08 on 2009-07-30
Hoom. Tell me what resolution your screen is set at?

---

### Post by emeraldgirl08 on 2009-07-30
My resolution is set for 1024X768. Don't know if yours is but the fonts and sizes are the key to the appearance you want. Also be sure to uncheck the box for pages picking the fonts they want to use.

**EDIT:** These are my settings so your solution may be to just uncheck the box. Don't want to screw up your settings! And if you change settings write your original settings down!

Open up Firefox.

Edit>>Preferences>>Fonts and Colors- Choose DejaVu Sans 14>>

Then go into the advanced.

Fonts for: Western

Proportional: Serif         Size: 14
Serif: DejaVu Sans 
Sans-serif: DejaVu Serif
Monospace: monospace        Size: 11
                     
              Minimum font size: 11

Uncheck the "allow pages to choose their own fonts, instead of my selections above.

Character Encoding: Western (ISO-8859-1)

---

### Post by Hoom@n on 2009-07-31
> **emeraldgirl08 said:**
> My resolution is set for 1024X768. Don't know if yours is but the fonts and sizes are the key to the appearance you want. Also be sure to uncheck the box for pages picking the fonts they want to use.

**EDIT:** These are my settings so your solution may be to just uncheck the box. Don't want to screw up your settings! And if you change settings write your original settings down!

Open up Firefox.

Edit>>Preferences>>Fonts and Colors- Choose DejaVu Sans 14>>

Then go into the advanced.

Fonts for: Western

Proportional: Serif         Size: 14
Serif: DejaVu Sans 
Sans-serif: DejaVu Serif
Monospace: monospace        Size: 11
                     
              Minimum font size: 11

Uncheck the "allow pages to choose their own fonts, instead of my selections above.

Character Encoding: Western (ISO-8859-1)
Thanks a lot. I'll take a look at ff settings in Windows asap and then decide what to do. I'll tell the result here.

---

