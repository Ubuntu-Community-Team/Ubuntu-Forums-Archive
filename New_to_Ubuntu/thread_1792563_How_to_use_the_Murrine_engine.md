---
title: "How to use the Murrine engine?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by OkosBokos on 2011-06-28
I've tried to install [this]("http://www.cimitan.com/murrine/node/130") theme, but it doesn't work properly. Here's how it looks:

[http://i56.tinypic.com/1g0mrr.jpg](http://i56.tinypic.com/1g0mrr.jpg)

and here's how it should look:

[http://www.cimitan.com/murrine/files/imagecache/screenshot_full/chrome.png](http://www.cimitan.com/murrine/files/imagecache/screenshot_full/chrome.png)

You can see that the window bar is from the ambiance theme and that the upper panel looks like it's made from two different halves. I used the System > Preferences > Appearance Preferences to activate the theme and Emerald Theme Manager for Chrome.emerald. Now, apart from importing Chrome.emerald into Emerald, I didn't do anything with that. There aren't any "use", "apply" or "OK" buttons so I'm guessing that's that.

I've searched all over the Internet and this forum, but since I've been using Ubuntu for about a month and a half, most of that has been like reading klingon.

---

### Post by Frogs Hair on 2011-06-28
I have installed the theme and doesn't appear to include a window border. You can apply a different window border from Appearance Preferences > Themes > Customize > Window Borders. 

In the screen shot I applied a border from a different theme and an icon set for dark panels .

---

### Post by hhh on 2011-06-28
It's a little tough to know what the exact differences are since the OP's screenshot shows Firefox while Cimi's screenshot shows Gedit and a media player, but here's the thing... as far as I can tell, Cimi isn't using the Emerald theme at all in that screenshot, he's using Compiz's default Cairo decorations. See this link...
[http://wiki.compiz.org/Decorators/GTKWindowDecorator](http://wiki.compiz.org/Decorators/GTKWindowDecorator)

Specifically, note the Cairo screenshot and this part...> The Cairo based window decorator can be enabled by navigating in GConf to /apps/gwd/use_metacity_theme and changing it to FALSE.

And, of course, make sure that Emerald is NOT being started.

Hope that helps.

---

### Post by mcduck on 2011-06-28
Seems to be working the way it's supposed to.

GTK themes have no effect on window borders, that's the window manager's responsibility (using either Metacity or Emerald themes). You said that youy have set an Emerald theme, but have you configured Compiz to use Emerald as it's default decorator? If yes, you might still have to restart Emerald after switching it's theme to see the changes.

What comes to the panel, the theme is probably too old to include actual definitions for indicator-applet background, so they end using normal application background instead. You could ask the theme's author to update the theme, or perhaps try doing it yourself. Either way, panel theming through GTK them has always been more or less problematic thing to do, usually the best approach is to simply remove any panel-related stuff from the GK theme and apply a background image (or color) directly through the panel's settings. Works better and also allows you to use some features that don't work if the image is applied through a GTK theme, like scaling and rotating the image to fit the panel's size and orientation.

---

### Post by hhh on 2011-06-28
> **mcduck said:**
> GTK themes have no effect on window borders...GTK themes affect the color of Window borders when the Cairo window decorator is used. You obviously ignored my first post. Quack.

---

### Post by mcduck on 2011-06-28
> **hhh said:**
> GTK themes affect the color of Window borders when the Cairo window decorator is used. You obviously ignored my first post. Quack.

Well, true about the color thing, and the GTK theme can also affect the color of a Metacity theme (if the Metacity theme is made to work that way).

What I *meant* was that the GTK theme doesn't change how the window borders are styled, as that's defined by the window manager (or decorator if you use Compiz).

How is this relevant to this problem, anyway? The color will be correct as soon as the OP gets the correct theme & decorator to work.

It's also true that the screenshot from Cimi's page looks like it's using the built-in Compiz decorations instead of GWD or Emerald, but the OP said he had installed Emerald theme that's supposed to go with the theme, so I assume that's what he'd like to use.

---

### Post by hhh on 2011-06-28
> **mcduck said:**
> How is this relevant to this problem, anyway?
I was going to post that you're right, it's only relevant if the OP wanted what I *thought* were Cairo decorations... but then I decided to wait till I had a few minutes to actually install the theme. The Emerald theme actually does look like Cimi's screenshot (forgive the transparency, I'm using gtk2-module-rgba)...

[[img]http://s2.postimage.org/1m5h6ggpw/Screenshot_06282011_05_39_45_PM.jpg[/img]](http://s2.postimage.org/55rew9jmb/Screenshot_06282011_05_39_45_PM.png)

> **OkosBokos said:**
> Now, apart from importing Chrome.emerald into Emerald, I didn't do anything with that. There aren't any "use", "apply" or "OK" buttons so I'm guessing that's that.
One more step, under Theme Settings>>Themes (the page the Emerald Theme Manager opens to) scroll through your list of themes to the bottom and click "Chrome".

---

