---
title: "Question about theme"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-20
Hi,
I was at the shops yesterday and I quickly flicked through a linux magazine.

It showed the gnome shell but the panel at the top was transparent?

I was wondering how the heck this would have been done?

I know you can use emerald for transparent Window borders, but the panel?

How did they do that?

---

### Post by mcduck on 2009-03-20
For a simple transparent panel you can just right-click the panel, select "Properties" and on the Background-tab select "Solid Color" and adjust the color & transparency as you wish. 

If you want more complex graphics, you can use pretty much any picture as the panel background. Transparency works at least with both .PNG and .SVG images so you can get nice glass-looking panels or panels with both transparent and opaque areas.

If you make the picture exactly the same size your panel is you can also create more details in the panel, like rounded corners and details for different applets you have in your panel.

You can also find ready-made panel backgrounds from these forums, the web, and specifically from [http://gnome-look.org/]("http://gnome-look.org/").

---

### Post by Gp. on 2009-03-20
On the menu at gnome-look, what sub category do I choose to find panel backgrounds?

---

### Post by mcduck on 2009-03-20
Most likely the "Other"-category, but I recommend just using the search instead.

---

### Post by Gp. on 2009-03-20
And how do I make the font colour different for the panel?
Say if I choose black as a solid colour or have a black background,how can I make the text white?

---

### Post by billgoldberg on 2009-03-20
> **Gp. said:**
> Hi,
I was at the shops yesterday and I quickly flicked through a linux magazine.

It showed the gnome shell but the panel at the top was transparent?

I was wondering how the heck this would have been done?

I know you can use emerald for transparent Window borders, but the panel?

How did they do that?

I wrote a little how-to on that

[http://linuxowns.wordpress.com/2008/03/10/transparent-panel/](http://linuxowns.wordpress.com/2008/03/10/transparent-panel/)

Opacity setting in compiz fusion now has it's own little section.

---

### Post by mcduck on 2009-03-23
> **Gp. said:**
> And how do I make the font colour different for the panel?
Say if I choose black as a solid colour or have a black background,how can I make the text white?

You can create a file called ".gtkrc-2.0" in your home directory, and then add following code to that file:
```

style "panelapplet"
{
  fg[NORMAL] = "#ffffff"
}
widget "*PanelWidget*" style "panelapplet"
widget "*PanelApplet*" style "panelapplet"
widget ".clock-applet-button.*" style "panelapplet"

```
When done, save the file and log out & back again. Text in your panels should now be white.. :)

Edit: Using Compiz for panel transparency gives you real transparency while panel's own transparency setting and background images only show your wallpaper through the panel. However, Compiz makes everything in the panel transparent, meaning that all your icons and text will become transparent as well.. Also if you want partial transparency or nice glass effects Compiz won't be any use.

---

### Post by Gp. on 2009-03-23
I tried doing it with compiz. It didn't seem to change the panel at all.

---

### Post by cmcesq on 2009-03-29
Hello mates!  I must confess I'm a complete newbie to Ubuntu/Linux but I'm trying to learn this after decades of DOS/Windows.

Yet I'm having way too much trouble with what I assume should be something pretty easy: installing a theme.

I've d/l several GDM themes from GNOME-look.org and not a single one has worked.  I think I understand that GDM is the login screen, so is that why it's not working (cuz I'm trying to utilize it as a desktop theme)?

If so, then what type of theme do I want?

---

