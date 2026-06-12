---
title: "Awesome Customisations"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-10
What themes? customisations? icons? are in use in the attachments? I don't remember where I got the pictures from, just saved them to disk some time ago when I saw them.

Also 2 other questions:

1) What's the easiest way to replace the default ubuntu menu icon? the gconf method is too round about to easily tell people and doesn't always work. Ubuntu tweak offered an easy way but it did not work for me in 8.10 and does not anymore in 9.04 either. Does it work for anyone here? Maybe I need a newer version of ubuntu tweak.
The customised icon should be 24x24 and .png right? What if the panel is smaller/bigger? Does the file need to be adjusted as well?

2) Where can I find cairo themes made by various people? I looked through the cairo thread. You can export themes from cairo (its not as easy as compiz profile exporting but can be done by extracting from config/cairo-dock/themes manually).
 
3) Is there a better dock available? I've tried Cairo, AWN, Kiba, Simdock and the gdesklets dock but to be honest they are all a pain to configure and/or not nearly as good as the windows third party and mac docs. Something like Rocketdock or Objectdock for windows would be awesome. Only Cairo comes close but is an absoluter nightmare to configure, slighlty buggy and is not at all smooth (tried on multiple comps, video cards)

Thanks you very much for your help

---

### Post by spiderbatdad on 2009-05-10
IDK but would love to find the theme in first screenshot. It looks more like a custom icon theme and even some nautilus scripts than any gtk theme.

---

### Post by gjoellee on 2009-05-10
Please notice that those pictures are mockups. There is however a theme that is quite similar to mockup 2 and 3. Here: [http://www.gnome-look.org/content/show.php/willibex?content=86844](http://www.gnome-look.org/content/show.php/willibex?content=86844)

---

### Post by Temposs on 2009-05-10
Another dock you didn't mention is the Docky theme for Gnome-Do. I'm using it now. Try it out :-)

---

### Post by spiderbatdad on 2009-05-10
mostly i was impressed with the folder icons...found jungle dark at gnome look. They're pretty cool. [http://www.gnome-look.org/content/show.php/Jungle+Green%2BBlack%2BOrange%2BPortable?content=82403](http://www.gnome-look.org/content/show.php/Jungle+Green%2BBlack%2BOrange%2BPortable?content=82403)

---

### Post by Andy06 on 2009-05-10
Any ideas on how to change the menu icon?

---

### Post by ninjapirate89 on 2009-05-10
> **Temposs said:**
> Another dock you didn't mention is the Docky theme for Gnome-Do. I'm using it now. Try it out :-)

I second Docky. It is very good and hasn't ever given me any trouble. The only downside is it isn't very customizable.

---

### Post by spiderbatdad on 2009-05-10
> **Andy06 said:**
> Any ideas on how to change the menu icon?

well the gconf method seems easier than the way this was done in the past, by locating and replacing the icon in...i think /usr/share/icons/human/
You can also do something like putting the .png in /scalable/places/distributor-logo.png inside the directory ~/.icons/<theme>/

---

### Post by Andy06 on 2009-05-11
Lol if I tell that to anyone over the phone, they'll probably have a heart attack. 
That's the way I've done it for myself. But I'm looking for a easier way to tell others how to do it. The simplest was the ubuntu tweak GUI method which was as simple as selecting the custom icon and selecting "open". However that does not seem to work any more.

How I wish they include an easier way to do this in 9.10.......

---

### Post by Andy06 on 2009-05-11
I changed by menu through gconf some months ago, just to confirm this is the way right:

apps>panel>objects, then locate the menu object, whichever number it is, then check use_custom_icon, then fill in the path in the custom icon field.

Still the same? anything easier?

---

