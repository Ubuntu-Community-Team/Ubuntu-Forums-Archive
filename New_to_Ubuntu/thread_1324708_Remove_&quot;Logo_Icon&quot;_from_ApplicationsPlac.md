---
title: "Remove &quot;Logo Icon&quot; from Applications/Places/System Menu"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-12
Just wondering if I can remove this icon, not replace it with something transparent, as I want to place the window list icon to where this icon normally goes. I want to remove the icon and the space that icon takes up.

---

### Post by coldReactive on 2009-11-12
bump, it's really annoying that I can't REMOVE the icon AND the space that the icon takes up!

I'll be bumping this until I get a response, even if that takes forever.

Yes, I've searched google, no, I'm not looking to REPLACE the icon with a transparent PNG, because then I'll have a big blank space between the menus and the window list applet!

Yes, I've already searched the forums (through google even.) Most people want to change the icon, make the icon appear again when it's disappeared, or just remove the arrow. But I want to remove the icon AND the space the icon normally makes.

---

### Post by coldReactive on 2009-11-12
Also see this for why I ain't using gnome2-globalmenu:

[http://ubuntuforums.org/showthread.php?t=1324792](http://ubuntuforums.org/showthread.php?t=1324792)

---

### Post by coldReactive on 2009-11-12
bump

---

### Post by coldReactive on 2009-11-13
bump

---

### Post by coldReactive on 2009-11-13
bump

---

### Post by falconindy on 2009-11-13
Find out the name of the theme you're using (dig around /usr/share/themes) and then make the following 1x24 .png in your home directory:

$HOME/.icons/<theme-name>/24x24/places/start-here.png

After logging out and back in, it will override the icon on the main menu.

---

### Post by coldReactive on 2009-11-13
> **falconindy said:**
> Find out the name of the theme you're using (dig around /usr/share/themes) and then make the following 1x24 .png in your home directory:

$HOME/.icons/<theme-name>/24x24/places/start-here.png

After logging out and back in, it will override the icon on the main menu.

What if it's the default humanity theme? :|

---

### Post by SunnyRabbiera on 2009-11-13
Actually I dont think its entirely plausible to remove the icon
There is just no way to do it to my knowledge, sorry.

---

### Post by falconindy on 2009-11-13
My 10.04 VM has a theme called "Human". It might also be Human-Clearlooks. Worst case scenario, make a bunch of trees (for multiple themes) and use a single start-here.png with several symlinks.

---

### Post by coldReactive on 2009-11-13
> **SunnyRabbiera said:**
> Actually I dont think its entirely plausible to remove the icon
There is just no way to do it to my knowledge, sorry.

I'm sorry, but I can remove the arrow completely system wide, so I'm sure there is a way to remove the icon fully system wide. So I won't believe that.

---

### Post by falconindy on 2009-11-13
> **SunnyRabbiera said:**
> Actually I dont think its entirely plausible to remove the icon
There is just no way to do it to my knowledge, sorry.
I **just** confirmed that my method works. The icon won't be stretched back to 24x24 size.

---

### Post by coldReactive on 2009-11-13
> **falconindy said:**
> I **just** confirmed that my method works. The icon won't be stretched back to 24x24 size.

So what about the humanity icons? They're all svgs.

---

### Post by falconindy on 2009-11-13
> **coldReactive said:**
> So what about the humanity icons? They're all svgs.

You found a start-here.svg? Uggh... lemme get my VM back up.

edit: Wow, that **would** happen... Directory structure has changed markedly too. Shouldn't be a problem to fire up Inkscape and make a 1x24 blank svg.

---

### Post by coldReactive on 2009-11-13
> **falconindy said:**
> You found a start-here.svg? Uggh... lemme get my VM back up.

edit: Wow, that **would** happen... Directory structure has changed markedly too. Shouldn't be a problem to fire up Inkscape and make a 1x24 blank svg.

Or open a 1x24 PNG in inkscape, then save it as a 1x24 inkscape svg.

Also, the width of the menu bar still annoys me, notice how there's a blank space?

[img]http://i35.tinypic.com/14y4hh2.png[/img]

Better than nothing I suppose.

---

### Post by durand on 2009-11-13
Do you mean the height of the menu bar? Because you can change that by right clicking on it.

---

### Post by Simian Man on 2009-11-13
If you want to minimize wasted screen space, why not add the "Main Menu", as opposed to "Menu Bar", to your panel instead?  This is just the start-here logo with Applications, Places and System under that.

---

### Post by coldReactive on 2009-11-13
> **Simian Man said:**
> If you want to minimize wasted screen space, why not add the "Main Menu", as opposed to "Menu Bar", to your panel instead?  This is just the start-here logo with Applications, Places and System under that.

What I'd really like is global menu actually. But integrated with the main menu.

---

### Post by wojox on 2009-11-13
Is that top panel seriously that big?

---

### Post by coldReactive on 2009-11-13
> **wojox said:**
> Is that top panel seriously that big?

No, it's just blown up with gimp so you can see it better. :|

I wish global menu would compile.

---

### Post by stevenswall on 2011-09-11
Better late than never...

The System Monitor Applet can be increased in width to push the menu icon underneath the Window Selector Applet if it is placed on the far left, see the screenshot for details. (Ubuntu 10.10)

[[IMG]http://www.mediafire.com/imgbnc.php/566519139b27606b6b7dc52e33072826799a5645b1cf0343b5c02b92325ecc302g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=qm6nmbp7qzi7657&thumb=5)

---

