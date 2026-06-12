---
title: "Firefox Fonts (again)"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Prosis on 2009-03-19
Hello

Here are two screenshots for two websites I visit a lot (matthewgood.org and jlogique.ca).  On Ubuntu, they are absolutely ugly.

Now I've tried all the tricks I could find, Microsoft Fonts, putting the Windows fonts in /usr/share/fonts/truetype for the font cache, setting the fonts in firefox to the same as on Windows, enabling font smoothing in Firefox, modifying firefox configs in about:config, etc. etc. etc.  Nothing does it.

Can anyone help with this?

Thank you

---

### Post by ufuxlinux on 2009-03-19
You can try a few things:

1. In Firefox preferences, choose Arial as a sans-serif font.

2. You can try playing with fontconfig configuration.

   ```
sudo ln -sf /etc/fonts/conf.avail/70-no-bitmaps.conf /etc/fonts/conf.d/70-no-bitmaps.conf
```

You have to logout and login to see the effect of option 2.

---

### Post by Kellemora on 2009-03-19
Hi Prosis

The default is to allow web sites to select their own fonts.
If they don't then they use your default font, which is probably set to serif 12.

I changed mine to serif 16 and it made a world of difference.
I also tried turning off the checkbox to not let them use their own font's, that didn't work out so well.

On one machine with a small monitor, I set the default from serif to ARIAL and that makes the letters look more like the Windows Standard (which is Arial) for web sites that don't provide their own fonts.

Oh, I also set MINIMUM font size from NONE to 12 point.
That made a LOT of things easier to read on these old eyes.

Just go to the web site you read the most, make some changes in the settings and then hit reload to see if you like it that way.
Some setting require a restart of Firefox, but not all of them.

TTUL
Gary

---

### Post by Prosis on 2009-03-19
Already did all those as well :(

So basically the solution is to set Firefox for each most visited website? :(

---

### Post by Prosis on 2009-03-20
Or maybe I should use another browser?

---

### Post by humphreybc on 2009-03-20
This may be of use. I find these font settings work best for Ubuntu and Firefox on LCD screens:

Thanks

---

### Post by philinux on 2009-03-20
On the lcd smoothing setting click the details button and try slight hinting remember to close and restart FF or the effects dont show.

---

### Post by Prosis on 2009-03-20
Thanks for your suggestions.  Unfortunately, no success.

I've noticed something though.  I have Helvetica installed.  The title in the first screenshot that says "Murderers Are Murderers" is supposed to be Helvetica.  Now I wrote that in OpenOffice and set the font to Helvetica and it looks the same as on the Windows screenshot.  So it's like Firefox doesn't see Helvetica or doesn't know that it's Helvetica...

---

### Post by Prosis on 2009-03-20
I,m pretty sure that's the key.  I tried with Firefox 3, Firefox 3.1 Beta, Iceweasel and Chronium and they all use another font than Helvetica...how can I configure the browsers to use it?

Nope it's Helvetica, it's just the way Ubuntu interprets it...

---

### Post by Kellemora on 2009-03-20
Hi Prosis

I'm not going to be much help at all here.
BUT, there is a file on the computer that tells WHAT font's to substitute to another.  Trouble is, I don't remember where or what this file is.  It's been like 6 months since I made the changes to it.

If I recall, Helvetica was one of those substituted to something else.
It shouldn't have if Helvetica was installed, but still did so anyhow.
Seems like we changed it to substitute Helvetica for Helvetica and it fixed it.

I hope someone else knows what file I'm talking about and can direct you to it.

TTUL
Gary

---

### Post by Prosis on 2009-03-20
This rings a bell...I'll have a look.  Thank you :)

---

### Post by Prosis on 2009-03-23
I can't find the file...I modified some files in /etc/fonts but it didn't change anything...does anyone know which file it is?

But, I have modified some files to adjust some things so the second screenshot has been fixed!:D

---

### Post by iBurger on 2009-04-06
I'd like to share some ideas;

General
#######
Setting the DPI in Font Rendering Details matters. (lower it down, if it looks better)

Find out your dpi:

```
xdpyinfo | grep -b1 dot
```


System Fonts
############
The Tahoma font I manually installed from my Windows XP machine, looks really pretty. Better than the one that can be downloaded.


Firefox
#######
about:config

- tweak;
**gfx.use_text_smoothing_setting** to true.


Settings:

[IMG]http://img259.imageshack.us/img259/9746/gnome1.png[/IMG]

[IMG]http://img259.imageshack.us/img259/8547/gnome2.png[/IMG]

[IMG]http://img11.imageshack.us/img11/1225/firefoxfonts.png[/IMG]

Example websites:
[[IMG]http://img135.imageshack.us/img135/7408/screenshotworldbusiness.th.png[/IMG]](http://img135.imageshack.us/my.php?image=screenshotworldbusiness.png)
[[IMG]http://img135.imageshack.us/img135/2694/screenshotubuntuforumsv.th.png[/IMG]](http://img135.imageshack.us/my.php?image=screenshotubuntuforumsv.png)
[[IMG]http://img410.imageshack.us/img410/5162/screenshotcnncombreakin.th.png[/IMG]](http://img410.imageshack.us/my.php?image=screenshotcnncombreakin.png)

---

### Post by iBurger on 2009-04-06
foot note. 

As others have pointed out; setting a minimum font size and disallowing other websites to use their own fonts makes a landmark change.

---

