---
title: "Transfering Windows Fonts, is is possible?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2009-04-24
Is there anyway to transfer the Windows fonts to my Ubuntu Machine?  Or maybe I don't know how to set up properly.

I notice in OpenOffice that there is no font called Arial or Times New Roman.  I found out that if I type the font name in then it does change to the specified font.  One issue I have is with PDFs.  If the PDF can't find the font it was created with, it picks a similar font.  If I open that PDF on a windows machine, the font is fine...

Thanks in Advance

---

### Post by robertc36 on 2009-04-24
There you go check this site [http://appnr.com/?search=fonts](http://appnr.com/?search=fonts)

---

### Post by crjackson on 2009-04-24
> **J0hnnyBr@v0 said:**
> Is there anyway to transfer the Windows fonts to my Ubuntu Machine?  Or maybe I don't know how to set up properly.

I notice in OpenOffice that there is no font called Arial or Times New Roman.  I found out that if I type the font name in then it does change to the specified font.  One issue I have is with PDFs.  If the PDF can't find the font it was created with, it picks a similar font.  If I open that PDF on a windows machine, the font is fine...

Thanks in Advance

```
sudo apt-get install ubuntu-restricted-extras
```

This installs many needed things with one of the being msttcore fonts (microsoft truetype fonts).

---

### Post by Didius Falco on 2009-04-24
In Synaptic,search for "msttcorefonts" and you'll get a package of fonts from Microsoft. That should take care of most of what you are after.

If you search Synaptic for "fontypython", you'll find a TTF manager that you may find useful.

Finally,

here is a guide to manually installing TT fonts:

[http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/](http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/)

Have font! ;)

---

### Post by ugriffin on 2009-04-24
It's quite simple.

Go to your C drive>Windows>Fonts> and copy-paste these fonts to a new folder you will create. I suggest you place it on your home folder on a folder named .fonts: this way the folder with your fonts shall remain invisible and trouble you no more. Paste the fonts to wherever you choose it to be (wether on my advice or somewhere else). Now, once the fonts are transferred, right click and select "install fonts".


Have fun.

---

### Post by J0hnnyBr@v0 on 2009-04-24
Thanks to everyone who posted here...worked like a charm!!

The PDF I created was done in Office 2007 last year with Cambria as the font...or something similar...that did not install, but I see all the old familiars!

Thanks Again,
Eric

---

### Post by crjackson on 2009-04-24
> **J0hnnyBr@v0 said:**
> Thanks to everyone who posted here...worked like a charm!!

The PDF I created was done in Office 2007 last year with Cambria as the font...or something similar...that did not install, but I see all the old familiars!

Thanks Again,
Eric


Go to my blog and get instructions on that font, it's pretty easy..

[http://buck-nasty.blogspot.com/2009/02/install-vista-fonts-on-ubuntu.html](http://buck-nasty.blogspot.com/2009/02/install-vista-fonts-on-ubuntu.html)

---

### Post by loobyloo on 2009-04-27
> **crjackson said:**
> Go to my blog and get instructions on that font, it's pretty easy..

[http://buck-nasty.blogspot.com/2009/02/install-vista-fonts-on-ubuntu.html](http://buck-nasty.blogspot.com/2009/02/install-vista-fonts-on-ubuntu.html)

Wow...thanks for the bit about updating the cache. It started spilling out tons of stuff!

---

