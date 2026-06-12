---
title: "Theme text areas?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Syndacate on 2008-12-26
Hey,

Is there an option to edit settings in themes for text areas?

I like dark themes a lot - but with dark themes come these dark *** text areas and some (most) of the time I get this black text on black background type stuff.  Where in the themes would it be to change the text areas & text font colors to their defaults?

8.10
metaciy/gnome

---

### Post by adobrakic on 2008-12-26
I know exactly what you mean, since I only use dark themes. 
What I usually do is when I install a theme via Appearance, I customize the theme right after applying it. 

I click on Customize (third from left), and go to 'Colo(u)rs', and in Input Boxes, I change that to white.

I hope this is what you're looking for.

Peace!

---

### Post by Syndacate on 2008-12-26
> **adobrakic said:**
> I know exactly what you mean, since I only use dark themes. 
What I usually do is when I install a theme via Appearance, I customize the theme right after applying it. 

I click on Customize (third from left), and go to 'Colo(u)rs', and in Input Boxes, I change that to white.

I hope this is what you're looking for.

Peace!

Alright, my lappy is copying a bunch of files so is stuck in OS X - I'll give that a whirl when it completes and let you know how I make out.

- Dark themes rules
- Dark text areas suck :-P.

Sometimes it's nice to use white text on black background - but when you're programming, and it starts all the syntax highlighting, I'd just wish it was regular, lol.

Thx.

---

### Post by Syndacate on 2008-12-28
Blah.

Anymore suggestions?

That doesn't work, ALL the options in the colors tab are whited out (un-editable) and at the top there's a lightbulb that says "*The current control theme does not support color schemes.*"

Anybody have any other suggestions, or a suggestion of a dark theme which does "support color schemes?" so I can change it to white.

I really love dark themes, but I **NEED** my text boxes to be default colors because I need to see the syntax highlighting (and the text for that matter) for my programming stuff.

Any help would be greatly appreciated - I'm kinda pushed for time as I go back to school Jan 4th and need all my IDE's and Text Editors working flawlessly by then.  I mean if worse comes to worse I can always select a lighter theme, but since I have bad eyes, that really kills me (eyes hurt, then tired, then headache, it's a bitch).

TIA!!!!!!

---

### Post by appi2012 on 2008-12-28
That means the author of the theme you're using coded the theme such that it is not editable. However, if you find the gtkrc file that corresponds to the theme, you should be able to change this. If you have time, then this is what you should do:

Open the gtkrc file in gedit by pressing Alt+f2, and typing:
```
gedit /home/[username]/.themes/[ThemeName]/gtk-2.0/gtkrc
```

Near the top of the file, there should be an section like this:
```
	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = @fg_color
	fg[INSENSITIVE]   = darker (@bg_color)

	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.02, @bg_color)
	bg[SELECTED]	  = @selected_bg_color
	bg[INSENSITIVE]   = @bg_color
	bg[ACTIVE]        = shade (0.9, @bg_color)

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (0.95, @bg_color)
	base[ACTIVE]      = shade (0.9, @selected_bg_color)
	base[SELECTED]    = @selected_bg_color
	base[INSENSITIVE] = @bg_color

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = @text_color
	text[ACTIVE]      = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)
```
But in your case, instead of the @textcolor or whatever, it would be a fixed color, like #020202. Find the base[NORMAL] line, and change it so that it is equal to '#FFFFFF' or choose whatever hex code you like (That's light).

Then save the file, and close it. Now, go to Appearance and change the theme to another one, and then change it back. That should fix the text areas! Hope that helps!

---

### Post by I wanted to leave on 2008-12-28
Ubuntu Dust GTK and Firefox themes...

[https://wiki.ubuntu.com/Artwork/Incoming/DustTheme?action=show&redirect=Artwork%2FIncoming%2FIntrepid%2FDustTheme](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme?action=show&redirect=Artwork%2FIncoming%2FIntrepid%2FDustTheme)

---

### Post by guitarzan on 2008-12-28
You could try 'Slickness Black,' that's one of my favorite dark themes. It supports color schemes.
[http://gnome-look.org/content/show.php/Slickness+Black?content=73210](http://gnome-look.org/content/show.php/Slickness+Black?content=73210)

You might also try Dust, that's my all-time favorite but not entirely dark.
[https://wiki.ubuntu.com/Artwork/Incoming/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme)

Hope I helped!

---

### Post by Syndacate on 2008-12-30
> **appi2012 said:**
> That means the author of the theme you're using coded the theme such that it is not editable. However, if you find the gtkrc file that corresponds to the theme, you should be able to change this. If you have time, then this is what you should do:

Open the gtkrc file in gedit by pressing Alt+f2, and typing:
```
gedit /home/[username]/.themes/[ThemeName]/gtk-2.0/gtkrc
```

Near the top of the file, there should be an section like this:
```
	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = @fg_color
	fg[INSENSITIVE]   = darker (@bg_color)

	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.02, @bg_color)
	bg[SELECTED]	  = @selected_bg_color
	bg[INSENSITIVE]   = @bg_color
	bg[ACTIVE]        = shade (0.9, @bg_color)

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (0.95, @bg_color)
	base[ACTIVE]      = shade (0.9, @selected_bg_color)
	base[SELECTED]    = @selected_bg_color
	base[INSENSITIVE] = @bg_color

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = @text_color
	text[ACTIVE]      = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)
```
But in your case, instead of the @textcolor or whatever, it would be a fixed color, like #020202. Find the base[NORMAL] line, and change it so that it is equal to '#FFFFFF' or choose whatever hex code you like (That's light).

Then save the file, and close it. Now, go to Appearance and change the theme to another one, and then change it back. That should fix the text areas! Hope that helps!

Hey, thanks, that almost fixed the problem - it allows me to type, anyway, but I killed some other stuff in the process.

Is there a place that shows an example of what each of those is?  Because Blindly editing them is causing problems, although I did get black on white background, I have some other things plaguing me, like black text on black background for the side bar, or white on white for editing text.

So I'd really need to find an explanation on which each of those options specifically does.

I googled the hell out of it to no avail.  This is def. where I want to be looking though, so thanks for the direction.  Any help on where to find an explanation would be greatly appreciated.

PS:  Not for the whole thing (although that would rock), just the 4 blocks that you showed me.  I'm sure somebody had to write something up.

---

### Post by appi2012 on 2009-01-04
There is an application called TheUnofficialWidgetFactory that you could install which would show you what all the widgets in the theme would look like.

The website is:
[http://gnome-look.org/content/show.php/The+Unofficial+Widget+Factory+(DEB)?content=84209](http://gnome-look.org/content/show.php/The+Unofficial+Widget+Factory+(DEB)?content=84209)

Also, could you attach your gtkrc file so I could look at it and see what the problem is.

Or, you could take the easy way out and install another theme.

---

### Post by Syndacate on 2009-01-06
I'll take a look at that link, but probably choose the latter, easier method.

Thanks for all your help.

---

