---
title: "Have fonts. Now what?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by lile001 on 2009-10-03
I'm noticing there are a whole bunch of fonts on my system that all look the same.  The fonts that come with Ubuntu, by and large, come in three classes:

1.  Fonts indistinguishable from Arial
2. Fonts indistinguishable from Times New Roman
3. Fonts which render fun but unreadable characters such as WINGDINGS. 

There are a few exceptions, but what about the fancy handwriting or Olde English Calligraphy?  

I have a couple of fancy handwriting script TTF files I'd like to add in order to use them in GIMP, maybe in Openoffice as well.  

How do I add fonts in UBUNTU?

---

### Post by halitech on 2009-10-03
there are 2 ways of doing this. you can copy the fonts to /usr/share/fonts or you can create a folder called .fonts (the . in front is important) in your /home folder and place them there. Personally I prefer placing them in ~/.fonts but your choice.

---

### Post by lile001 on 2009-10-03
That's it?  Just copy a .ttf file in there?

---

### Post by halitech on 2009-10-03
yup, just copy to either location you prefer. May need to log out and back in to see them but I havent had to.

---

### Post by Copernicus1234 on 2009-10-03
Also check out the even easier way to install fonts in Ubuntu 9.10 Karmic Koala: [http://www.omgubuntu.co.uk/2009/10/install-font-ubuntu-easy.html]("http://www.omgubuntu.co.uk/2009/10/install-font-ubuntu-easy.html")

Final release in less than a month. :)

---

### Post by Kapitän Rotbart on 2009-10-03
You can refresh fonts after deploying them by using this awesome command: **fc-cache -f -v**.

After dropping your fonts in your ~/.fonts folder, run that command and they're ready to use.

BTW, it is indeed a nice feature in Karmic, but I want to be able to install a bunch of fonts at once, so I'll drop 'em in the ~/.fonts folder and refresh until Ubuntu will let me install many fonts at once via Nautilus, Apps Center or however they plan on doing it.

---

### Post by xe1ufo on 2009-11-30
In Ubuntu 9.10, I simply went to my C:\Windows\fonts folders and double clicked on the ones I wanted in Ubuntu. When the font preview page for each one opens, there is a button on the right that says "Install Font".

In my case, I had a file in OpenOffice.org which needed the Wingdings font. I double-clicked on Wingdings, installed it, then closed and reopened OpenOffice.org and voila!

---

