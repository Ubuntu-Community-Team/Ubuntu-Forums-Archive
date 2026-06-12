---
title: "Windows fonts not displaying in Firefox"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by jaguax on 2009-03-14
I installed the Windows core fonts and double checked that they are in the fonts folder, yet all of the web pages I go to are still using the Linux fonts which makes them look weird. Any ideas on how to get Firefox to use the Windows fonts?

---

### Post by martrn on 2009-03-14
Whats a windows font ?

Edit --> Preferences -->  Content(Tab)

Scroll to "Fonts/Colours 
Click on Advanced

and change the fonts around.

Whats a windows font ?

---

### Post by jaguax on 2009-03-14
A Windows font is a font from Windows, heh. Like Arial, Times New Roman, Verdana, etc... Most web pages on the internet use these fonts.

The font to be displayed on a web page is specified in the html or css, so if it says Verdana for example then it should use the Verdana font, but in Ubuntu the web pages are being displayed in Linux fonts. It just doesn't look right.

---

### Post by Kareeser on 2009-03-14
sudo apt-get install msttcorefonts

---

### Post by martrn on 2009-03-14
> **Kareeser said:**
> sudo apt-get install msttcorefonts

Don't forget to re-generate the font cache :

```
sudo fc-cache -fv
```

Then from firefox menu select :
Edit --> Preferences --> Content(Tab)
Scroll to "Fonts/Colours
Click on Advanced
Then select the fonts you want.

---

### Post by jaguax on 2009-03-14
> **martrn said:**
> Don't forget to re-generate the font cache :

```
sudo fc-cache -fv
```

Then from firefox menu select :
Edit --> Preferences --> Content(Tab)
Scroll to "Fonts/Colours
Click on Advanced
Then select the fonts you want.

I already did all of that. The pages are still not displaying the fonts that they're supposed to. :(

---

