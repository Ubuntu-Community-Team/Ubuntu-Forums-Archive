---
title: "Microsoft Fonts in Firefox"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Souljah on 2009-01-31
Hi,

I'm sorry if this is the wrong place for it. I've been wanting to get the fonts tahoma or verdana in firefox but using the ones provided by firefox aren't that great. Maybe I can download the free versions of these fonts somewhere? How do I get them to show up on firefox? Some help would be greatly appreciated. Thanks a lot.

Ryan

---

### Post by SqRt7744 on 2009-01-31
if you open a terminal window (Applications->Accessories->Terminal) and enter:
sudo apt-get install msttcorefonts

...i think you will then have the fonts you are looking for...
good luck.

---

### Post by Souljah on 2009-01-31
> **SqRt7744 said:**
> if you open a terminal window (Applications->Accessories->Terminal) and enter:
sudo apt-get install msttcorefonts

...i think you will then have the fonts you are looking for...
good luck.
Right. That has been installed. However, can only change the appearance of the fonts on the desktop and apps, Can't see the fonts appear inside firefox.

---

### Post by steveneddy on 2009-01-31
In Firefox:

Edit --> Preferences --> Content Tab

Go down and select the font you would like to use.

Close when finished.

---

### Post by tturrisi on 2009-01-31
AFAIK, Tahoma is not included in the msttcorefonts package. You need to manually install the Tahoma font.  It was added at one point, but the the bold tahoma was not included.  And the package had bugs.  It may now be included again.

However, this is the best way to get the tahoma (or other ttf fonts) installed:
[http://warren.guy.net.au/docs/ubuntu-font-configuration.html](http://warren.guy.net.au/docs/ubuntu-font-configuration.html)

---

### Post by Souljah on 2009-01-31
Managed to get the font Verdana in firefox. However, it seems to only appear if I were to select that font in the desktop environment. Regardless, it's all right. I'll experiment and stuff. Topic can be closed.

---

### Post by steveneddy on 2009-02-01
Glad you figured it out.

I actually just copy a .ttf from a Windows machine that I want to use and put it in my [COLOR=Red]**.fonts**[/COLOR] folder.

---

### Post by Souljah on 2009-02-01
That might be a good idea. I think I will try that, but just one question. Where is the .fonts folder located?

---

### Post by wangsuda on 2009-02-01
> **julian5 said:**
> you can download fonts from a lot of websites (just google it) and then put the downloaded .ttf files into /usr/share/fonts/truetype
It’s simple:
1: Open Applications / Accesories / Console
2: sudo cp Desktop/downld_fnts/*.ttf /usr/share/fonts/truetype
3: Ready

I copied my font folder from windows, however it is not letting me paste the font folder or the fonts into the folder. Any suggestions?

---

### Post by pritamps on 2009-02-01
> **wangsuda said:**
> I copied my font folder from windows, however it is not letting me paste the font folder or the fonts into the folder. Any suggestions?

It might be a permissions problems. Copy the fonts using sudo.

---

### Post by wangsuda on 2009-02-01
> **pritamps said:**
> It might be a permissions problems. Copy the fonts using sudo.

How would the code look for that one?

---

### Post by PriceChild on 2009-02-02
*thread moved*

---

