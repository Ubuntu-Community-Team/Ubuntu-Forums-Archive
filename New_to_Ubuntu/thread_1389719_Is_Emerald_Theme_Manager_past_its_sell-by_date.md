---
title: "Is Emerald Theme Manager past its sell-by date?"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-01-24
I've got Emerald installed, and I set it up somehow long in the distant past, but I heard that it hasn't had any development for yonks.

I see that its website still refers to Beryl, which I think has now gone bye-bye, having been taken over by Compiz.

So, if I want to keep my system modern, I'd quite like to get rid of Emerald and replace it with something that's a bit more integrated into Gnome/Compiz.

Any suggestions?

---

### Post by lidex on 2010-01-24
> Is Emerald Theme Manager past its sell-by date?
My answer is no, at least for me. You can always fall back to ubuntu's default, Metacity/GTK Window Decorator. 

Info here:
[http://wiki.compiz.org/Plugins/Decoration]("http://wiki.compiz.org/Plugins/Decoration")

Compiz Themes:
[http://compiz-themes.org/]("http://compiz-themes.org/")

BTW: Nice avatar? ;-)

---

### Post by ikt on 2010-01-24
> **Roger Allott said:**
> So, if I want to keep my system modern, I'd quite like to get rid of Emerald and replace it with something that's a bit more integrated into Gnome/Compiz.

Any suggestions?

There are quite a few theme's that do not rely on emerald.

Some good ones are listed here:

[http://www.omgubuntu.co.uk/search/label/themes](http://www.omgubuntu.co.uk/search/label/themes)

---

### Post by Roger Allott on 2010-01-25
> **lidex said:**
> You can always fall back to ubuntu's default, Metacity/GTK Window Decorator. 

Info here:
[http://wiki.compiz.org/Plugins/Decoration]("http://wiki.compiz.org/Plugins/Decoration")

Compiz Themes:
[http://compiz-themes.org/]("http://compiz-themes.org/")
Thanks. If I simply uninstall Emerald via Synaptic, will Metacity simply become my Window Decorator?

How do I launch Metacity?

> **lidex said:**
> BTW: Nice avatar? ;-)
Greta Scacchi. She was particularly stunning in White Mischief.

---

### Post by lidex on 2010-01-25
> Thanks. If I simply uninstall Emerald via Synaptic, will Metacity simply become my Window Decorator?

I believe so.

> How do I launch Metacity?

In a terminal:
```
metacity --replace
```

I would go into CompizConfig Settings Manager and under "Window Decoration" clear the "Command" field.

---

### Post by Roger Allott on 2010-01-25
OK. So I've uninstalled Emerald through Synaptic, but something odd happens when I run:
> **lidex said:**
> 
In a terminal:
```
metacity --replace
```
After entering that, the Terminal hangs, all window decoration disappears, and I can't close any apps. I can reboot, after which I'm back to a slightly revised version of my set-up, without the colour on the top border that Emerald had in its settings.

If I enter:
```
metacity
```
I get the following response:
```
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```


[QUOTE=lidex;8723103]I would go into CompizConfig Settings Manager and under "Window Decoration" clear the "Command" field.
At the moment, that field has "/usr/bin/compiz-decorator" in it. Are you saying that should be blank? If so, could you please explain why?

---

### Post by nishant.singh28 on 2010-01-25
Install Compiz Fusion Icon. Run it. Right Click on it in System Tray and select Window Manager as Metacity

---

### Post by Roger Allott on 2010-01-25
> **nishant.singh28 said:**
> Install Compiz Fusion Icon. Run it. Right Click on it in System Tray and select Window Manager as Metacity

Thanks. That's useful. But it leaves me with the question of whether I want Metacity as my Window Manager, because when I select it, I lose my cube!

Another question arises though about my Compiz Options. The Fusion Icon has 2 options - Loose Bindings and Indirect Rendering. What do they mean?

---

### Post by lidex on 2010-01-25
> **Roger Allott said:**
> OK. So I've uninstalled Emerald through Synaptic, but something odd happens when I run:
[QUOTE=lidex;8723103]
In a terminal:
```
metacity --replace
```
After entering that, the Terminal hangs, all window decoration disappears, and I can't close any apps. I can reboot, after which I'm back to a slightly revised version of my set-up, without the colour on the top border that Emerald had in its settings.

If I enter:
```
metacity
```
I get the following response:
```
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```



At the moment, that field has "/usr/bin/compiz-decorator" in it. Are you saying that should be blank? If so, could you please explain why?

No. I was looking at mine with emerald in it. You're good. And you don't need to run the previous command as metacity is already running -- it's just used to change to metacity when another is running.

Some more of interest:
[http://wiki.compiz.org/Decorators/GTKWindowDecorator]("http://wiki.compiz.org/Decorators/GTKWindowDecorator")

---

