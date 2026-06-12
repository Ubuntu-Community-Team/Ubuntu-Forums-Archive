---
title: "making clear title bars/etc."
date: 2009-07-06
forum: New to Ubuntu
---

### Post by thomz92 on 2009-07-06
hey

i was wondering if there was any way to make a title bar or menu bars transparent using compiz manager? I want it to look kind of like vista

thanks

---

### Post by CatKiller on 2009-07-06
You'll probably want to use Emerald as your window decorator. There are many many posts on the topic, and many themes available.

---

### Post by thomz92 on 2009-07-06
i dont really understand how this works... if i have emerald as my window decorator, will compiz effects still be there?

---

### Post by DeanoCYM on 2009-07-06
> **thomz92 said:**
> i dont really understand how this works... if i have emerald as my window decorator, will compiz effects still be there?

Yeah compiz fusion works great with emerald.
Install emerald and the themes (you'll need to import themes into emerald).

```
 
sudo apt-get update
sudo apt-get install emerald

```

Then there's lots of themes with transparency for you to mess around with.

Oh yeah almost forgot, you need to run to use emerald as the window decorator.

```
 emerald --replace 
```

hope this works for you!
-Rhys Thomas

---

### Post by CatKiller on 2009-07-06
> **thomz92 said:**
> if i have emerald as my window decorator, will compiz effects still be there?

Absolutely. Compiz is a window manager. It keeps track of the insides of windows. Emerald is a window decorator, which means that it just draws the outside parts - the titlebar, window controls, that sort of thing. You can mix-and-match either of these components to your heart's content.

---

### Post by thomz92 on 2009-07-06
ok thanks. is there anyway i can do that with compiz? (in other words, without installing emerald)

---

### Post by Tibuda on 2009-07-06
> **thomz92 said:**
> ok thanks. is there anyway i can do that with compiz? (in other words, without installing emerald)

Yes, but it is not very noob-friendly.

Open the Gnome configuration editor (Alt+F2, gconf-editor), search for /apps/gwd, and change metacity_theme_opacity and metacity_theme_active_opacity.

---

### Post by Tyke91 on 2009-07-06
even then, you're using metacity to decorate the windows. Compiz doesn't actually draw window decorations by its self. 

just install emerald themes, you will like them ^_^

---

### Post by Yvan300 on 2009-07-06
Follow the instructions here [http://badoh.com/2008/11/howto-give-ubuntu-transparent-menus/](http://badoh.com/2008/11/howto-give-ubuntu-transparent-menus/)

Very strait forward.

---

### Post by thomz92 on 2009-08-03
yvan300 - thank you! is there any way to do the same thing with the title bars of windows?

---

### Post by CatKiller on 2009-08-03
> **thomz92 said:**
> yvan300 - thank you! is there any way to do the same thing with the title bars of windows?

Compiz doesn't draw the title bars. The Window Decorator does that. If you want to have transparent window decorations, then you'll need to use a window decorator that can do it. Like Emerald.

---

### Post by thomz92 on 2009-08-03
gotcha. how about the main bar along the top/bottom of the screen?

---

### Post by theGlitch on 2009-08-03
I made the top and bottom panels of the screen transparent by right clicking them and playing with the preferences.

---

### Post by CatKiller on 2009-08-03
> **thomz92 said:**
> gotcha. how about the main bar along the top/bottom of the screen?

You mean the panels? They have their own built-in transparency, but it's a bit of a hack; they actually draw some of the desktop background as a solid fill. There's probably some way to do it with Compiz, using window-matching the same as the menus, but whenever I tried it it made the applets transparent too. I lost interest fairly quickly, so although there may be an easy way to do it now, I don't know what it is.

---

### Post by thomz92 on 2009-08-03
so theres no "real" transparency for them? (you can move windows under them and see them move through the panel)

---

### Post by CatKiller on 2009-08-03
> **thomz92 said:**
> so theres no "real" transparency for them? (you can move windows under them and see them move through the panel)

Not that I know of, but then I didn't look for long. You aren't likely to have windows beneath the panel anyway.

What would be nice is if it had the same behaviour as gnome-terminal; if you haven't got compositing then that uses the same hack for transparency, but if you do then it uses proper transparency. But it hasn't happened yet, AFAIK.

---

### Post by kayvortex on 2009-08-03
As *CatKiller* says, you can make the panel transparent, but that includes the *whole* thing, applets 'n' all. Still, I have it done combined with GNOME's transparency hack, which enables them to be transparent without loosing any real readability.

Right click on the panel and select *Properties*. Then click on the *Background* tab and check the "Solid Colour" button. Move the bar to adjust the transparency. (Selecting a different colour can also improve readability; so, depending on your background, perhaps change the colour from white to black or vice versa.)

Then, in a terminal type:

```
compizconfig-settings-manager
```

(or just select it from fusion-icon if you have that installed and running. You may also need to apt-get install compizconfig-settings-manager if you don't already have it). Check the box next to "Enable Opacity, Brightness and Saturation", and then click on it itself. Under "Window specific settings" press "New" and enter "type=Dock" and move the bar to a suitable transparency level. That should be it.

---

### Post by Yvan300 on 2009-08-04
Well with the titile bar aka the panel, right click it, click properties, hit the background tab, and click on the style radio button, and adjust the transparency according to how see through you want it to be. 

Now for the window borders, you have to download and configure emerald and change it's settings to show transparency. I am not sure how to do that at the moment. 

Cheers.

---

